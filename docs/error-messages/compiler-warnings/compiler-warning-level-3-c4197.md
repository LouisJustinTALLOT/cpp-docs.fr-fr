---
title: Avertissement du compilateur (niveau 3) C4197
ms.date: 11/04/2016
f1_keywords:
- C4197
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
ms.openlocfilehash: fbc3fbf7f7408f854b1de969688dfbd25e826d84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161592"
---
# <a name="compiler-warning-level-3-c4197"></a>Avertissement du compilateur (niveau 3) C4197

'type' : la volatile de niveau supérieur dans le cast est ignorée

Le compilateur a détecté un cast en un type r-value qui est qualifié avec [volatile](../../cpp/volatile-cpp.md), ou un cast d’un type r-value en un type qualifié avec volatile. Selon la norme C (6.5.3), les propriétés associées aux types qualifiés sont significatives uniquement pour les expressions l-value.

L’exemple suivant génère l’C4197 :

```cpp
// C4197.cpp
// compile with: /W3
#include <stdio.h>
#include <signal.h>
#include <stdlib.h>

void sigproc(int);
struct S
{
   int i;
} s;

int main()
{
   signal(SIGINT, sigproc);
   s.i = 1;
   S *pS = &s;
   for ( ; (volatile int)pS->i ; )   // C4197
      break;
   // for ( ; *(volatile int *)&pS->i ; )   // OK
   //    break;
}

void sigproc(int) // ctrl-C
{
   signal(SIGINT, sigproc);
   s.i = 0;
}
```
