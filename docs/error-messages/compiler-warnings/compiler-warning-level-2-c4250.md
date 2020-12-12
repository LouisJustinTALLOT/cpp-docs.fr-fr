---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4250'
title: Avertissement du compilateur (niveau 2) C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: 04ffb555912c53cb4208cb82ba63c1424ef617e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321863"
---
# <a name="compiler-warning-level-2-c4250"></a>Avertissement du compilateur (niveau 2) C4250

'classe1 ' : hérite de’Class2 :: Member’via la dominance

Deux membres ou plus portent le même nom. Celui de l’élément `class2` est hérité, car il s’agit d’une classe de base pour les autres classes qui contenaient ce membre.

Pour supprimer C4250, utilisez le pragma [Warning](../../preprocessor/warning.md) .

Étant donné qu’une classe de base virtuelle est partagée entre plusieurs classes dérivées, un nom dans une classe dérivée domine un nom dans une classe de base. Par exemple, étant donné la hiérarchie de classes suivante, il existe deux définitions de Func héritées dans Diamond : l’instance VBC :: Func () via la classe faible et la classe dominant :: Func () via la classe dominante. Un appel non qualifié de Func () via un objet de classe Diamond appelle toujours l’instance de Domin :: Func ().  Si la classe faible devait introduire une instance de Func (), aucune définition ne dominerait et l’appel serait marqué comme ambigu.

## <a name="examples"></a>Exemples

```cpp
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

L’exemple suivant génère l’C4250.

```cpp
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

Cet exemple présente une situation plus complexe. L’exemple suivant génère l’C4250.

```cpp
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
