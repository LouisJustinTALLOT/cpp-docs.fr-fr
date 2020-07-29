---
title: Type int
ms.date: 11/04/2016
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
ms.openlocfilehash: 2bfd9e108b36f073635c6d9e55e2299764dcb309
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198864"
---
# <a name="type-int"></a>Type int

La taille d’un **`signed int`** **`unsigned int`** élément ou est la taille standard d’un entier sur un ordinateur particulier. Par exemple, dans les systèmes d’exploitation 16 bits, le **`int`** type est généralement 16 bits, ou 2 octets. Dans les systèmes d’exploitation 32 bits, le **`int`** type est généralement 32 bits, ou 4 octets. Par conséquent, le **`int`** type est équivalent à **`short int`** ou au **`long int`** type, et le **`unsigned int`** type est équivalent à ou au **`unsigned short`** **`unsigned long`** type, selon l’environnement cible. Les **`int`** types représentent tous des valeurs signées, sauf indication contraire.

Les spécificateurs **`int`** de type et **`unsigned int`** (ou simplement **`unsigned`** ) définissent certaines fonctionnalités du langage C (par exemple, le **`enum`** type). Dans ces cas, les définitions de **`int`** et **`unsigned int`** pour une implémentation particulière déterminent le stockage réel.

**Spécifique à Microsoft**

Les entiers signés sont représentés sous la forme d'un complément à deux. Le bit le plus significatif indique le signe : 1 pour les nombres négatifs, 0 pour les nombres positifs et zéro. La plage de valeurs est donnée en valeurs [entières C et C++](../c-language/cpp-integer-limits.md), qui sont extraites des limites. Fichier d’en-tête H.

**FIN spécifique à Microsoft**

> [!NOTE]
> Les **`int`** **`unsigned int`** spécificateurs de type et sont largement utilisés dans les programmes C car ils permettent à un ordinateur particulier de gérer des valeurs entières de la façon la plus efficace pour cet ordinateur. Toutefois, étant donné que les tailles **`int`** des **`unsigned int`** types et varient, les programmes qui dépendent d’une **`int`** taille spécifique peuvent ne pas être portables vers d’autres ordinateurs. Pour rendre les programmes plus portables, vous pouvez utiliser des expressions avec l' **`sizeof`** opérateur (comme indiqué dans [l' `sizeof` opérateur](../c-language/sizeof-operator-c.md)) au lieu de tailles de données codées en dur.

## <a name="see-also"></a>Voir aussi

[Stockage des types de base](../c-language/storage-of-basic-types.md)
