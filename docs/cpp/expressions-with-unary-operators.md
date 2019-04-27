---
title: Expressions avec opérateurs unaires
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
ms.openlocfilehash: a13b86755a5e309a51a0e2e14faa1157b7e95ea0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183868"
---
# <a name="expressions-with-unary-operators"></a>Expressions avec opérateurs unaires

Les opérateurs unaires agissent sur un seul opérande dans une expression. Opérateurs unaires :

- [Opérateur d’indirection (*)](../cpp/indirection-operator-star.md)

- [Opérateur d’adresse (&)](../cpp/address-of-operator-amp.md)

- [Opérateur (+) plus unaire](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Opérateur de négation unaire (–)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Opérateur de négation logique ( !)](../cpp/logical-negation-operator-exclpt.md)

- [Opérateur de complément (~)](../cpp/one-s-complement-operator-tilde.md)

- [Opérateur de pré-incrémentation (++)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Opérateur de pré-décrémentation (-)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Opérateur de cast ()](../cpp/cast-operator-parens.md)

- [opérateur sizeof](../cpp/sizeof-operator.md)

- [__uuidof operator](../cpp/uuidof-operator.md)

- [__alignof operator](../cpp/alignof-operator.md)

- [New, opérateur](../cpp/new-operator-cpp.md)

- [opérateur delete](../cpp/delete-operator-cpp.md)

Ces opérateurs ont une associativité de droite à gauche. Les expressions unaires impliquent en général une syntaxe qui précède une expression primaire ou suffixée.

Voici les formes possibles des expressions unaires :

- *postfix-expression*

- `++` *unary-expression*

- `--` *unary-expression*

- *unary-operator* *cast-expression*

- **sizeof** *unary-expression*

- `sizeof(` *type-name* `)`

- `decltype(` *expression* `)`

- *allocation-expression*

- *deallocation-expression*

N’importe quel *postfix-expression* est considéré comme un *expression unaire*, et parce que toute expression primaire est considérée comme un *postfix-expression*, est toute expression primaire considéré comme un *expression unaire* également. Pour plus d’informations, consultez [Expressions suffixées](../cpp/postfix-expressions.md) et [Expressions primaires](../cpp/primary-expressions.md).

Un *-opérateur unaire* se compose d’une ou plusieurs des symboles suivants : `* & + - ! ~`

Le *cast-expression* est une expression unaire avec un transtypage facultatif pour modifier le type. Pour plus d’informations, consultez [opérateur de Cast : ()](../cpp/cast-operator-parens.md).

Un *expression* peut être toute expression. Pour plus d’informations, consultez [Expressions](../cpp/expressions-cpp.md).

Le *allocation-expression* fait référence à la **nouveau** opérateur. Le *désallocation-expression* fait référence à la **supprimer** opérateur. Pour plus d'informations, reportez-vous aux liens fournis plus haut dans cette rubrique.

## <a name="see-also"></a>Voir aussi

[Types d’expressions](../cpp/types-of-expressions.md)