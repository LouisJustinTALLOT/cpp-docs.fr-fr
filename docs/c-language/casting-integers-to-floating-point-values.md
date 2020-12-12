---
description: 'En savoir plus sur : le cast d’entiers en valeurs Floating-Point'
title: Cast d'entiers en valeurs à virgule flottante
ms.date: 11/04/2016
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
ms.openlocfilehash: 2a1a3ce5bf7aac98148c70eb62cdb3c377ca54f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214016"
---
# <a name="casting-integers-to-floating-point-values"></a>Cast d'entiers en valeurs à virgule flottante

**ANSI 3.2.1.3** Direction de la troncation lorsqu'un nombre intégral est converti en nombre à virgule flottante qui ne peut pas représenter exactement la valeur d'origine

Lorsqu'un nombre intégral est casté en une valeur à virgule flottante qui ne peut pas représenter exactement la valeur, la valeur est arrondie à la valeur appropriée (inférieure ou supérieure) la plus proche.

Par exemple, le cast d’un **`unsigned long`** (avec 32 bits de précision) en un **`float`** (dont la mantisse a une précision de 23 bits) arrondit le nombre au multiple le plus proche de 256. Les **`long`** valeurs 4 294 966 913 à 4 294 967 167 sont arrondies à la **`float`** valeur 4 294 967 040.

## <a name="see-also"></a>Voir aussi

[Mathématiques à virgule flottante](../c-language/floating-point-math.md)
