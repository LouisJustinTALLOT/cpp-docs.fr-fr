---
title: Erreur du compilateur C2843 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2843
dev_langs:
- C++
helpviewer_keywords:
- C2843
ms.assetid: 9d3f2ac4-eea5-4fed-abeb-e752f442bfcc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2fd76107368d7805fbecbd1fd00f67d9dad53cb5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109182"
---
# <a name="compiler-error-c2843"></a>Erreur du compilateur C2843

'membre' : ne peut pas prendre l'adresse d'une donnée membre non static ni d'une méthode de type managé ou WinRT

Une instance est requise pour prendre l'adresse des membres de données non statiques d'une interface ou d'une classe managée ou WinRT.

L'exemple suivant génère l'erreur C2843 et montre comment la corriger :

```
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
