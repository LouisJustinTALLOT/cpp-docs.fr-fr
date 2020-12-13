---
description: 'En savoir plus sur : rétrogradation des entiers'
title: Rétrogradation des entiers
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: d80adff34223d8aa785fa6ffa079a54af198a309
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186816"
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
