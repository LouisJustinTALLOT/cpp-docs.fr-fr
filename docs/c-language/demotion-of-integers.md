---
title: Rétrogradation des entiers
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: aee0a5041cd37b1fbad785b760b8cefde74eb195
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218882"
---
# <a name="demotion-of-integers"></a>Rétrogradation des entiers

**ANSI 3.2.1.2** Le résultat de la conversion d’un entier en un entier signé plus court, ou le résultat de la conversion d’un entier non signé en entier signé de longueur égale si la valeur ne peut pas être représentée

Lorsqu’un **`long`** entier est casté en **`short`** , ou un **`short`** est casté en un **`char`** , les octets les moins significatifs sont conservés.

Par exemple, cette ligne

```
short x = (short)0x12345678L;
```

assigne la valeur 0x5678 à `x`, et cette ligne

```
char y = (char)0x1234;
```

assigne la valeur 0x34 à `y`.

Lorsque **`signed`** les variables sont converties vers **`unsigned`** et vice versa, les modèles binaires restent les mêmes. Par exemple, Cast-2 (0xFE) en une **`unsigned`** valeur produit 254 (également 0xFE).

## <a name="see-also"></a>Voir aussi

[Entiers](../c-language/integers.md)
