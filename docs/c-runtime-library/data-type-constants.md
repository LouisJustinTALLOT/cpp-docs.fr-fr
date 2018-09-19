---
title: Constantes de type de données | Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
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
- LLONG_MIN
- LLONG_MAX
- ULLONG_MAX
- _I8_MIN
- _I8_MAX
- _UI8_MAX
- _I16_MIN
- _I16_MAX
- _UI16_MAX
- _I32_MIN
- _I32_MAX
- _UI32_MAX
- _I64_MIN
- _I64_MAX
- _UI64_MAX
- _I128_MIN
- _I128_MAX
- _UI128_MAX
- SIZE_MAX
- RSIZE_MAX
- LDBL_DIG
- LDBL_EPSILON
- LDBL_HAS_SUBNORM
- LDBL_MANT_DIG
- LDBL_MAX
- LDBL_MAX_10_EXP
- LDBL_MAX_EXP
- LDBL_MIN
- LDBL_MIN_10_EXP
- LDBL_MIN_EXP
- _LDBL_RADIX
- LDBL_TRUE_MIN
- DECIMAL_DIG
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
- LLONG_MIN constant
- LLONG_MAX constant
- ULLONG_MAX constant
- _I8_MIN constant
- _I8_MAX constant
- _UI8_MAX constant
- _I16_MIN constant
- _I16_MAX constant
- _UI16_MAX constant
- _I32_MIN constant
- _I32_MAX constant
- _UI32_MAX constant
- _I64_MIN constant
- _I64_MAX constant
- _UI64_MAX constant
- _I128_MIN constant
- _I128_MAX constant
- _UI128_MAX constant
- SIZE_MAX constant
- RSIZE_MAX constant
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ef742989b4af7a3698f6047098110ee58e29bf4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035667"
---
# <a name="data-type-constants"></a>Constantes de type de données

Les constantes de type de données sont des plages de valeurs dépendant de l’implémentation qui sont autorisées pour les types de données à virgule flottante et intégraux.

## <a name="integral-type-constants"></a>Constantes de type intégral

Ces constantes offrent les plages pour les types de données intégraux. Pour utiliser ces constantes, ajoutez l’en-tête limits.h dans votre fichier source :

```C
#include <limits.h>
```

> [!NOTE]
> L’option [/J](../build/reference/j-default-char-type-is-unsigned.md) du compilateur remplace le type par défaut **char** par **unsigned**.

|Constante|Value|Description|
|--------------|-----------|-------------|
|**CHAR_BIT**|8|Nombre de bits dans un **char**|
|**SCHAR_MIN**|(-128)|Valeur **char** signée minimale|
|**SCHAR_MAX**|127|Valeur **char** signée maximale|
|**UCHAR_MAX**|255 (0xff)|Valeur **unsigned** **char** maximale|
|**CHAR_MIN**|(-128) (0 si l’option **/J** est utilisée)|Valeur **char** minimale|
|**CHAR_MAX**|127 (255 si l’option **/J** est utilisée)|Valeur **char** maximale|
|**MB_LEN_MAX**|5|Nombre maximal d’octets dans un **char** multioctet|
|**SHRT_MIN**|-32768|Valeur **short** signée minimale|
|**SHRT_MAX**|32767|Valeur **short** signée maximale|
|**USHRT_MAX**|65535 (0xffff)|Valeur **unsigned** **short** maximale|
|**INT_MIN**|(-2147483647 - 1)|Valeur **int** signée minimale|
|**INT_MAX**|2147483647|Valeur **int** signée maximale|
|**UINT_MAX**|4294967295 (0xffffffff)|Valeur **unsigned** **int** maximale|
|**LONG_MIN**|(-2147483647L - 1)|Valeur **long** signée minimale|
|**LONG_MAX**|2147483647L|Valeur **long** signée maximale|
|**ULONG_MAX**|4294967295UL (0xfffffffful)|Valeur **unsigned** **long** maximale|
|**LLONG_MIN**|(-9223372036854775807LL - 1)|Valeur **long** **long** ou **__int64** signée minimale|
|**LLONG_MAX**|9223372036854775807LL|Valeur **long** **long** ou **__int64** signée maximale|
|**ULLONG_MAX**|0xffffffffffffffffull|Valeur **unsigned** **long** **long** maximale|
|**_I8_MIN**|(-127i8 - 1)|Valeur 8 bits signée minimale|
|**_I8_MAX**|127i8|Valeur 8 bits signée maximale|
|**_UI8_MAX**|0xffui8|Valeur 8 bits non signée maximale|
|**_I16_MIN**|(-32767i16 - 1)|Valeur 16 bits signée minimale|
|**_I16_MAX**|32767i16|Valeur 16 bits signée maximale|
|**_UI16_MAX**|0xffffui16|Valeur 16 bits non signée maximale|
|**_I32_MIN**|(-2147483647i32 - 1)|Valeur 32 bits signée minimale|
|**_I32_MAX**|2147483647i32|Valeur 32 bits signée maximale|
|**_UI32_MAX**|0xffffffffui32|Valeur 32 bits non signée maximale|
|**_I64_MIN**|(-9223372036854775807 - 1)|Valeur 64 bits signée minimale|
|**_I64_MAX**|9223372036854775807|Valeur 64 bits signée maximale|
|**_UI64_MAX**|0xffffffffffffffffui64|Valeur 64 bits non signée maximale|
|**_I128_MIN**|(-170141183460469231731687303715884105727i128 - 1)|Valeur 128 bits signée minimale|
|**_I128_MAX**|170141183460469231731687303715884105727i128|Valeur 128 bits signée maximale|
|**_UI128_MAX**|0xffffffffffffffffffffffffffffffffui128|Valeur 128 bits non signée maximale|
|**SIZE_MAX**|identique à **_UI64_MAX** si **_WIN64** est défini, ou **UINT_MAX**|Taille d’un entier natif maximal|
|**RSIZE_MAX**|identique à (**SIZE_MAX** >> 1)|Taille d’entier de bibliothèque sécurisée maximale|

