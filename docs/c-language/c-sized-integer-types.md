---
title: Types d'entier dimensionné C
ms.date: 11/04/2016
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
ms.openlocfilehash: 136065466d3adb4017cf18f2baf8c3387ffbd035
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313296"
---
# <a name="c-sized-integer-types"></a>Types d'entier dimensionné C

**Spécifique à Microsoft**

Microsoft C prend en charge les types d’entiers dimensionnés. Vous pouvez déclarer des variables de type entier de 8, 16, 32 ou 64 bits avec le spécificateur de type __int*n*, où *n* est la taille en bits de la variable de type entier. La valeur de *n* peut être 8, 16, 32 ou 64. L'exemple suivant déclare une variable de chacun des quatre types d'entiers dimensionnés :

```
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Les trois premiers types d'entiers dimensionnés sont des synonymes des types ANSI de la même taille, et permettent d'écrire du code portable qui se comporte de façon identique entre plusieurs plateformes. Notez que le type de données __int8 est synonyme du type char \_, _int16 est synonyme du type short et \__int32 est synonyme du type int. Le \_type de _int64 n’a pas d’équivalent ANSI équivalent.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Stockage de types de base](../c-language/storage-of-basic-types.md)
