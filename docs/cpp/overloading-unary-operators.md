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
ms.openlocfilehash: a21c62549f02dddda951c79a06617671ccfe2526
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227216"
---
# <a name="overloading-unary-operators"></a>Surcharge des opérateurs unaires

Les opérateurs unaires qui peuvent être surchargés sont les suivants :

1. `!`([not logique](../cpp/logical-negation-operator-exclpt.md))

1. `&`([adresse](../cpp/address-of-operator-amp.md))

1. `~`([complément à 1](../cpp/one-s-complement-operator-tilde.md))

1. `*`([déréférencement du pointeur](../cpp/indirection-operator-star.md))

1. `+`([plus unaire](../cpp/additive-operators-plus-and.md))

1. `-`([négation unaire](../cpp/additive-operators-plus-and.md))

1. `++`([incrément](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--`([décrémentation](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. opérateurs de conversion

Les opérateurs d’incrémentation et de décrémentation suffixés ( `++` et `--` ) sont traités séparément par [incrément et décrémentation](../cpp/increment-and-decrement-operator-overloading-cpp.md).

Les opérateurs de conversion sont également traités dans une rubrique distincte. consultez [conversions de types définis par l’utilisateur](../cpp/user-defined-type-conversions-cpp.md).

Les règles suivantes s'appliquent à tous les autres opérateurs unaires. Pour déclarer une fonction d'opérateur unaire en tant que membre non statique, vous devez la déclarer comme suit :

> *RET-type* **`operator`** *op* **()**

où *RET-type* est le type de retour et *op* est l’un des opérateurs listés dans le tableau précédent.

Pour déclarer une fonction d'opérateur unaire en tant que fonction globale, vous devez la déclarer comme suit :

> *RET-type* **`operator`** *op* **(** *arg* **)**

où *RET-type* et *op* sont les mêmes que ceux décrits pour les fonctions d’opérateur de membre et le *arg* est un argument de type classe sur lequel opérer.

> [!NOTE]
> Il n’y a aucune restriction sur les types de retour des opérateurs unaires. Par exemple, il paraîtrait logique pour l'opérateur NOT logique (`!`) de retourner une valeur intégrale, mais cela n'est pas appliqué.

## <a name="see-also"></a>Voir aussi

[Surcharge d’opérateur](../cpp/operator-overloading.md)
