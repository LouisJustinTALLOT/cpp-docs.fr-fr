---
title: Cast d'entiers en valeurs à virgule flottante
ms.date: 11/04/2016
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
ms.openlocfilehash: b3c65beee0cef4eb74d1bad3c03e5a9c11efae27
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227918"
---
# <a name="casting-integers-to-floating-point-values"></a>Cast d'entiers en valeurs à virgule flottante

**ANSI 3.2.1.3** Direction de la troncation lorsqu'un nombre intégral est converti en nombre à virgule flottante qui ne peut pas représenter exactement la valeur d'origine

Lorsqu'un nombre intégral est casté en une valeur à virgule flottante qui ne peut pas représenter exactement la valeur, la valeur est arrondie à la valeur appropriée (inférieure ou supérieure) la plus proche.

Par exemple, le cast d’un **`unsigned long`** (avec 32 bits de précision) en un **`float`** (dont la mantisse a une précision de 23 bits) arrondit le nombre au multiple le plus proche de 256. Les **`long`** valeurs 4 294 966 913 à 4 294 967 167 sont arrondies à la **`float`** valeur 4 294 967 040.

## <a name="see-also"></a>Voir aussi

[Mathématiques à virgule flottante](../c-language/floating-point-math.md)
