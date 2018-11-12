---
title: Expressions entre parenthèses
ms.date: 11/04/2016
helpviewer_keywords:
- parentheses
- expression evaluation, evaluation order
- expressions [C++], evaluating
- parentheses, expressions
ms.assetid: b8636147-6982-408c-9e64-29e40678ee43
ms.openlocfilehash: 0b58ed2483b404df957b8e9e95e41442403036c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505545"
---
# <a name="expressions-in-parentheses"></a>Expressions entre parenthèses

Vous pouvez placer n’importe quel opérande entre parenthèses sans modifier le type ou la valeur de l’expression entre crochets. Par exemple, dans l'expression :

```
( 10 + 5 ) / 5
```

les parenthèses autour de `10 + 5` signifient que la valeur de `10 + 5` est d’abord déterminée, puis elle devient l’opérande gauche de l’opérateur de division (**/**). Le résultat de `( 10 + 5 ) / 5` est égal à 3. Sans parenthèses, la valeur de `10 + 5 / 5` serait égale à 11.

Bien que les parenthèses aient une incidence sur la manière dont les opérandes sont regroupés dans une expression, elles ne peuvent pas garantir un ordre spécifique d'évaluation dans tous les cas. Par exemple, ni les parenthèses ni le regroupement de gauche à droite de l'expression suivante garantissent à quoi sera égale la valeur de `i` dans l'une ou l'autre des sous-expressions :

```
( i++ +1 ) * ( 2 + i )
```

Le compilateur est libre pour évaluer les deux côtés de la multiplication dans n'importe quel ordre. Si la valeur initiale de `i` est égale à zéro, la valeur de l'expression entière peut être déterminée sous la forme de l'une des deux instructions suivantes :

```
( 0 + 1 + 1 ) * ( 2 + 1 )
( 0 + 1 + 1 ) * ( 2 + 0 )
```

Les exceptions résultant des effets secondaires sont abordées dans la rubrique [Effets secondaires](../c-language/side-effects.md).

## <a name="see-also"></a>Voir aussi

[Expressions primaires C](../c-language/c-primary-expressions.md)