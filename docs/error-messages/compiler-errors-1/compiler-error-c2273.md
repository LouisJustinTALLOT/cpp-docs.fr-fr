---
title: Erreur du compilateur C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: f2ed5c49a9f8243fd5c9c302caf2876493c26bc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526387"
---
# <a name="compiler-error-c2273"></a>Erreur du compilateur C2273

'type' : non conforme à droite de l’opérateur '->'

Un type apparaît comme l’opérande de droite d’un `->` opérateur.

Cette erreur peut résulter en essayant d’accéder à une conversion de type défini par l’utilisateur. Utilisez le mot clé `operator` entre -> et `type`.

L’exemple suivant génère l’erreur C2273 :

```
// C2273.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};
int main() {
   MyClass * ClassPtr = new MyClass;
   int i = ClassPtr->int();   // C2273
   int j = ClassPtr-> operator int();   // OK
}
```