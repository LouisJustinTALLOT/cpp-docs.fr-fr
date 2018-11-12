---
title: Compilateur avertissement (niveau 3) C4197
ms.date: 11/04/2016
f1_keywords:
- C4197
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
ms.openlocfilehash: 6de07411a51c8436356e044cb397a65513827fdf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442573"
---
# <a name="compiler-warning-level-3-c4197"></a>Compilateur avertissement (niveau 3) C4197

'type' : volatile de niveau supérieur dans le cast est ignoré.

Le compilateur a détecté un cast de type vers un type qualifié [volatile](../../cpp/volatile-cpp.md), ou un cast de type vers un type à un certain type qualifié de volatile. Selon la norme du C (6.5.3), les propriétés associées aux types qualifiés sont significatives uniquement pour les expressions l-value.

L’exemple suivant génère l’erreur C4197 :

```
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