---
title: Types d’entier dimensionnés C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 037ff61dbe1d1d42d8b0c751fcdc83f01a8dd112
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101416"
---
# <a name="c-sized-integer-types"></a>Types d'entier dimensionné C

**Section spécifique à Microsoft**

Microsoft C prend en charge les types d’entiers dimensionnés. Vous pouvez déclarer des variables de type entier de 8, 16, 32 ou 64 bits avec le spécificateur de type __int*n*, où *n* est la taille en bits de la variable de type entier. La valeur de *n* peut être 8, 16, 32 ou 64. L'exemple suivant déclare une variable de chacun des quatre types d'entiers dimensionnés :

```
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Les trois premiers types d'entiers dimensionnés sont des synonymes des types ANSI de la même taille, et permettent d'écrire du code portable qui se comporte de façon identique entre plusieurs plateformes. Notez que le type de données __int8 est synonyme du type char, que \__int16 est synonyme du type short et que \__int32 est synonyme du type int. Le type \__int64 n'a pas d'équivalent ANSI.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Stockage de types de base](../c-language/storage-of-basic-types.md)