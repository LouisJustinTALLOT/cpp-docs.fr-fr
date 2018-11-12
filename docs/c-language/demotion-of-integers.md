---
title: Rétrogradation des entiers
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: 5dca8d414e7cf7dd04d405208ad6a86dd4372542
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480904"
---
# <a name="demotion-of-integers"></a>Rétrogradation des entiers

**ANSI 3.2.1.2** Le résultat de la conversion d’un entier en un entier signé plus court, ou le résultat de la conversion d’un entier non signé en entier signé de longueur égale si la valeur ne peut pas être représentée

Lorsqu’un entier **long** est casté en un **short** ou qu’un **short** est casté en un `char`, les octets moins significatifs sont conservés.

Par exemple, cette ligne

```
short x = (short)0x12345678L;
```

assigne la valeur 0x5678 à `x`, et cette ligne

```
char y = (char)0x1234;
```

assigne la valeur 0x34 à `y`.

Lorsque des variables signées sont converties en variables non signées et vice versa, les modèles binaires restent les mêmes. Par exemple, le cast de -2 (0xFE) en une valeur non signée produit 254 (également 0xFE).

## <a name="see-also"></a>Voir aussi

[Entiers](../c-language/integers.md)