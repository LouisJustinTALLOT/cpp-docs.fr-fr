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
ms.openlocfilehash: 971ef08c5e79f851c502ea872c541517065797c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372035"
---
# <a name="overloading-unary-operators"></a>Surcharge des opérateurs unaires

Les opérateurs unaires qui peuvent être surchargés sont les suivants :

1. `!`([logique PAS](../cpp/logical-negation-operator-exclpt.md))

1. `&`([adresse de](../cpp/address-of-operator-amp.md))

1. `~`([son complément](../cpp/one-s-complement-operator-tilde.md))

1. `*`([déréférence de pointeur](../cpp/indirection-operator-star.md))

1. `+`([unary plus](../cpp/additive-operators-plus-and.md))

1. `-`([négation non aary](../cpp/additive-operators-plus-and.md))

1. `++`([augmentation](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--`([décrément](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. opérateurs de conversion

Les opérateurs d’incrément et`++` de `--`décroissement postfixe ( et ) sont traités séparément dans [Increment et Decrement](../cpp/increment-and-decrement-operator-overloading-cpp.md).

Les opérateurs de conversion sont également discutés dans un autre sujet; voir [conversions de type définies par l’utilisateur](../cpp/user-defined-type-conversions-cpp.md).

Les règles suivantes s'appliquent à tous les autres opérateurs unaires. Pour déclarer une fonction d'opérateur unaire en tant que membre non statique, vous devez la déclarer comme suit :

> *ret-type* **opérateur** *op* **()**

où *le type de ret-type* est le type de retour et *op* est l’un des opérateurs énumérés dans le tableau précédent.

Pour déclarer une fonction d'opérateur unaire en tant que fonction globale, vous devez la déclarer comme suit :

> *ret-type* **opérateur** *op* **(** *arg* **)**

lorsque *le type de ret* et *op* sont décrits comme décrits pour les fonctions de l’opérateur membre et *l’arg* est un argument de type classe sur lequel fonctionner.

> [!NOTE]
> Il n’y a aucune restriction sur les types de retour des opérateurs unaires. Par exemple, il paraîtrait logique pour l'opérateur NOT logique (`!`) de retourner une valeur intégrale, mais cela n'est pas appliqué.

## <a name="see-also"></a>Voir aussi

[Surcharge de l’opérateur](../cpp/operator-overloading.md)
