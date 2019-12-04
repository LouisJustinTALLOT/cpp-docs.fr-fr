---
title: Erreur du compilateur C2273
ms.date: 11/04/2016
f1_keywords:
- C2273
helpviewer_keywords:
- C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
ms.openlocfilehash: 9cd46f7a8a0762fcae2bdec15b9b4be6384adb25
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758682"
---
# <a name="compiler-error-c2273"></a>Erreur du compilateur C2273

'type' : non conforme à droite de l’opérateur'-> '

Un type apparaît en tant qu’opérande droit d’un opérateur `->`.

Cette erreur peut être due à une tentative d’accès à une conversion de type défini par l’utilisateur. Utilisez le mot clé `operator` entre-> et `type`.

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
