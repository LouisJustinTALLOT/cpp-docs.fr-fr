---
title: isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l
ms.date: 4/2/2020
api_name:
- _iswxdigit_l
- iswxdigit
- isxdigit
- _isxdigit_l
- _o_iswxdigit
- _o_isxdigit
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswxdigit
- isxdigit
- _istxdigit
helpviewer_keywords:
- isxdigit function
- istxdigit function
- _iswxdigit_l function
- _istxdigit function
- _isxdigit_l function
- iswxdigit_l function
- isxdigit_l function
- hexadecimal characters
- iswxdigit function
ms.assetid: c8bc5146-0b58-4e3f-bee3-f2318dd0f829
ms.openlocfilehash: c2f6e7956048a30313ba8eb9a11a37fccdc49197
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342743"
---
# <a name="isxdigit-iswxdigit-_isxdigit_l-_iswxdigit_l"></a>isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l

Détermine si un entier représente un caractère qui est un chiffre hexadécimal.

## <a name="syntax"></a>Syntaxe

```C
int isxdigit(
   int c
);
int iswxdigit(
   wint_t c
);
int _isxdigit_l(
   int c,
   _locale_t locale
);
int _iswxdigit_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*C*<br/>
Entier à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne nonzero si *c* est une représentation particulière d’un chiffre hexadecimal. **isxdigit** retourne une valeur non zéro si *c* est un chiffre hexadecimal (A - F, a - f, ou 0 - 9). **iswxdigit** retourne une valeur nonzero si *c* est un personnage large qui correspond à un caractère hexadecimal chiffre. Chacune de ces routines retourne 0 si *c* ne satisfait pas l’état d’essai.

Pour le lieu "C", la fonction **iswxdigit** ne prend pas en charge les caractères hexadecimal Unicode.

Les versions de ces fonctions qui ont le **suffixe _l** utilisent le lieu qui est passé au lieu de la localisation actuelle pour leur comportement local-dépendant. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Le comportement de **l’isxdigit** et **_isxdigit_l** n’est pas défini si *c* n’est pas EOF ou dans la gamme 0 à 0xFF, inclusivement. Lorsqu’une bibliothèque CRT débagé est utilisée et *que c* n’est pas l’une de ces valeurs, les fonctions soulèvent une affirmation.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istxdigit**|**isxdigit**|**isxdigit**|**iswxdigit**|

## <a name="remarks"></a>Notes

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**isxdigit**|\<ctype.h>|
|**iswxdigit**|\<ctype.h> ou \<wchar.h>|
|**_isxdigit_l**|\<ctype.h>|
|**_iswxdigit_l**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
