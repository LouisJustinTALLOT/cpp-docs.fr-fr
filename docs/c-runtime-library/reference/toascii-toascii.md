---
title: toascii, __toascii | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __toascii
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
dev_langs:
- C++
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cead516a7e298e56d13d8f1a09a054057796ca64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408420"
---
# <a name="toascii-toascii"></a>toascii, __toascii

Convertit des caractères au format ASCII 7 bits par troncation.

## <a name="syntax"></a>Syntaxe

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère à convertir.

## <a name="return-value"></a>Valeur de retour

**__toascii** convertit la valeur de *c* de plage pour le code ASCII 7 bits et retourne le résultat. Il n’existe aucune valeur de retour réservée pour indiquer une erreur.

## <a name="remarks"></a>Notes

Le **__toascii** routine convertit le caractère donné en un caractère ASCII en tronquant pour les 7 bits de poids faible. Aucune autre transformation n’est appliquée.

Le **__toascii** routine est définie comme une macro, sauf si la macro de préprocesseur _CTYPE_DISABLE_MACROS est définie. Pour la compatibilité descendante, **toascii** est défini comme macro uniquement lorsque [ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md) n’est pas défini ou est défini sur 0 ; sinon, il n’est pas défini.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**ToAscii**, **__toascii**|C : \<ctype.h><br /><br /> C++ : \<cctype> ou \<ctype.h>|

Le **toascii** (macro) est une extension de POSIX, et **__toascii** est une implémentation spécifique à Microsoft de l’extension POSIX. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
[to, fonctions](../../c-runtime-library/to-functions.md)<br/>
