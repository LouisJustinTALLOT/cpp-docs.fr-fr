---
title: Avertissement du compilateur (niveau 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: 33a2a4e36a2c1d3a3900b9f2f8261df7bbce9b00
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214345"
---
# <a name="compiler-warning-level-4-c4487"></a>Avertissement du compilateur (niveau 4) C4487

'derived_class_function' : correspond à la méthode non virtuelle héritée’base_class_function’mais n’est pas explicitement marquée comme’New'

Une fonction dans une classe dérivée a la même signature qu’une fonction de classe de base non virtuelle. C4487 vous rappelle que la fonction de classe dérivée ne remplace pas la fonction de classe de base. Marquez explicitement la fonction de classe dérivée comme **`new`** pour résoudre cet avertissement.

Pour plus d’informations, voir [New (nouvel emplacement dans vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4487.

```cpp
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
