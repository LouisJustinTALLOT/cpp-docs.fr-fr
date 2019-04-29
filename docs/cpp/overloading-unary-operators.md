---
title: Surcharge des opérateurs unaires
ms.date: 11/04/2016
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
ms.openlocfilehash: 802380bad59534e8402020142e394b3948032476
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377223"
---
# <a name="overloading-unary-operators"></a>Surcharge des opérateurs unaires

Les opérateurs unaires qui peuvent être surchargés sont les suivants :

1. `!` ([NOT logique](../cpp/logical-negation-operator-exclpt.md))

1. `&` ([address-of](../cpp/address-of-operator-amp.md))

1. `~` ([complément](../cpp/one-s-complement-operator-tilde.md))

1. `*` ([déréférencement de pointeur](../cpp/indirection-operator-star.md))

1. `+` ([plus unaire](../cpp/additive-operators-plus-and.md))

1. `-` ([négation unaire](../cpp/additive-operators-plus-and.md))

1. `++` ([incrément](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--` ([décrémenter](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

9. opérateurs de conversion

L’incrément postfix et opérateurs de décrémentation (`++` et `--`) sont traités séparément dans [incrémenter et décrémenter](../cpp/increment-and-decrement-operator-overloading-cpp.md).

Les opérateurs de conversion sont également traités dans une rubrique distincte ; consultez [les Conversions de types définis par l’utilisateur](../cpp/user-defined-type-conversions-cpp.md).

Les règles suivantes s'appliquent à tous les autres opérateurs unaires. Pour déclarer une fonction d'opérateur unaire en tant que membre non statique, vous devez la déclarer comme suit :

> *ret-type* **operator** *op* **()**

où *ret-type* est le type de retour et *op* est un des opérateurs répertoriés dans le tableau précédent.

Pour déclarer une fonction d'opérateur unaire en tant que fonction globale, vous devez la déclarer comme suit :

> *ret-type* **operator** *op* **(** *arg* **)**

où *ret-type* et *op* sont celles décrites pour les fonctions d’opérateur de membre et le *arg* est un argument de type de classe à utiliser.

> [!NOTE]
>  Il n’y a aucune restriction sur les types de retour des opérateurs unaires. Par exemple, il paraîtrait logique pour l'opérateur NOT logique (`!`) de retourner une valeur intégrale, mais cela n'est pas appliqué.

## <a name="see-also"></a>Voir aussi

[Surcharge d'opérateur](../cpp/operator-overloading.md)