## <a name="floating-point-type-constants"></a>Constantes de type à virgule flottante

Les constantes suivantes donnent la plage et autres caractéristiques des types de données **long** **double**, **double** et **float**. Pour utiliser ces constantes, ajoutez l’en-tête float.h dans votre fichier source :

```C
#include <float.h>
```

|Constante|Value|Description|
|--------------|-----------|-----------------|
|**DBL_DECIMAL_DIG**|17|Nombre de chiffres décimaux de précision de l’arrondi|
|**DBL_DIG**|15|# de chiffres décimaux de précision|
|**DBL_EPSILON**|2,2204460492503131e-016|Plus petit nombre, comme 1.0 + **DBL_EPSILON** != 1.0|
|**DBL_HAS_SUBNORM**|1|Le type prend en charge les nombres sous-normalisés (dénormalisés)|
|**DBL_MANT_DIG**|53|Nombre de bits dans le significande (mantisse)|
|**DBL_MAX**|1,7976931348623158e+308|Valeur maximale|
|**DBL_MAX_10_EXP**|308|Exposant décimal maximal|
|**DBL_MAX_EXP**|1024|Exposant binaire maximal|
|**DBL_MIN**|2,2250738585072014E-308|Valeur positive normalisée minimale|
|**DBL_MIN_10_EXP**|(-307)|Exposant décimal minimal|
|**DBL_MIN_EXP**|(-1021)|Exposant binaire minimal|
|**_DBL_RADIX**|2|Radical d’exposant|
|**DBL_TRUE_MIN**|4.9406564584124654e-324|Valeur sous-normalisée positive minimale|
|**FLT_DECIMAL_DIG**|9|Nombre de chiffres décimaux de précision de l’arrondi|
|**FLT_DIG**|6|Nombre de chiffres décimaux de précision|
|**FLT_EPSILON**|1,192092896e-07F|Plus petit nombre, comme 1.0 + **FLT_EPSILON** != 1.0|
|**FLT_HAS_SUBNORM**|1|Le type prend en charge les nombres sous-normalisés (dénormalisés)|
|**FLT_MANT_DIG**|24|Nombre de bits dans le significande (mantisse)|
|**FLT_MAX**|3,402823466e+38F|Valeur maximale|
|**FLT_MAX_10_EXP**|38|Exposant décimal maximal|
|**FLT_MAX_EXP**|128|Exposant binaire maximal|
|**FLT_MIN**|1,175494351e-38F|Valeur positive normalisée minimale|
|**FLT_MIN_10_EXP**|(-37)|Exposant décimal minimal|
|**FLT_MIN_EXP**|(-125)|Exposant binaire minimal|
|**FLT_RADIX**|2|Radical d’exposant|
|**FLT_TRUE_MIN**|1.401298464e-45F|Valeur sous-normalisée positive minimale|
|**LDBL_DIG**|15|# de chiffres décimaux de précision|
|**LDBL_EPSILON**|2,2204460492503131e-016|Plus petit nombre, comme 1.0 + **LDBL_EPSILON** != 1.0|
|**LDBL_HAS_SUBNORM**|1|Le type prend en charge les nombres sous-normalisés (dénormalisés)|
|**LDBL_MANT_DIG**|53|Nombre de bits dans le significande (mantisse)|
|**LDBL_MAX**|1,7976931348623158e+308|Valeur maximale|
|**LDBL_MAX_10_EXP**|308|Exposant décimal maximal|
|**LDBL_MAX_EXP**|1024|Exposant binaire maximal|
|**LDBL_MIN**|2,2250738585072014E-308|Valeur positive normalisée minimale|
|**LDBL_MIN_10_EXP**|(-307)|Exposant décimal minimal|
|**LDBL_MIN_EXP**|(-1021)|Exposant binaire minimal|
|**_LDBL_RADIX**|2|Radical d’exposant|
|**LDBL_TRUE_MIN**|4.9406564584124654e-324|Valeur sous-normalisée positive minimale|
|**DECIMAL_DIG**|same as **DBL_DECIMAL_DIG**|Chiffres décimaux (doubles) par défaut de précision de l’arrondi|

## <a name="see-also"></a>Voir aussi

[Constantes globales](../c-runtime-library/global-constants.md)
