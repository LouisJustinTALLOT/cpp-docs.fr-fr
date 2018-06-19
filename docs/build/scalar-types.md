---
title: Types scalaires | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5490bb33cafd8d2942e434ab9c50e34441506463
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381169"
---
# <a name="scalar-types"></a>Types scalaires
Bien que l’accès aux données peuvent provenir d’un alignement quelconque, il est recommandé d’aligner les données sur leur limite naturelle afin d’éviter la perte de performances (ou plusieurs). Les énumérations sont des entiers constants et sont traitées comme des entiers 32 bits. Le tableau suivant décrit la définition de type et le stockage recommandé pour celle-ci en ce qui concerne l’alignement en utilisant les valeurs d’alignement suivantes :  
  
-   Octet - 8 bits  
  
-   Word - 16 bits  
  
-   Double mot - 32 bits  
  
-   Word Quad - 64 bits  
  
-   octa Word - 128 bits  
  
|||||  
|-|-|-|-|  
|Type scalaire|Type de données C|Taille de stockage (en octets)|Alignement recommandé|  
|**INT8**|`char`|1|Byte|  
|**UINT8**|`unsigned char`|1|Byte|  
|**INT16**|**short**|2|Word|  
|**UINT16**|**unsigned short**|2|Word|  
|**INT32**|**int, long**|4|Mot double|  
|**UINT32**|**entier long non signé**|4|Mot double|  
|**INT64**|`__int64`|8|Mot quadruple|  
|**UINT64**|**unsigned __int64**|8|Mot quadruple|  
|**FP32 (simple précision)**|**float**|4|Mot double|  
|**FP64 (double précision)**|**double**|8|Mot quadruple|  
|**POINTEUR**|**\***|8|Mot quadruple|  
|`__m64`|**__m64 struct**|8|Mot quadruple|  
|`__m128`|**struct __m128**|16|Octaword|  
  
## <a name="see-also"></a>Voir aussi  
 [Types et stockage](../build/types-and-storage.md)