---
title: Instructions goto et étiquetées (C)
ms.date: 11/04/2016
f1_keywords:
- goto
helpviewer_keywords:
- labeled statement
- statements, labeled
- goto keyword [C]
ms.assetid: 3d0473dc-4b18-4fcc-9616-31a38499d7d7
ms.openlocfilehash: d84aa6701ef030dc494f6a40a7223d6f9bcd5073
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199982"
---
# <a name="goto-and-labeled-statements-c"></a>Instructions goto et étiquetées (C)

L' **`goto`** instruction transfère le contrôle à une étiquette. L'étiquette donnée doit résider dans la même fonction et peut apparaître devant une seule instruction dans la même fonction.

## <a name="syntax"></a>Syntaxe

*instruction*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction étiquetée*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instruction Jump*

*instruction Jump*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`goto`**  *identificateur*  **;**

*instruction étiquetée*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*  **:**  *instruction*

Une étiquette d’instruction est significative uniquement pour une **`goto`** instruction. dans tout autre contexte, une instruction étiquetée est exécutée sans tenir compte de l’étiquette.

*jump-statement* doit résider dans la même fonction et peut apparaître devant une seule instruction dans la même fonction. L’ensemble de noms d' *identificateur* suivant un **`goto`** a son propre espace de noms, les noms n’interfèrent donc pas avec d’autres identificateurs. Les étiquettes ne peuvent pas être redéclarées. Pour plus d'informations, consultez [Espaces de noms](../c-language/name-spaces.md).

Il s’agit d’un bon style de programmation pour utiliser l' **`break`** **`continue`** instruction, et **`return`** de préférence à **`goto`** chaque fois que cela est possible. Étant donné que l' **`break`** instruction se termine uniquement à partir d’un niveau de la boucle, un **`goto`** peut être nécessaire pour quitter une boucle dans une boucle profondément imbriquée.

Cet exemple illustre l' **`goto`** instruction :

```c
// goto.c
#include <stdio.h>

int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 3; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 5 )
                goto stop;
        }
    }

    /* This message does not print: */
    printf_s( "Loop exited. i = %d\n", i );

    stop: printf_s( "Jumped to stop. i = %d\n", i );
}
```

Dans cet exemple, une **`goto`** instruction transfère le contrôle au point étiqueté `stop` lorsque `i` est égal à 5.

## <a name="see-also"></a>Voir aussi

[Instructions](../c-language/statements-c.md)
