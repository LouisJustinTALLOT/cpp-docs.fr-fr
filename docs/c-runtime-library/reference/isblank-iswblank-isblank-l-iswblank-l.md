---
title: isblank, iswblank, _isblank_l, _iswblank_l
ms.date: 4/2/2020
api_name:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
- _o_isblank
- _o_iswblank
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
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
ms.openlocfilehash: 736a0791f1e5ee4b11e61164861cc6dc0c7a9c87
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343895"
---
# <a name="isblank-iswblank-_isblank_l-_iswblank_l"></a>isblank, iswblank, _isblank_l, _iswblank_l

Détermine si un entier représente un caractère vide.

## <a name="syntax"></a>Syntaxe

```C
int isblank(
   int c
);
int iswblank(
   wint_t c
);
int _isblank_l(
   int c,
   _locale_t locale
);
int _iswblank_l(
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

Chacune de ces routines renvoie nonzero si *c* est une représentation particulière d’un espace ou un caractère d’onglet horizontal, ou est l’un d’un ensemble local spécifique de caractères qui sont utilisés pour séparer les mots dans une ligne de texte. **isblank** renvoie une valeur non zéro si *c* est un personnage spatial (0x20) ou un caractère d’onglet horizontal (0x09). Le résultat de l’état d’essai pour les fonctions **isblank** dépend de la **LC_CTYPE** cadre de catégorie du lieu; pour plus d’informations, voir [setlocale, _wsetlocale](setlocale-wsetlocale.md). Les versions de ces fonctions qui n’ont pas le **suffixe _l** utilisent le lieu actuel pour tout comportement local-dépendant; les versions qui ont le **suffixe _l** sont identiques, sauf qu’ils utilisent le lieu qui est passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

**iswblank** retourne une valeur non zéro si *c* est un caractère large qui correspond à un espace standard ou un caractère d’onglet horizontal.

Le comportement de **l’isblank** et **_isblank_l** n’est pas défini si *c n’est* pas EOF ou dans la gamme 0 à 0xFF, inclusive. Lorsqu’une bibliothèque CRT débagé est utilisée et *que c* n’est pas l’une de ces valeurs, les fonctions soulèvent une affirmation.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**isblank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="remarks"></a>Notes

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**isblank**|\<ctype.h>|
|**iswblank**|\<ctype.h> ou \<wchar.h>|
|**_isblank_l**|\<ctype.h>|
|**_iswblank_l**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
