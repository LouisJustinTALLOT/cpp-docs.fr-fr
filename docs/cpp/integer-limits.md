---
description: 'En savoir plus sur : limites des entiers'
title: Limites d'entier
ms.date: 01/29/2018
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
ms.openlocfilehash: 78081f8af1c3d1e1f9f71e5d61dea4ee2bd7085c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345522"
---
# <a name="integer-limits"></a>Limites d'entier

**Spécifique à Microsoft**

Les limites pour les types d'entiers sont répertoriées dans le tableau ci-dessous. Les macros de préprocesseur pour ces limites sont également définies lorsque vous incluez le fichier d’en-tête standard \<climits> .

## <a name="limits-on-integer-constants"></a>Limites appliquées aux constantes entières

| Constante | Signification | Valeur |
|--|--|--|
| `CHAR_BIT` | Nombre de bits dans la plus petite variable qui n'est pas un champ de bits | 8 |
| `SCHAR_MIN` | Valeur minimale d’une variable de type **`signed char`** . | -128 |
| `SCHAR_MAX` | Valeur maximale d’une variable de type **`signed char`** . | 127 |
| `UCHAR_MAX` | Valeur maximale d’une variable de type **`unsigned char`** . | 255 (0xff) |
| `CHAR_MIN` | Valeur minimale d’une variable de type **`char`** . | -128 ; 0 si l' **`/J`** option est utilisée |
| `CHAR_MAX` | Valeur maximale d’une variable de type **`char`** . | 127 ; 255 si l' **`/J`** option est utilisée |
| `MB_LEN_MAX` | Nombre maximal d'octets dans une constante à multiples caractères | 5 |
| `SHRT_MIN` | Valeur minimale d’une variable de type **`short`** . | -32768 |
| `SHRT_MAX` | Valeur maximale d’une variable de type **`short`** . | 32767 |
| `USHRT_MAX` | Valeur maximale d’une variable de type **`unsigned short`** . | 65535 (0xffff) |
| `INT_MIN` | Valeur minimale d’une variable de type **`int`** . | -2147483648 |
| `INT_MAX` | Valeur maximale d’une variable de type **`int`** . | 2147483647 |
| `UINT_MAX` | Valeur maximale d’une variable de type **`unsigned int`** . | 4294967295 (0xffffffff) |
| `LONG_MIN` | Valeur minimale d’une variable de type **`long`** . | -2147483648 |
| `LONG_MAX` | Valeur maximale d’une variable de type **`long`** . | 2147483647 |
| `ULONG_MAX` | Valeur maximale d’une variable de type **`unsigned long`** . | 4294967295 (0xffffffff) |
| `LLONG_MIN` | Valeur minimale d’une variable de type **`long long`** | -9223372036854775808 |
| `LLONG_MAX` | Valeur maximale d’une variable de type **`long long`** | 9223372036854775807 |
| `ULLONG_MAX` | Valeur maximale d’une variable de type **`unsigned long long`** | 18446744073709551615 (0xffffffffffffffff) |

Si une valeur dépasse la plus grande représentation d'entier, le compilateur Microsoft génère une erreur.

## <a name="see-also"></a>Voir aussi

[Limites flottantes](../cpp/floating-limits.md)
