---
title: break, instruction (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: b38ff6c535c142bd15ea09a4d7c80010c3fff31f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149815"
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
