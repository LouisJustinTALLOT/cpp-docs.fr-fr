---
description: 'En savoir plus sur : instruction Break (C)'
title: break, instruction (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: 54f20de08661073a65ee0b8c50cf877e719aadcf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211646"
---
# <a name="break-statement-c"></a>break, instruction (C)

L' **`break`** instruction termine l’exécution de l’instruction,, ou englobante la plus proche **`do`** **`for`** **`switch`** **`while`** dans laquelle elle apparaît. Le contrôle est transmis à l'instruction qui suit l'instruction terminée.

## <a name="syntax"></a>Syntaxe

*instruction Jump*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**break ;**

L' **`break`** instruction est fréquemment utilisée pour mettre fin au traitement d’un cas particulier dans **`switch`** une instruction. L’absence d’une instruction itérative englobante **`switch`** génère une erreur.

Dans les instructions imbriquées, l' **`break`** instruction met un terme **`do`** uniquement **`for`** à l’instruction,, **`switch`** ou **`while`** qui l’englobe immédiatement. Vous pouvez utiliser une **`return`** **`goto`** instruction ou pour transférer le contrôle à un autre endroit de la structure imbriquée.

Cet exemple illustre l' **`break`** instruction :

```C
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

[Break (instruction)](../cpp/break-statement-cpp.md)
