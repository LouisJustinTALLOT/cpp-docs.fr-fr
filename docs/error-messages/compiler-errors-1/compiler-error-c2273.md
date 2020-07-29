---
title: Erreur du compilateur C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: f5780c299eb4da03ece3611ee55062ee7ebcdaae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212785"
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
