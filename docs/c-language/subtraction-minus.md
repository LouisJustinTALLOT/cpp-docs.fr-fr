---
title: Soustraction (-)
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
ms.openlocfilehash: 5c9510cf3708ef049b5dac213fa3de894fcd4a07
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147605"
---
# <a name="subtraction--"></a>Soustraction (-)

L’opérateur de soustraction (**-**) soustrait le second opérande du premier. Les deux opérandes peuvent être des types intégraux ou flottants, ou un opérande peut être un pointeur et l’autre un entier.

Lorsque deux pointeurs sont soustraits, la différence est convertie en une valeur intégrale signée en décomposant la différence par la taille d'une valeur du type que les pointeurs traitent. La taille de la valeur intégrale est définie par le type **ptrdiff_t** dans le fichier include STDDEF.H standard. Le résultat représente le nombre de positions de mémoire de ce type entre les deux adresses. Le résultat est forcément explicite pour deux éléments du même tableau, comme indiqué dans [Opérations arithmétiques sur les pointeurs](../c-language/pointer-arithmetic.md).

Lorsqu’une valeur entière est ensuite soustraite d’une valeur de pointeur, l’opérateur de soustraction convertit la valeur entière (*i*) en la multipliant par la taille de la valeur que le pointeur adresse. Après la conversion, la valeur entière représente les emplacements de mémoire *i*, où chaque position a une longueur spécifiée par le type pointeur. Lorsque la valeur entière convertie est ensuite soustraite de la valeur du pointeur, le résultat est les positions *i* de l’adresse mémoire avant l’adresse d’origine. Le nouveau pointeur pointe vers une valeur du type traité par la valeur de pointeur d'origine.

## <a name="see-also"></a>Voir aussi

[Opérateurs additifs C](../c-language/c-additive-operators.md)
