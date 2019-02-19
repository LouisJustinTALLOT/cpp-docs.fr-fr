---
title: Conversions vers et depuis les types pointeur
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
ms.openlocfilehash: 2d907dbcf4f826d364fb68ce65f7d44c6cfe97cd
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147241"
---
# <a name="conversions-to-and-from-pointer-types"></a>Conversions vers et depuis les types pointeur

Un pointeur vers un type valeur peut être converti en un pointeur vers un type différent. Toutefois, le résultat peut être indéfini en raison des spécifications d'alignement et des tailles de types différents présents dans le stockage. Un pointeur vers un objet peut être converti en un pointeur vers un objet dont le type requiert moins d'alignement ou un alignement aussi strict, et inversement sans modification.

Un pointeur vers `void` peut être converti vers ou depuis un pointeur vers tout type, sans restriction ni perte d'informations. Si le résultat est converti vers le type d'origine, le pointeur d'origine est récupéré.

Si un pointeur est converti en un autre pointeur avec le même type mais des qualificateurs différents ou supplémentaires, le nouveau pointeur est identique à l'ancien, mais des restrictions sont imposées par le nouveau qualificateur.

Une valeur de pointeur peut également être convertie en une valeur intégrale. Le chemin de conversion dépend de la taille du pointeur et de la taille du type intégral selon les règles indiquées ci-dessous.

- Si la taille du pointeur est supérieure ou égale à la taille du type intégral, le pointeur se comporte comme une valeur non signée dans la conversion, mais il ne peut pas être converti en une valeur à virgule flottante.

- Si le pointeur est plus petit que le type intégral, il est d'abord converti en un pointeur avec la même taille qu'un type intégral puis en type intégral.

Inversement, un type intégral peut être converti en un type pointeur selon les règles indiquées ci-dessous.

- Si le type intégral est de la même taille que le type pointeur, la conversion fait simplement que la valeur intégrale est traitée comme un pointeur (un entier non signé).

- Si la taille du type intégral est différente de la taille du type pointeur, le type intégral est d’abord converti en la taille du pointeur, en utilisant les chemins de conversion indiqués dans les tableaux [Conversion de types intégraux signés](../c-language/conversions-from-signed-integral-types.md) et [Conversion de types intégraux non signés](../c-language/conversions-from-unsigned-integral-types.md). Il est ensuite traité comme une valeur de pointeur.

Une expression constante intégrale avec la valeur 0 ou cette même expression castée en type **void** <strong>\*</strong> peut être convertie par un cast de type, par assignation ou par comparaison en un pointeur de tout type. Il en résulte un pointeur null qui équivaut à un autre pointeur null du même type, mais ce pointeur null n'est pas égal à un pointeur vers une fonction ou un objet. Les entiers autres que la constante 0 peuvent être convertis en type pointeur, mais le résultat n'est pas portable.

## <a name="see-also"></a>Voir aussi

[Conversions d’assignation](../c-language/assignment-conversions.md)
