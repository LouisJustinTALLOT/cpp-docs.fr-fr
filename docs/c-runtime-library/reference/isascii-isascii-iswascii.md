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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: aeb9c27fee4d179cc16caa50c6f0aae521402beb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343911"
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

*C*<br/>
Entier à tester.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne nonzero si **c** est une représentation particulière d’un caractère ASCII. **__isascii** retourne une valeur non zéro si **c** est un caractère ASCII (dans la gamme 0x00 - 0x7F). **iswascii** retourne une valeur non zéro si **c** est une représentation à caractère large d’un caractère ASCII. Chacune de ces routines retourne 0 si **c** ne satisfait pas l’état d’essai.

## <a name="remarks"></a>Notes

Les **deux __isascii** et **iswascii** sont implémentées comme macros à moins que le macro-_CTYPE_DISABLE_MACROS préprocesseur soit défini.

Pour la compatibilité rétrograde, **isascii n’est** mis en œuvre comme macro que si [&#95;&#95;&#95;&#95;STDC](../../preprocessor/predefined-macros.md) n’est pas définie ou est définie comme 0; sinon il n’est pas défini.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**isascii**, **__isascii**|C : \<ctype.h><br /><br /> C++ : \<cctype> ou \<ctype.h>|
|**iswascii**|C : \<wctype.h>, \<ctype.h> ou \<wchar.h><br /><br /> C++ : \<cwctype>, \<cctype>, \<wctype.h>, \<ctype.h> ou \<wchar.h>|

Les **fonctions isascii**, **__isascii** et **iswascii** sont spécifiques à Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
