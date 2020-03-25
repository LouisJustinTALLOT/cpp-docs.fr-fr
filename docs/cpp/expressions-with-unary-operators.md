---
title: Expressions avec opérateurs unaires
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
ms.openlocfilehash: 26aad64e5b9c7a496c2e6bb131b82740c06abe07
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188972"
---
# <a name="expressions-with-unary-operators"></a>Expressions avec opérateurs unaires

Les opérateurs unaires agissent sur un seul opérande dans une expression. Opérateurs unaires :

- [Opérateur d’indirection (*)](../cpp/indirection-operator-star.md)

- [Opérateur d’adresse (&)](../cpp/address-of-operator-amp.md)

- [Opérateur plus unaire (+)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Opérateur de négation unaire (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Opérateur de négation logique ( !)](../cpp/logical-negation-operator-exclpt.md)

- [Opérateur de complément à 1 (~)](../cpp/one-s-complement-operator-tilde.md)

- [Opérateur de préfixe d’incrémentation (+ +)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Opérateur de décrémentation de préfixe (--)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Opérateur de conversion ()](../cpp/cast-operator-parens.md)

- [Opérateur sizeof](../cpp/sizeof-operator.md)

- [opérateur __uuidof](../cpp/uuidof-operator.md)

- [opérateur __alignof](../cpp/alignof-operator.md)

- [nouvel opérateur](../cpp/new-operator-cpp.md)

- [Delete (opérateur)](../cpp/delete-operator-cpp.md)

Ces opérateurs ont une associativité de droite à gauche. Les expressions unaires impliquent en général une syntaxe qui précède une expression primaire ou suffixée.

Voici les formes possibles des expressions unaires :

- *postfix-expression*

- `++` *unaire-expression*

- `--` *unaire-expression*

- *unaire-opérateur* *Cast-expression*

- **sizeof** *-unary-expression*

- *nom du type de* `sizeof(` `)`

- *expression* `decltype(` `)`

- *allocation-expression*

- *désallocation-expression*

Tout *suffixe-expression* est considéré comme une expression *unaire*, et comme toute expression primaire est considérée comme *suffix-expression*, les expressions primaires sont également considérées comme une *expression unaire* . Pour plus d’informations, consultez [expressions suffixées](../cpp/postfix-expressions.md) et [expressions primaires](../cpp/primary-expressions.md).

Un *opérateur unaire* se compose d’un ou plusieurs des symboles suivants : `* & + - ! ~`

*Cast-expression* est une expression unaire avec un cast facultatif pour modifier le type. Pour plus d’informations, consultez [opérateur de Cast : ()](../cpp/cast-operator-parens.md).

Une *expression* peut être n’importe quelle expression. Pour plus d’informations, consultez [expressions](../cpp/expressions-cpp.md).

L' *expression d’allocation* fait référence au **nouvel** opérateur. L' *expression de désallocation* fait référence à l’opérateur **Delete** . Pour plus d'informations, reportez-vous aux liens fournis plus haut dans cette rubrique.

## <a name="see-also"></a>Voir aussi

[Types d’expressions](../cpp/types-of-expressions.md)
