---
title: Types d'entier
ms.date: 07/22/2020
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
ms.openlocfilehash: 61ed64c613bc88ed5bf62999ba77fa4090c1ec4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211799"
---
# <a name="integer-types"></a>Types d'entier

Chaque constante entière reçoit un type en fonction de sa valeur et de la façon dont il est exprimé. Vous pouvez forcer une constante entière à être de type **`long`** en ajoutant la lettre **`l`** ou **`L`** à la fin de la constante ; vous pouvez la forcer à être de type **`unsigned`** en ajoutant **`u`** ou **`U`** à la valeur. La lettre minuscule **`l`** peut être confondue avec le chiffre 1 et doit être évitée. Certaines formes de **`long`** constantes entières sont les suivantes :

```C
/* Long decimal constants */
10L
79L

/* Long octal constants */
012L
0115L

/* Long hexadecimal constants */
0xaL or 0xAL
0X4fL or 0x4FL

/* Unsigned long decimal constant */
776745UL
778866LU
```

Le type que vous assignez à une constante dépend de la valeur que cette constante représente. La valeur d'une constante doit être dans la plage de valeurs pouvant être représentées pour son type. Le type d’une constante détermine quelles conversions sont exécutées lorsque la constante est utilisée dans une expression ou lorsque le signe moins ( **`-`** ) est appliqué. La liste suivante résume les règles de conversion des constantes entières.

- Le type d’une constante décimale sans suffixe est **`int`** , **`long int`** ou **`unsigned long int`** . Le premier de ces trois types dans lesquels la valeur de la constante peut être représentée est le type assigné à la constante.

- Le type assigné aux constantes octales et hexadécimales sans suffixes est **`int`** , **`unsigned int`** , **`long int`** ou **`unsigned long int`** selon la taille de la constante.

- Le type assigné aux constantes avec un **`u`** **`U`** suffixe ou est **`unsigned int`** ou **`unsigned long int`** en fonction de leur taille.

- Le type assigné aux constantes avec un **`l`** **`L`** suffixe ou est **`long int`** ou **`unsigned long int`** en fonction de leur taille.

- Le type assigné aux constantes avec un **`u`** ou un **`U`** et **`l`** un **`L`** suffixe est **`unsigned long int`** .

## <a name="see-also"></a>Voir aussi

[Constantes entières C](../c-language/c-integer-constants.md)
