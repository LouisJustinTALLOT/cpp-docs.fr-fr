---
title: Erreur du compilateur C3731
ms.date: 11/04/2016
f1_keywords:
- C3731
helpviewer_keywords:
- C3731
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
ms.openlocfilehash: 9acf80eec0d36db64fa070d691533e7085754ac0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752949"
---
# <a name="compiler-error-c3731"></a>Erreur du compilateur C3731

événement’fonction1 'et gestionnaire’fonction2 'incompatibles ; la source d’événements et le gestionnaire d’événements doivent être du même type

La source de l’événement et le récepteur d’événements doivent avoir le même type (par exemple `native` et les types de `com`). Pour corriger cette erreur, définissez les types de la source de l’événement et celui du gestionnaire d’événements.

L’exemple suivant génère l’C3731 :

```cpp
// C3731.cpp
// compile with: /clr
#using <mscorlib.dll>
[event_source(native)]
struct A {
   __event void MyEvent();
};

[event_receiver(managed)]
// try the following line instead
// [event_receiver(native)]
struct B {
   void func();
   B(A a) {
      __hook(&A::MyEvent, &a, &B::func);   // C3731
   }
};

int main() {
}
```
