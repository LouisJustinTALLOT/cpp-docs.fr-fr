---
title: Erreur du compilateur C2247
ms.date: 11/04/2016
f1_keywords:
- C2247
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
ms.openlocfilehash: e82b406b20d77a824b62207b1766fec55ac65c5c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758903"
---
# <a name="compiler-error-c2247"></a>Erreur du compilateur C2247

'identifier’n’est pas accessible, car’class’utilise’specifier’pour hériter de’class'

`identifier` est hérité d’une classe déclarée avec un accès privé ou protégé.

L’exemple suivant génère l’C2247 :

```cpp
// C2247.cpp
class A {
public:
   int i;
};
class B : private A {};    // B inherits a private A
class C : public B {} c;   // so even though C's B is public
int j = c.i;               // C2247, i not accessible
```

Cette erreur peut également être générée en raison du travail de conformité du compilateur pour Visual Studio .NET 2003 : contrôle d’accès avec des membres protégés. Un membre protégé (n) est accessible uniquement par le biais d’une fonction membre d’une classe (B) qui hérite de la classe (A) dont il (n) est membre.

Pour obtenir un code valide dans les versions Visual Studio .NET 2003 et Visual Studio .NET de Visual C++, déclarez le membre comme un Friend du type. L’héritage public peut également être utilisé.

```cpp
// C2247b.cpp
// compile with: /c
// C2247 expected
class A {
public:
   void f();
   int n;
};

class B: protected A {
   // Uncomment the following line to resolve.
   // friend void A::f();
};

void A::f() {
   B b;
   b.n;
}
```

C2247 peut également être généré à la suite du travail de conformité du compilateur pour Visual Studio .NET 2003 : les classes de base privées sont désormais inaccessibles. Une classe (A) qui est une classe de base privée pour un type (B) ne doit pas être accessible à un type (C) qui utilise B comme classe de base.

Pour obtenir un code valide dans les versions Visual Studio .NET 2003 et Visual Studio .NET de Visual C++, utilisez l’opérateur Scope.

```cpp
// C2247c.cpp
// compile with: /c
struct A {};

struct B: private A {};

struct C : B {
   void f() {
      A *p1 = (A*) this;   // C2247
      // try the following line instead
      // ::A *p2 = (::A*) this;
   }
};
```
