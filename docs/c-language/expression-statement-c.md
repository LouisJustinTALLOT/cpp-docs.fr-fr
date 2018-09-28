---
title: Instruction d'expression (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73071e5cc3eef20895e4eff3bade8e37066dfd71
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765955"
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