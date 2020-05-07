---
title: isascii, __isascii, iswascii
ms.date: 4/2/2020
api_name:
- iswascii
- __isascii
- _o_iswascii
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
ms.openlocfilehash: 3e04b85c9ce7519593802c21311315d534dce6a5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919783"
---
# <a name="isascii-__isascii-iswascii"></a>isascii, __isascii, iswascii

Détermine si un caractère particulier est un caractère ASCII.

## <a name="syntax"></a>Syntaxe

```C
int __isascii(
   int c
);
int iswascii(
   wint_t c
);

#define isascii __isascii
```

### <a name="parameters"></a>Paramètres

*secteur*<br/>
Entier à tester.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne une valeur différente de zéro si **c** est une représentation particulière d’un caractère ASCII. **__isascii** retourne une valeur différente de zéro si **c** est un caractère ASCII (dans la plage 0x00-0x7F). **iswascii** retourne une valeur différente de zéro si **c** est une représentation à caractères larges d’un caractère ASCII. Chacune de ces routines retourne 0 si **c** ne satisfait pas la condition de test.

## <a name="remarks"></a>Notes 

**__Isascii** et **iswascii** sont implémentées en tant que macros, sauf si la macro de préprocesseur _CTYPE_DISABLE_MACROS est définie.

Pour la compatibilité descendante, **isascii** est implémenté en tant que macro uniquement si [&#95;&#95;STDC&#95;&#95;](../../preprocessor/predefined-macros.md) n’est pas défini ou s’il est défini sur 0. dans le cas contraire, il n’est pas défini.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**isascii**, **__isascii**|C : \<ctype.h><br /><br /> C++ : \<cctype> ou \<ctype.h>|
|**iswascii**|C : \<wctype.h>, \<ctype.h> ou \<wchar.h><br /><br /> C++ : \<cwctype>, \<cctype>, \<wctype.h>, \<ctype.h> ou \<wchar.h>|

Les fonctions **isascii**, **__isascii** et **iswascii** sont spécifiques à Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
