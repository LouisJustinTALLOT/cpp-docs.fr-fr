---
title: Avertissement du compilateur (niveau 2) C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: 8baf3c03c87dc70a80b785d7f81cbee4e1d828f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349709"
---
# <a name="compiler-warning-level-2-c4250"></a>Avertissement du compilateur (niveau 2) C4250

'classe1' : hérite de 'classe2::membre' via la dominance

Deux ou plusieurs membres ont le même nom. Celui de `class2` est héritée car c’est une classe de base pour les autres classes qui contenaient ce membre.

Pour supprimer l’erreur C4250, utilisez le [avertissement](../../preprocessor/warning.md) pragma.

Étant donné que la classe de base virtuelle est partagée entre plusieurs classes dérivées, un nom dans une classe dérivée domine un nom dans une classe de base. Par exemple, étant donné la hiérarchie de classe suivante, il y a deux définitions de func héritées dans un losange : l’instance ::Func() via la classe faible et le dominant :: func() via la classe dominante. Un appel non qualifié de func() via un objet de classe en losange, appelle toujours l’instance dominate::func.  Si la classe faible ont été d’introduire une instance de func(), ni dépasse celle de définition et l’appel est signalée comme ambiguë.

```
// C4250.cpp
// compile with: /c /W2
#include <stdio.h>
struct vbc {
   virtual void func() { printf("vbc::func\n"); }
};

struct weak : public virtual vbc {};

struct dominant : public virtual vbc {
   void func() { printf("dominant::func\n"); }
};

struct diamond : public weak, public dominant {};

int main() {
   diamond d;
   d.func();   // C4250
}
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4250.

```
// C4250_b.cpp
// compile with: /W2 /EHsc
#include <iostream>
using namespace std;
class A {
public:
   virtual operator int () {
      return 2;
   }
};

class B : virtual public A {
public:
   virtual operator int () {
      return 3;
   }
};

class C : virtual public A {};

class E : public B, public C {};   // C4250

int main() {
   E eObject;
   cout << eObject.operator int() << endl;
}
```

## <a name="example"></a>Exemple

Cet exemple montre une situation plus complexe. L’exemple suivant génère l’erreur C4250.

```
// C4250_c.cpp
// compile with: /W2 /EHsc
#include <iostream>
using namespace std;

class V {
public:
   virtual int f() {
      return 1024;
   }
};

class B : virtual public V {
public:
   int b() {
      return f(); // B::b() calls V::f()
   }
};

class M : virtual public V {
public:
   int f() {
      return 7;
   }
};

// because of dominance, f() is M::f() inside D,
// changing the meaning of B::b's f() call inside a D
class D : public B, public M {};   // C4250

int main() {
   D d;
   cout << "value is: " << d.b();   // invokes M::f()
}
```