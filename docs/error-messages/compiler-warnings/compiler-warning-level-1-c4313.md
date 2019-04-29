---
title: Avertissement du compilateur (niveau 1) C4313
ms.date: 11/04/2016
f1_keywords:
- C4313
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
ms.openlocfilehash: 774af2d5d29112d56adf97e22d1bdd758a816ef1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352934"
---
# <a name="compiler-warning-level-1-c4313"></a>Avertissement du compilateur (niveau 1) C4313

’fonction’ : conflit entre ’spécificateur de format’ dans la chaîne de format et l’argument nombre de type ’type’

Il existe un conflit entre le format spécifié et la valeur que vous transmettez. Par exemple, vous avez transmis un paramètre 64 bits à un spécificateur de format %d non qualifié qui attend un paramètre entier 32 bits. Cet avertissement est uniquement en vigueur quand le code est compilé pour des cibles 64 bits.

## <a name="example"></a>Exemple

L'exemple de code suivant génère l'avertissement C4313 quand il est compilé pour une cible 64 bits.

```
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