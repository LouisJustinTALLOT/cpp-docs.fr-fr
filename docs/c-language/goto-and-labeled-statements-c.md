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
ms.openlocfilehash: b23e7e6310ba4ed968e2eac8e6d07d81ee4e79ba
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151947"
---
# <a name="goto-and-labeled-statements-c"></a>Instructions goto et étiquetées (C)

L'instruction `goto` transfère le contrôle à une étiquette. L'étiquette donnée doit résider dans la même fonction et peut apparaître devant une seule instruction dans la même fonction.

## <a name="syntax"></a>Syntaxe

*instruction* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*labeled-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jump-statement*

*saut-instruction* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**goto**  *identifier*  **;**

*labeled-statement* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*  **:**  *statement*

Une étiquette d'instruction est uniquement explicite pour une instruction `goto`. Dans tout autre contexte, une instruction étiquetée est exécutée sans tenir compte de l'étiquette.

*jump-statement* doit résider dans la même fonction et peut apparaître devant une seule instruction dans la même fonction. L'ensemble des noms *identifier* suivant une instruction `goto` a son propre espace de noms et les noms n'interfèrent donc pas avec d'autres identificateurs. Les étiquettes ne peuvent pas être redéclarées. Pour plus d'informations, consultez [Espaces de noms](../c-language/name-spaces.md).

Il est toutefois conseillé d'utiliser l'instruction **break**, **continue** et `return` plutôt que `goto` dans la mesure du possible. Étant donné que l'instruction **break** n'exécute une sortie que d'un niveau de la boucle, une instruction `goto` peut être nécessaire pour quitter une boucle dans une boucle profondément imbriquée.

Cet exemple illustre l'instruction `goto` :

```
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

Dans cet exemple, une instruction `goto` transfère le contrôle au point étiqueté `stop` lorsque `i` est égal à 5.

## <a name="see-also"></a>Voir aussi

[Instructions](../c-language/statements-c.md)
