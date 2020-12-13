---
description: 'En savoir plus sur : erreur du compilateur C2273'
title: Erreur du compilateur C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: 656b5477682ace779cd872b2233d911cfb67c0e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336260"
---
# <a name="compiler-error-c2273"></a>Erreur du compilateur C2273

'type' : non conforme à droite de l’opérateur'-> '

Un type apparaît en tant qu’opérande droit d’un `->` opérateur.

Cette erreur peut être due à une tentative d’accès à une conversion de type défini par l’utilisateur. Utilisez le mot clé **`operator`** between-> et `type` .

L’exemple suivant génère l’C2273 :

```cpp
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
