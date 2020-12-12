---
description: 'En savoir plus sur : erreur du compilateur C2274'
title: Erreur du compilateur C2274
ms.date: 11/04/2016
f1_keywords:
- C2274
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
ms.openlocfilehash: 31b9d63b9cf87114ce2d1d79f1f38fff97d4ebbb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268351"
---
# <a name="compiler-error-c2274"></a>Erreur du compilateur C2274

'type' : non conforme à droite de l’opérateur'. '

Un type apparaît en tant qu’opérande droit d’un opérateur d’accès aux membres (.).

Cette erreur peut être due à une tentative d’accès à une conversion de type défini par l’utilisateur. Utilisez le mot clé **`operator`** entre le point et `type` .

L’exemple suivant génère l’erreur C2286 :

```cpp
// C2274.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};

int main() {
   MyClass ClassName;
   int i = ClassName.int();   // C2274
   int j = ClassName.operator int();   // OK
}
```
