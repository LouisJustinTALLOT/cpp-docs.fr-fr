---
title: Types scalaires
ms.date: 11/04/2016
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
ms.openlocfilehash: 0c2fa18022763564a29b6a96f8ce719039dcd216
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492060"
---
# <a name="scalar-types"></a>Types scalaires

Bien que l’accès aux données peuvent provenir d’un alignement quelconque, il est recommandé d’aligner les données sur leur limite naturelle afin d’éviter la perte de performances (ou plusieurs). Les enums sont des entiers constants et sont traités comme des entiers 32 bits. Le tableau suivant décrit la définition de type et le stockage recommandé pour celle-ci en ce qui concerne l’alignement en utilisant les valeurs d’alignement suivantes :

- Byte - 8 bits

- Word - 16 bits

- Double mot - 32 bits

- Word Quad - 64 bits

- Huit Word - 128 bits

|||||
|-|-|-|-|
|Type scalaire|Type de données C|Taille de stockage (en octets)|Alignement recommandé|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|Word|
|**UINT16**|**unsigned short**|2|Word|
|**INT32**|**int**, **long**|4|Mot double|
|**UINT32**|**unsigned int, unsigned long**|4|Mot double|
|**INT64**|**__int64**|8|Mot quadruple|
|**UINT64**|**unsigned __int64**|8|Mot quadruple|
|**FP32 (simple précision)**|**float**|4|Mot double|
|**FP64 (double précision)**|**double**|8|Mot quadruple|
|**POINTEUR**|<strong>\*</strong>|8|Mot quadruple|
|**__m64**|**__m64 de struct**|8|Mot quadruple|
|**__m128**|**__m128 de struct**|16|Octaword|

## <a name="see-also"></a>Voir aussi

[Types et stockage](../build/types-and-storage.md)