---
description: 'En savoir plus sur : erreur du compilateur C3228'
title: Erreur du compilateur C3228
ms.date: 11/04/2016
f1_keywords:
- C3228
helpviewer_keywords:
- C3228
ms.assetid: 9015adf9-17b0-4312-b4a7-c1f33e4126f4
ms.openlocfilehash: f245555674d7ce9dcd48697d7ff1fd3016750f40
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304127"
---
# <a name="compiler-error-c3228"></a>Erreur du compilateur C3228

'function' : l’argument de type générique de 'param' ne peut pas être 'type', il doit s’agir d’un type valeur ou d’un type de handle

Un type incorrect a été transmis comme argument de type générique.

L’exemple suivant génère l’erreur C3228 :

```cpp
// C3228.cpp
// compile with: /clr
class A {};

value class B {};

generic <class T>
void Test() {}

ref class C {
public:
   generic <class T>
   static void f() {}
};

int main() {
   C::f<A>();   // C3228
   C::f<B>();   // OK

   Test<C>();   // C3228
   Test<C ^>();   // OK
}
```
