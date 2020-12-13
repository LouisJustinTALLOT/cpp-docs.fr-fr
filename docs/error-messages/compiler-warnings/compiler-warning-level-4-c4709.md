---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4709'
title: Avertissement du compilateur (niveau 4) C4709
ms.date: 11/04/2016
f1_keywords:
- C4709
helpviewer_keywords:
- C4709
ms.assetid: 8abfdd45-8c70-4c27-b0fb-ca0c3f0fccf9
ms.openlocfilehash: 3138b8d95fd05cac113166ee9de9e7979f08223d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136225"
---
# <a name="compiler-warning-level-4-c4709"></a>Avertissement du compilateur (niveau 4) C4709

opérateur virgule dans une expression d’index de tableau

Lorsqu’une virgule se produit dans une expression d’index de tableau, le compilateur utilise la valeur après la dernière virgule.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4709 :

```cpp
// C4709.cpp
// compile with: /W4
#include <stdio.h>

int main()
{
    int arr[2][2];
    arr[0][0] = 10;
    arr[0][1] = 11;

    // Prints 10, not 11
    printf_s("\n%d",arr[0][1,0]);   // C4709
}
```
