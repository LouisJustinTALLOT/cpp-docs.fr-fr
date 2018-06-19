---
title: Constantes de type de données | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- FLT_MIN
- SHRT_MAX
- CHAR_MIN
- MB_LEN_MAX
- DBL_EPSILON
- SHRT_MIN
- _FLT_RADIX
- FLT_DIG
- FLT_MAX_10_EXP
- FLT_MANT_DIG
- DBL_MAX_EXP
- SCHAR_MIN
- SCHAR_MAX
- DBL_MIN
- FLT_MIN_10_EXP
- _DBL_ROUNDS
- USHRT_MAX
- FLT_MAX_EXP
- LONG_MAX
- DBL_MAX
- DBL_DIG
- FLT_MIN_EXP
- INT_MIN
- DBL_MIN_10_EXP
- CHAR_BIT
- INT_MAX
- ULONG_MAX
- DBL_MIN_EXP
- LONG_MIN
- _FLT_ROUNDS
- DBL_MANT_DIG
- _DBL_RADIX
- CHAR_MAX
- FLT_MAX
- DBL_MAX_10_EXP
- UCHAR_MAX
- FLT_EPSILON
- UINT_MAX
dev_langs:
- C++
helpviewer_keywords:
- DBL_MAX_EXP constant
- _DBL_RADIX constant
- FLT_MIN_EXP constant
- DBL_EPSILON constant
- INT_MIN constant
- FLT_EPSILON constant
- DBL_MANT_DIG constant
- _FLT_RADIX constant
- DBL_MIN constant
- USHRT_MAX constant
- FLT_MAX_10_EXP constant
- _FLT_ROUNDS constant
- data type constants [C++]
- _DBL_ROUNDS constant
- CHAR_MAX constant
- FLT_MAX_EXP constant
- FLT_MIN constant
- CHAR_MIN constant
- FLT_MIN_10_EXP constant
- DBL_MIN_EXP constant
- SCHAR_MAX constant
- FLT_RADIX constant
- CHAR_BIT constant
- UCHAR_MAX constant
- DBL_RADIX constant
- FLT_ROUNDS constant
- LONG_MIN constant
- SHRT_MAX constant
- LONG_MAX constant
- DBL_MAX_10_EXP constant
- DBL_MIN_10_EXP constant
- INT_MAX constant
- constants [C++], data type
- ULONG_MAX constant
- FLT_DIG constant
- MB_LEN_MAX constant
- DBL_DIG constant
- SHRT_MIN constant
- DBL_MAX constant
- DBL_ROUNDS constant
- FLT_MAX constant
- UINT_MAX constant
- FLT_MANT_DIG constant
- SCHAR_MIN constant
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf9a64b81ae90c517e9cd15e796dfb1333c7b08c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392144"
---
# <a name="data-type-constants"></a>Constantes de type de données
Les constantes de type de données sont des plages de valeurs dépendant de l’implémentation qui sont autorisées pour les types de données intégraux. Les constantes répertoriées ci-dessous donnent les plages des types de données intégraux, et sont définies dans LIMITS.H.  
  
> [!NOTE]
>  L’option /J du compilateur remplace le type par défaut `char` par `unsigned`.  
  
|Constante|Value|Signification|  
|--------------|-----------|-------------|  
|**SCHAR_MAX**|127|Valeur `char` signée maximale|  
|**SCHAR_MIN**|-128|Valeur `char` signée minimale|  
|**UCHAR_MAX**|255 (0xff)|Valeur `unsigned char` maximale|  
|**CHAR_BIT**|8|Nombre de bits dans un `char`|  
|**USHRT_MAX**|65535 (0xffff)|Valeur **unsigned short** maximale|  
|**SHRT_MAX**|32767|Valeur **short** (signée) maximale|  
|**SHRT_MIN**|-32768|Valeur **short** (signée) minimale|  
|**UINT_MAX**|4294967295 (0xffffffff)|Valeur `unsigned int` maximale|  
|**ULONG_MAX**|4294967295 (0xffffffff)|Valeur `unsigned long` maximale|  
|**INT_MAX**|2147483647|Valeur `int` (signée) maximale|  
|**INT_MIN**|-2147483647-1|Valeur `int` (signée) minimale|  
|**LONG_MAX**|2147483647|Valeur **long** (signée) maximale|  
|**LONG_MIN**|-2147483647-1|Valeur **long** (signée) minimale|  
|**CHAR_MAX**|127 (255 si l’option /J est utilisée)|Valeur `char` maximale|  
|**CHAR_MIN**|-128 (0 si l’option /J est utilisée)|Valeur `char` minimale|  
|**MB_LEN_MAX**|2|Nombre maximal d’octets dans un `char` multioctet|  
|**_I64_MAX**|9223372036854775807|Valeur __**int64** (signée) maximale|  
|**_I64_MIN**|-9223372036854775807-1|Valeur __**int64** (signée) minimale|  
|**_UI64_MAX**|0xffffffffffffffff|Valeur __**int64** (non signée) maximale|  
  
 Les constantes suivantes donnent la plage et les autres caractéristiques des types de données **double** et **float**, et sont définies dans FLOAT.H :  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**DBL_DIG**|15|# de chiffres décimaux de précision|  
|**DBL_EPSILON**|2,2204460492503131e-016|Le plus petit de sorte que 1.0+**DBL_EPSILON** !=1.0|  
|**DBL_MANT_DIG**|53|# de bits dans la mantisse|  
|**DBL_MAX**|1,7976931348623158e+308|Valeur maximale|  
|**DBL_MAX_10_EXP**|308|Exposant décimal maximal|  
|**DBL_MAX_EXP**|1024|Exposant binaire maximal|  
|**DBL_MIN**|2,2250738585072014E-308|Valeur positive minimale|  
|**DBL_MIN_10_EXP**|(-307)|Exposant décimal minimal|  
|**DBL_MIN_EXP**|(-1021)|Exposant binaire minimal|  
|**_DBL_RADIX**|2|Radical d’exposant|  
|**_DBL_ROUNDS**|1|Arrondi d’addition : au plus proche|  
|**FLT_DIG**|6|Nombre de chiffres décimaux de précision|  
|**FLT_EPSILON**|1,192092896e-07F|Le plus petit de sorte que 1.0+**FLT_EPSILON** !=1.0|  
|**FLT_MANT_DIG**|24|Nombre de bits dans la mantisse|  
|**FLT_MAX**|3,402823466e+38F|Valeur maximale|  
|**FLT_MAX_10_EXP**|38|Exposant décimal maximal|  
|**FLT_MAX_EXP**|128|Exposant binaire maximal|  
|**FLT_MIN**|1,175494351e-38F|Valeur positive minimale|  
|**FLT_MIN_10_EXP**|(-37)|Exposant décimal minimal|  
|**FLT_MIN_EXP**|(-125)|Exposant binaire minimal|  
|**FLT_RADIX**|2|Radical d’exposant|  
|**FLT_ROUNDS**|1|Arrondi d’addition : au plus proche|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes globales](../c-runtime-library/global-constants.md)