---
description: 'En savoir plus sur : erreur du compilateur C2660'
title: Erreur du compilateur C2660
ms.date: 11/04/2016
f1_keywords:
- C2660
helpviewer_keywords:
- C2660
ms.assetid: 2e01a1db-4f00-4df6-a04d-cb6f70a6922b
ms.openlocfilehash: 5490ce80ef410c0ce089e46ddd80aa82785ec3cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136434"
---
# <a name="compiler-error-c2660"></a>Erreur du compilateur C2660

'fonction' : la fonction ne prend pas de paramètres numériques

La fonction est appelée avec un nombre incorrect de paramètres.

C2660 peut se produire si vous appelez accidentellement une fonction API Windows plutôt qu’une fonction membre MFC portant le même nom. Pour résoudre ce problème :

- Ajustez l’appel de fonction pour qu’il soit conforme au format de l’appel de fonction membre.

- Utilisez l’opérateur de résolution de portée ( `::` ) pour indiquer au compilateur de rechercher le nom de la fonction dans l’espace de noms global.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C2660.

```cpp
// C2660.cpp
void func( int, int ) {}

int main() {
   func( 1 );   // C2660 func( int ) not declared
   func( 1, 0 );   // OK
}
```

C2660 peut également se produire si vous tentez d’appeler directement la méthode dispose d’un type managé. Pour plus d’informations, consultez [destructeurs et finaliseurs](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers). L’exemple suivant génère l’C2660.

```cpp
// C2660_a.cpp
// compile with: /clr
using namespace System;
using namespace System::Threading;

void CheckStatus( Object^ stateInfo ) {}

int main() {
   ManualResetEvent^ event = gcnew ManualResetEvent( false );
   TimerCallback^ timerDelegate = gcnew TimerCallback( &CheckStatus );
   Timer^ stateTimer = gcnew Timer( timerDelegate, event, 1000, 250 );

   stateTimer->Dispose();   // C2660
   stateTimer->~Timer();   // OK
}
```

C2660 se produit si une classe dérivée masque une fonction.

```cpp
// C2660b.cpp
// C2660 expected
#include <stdio.h>

class f {
public:
   void bar() {
      printf_s("in f::bar\n");
    }
};

class f2 : public f {
public:
   void bar(int i){printf("in f2::bar\n");}
   // Uncomment the following line to resolve.
   // using f::bar;   // - using declaration added
   // or
   // void bar(){__super::bar();}
};

int main() {
   f2 fObject;
   fObject.bar();
}
```

C2660 peut se produire si vous appelez une propriété indexée de manière incorrecte.

```cpp
// C2660c.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(1.9) {}
   property double MyProp[] {
      double get(int i) {
         return d;
      }
   }   // end MyProp definition
};

int main() {
   X ^ MyX = gcnew X();
   System::Console::WriteLine(MyX->MyProp(1));   // C2660
   System::Console::WriteLine(MyX->MyProp[1]);   // OK
}
```

C2660 peut se produire si vous appelez une propriété indexée de manière incorrecte.

```cpp
// C2660d.cpp
// compile with: /clr
ref class A{
public:
   property int default[int,int] {
      int get(int a, int b) {
         return a + b;
      }
   }
};

int main() {
   A^ a = gcnew A;
   int x = a[3][5];   // C2660
   int x2 = a[3,5];   // OK
}
```

C2660 peut se produire si vous définissez un nouvel opérateur dans une classe de modèle, mais que l’opérateur New crée un objet dont le type est différent du type englobant.

```cpp
// C2660e.cpp
// compile with: /c
#include <malloc.h>

template <class T> class CA {
private:
    static T** line;
   void* operator new (size_t, int i) {
      return 0;
   }
   void operator delete(void* pMem, int i) {
      free(pMem);
   }

public:
   CA () { new (1) T(); }   // C2660
   // try the following line instead
   // CA () { new (1) CA<int>(); }
};

typedef CA <int> int_CA;

void AAA() {
   int_CA  list;
}
```
