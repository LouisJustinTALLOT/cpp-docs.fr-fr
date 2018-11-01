---
title: Avertissement du compilateur (niveau 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: 743069c0ed3103a2ed8d459def65083146b971e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497014"
---
# <a name="compiler-warning-level-4-c4487"></a>Avertissement du compilateur (niveau 4) C4487

'fonction_classe_dérivée' : correspond à la méthode non virtuelle héritée 'fonction_classe_base' mais n’est pas explicitement marqué comme 'new'

Une fonction dans une classe dérivée a la même signature qu’une fonction de la classe de base non virtuelle. C4487 vous rappelle que la fonction de la classe dérivée ne remplace pas la fonction de la classe de base. Marquer explicitement la fonction de la classe dérivée en tant que `new` pour résoudre cet avertissement.

Pour plus d’informations, consultez [new (nouvel emplacement dans vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C4487.

```
// C4487.cpp
// compile with: /W4 /clr
using namespace System;
public ref struct B {
   void f() { Console::WriteLine("in B::f"); }
   void g() { Console::WriteLine("in B::g"); }
};

public ref struct D : B {
   void f() { Console::WriteLine("in D::f"); }   // C4487
   void g() new { Console::WriteLine("in D::g"); }   // OK
};

int main() {
   B ^ a = gcnew D;
   // will call base class functions
   a->f();
   a->g();
}
```