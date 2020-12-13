---
description: 'En savoir plus sur : erreur du compilateur C2180'
title: Erreur du compilateur C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 46ab20e3abfc35355543f90389677737e231257f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335186"
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
