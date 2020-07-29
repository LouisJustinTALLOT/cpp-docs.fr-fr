---
title: Erreur du compilateur C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 3794a1ce0fcbe60c06cb3efca45a3081e85c17ce
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87210018"
---
# <a name="compiler-error-c2180"></a>Erreur du compilateur C2180

l'expression de contrôle a le type 'type'

L’expression de contrôle dans **`if`** une **`while`** instruction,, **`for`** ou **`do`** est une expression castée en **`void`** . Pour résoudre ce problème, remplacez l’expression de contrôle par une expression qui produit un **`bool`** ou un type qui peut être converti en **`bool`** .

L'exemple suivant génère l'erreur C2180 :

```c
// C2180.c

int main() {
   while ((void)1)   // C2180
      return 1;
   while (1)         // OK
      return 0;
}
```
