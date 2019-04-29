---
title: isascii, __isascii, iswascii
ms.date: 11/04/2016
apiname:
- iswascii
- __isascii
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: d150e7bb335dc77ed86f445128eebf97b8be5ac3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287467"
---
# <a name="isascii-isascii-iswascii"></a>isascii, __isascii, iswascii

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

*c*<br/>
Entier à tester.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne différente de zéro si **c** est une représentation particulière d’un caractère ASCII. **__isascii** retourne une valeur différente de zéro si **c** est un caractère ASCII (dans la plage 0 x 00 - 0x7F). **iswascii** retourne une valeur différente de zéro si **c** est une représentation de caractères larges d’un caractère ASCII. Chacune de ces routines retourne 0 si **c** ne satisfait pas la condition de test.

## <a name="remarks"></a>Notes

Les deux **__isascii** et **iswascii** sont implémentées en tant que macros, sauf si la macro de préprocesseur _CTYPE_DISABLE_MACROS est définie.

Pour la compatibilité descendante, **isascii** est implémenté en tant que macro que si [ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md) n’est pas défini ou est définie comme 0 ; sinon, il n’est pas défini.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**isascii**, **__isascii**|C : \<ctype.h><br /><br /> C++ : \<cctype> ou \<ctype.h>|
|**iswascii**|C : \<wctype.h>, \<ctype.h> ou \<wchar.h><br /><br /> C++ : \<cwctype>, \<cctype>, \<wctype.h>, \<ctype.h> ou \<wchar.h>|

Le **isascii**, **__isascii** et **iswascii** fonctions sont propres à Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
