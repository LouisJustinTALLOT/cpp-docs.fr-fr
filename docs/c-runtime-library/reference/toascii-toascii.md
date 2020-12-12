---
description: 'En savoir plus sur : toascii, __toascii'
title: toascii, __toascii
ms.date: 11/04/2016
api_name:
- __toascii
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
ms.openlocfilehash: 9f1718da5e7d701bb6cc6ea68c1e21b6fe4283f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318349"
---
# <a name="toascii-__toascii"></a>toascii, __toascii

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

## <a name="return-value"></a>Valeur renvoyée

**__toascii** convertit la valeur de *c* en plage ASCII 7 bits et retourne le résultat. Il n’existe aucune valeur de retour réservée pour indiquer une erreur.

## <a name="remarks"></a>Notes

La routine **__toascii** convertit le caractère donné en un caractère ASCII en le tronquant aux 7 bits de poids faible. Aucune autre transformation n’est appliquée.

La routine **__toascii** est définie en tant que macro, sauf si la macro de préprocesseur _CTYPE_DISABLE_MACROS est définie. Pour la compatibilité descendante, **toascii** est défini comme une macro uniquement lorsque [&#95;&#95;STDC&#95;&#95;](../../preprocessor/predefined-macros.md) n’est pas défini ou est défini sur 0 ; dans le cas contraire, il n’est pas défini.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**toascii**, **__toascii**|Secteur \<ctype.h><br /><br /> C++ : \<cctype> ou \<ctype.h>|

La macro **toascii** est une extension POSIX, et **__toascii** est une implémentation spécifique à Microsoft de l’extension POSIX. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[is, ISW, routines](../../c-runtime-library/is-isw-routines.md)<br/>
[à des fonctions](../../c-runtime-library/to-functions.md)<br/>
