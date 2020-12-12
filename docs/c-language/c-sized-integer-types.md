---
description: 'En savoir plus sur : types d’entiers dimensionnés C'
title: Types d'entier dimensionné C
ms.date: 07/22/2020
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
ms.openlocfilehash: ad50806f52638884da69e109da252379dea0d571
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300123"
---
# <a name="c-sized-integer-types"></a>Types d'entier dimensionné C

**Spécifique à Microsoft**

Microsoft C prend en charge les types d’entiers dimensionnés. Vous pouvez déclarer des variables de type entier 8, 16, 32 ou 64 bits à l’aide du `__intN` spécificateur de type, où *`N`* est la taille, en bits, de la variable entière. La valeur de *n* peut être 8, 16, 32 ou 64. L'exemple suivant déclare une variable de chacun des quatre types d'entiers dimensionnés :

```C
__int8  nSmall;     // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Les trois premiers types d’entiers dimensionnés sont des synonymes des types ANSI qui ont la même taille. Elles sont utiles pour écrire du code portable qui se comporte de manière identique sur plusieurs plateformes. Le **`__int8`** type de données est synonyme de type, **`char`** **`__int16`** est synonyme de type **`short`** , **`__int32`** est synonyme de type **`int`** et **`__int64`** est synonyme de type **`long long`** .

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Stockage des types de base](../c-language/storage-of-basic-types.md)
