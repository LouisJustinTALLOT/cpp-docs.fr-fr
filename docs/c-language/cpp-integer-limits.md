---
title: Limites d’entier C++ | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02a4194d69bf07d27777ad30cf9ed0e5794c04c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136281"
---
# <a name="c-integer-limits"></a>Limites d'entier C++

**Section spécifique à Microsoft**

Les limites pour les types d'entiers sont répertoriées dans le tableau ci-dessous. Ces limites sont définies dans le fichier d'en-tête standard LIMITS.H. Microsoft C permet également la déclaration de variables de type entier dimensionnées, qui sont des types intégraux d'une taille de 8, 16 ou 32 bits. Pour plus d'informations sur les entiers dimensionnés, consultez [Types d'entiers dimensionnés](../c-language/c-sized-integer-types.md).

## <a name="limits-on-integer-constants"></a>Limites appliquées aux constantes entières

|**Constante**|Signification|Value|
|------------------|-------------|-----------|
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
|**INT_MIN**|Valeur minimale d’une variable de type **int**.|-2147483647 - 1|
|**INT_MAX**|Valeur maximale d’une variable de type **int**.|2147483647|
|**UINT_MAX**|Valeur maximale d’une variable de type **unsigned int**.|4294967295 (0xffffffff)|
|**LONG_MIN**|Valeur minimale d'une variable de type **long**.|-2147483647 - 1|
|**LONG_MAX**|Valeur maximale d'une variable de type **long**.|2147483647|
|**ULONG_MAX**|Valeur maximale d’une variable de type **unsigned long**.|4294967295 (0xffffffff)|

Si une valeur dépasse la plus grande représentation d'entier, le compilateur Microsoft génère une erreur.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Constantes entières C](../c-language/c-integer-constants.md)
