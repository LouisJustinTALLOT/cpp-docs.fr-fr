---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4487'
title: Avertissement du compilateur (niveau 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: a750152e6920f9e012f3a1b7d093b68749e6fe8d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203469"
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
