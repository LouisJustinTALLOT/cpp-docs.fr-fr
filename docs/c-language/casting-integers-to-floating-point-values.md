---
title: Cast de nombres entiers en nombres à virgule flottante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a81b72a7dfedbc1d6033d53bde63be22943abb08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055219"
---
# <a name="casting-integers-to-floating-point-values"></a>Cast d'entiers en valeurs à virgule flottante

**ANSI 3.2.1.3** Direction de la troncation lorsqu'un nombre intégral est converti en nombre à virgule flottante qui ne peut pas représenter exactement la valeur d'origine

Lorsqu'un nombre intégral est casté en une valeur à virgule flottante qui ne peut pas représenter exactement la valeur, la valeur est arrondie à la valeur appropriée (inférieure ou supérieure) la plus proche.

Par exemple, effectuer un cast d'un type **long non signé** (avec 32 bits de précision) en type **flottant** (dont la précision de la mantisse est 23 bits) arrondit le nombre au multiple de 256 le plus proche. Toutes les valeurs **long** 4,294,966,913 à 4,294,967,167 sont arrondies à la valeur **flottante** 4,294,967,040.

## <a name="see-also"></a>Voir aussi

[Mathématiques à virgule flottante](../c-language/floating-point-math.md)