---
description: En savoir plus sur les limites des entiers C et C++
title: Limites des entiers C et C++
ms.date: 10/21/2019
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
ms.openlocfilehash: c9d15e5366acb482f688e1c5020c43ee83e4e802
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292973"
---
# <a name="c-and-c-integer-limits"></a>Limites des entiers C et C++

**Spécifique à Microsoft**

Les limites pour les types d’entiers en C et C++ sont répertoriées dans le tableau suivant. Ces limites sont définies dans le fichier d’en-tête standard C `<limits.h>` . L’en-tête de la bibliothèque standard C++ `<limits>` comprend `<climits>` , qui comprend `<limits.h>` .

Microsoft C permet également la déclaration de variables de type entier dimensionnées, qui sont des types intégraux de 8, 16, 32 ou 64 bits. Pour plus d’informations sur les entiers dimensionnés en C, consultez [types d’entiers dimensionnés](../c-language/c-sized-integer-types.md).

## <a name="limits-on-integer-constants"></a>Limites appliquées aux constantes entières

|**Constant**|Signification|Valeur|
|------------------|-------------|-----------|
|**CHAR_BIT**|Nombre de bits dans la plus petite variable qui n'est pas un champ de bits|8|
|**SCHAR_MIN**|Valeur minimale d’une variable de type **`signed char`** .|-128|
|**SCHAR_MAX**|Valeur maximale d’une variable de type **`signed char`** .|127|
|**UCHAR_MAX**|Valeur maximale d’une variable de type **`unsigned char`** .|255 (0xff)|
|**CHAR_MIN**|Valeur minimale d’une variable de type **`char`** .|-128 ; 0 si l'option /J est utilisée|
|**CHAR_MAX**|Valeur maximale d’une variable de type **`char`** .|127 ; 255 si l'option /J est utilisée|
|**MB_LEN_MAX**|Nombre maximal d'octets dans une constante à multiples caractères|5|
|**SHRT_MIN**|Valeur minimale d’une variable de type **`short`** .|-32768|
|**SHRT_MAX**|Valeur maximale d’une variable de type **`short`** .|32767|
|**USHRT_MAX**|Valeur maximale d’une variable de type **`unsigned short`** .|65535 (0xffff)|
|**INT_MIN**|Valeur minimale d’une variable de type **`int`** .|-2147483647 - 1|
|**INT_MAX**|Valeur maximale d’une variable de type **`int`** .|2147483647|
|**UINT_MAX**|Valeur maximale d’une variable de type **`unsigned int`** .|4294967295 (0xffffffff)|
|**LONG_MIN**|Valeur minimale d’une variable de type **`long`** .|-2147483647 - 1|
|**LONG_MAX**|Valeur maximale d’une variable de type **`long`** .|2147483647|
|**ULONG_MAX**|Valeur maximale d’une variable de type **`unsigned long`** .|4294967295 (0xffffffff)|
|**LLONG_MIN**|Valeur minimale d’une variable de type **`long long`** .|-9 223 372 036 854 775 807-1|
|**LLONG_MAX**|Valeur maximale d’une variable de type **`long long`** .|9,223,372,036,854,775,807|
|**ULLONG_MAX**|Valeur maximale d’une variable de type **`unsigned long long`** .|18446744073709551615 (0xFFFFFFFFFFFFFFFF)|

Si une valeur dépasse la plus grande représentation d'entier, le compilateur Microsoft génère une erreur.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Constantes entières C](../c-language/c-integer-constants.md)
