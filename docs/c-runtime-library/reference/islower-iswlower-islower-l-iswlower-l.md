---
description: 'En savoir plus sur : IsLower, iswlower, _islower_l, _iswlower_l'
title: islower, iswlower, _islower_l, _iswlower_l
ms.date: 4/2/2020
api_name:
- iswlower
- _islower_l
- islower
- _iswlower_l
- _o_islower
- _o_iswlower
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _istlower
- islower
- _ismbclower_l
- _liswlower_l
- _istlower_l
- _iswlower_l
- _islower _l
- _islower_l
- iswlower
helpviewer_keywords:
- _islower _l function
- _ismbclower_l function
- islower function
- _iswlower_l function
- _liswlower_l function
- _istlower_l function
- istlower function
- _istlower function
- iswlower function
- _islower_l function
ms.assetid: fcc3b70a-2b47-45fd-944d-e5c1942e6457
ms.openlocfilehash: cf4b127e46a18308da9e51880b7c10b2e2f4aa06
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256443"
---
# <a name="islower-iswlower-_islower_l-_iswlower_l"></a>islower, iswlower, _islower_l, _iswlower_l

Détermine si un entier représente un caractère minuscule.

## <a name="syntax"></a>Syntaxe

```C
int islower(
   int c
);
int iswlower(
   wint_t c
);
int islower_l(
   int c,
   _locale_t locale
);
int _iswlower_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Entier à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

Chacune de ces routines retourne une valeur différente de zéro si *c* est une représentation particulière d’un caractère minuscule. **IsLower** retourne une valeur différente de zéro si *c* est un caractère minuscule (a-z). **iswlower** retourne une valeur différente de zéro si *c* est un caractère élargi qui correspond à une lettre minuscule, ou si *c* est l’un des jeux de caractères larges définis par l’implémentation pour lesquels aucun des **iswcntrl**, **iswdigit**, **iswpunct** ou **iswspace** n’est différent de zéro. Chacune de ces routines retourne 0 si *c* ne satisfait pas la condition de test.

Les versions de ces fonctions qui ont le suffixe **_L** utilisent les paramètres régionaux qui sont passés au lieu des paramètres régionaux actuels pour leur comportement dépendant des paramètres régionaux. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Le comportement de **IsLower** et **_islower_l** n’est pas défini si *c* n’est pas EOF ni dans la plage 0 à 0xFF, inclus. Quand une bibliothèque CRT de débogage est utilisée et que *c* n’est pas l’une de ces valeurs, les fonctions déclenchent une assertion.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istlower**|**islower**|[_ismbclower](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**iswlower**|
|**_istlower_l**|`_islower _l`|[_ismbclower_l](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**_liswlower_l**|

## <a name="remarks"></a>Notes

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**islower**|\<ctype.h>|
|**iswlower**|\<ctype.h> ou \<wchar.h>|
|**_islower_l**|\<ctype.h>|
|**_swlower_l**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification des caractères](../../c-runtime-library/character-classification.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[is, ISW, routines](../../c-runtime-library/is-isw-routines.md)<br/>
