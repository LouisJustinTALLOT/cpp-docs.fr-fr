---
title: Compilateur avertissement (niveau 3) C4197 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4197
dev_langs:
- C++
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa119e0b1afd3f660dd04040965006f1b52cad01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290424"
---
# <a name="compiler-warning-level-3-c4197"></a>Compilateur avertissement (niveau 3) C4197
'type' : volatile de niveau supérieur dans le cast est ignoré.  
  
 Le compilateur a détecté un cast de type vers un type qualifié [volatile](../../cpp/volatile-cpp.md), ou un cast de type vers un type en un type qualifié de volatile. Selon la norme du C (6.5.3), les propriétés associées aux types qualifiés sont significatives uniquement pour les expressions l-value.  
  
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