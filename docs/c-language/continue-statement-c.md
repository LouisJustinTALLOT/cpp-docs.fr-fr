---
description: 'En savoir plus sur : instruction continue (C)'
title: continue, instruction (C)
ms.date: 11/04/2016
f1_keywords:
- continue
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.assetid: 969f293a-45fe-48a7-b4c6-287ba27a631d
ms.openlocfilehash: 03e6493310655f20e61156d26b88ae2b08a40cdc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293246"
---
# <a name="continue-statement-c"></a>continue, instruction (C)

L' **`continue`** instruction passe le contrôle à l’itération suivante de l’instruction englobante **`do`** , **`for`** , ou la plus proche **`while`** dans laquelle elle apparaît, en ignorant toutes les instructions restantes dans le corps de l' **`do`** **`for`** instruction, ou **`while`** .

## <a name="syntax"></a>Syntaxe

*instruction Jump*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pouvoir**

L’itération suivante d’une **`do`** **`for`** instruction, ou **`while`** est déterminée comme suit :

- Dans une **`do`** instruction ou **`while`** , l’itération suivante démarre en réévaluant l’expression de l' **`do`** **`while`** instruction ou.

- Une **`continue`** instruction dans une **`for`** instruction provoque l’évaluation de l’expression de boucle de l' **`for`** instruction. Ensuite le compilateur réévalue l'expression conditionnelle et, selon le résultat, termine ou itère le corps de l'instruction. Consultez [l’instruction for](../c-language/for-statement-c.md) pour plus d’informations sur l' **`for`** instruction et ses non terminaux.

Voici un exemple de l' **`continue`** instruction :

```C
while ( i-- > 0 )
{
    x = f( i );
    if ( x == 1 )
        continue;
    y += x * x;
}
```

Dans cet exemple, le corps de l'instruction est exécuté alors que `i` est supérieur à 0. `f(i)`La première est assignée à `x` ; ensuite, si `x` est égal à 1, l' **`continue`** instruction est exécutée. Le reste des instructions du corps sont ignorées, et l'exécution se poursuit en haut de la boucle avec l'évaluation du test de boucle.

## <a name="see-also"></a>Voir aussi

[continue (instruction)](../cpp/continue-statement-cpp.md)
