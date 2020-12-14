---
description: 'En savoir plus sur : erreur du compilateur C3731'
title: Erreur du compilateur C3731
ms.date: 11/04/2016
f1_keywords:
- C3731
helpviewer_keywords:
- C3731
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
ms.openlocfilehash: 8a7ad836083a8c103df7becd7605a0dfd0efeea7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245081"
---
# <a name="compiler-error-c3731"></a>Erreur du compilateur C3731

événement’fonction1 'et gestionnaire’fonction2 'incompatibles ; la source d’événements et le gestionnaire d’événements doivent être du même type

La source de l’événement et le récepteur d’événements doivent avoir le même type (par exemple `native` vs. `com` types). Pour corriger cette erreur, définissez les types de la source de l’événement et celui du gestionnaire d’événements.

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
