---
description: 'En savoir plus sur : erreur du compilateur C2148'
title: Erreur du compilateur C2148
ms.date: 11/04/2016
f1_keywords:
- C2148
helpviewer_keywords:
- C2148
ms.assetid: e510c2c9-7b57-4ce8-be03-ba363e2cc5d9
ms.openlocfilehash: 253d3d491a17002ab885649c010190833c59f687
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235357"
---
# <a name="compiler-error-c2148"></a>Erreur du compilateur C2148

la taille totale du tableau ne doit pas dépasser 0x7FFFFFFF octets

Un tableau dépasse la limite. Réduisez la taille du tableau.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2148 :

```cpp
// C2148.cpp
#include <stdio.h>
#include <stdlib.h>

int main( ) {
   char MyArray[0x7ffffffff];   // C2148
   char * MyArray2 = (char *)malloc(0x7fffffff);

   if (MyArray2)
      printf_s("It worked!");
   else
      printf_s("It didn't work.");
}
```
