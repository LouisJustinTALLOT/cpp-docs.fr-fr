---
description: 'En savoir plus sur : erreur du compilateur C2843'
title: Erreur du compilateur C2843
ms.date: 11/04/2016
f1_keywords:
- C2843
helpviewer_keywords:
- C2843
ms.assetid: 9d3f2ac4-eea5-4fed-abeb-e752f442bfcc
ms.openlocfilehash: 3ca201167d6745de8d0b0e8f27a414eebe8a75a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119955"
---
# <a name="compiler-error-c2843"></a>Erreur du compilateur C2843

'membre' : ne peut pas prendre l'adresse d'une donnée membre non static ni d'une méthode de type managé ou WinRT

Une instance est requise pour prendre l'adresse des membres de données non statiques d'une interface ou d'une classe managée ou WinRT.

L'exemple suivant génère l'erreur C2843 et montre comment la corriger :

```cpp
// C2843_2.cpp
// compile with: /clr
public ref class C {
public:
   int m_i;
};

ref struct MyStruct {
   static void sf() {}
   void f() {}
};

int main() {
   MyStruct ^ps = gcnew MyStruct;
   void (__clrcall MyStruct::*F1)() = & MyStruct::f;   // C2843
   void (__clrcall MyStruct::*F2)() = & ps->f;   // C2843
   void (__clrcall MyStruct::*F3)();   // C2843

   void (__clrcall *F5)() = MyStruct::sf;   // OK
   void (__clrcall *F6)() = & ps->sf;   // OK

   interior_ptr<int> i = &C::m_i; // C2843
   C ^x = gcnew C();
   interior_ptr<int> ii = &x->m_i;
}
```
