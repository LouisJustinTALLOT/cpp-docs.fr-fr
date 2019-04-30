---
title: Avertissement du compilateur (niveau 1) C4378
ms.date: 11/04/2016
f1_keywords:
- C4378
helpviewer_keywords:
- C4378
ms.assetid: d08e11ef-891a-4752-9a5e-360e7394acf7
ms.openlocfilehash: 6197bd66214785d515bb1b73ceaf5a68d6751e79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410406"
---
# <a name="compiler-warning-level-1-c4378"></a>Avertissement du compilateur (niveau 1) C4378

Les pointeurs de fonction pour l’exécution des initialiseurs ; envisagez de System::ModuleHandle::ResolveMethodHandle

Sous **/CLR**, symboles d’initialiseurs contiennent des jetons de fonction, pas les pointeurs de fonctions.  Vous devez convertir les jetons à l’aide de pointeurs de <xref:System.ModuleHandle.ResolveMethodHandle%2A>.

## <a name="example"></a>Exemple

L’exemple suivant génère C4378.

```
// C4378.cpp
// compile with: /W1 /clr /c
typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors to call
PF pfx[200];   // ptrs to those dtors, watch for overflow

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() {}
   ~A() {}
};

A aaaa;

#pragma data_seg(".mine$a")
PF InitSegStart = (PF)1;
#pragma data_seg(".mine$z")
PF InitSegEnd = (PF)1;
#pragma data_seg()

void InitializeObjects () {
   PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if (*x)
         (*x)();
}

#pragma init_seg(".mine$m",myexit)   // C4378
A bbbb;   // crash

int main () {
   InitializeObjects();
}
```

## <a name="example"></a>Exemple

L’exemple suivant montre comment résoudre C4378.

```
// C4378_b.cpp
// compile with: /clr
#pragma warning(disable:4378)
using namespace System;
typedef void (__cdecl *PF)(void);
typedef void (__clrcall * CLRPF)(void);

int cxpf = 0;  // number of destructors we need to call
PF pfx[200];   // ptrs to those dtors. Watch out for overflow!

ref class TypeClassHolder {
public:
   static TypeClassHolder ^typeClass = gcnew TypeClassHolder();
};

CLRPF FuncTokenToFuncPtr(PF tknFunc) {
   ModuleHandle type =
      Type::GetTypeFromHandle(Type::GetTypeHandle(TypeClassHolder::typeClass))->Module->ModuleHandle;
   return (CLRPF)type.ResolveMethodHandle((int)(size_t)(tknFunc)).GetFunctionPointer().ToPointer();
}

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() {}
   ~A() {}
};

A aaaa;

#pragma data_seg(".mine$a")
PF InitSegStart = (PF)1;
#pragma data_seg(".mine$z")
PF InitSegEnd = (PF)1;
#pragma data_seg()

void InitializeObjects () {
   PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if(*x) {
         CLRPF realppfunc;
         realppfunc = FuncTokenToFuncPtr(*x);
         (realppfunc)();
      }
}

#pragma init_seg(".mine$m",myexit)
A bbbb; // constructor call succeeds

int main () {
   InitializeObjects();
}
```