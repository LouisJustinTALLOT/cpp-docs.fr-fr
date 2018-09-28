---
title: Instruction break (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- break
dev_langs:
- C++
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aeec33d61f21c34e52d582ebc3c0ef7313bb511f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755032"
---
# <a name="break-statement-c"></a>break, instruction (C)
L'instruction `break` termine l'exécution de l'instruction `do`, `for`, `switch` ou `while` englobante la plus proche dans laquelle elle figure. Le contrôle est transmis à l'instruction qui suit l'instruction terminée.  
  
## <a name="syntax"></a>Syntaxe

*saut-instruction* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**break ;**
  
L'instruction `break` est fréquemment utilisée pour mettre fin au traitement d'un cas particulier dans une instruction `switch`. L'absence d'une instruction itérative ou `switch` englobante génère une erreur.  
  
Dans les instructions imbriquées, l'instruction `break` met un terme uniquement à l'instruction `do`, `for`, `switch` ou `while` qui l'englobe immédiatement. Vous pouvez utiliser une instruction `return` ou `goto` pour transférer le contrôle hors de la structure imbriquée.  
  
L'exemple suivant illustre l'instruction `break` :  
  
```  
#include <stdio.h>  
int main() {  
   char c;  
   for(;;) {  
      printf_s( "\nPress any key, Q to quit: " );  
  
      // Convert to character value  
      scanf_s("%c", &c);  
      if (c == 'Q')  
          break;  
   }  
} // Loop exits only when 'Q' is pressed  
```  
  
## <a name="see-also"></a>Voir aussi  
[Instruction break](../cpp/break-statement-cpp.md)