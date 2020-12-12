---
description: 'En savoir plus sur : expressions avec opérateurs unaires'
title: Expressions avec opérateurs unaires
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
ms.openlocfilehash: 6714727d0a4b2c386c37550151df21062534376e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186504"
---
# <a name="expressions-with-unary-operators"></a>Expressions avec opérateurs unaires

Les opérateurs unaires agissent sur un seul opérande dans une expression. Opérateurs unaires :

- [Opérateur d’indirection (*)](../cpp/indirection-operator-star.md)

- [Opérateur d’adresse (&)](../cpp/address-of-operator-amp.md)

- [Opérateur plus unaire (+)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Opérateur de négation unaire (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Opérateur de négation logique ( !)](../cpp/logical-negation-operator-exclpt.md)

- [Opérateur de complément à 1 (~)](../cpp/one-s-complement-operator-tilde.md)

- [Opérateur d'incrémentation de préfixe (++)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Opérateur de décrémentation de préfixe (--)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Opérateur de conversion ()](../cpp/cast-operator-parens.md)

- [`sizeof` and](../cpp/sizeof-operator.md)

- [`__uuidof` and](../cpp/uuidof-operator.md)

- [`alignof` and](../cpp/alignof-operator.md)

- [`new` and](../cpp/new-operator-cpp.md)

- [`delete` and](../cpp/delete-operator-cpp.md)

Ces opérateurs ont une associativité de droite à gauche. Les expressions unaires impliquent en général une syntaxe qui précède une expression primaire ou suffixée.

Voici les formes possibles des expressions unaires :

- *postfix-expression*

- `++` *unary-expression*

- `--` *unary-expression*

- *unaire-opérateur* *Cast-expression*

- **`sizeof`***unaire-expression*

- `sizeof(`*nom du type*`)`

- `decltype(`*expression*`)`

- *allocation-expression*

- *désallocation-expression*

Tout *suffixe-expression* est considéré comme une expression *unaire*, et comme toute expression primaire est considérée comme *suffix-expression*, les expressions primaires sont également considérées comme une *expression unaire* . Pour plus d’informations, consultez [expressions suffixées](../cpp/postfix-expressions.md) et [expressions primaires](../cpp/primary-expressions.md).

Un *opérateur unaire* se compose d’un ou plusieurs des symboles suivants : `* & + - ! ~`

*Cast-expression* est une expression unaire avec un cast facultatif pour modifier le type. Pour plus d’informations, consultez [opérateur de Cast : ()](../cpp/cast-operator-parens.md).

Une *expression* peut être n’importe quelle expression. Pour plus d’informations, consultez [expressions](../cpp/expressions-cpp.md).

L' *expression d’allocation* fait référence à l' **`new`** opérateur. L' *expression de désallocation* fait référence à l' **`delete`** opérateur. Pour plus d'informations, reportez-vous aux liens fournis plus haut dans cette rubrique.

## <a name="see-also"></a>Voir aussi

[Types d’expressions](../cpp/types-of-expressions.md)
