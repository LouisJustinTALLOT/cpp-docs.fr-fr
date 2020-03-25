---
title: Avertissement du compilateur (niveau 1) C4313
ms.date: 11/04/2016
f1_keywords:
- C4313
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
ms.openlocfilehash: 14ac938d62b4c5b6f22957268721aea9c3ffef22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163048"
---
# <a name="compiler-warning-level-1-c4313"></a>Avertissement du compilateur (niveau 1) C4313

’fonction’ : conflit entre ’spécificateur de format’ dans la chaîne de format et l’argument nombre de type ’type’

Il existe un conflit entre le format spécifié et la valeur que vous transmettez. Par exemple, vous avez transmis un paramètre 64 bits à un spécificateur de format %d non qualifié qui attend un paramètre entier 32 bits. Cet avertissement est uniquement en vigueur quand le code est compilé pour des cibles 64 bits.

## <a name="example"></a>Exemple

L'exemple de code suivant génère l'avertissement C4313 quand il est compilé pour une cible 64 bits.

```cpp
// C4313.cpp
// Compile by using: cl /W1 C4313.cpp
#include <stdio.h>
int main() {
   int * pI = 0;
   printf("%d", pI);   // C4313 on 64-bit platform code
   // Try one of the following lines instead:
   // printf("%p\n", pI);
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information
}
```
