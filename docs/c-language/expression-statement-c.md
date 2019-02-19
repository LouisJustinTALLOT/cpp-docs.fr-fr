---
title: Instruction d'expression (C)
ms.date: 11/04/2016
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
ms.openlocfilehash: 736ed4fbbd9f87c675c0bb9566c6c31287e77917
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148788"
---
# <a name="expression-statement-c"></a>Instruction d'expression (C)

Lorsqu'une instruction d'expression est exécutée, l'expression est évaluée selon les règles définies dans [Expressions et assignations](../c-language/expressions-and-assignments.md).

## <a name="syntax"></a>Syntaxe

*expression-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*<sub>opt</sub> **;**

Tous les effets secondaires de l'évaluation de l'expression sont menés à terme avant l'exécution de l'instruction suivante. Une instruction d'expression vide est appelée « instruction null ». Pour plus d'informations, consultez [Instruction null](../c-language/null-statement-c.md).

Les exemples suivants illustrent des instructions d'expression.

```C
x = ( y + 3 );            /* x is assigned the value of y + 3  */
x++;                      /* x is incremented                  */
x = y = 0;                /* Both x and y are initialized to 0 */
proc( arg1, arg2 );       /* Function call returning void      */
y = z = ( f( x ) + 3 );   /* A function-call expression        */
```

Dans la dernière instruction, l'expression d'appel de fonction, la valeur de l'expression, qui inclut toute valeur retournée par la fonction, est augmentée de 3 unités puis assignée aux variables `y` et `z`.

## <a name="see-also"></a>Voir aussi

[Instructions](../c-language/statements-c.md)
