---
title: Erreur du compilateur C3731
ms.date: 11/04/2016
f1_keywords:
- C3731
helpviewer_keywords:
- C3731
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
ms.openlocfilehash: 5acc33869648f83cd44bc557128c685f521ddf88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328066"
---
# <a name="compiler-error-c3731"></a>Erreur du compilateur C3731

événement incompatible 'fonction1' et le gestionnaire 'fonction2' ; source d’événement et le Gestionnaire d’événements doivent être du même type

La source d’événements et un récepteur d’événements doivent avoir le même type (par exemple `native` et `com` types). Pour corriger cette erreur, vérifiez les types de la source d’événements et la correspondance de gestionnaire d’événements.

L’exemple suivant génère C3731 :

```
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