---
title: Spécificateurs de type de données et équivalents
description: Décrit les spécificateurs de type de données Microsoft Visual C et leurs équivalents.
ms.date: 11/04/2016
helpviewer_keywords:
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.openlocfilehash: 6a1231bc19617dddf1cc01d4c5e7db2863f1055f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207044"
---
# <a name="data-type-specifiers-and-equivalents"></a>Spécificateurs de type de données et équivalents

Cette documentation utilise généralement les formes des spécificateurs de type figurant dans le tableau ci-dessous plutôt que les formulaires longs. Il suppose également que le **`char`** type est signé par défaut. Tout au long de cette documentation, **`char`** est équivalent à **`signed char`** .

## <a name="type-specifiers-and-equivalents"></a>Spécificateurs de type et équivalents

| Spécificateur de type | Équivalent(s) |
|--|--|
| **`signed char`**<sup>1,0</sup> | **`char`** |
| **`signed int`** | **`signed`**, **`int`** |
| **`signed short int`** | **`short`**, **`signed short`** |
| **`signed long int`** | **`long`**, **`signed long`** |
| **`unsigned char`** | — |
| **`unsigned int`** | **`unsigned`** |
| **`unsigned short int`** | **`unsigned short`** |
| **`unsigned long int`** | **`unsigned long`** |
| **`float`** | — |
| **`long double`**<sup>2</sup> | — |

<sup>1</sup> quand vous rendez le **`char`** type non signé par défaut (en spécifiant l' **`/J`** option du compilateur), vous ne pouvez pas abréger **`signed char`** en tant que **`char`** .

<sup>2</sup> dans les systèmes d’exploitation 32 bits et 64 bits, le compilateur Microsoft C mappe **`long double`** en type **`double`** .

**Spécifique à Microsoft**

Vous pouvez spécifier l' **`/J`** option de compilateur pour remplacer le type par défaut par **`char`** **`signed char`** **`unsigned char`** . Lorsque cette option est activée, **`char`** signifie comme **`unsigned char`** et vous devez utiliser le **`signed`** mot clé pour déclarer une valeur de caractère signée. Si une **`char`** valeur est déclarée explicitement **`signed`** , l' **`/J`** option n’affecte pas celle-ci et la valeur est étendue par un signe lorsqu’elle est élargie à un **`int`** type. Le **`char`** type est étendu par zéro lorsqu’il est élargi au **`int`** type.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Spécificateurs de type C](../c-language/c-type-specifiers.md)
