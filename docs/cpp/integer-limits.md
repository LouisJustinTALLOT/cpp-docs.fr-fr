---
title: Limites d’entier | Documents Microsoft
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 656873dc510f53fc05250a28c61cc452078c4aca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420609"
---
# <a name="integer-limits"></a>Limites d'entier

**Section spécifique à Microsoft**

Les limites pour les types d'entiers sont répertoriées dans le tableau ci-dessous. Ces limites sont également définies dans le fichier d’en-tête standard < limits.h >.

## <a name="limits-on-integer-constants"></a>Limites appliquées aux constantes entières

|Constante|Signification|Value|
|--------------|-------------|-----------|
|**CHAR_BIT**|Nombre de bits dans la plus petite variable qui n'est pas un champ de bits|8|
|**SCHAR_MIN**|Valeur minimale d'une variable de type **signed char**.|-128|
|**SCHAR_MAX**|Valeur maximale d'une variable de type **signed char**.|127|
|**UCHAR_MAX**|Valeur maximale d’une variable de type **unsigned char**.|255 (0xff)|
|**CHAR_MIN**|Valeur minimale d’une variable de type **char**.|-128 ; 0 si l'option /J est utilisée|
|**CHAR_MAX**|Valeur maximale d’une variable de type **char**.|127 ; 255 si l'option /J est utilisée|
|**MB_LEN_MAX**|Nombre maximal d'octets dans une constante à multiples caractères|5|
|**SHRT_MIN**|Valeur minimale d'une variable de type **short**.|-32768|
|**SHRT_MAX**|Valeur maximale d'une variable de type **short**.|32767|
|**USHRT_MAX**|Valeur maximale d'une variable de type **unsigned short**.|65535 (0xffff)|
|**INT_MIN**|Valeur minimale d’une variable de type **int**.|-2147483648|
|**INT_MAX**|Valeur maximale d’une variable de type **int**.|2147483647|
|**UINT_MAX**|Valeur maximale d’une variable de type **unsigned int**.|4294967295 (0xffffffff)|
|**LONG_MIN**|Valeur minimale d'une variable de type **long**.|-2147483648|
|**LONG_MAX**|Valeur maximale d'une variable de type **long**.|2147483647|
|**ULONG_MAX**|Valeur maximale d’une variable de type **unsigned long**.|4294967295 (0xffffffff)|
|**LLONG_MIN**|Valeur minimale d’une variable de type **long**|-9223372036854775808|
|**LLONG_MAX**|Valeur maximale d’une variable de type **long**|9223372036854775807|
|**ULLONG_MAX**|Valeur maximale d’une variable de type **long long non signé**|18446744073709551615 (0xffffffffffffffff)|

Si une valeur dépasse la plus grande représentation d'entier, le compilateur Microsoft génère une erreur.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Limites des valeurs à virgule flottante](../cpp/floating-limits.md)  
