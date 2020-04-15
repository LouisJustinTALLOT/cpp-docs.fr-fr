---
title: ispunct, iswpunct, _ispunct_l, _iswpunct_l
ms.date: 4/2/2020
api_name:
- ispunct
- _iswpunct_l
- iswpunct
- _ispunct_l
- _o_ispunct
- _o_iswpunct
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
- iswpunct
- _istpunct
- ispunct
helpviewer_keywords:
- _istpunct function
- _ispunct_l function
- iswpunct function
- ispunct function
- istpunct function
- ispunct_l function
- _iswpunct_l function
- iswpunct_l function
ms.assetid: 94403240-85c8-40a4-9c2b-e3e95c729c76
ms.openlocfilehash: 3072f147d2adff2c50304d2d2052947ca32cb060
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342809"
---
# <a name="ispunct-iswpunct-_ispunct_l-_iswpunct_l"></a>ispunct, iswpunct, _ispunct_l, _iswpunct_l

Détermine si un entier représente un caractère de ponctuation.

## <a name="syntax"></a>Syntaxe

```C
int ispunct(
   int c
);
int iswpunct(
   wint_t c
);
int _ispunct_l(
   int c,
   _locale_t locale
);
int _iswpunct_l(
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

Chacune de ces routines retourne nonzero si *c* est une représentation particulière d’un caractère de ponctuation. **ispunct renvoie** une valeur nonzero pour tout personnage imprimable qui n’est pas un personnage de l’espace ou un personnage pour lequel **isalnum** est nonzero. **iswpunct** retourne une valeur nonzero pour tout personnage grand imprimable qui n’est ni le caractère large de l’espace, ni un caractère large pour lequel **iswalnum** est nonzero. Chacune de ces routines retourne 0 si *c* ne satisfait pas l’état d’essai.

Le résultat de l’état d’essai de la fonction **ispunct** dépend du **LC_CTYPE** cadre de la catégorie du lieu; voir [setlocale, _wsetlocale](setlocale-wsetlocale.md) pour plus d’informations. Les versions de ces fonctions qui n’ont pas le **suffixe _l** utilisent le lieu actuel pour tout comportement local-dépendant; les versions qui ont le **suffixe _l** sont identiques, sauf qu’ils utilisent le lieu qui est passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Le comportement de **l’ispunct** et **_ispunct_l** n’est pas défini si *c* n’est pas EOF ou dans la gamme 0 à 0xFF, inclusive. Lorsqu’une bibliothèque CRT débagé est utilisée et *que c* n’est pas l’une de ces valeurs, les fonctions soulèvent une affirmation.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **Istpunct**|**ispunct**|[_ismbcpunct](ismbcgraph-functions.md)|**iswpunct**|

## <a name="remarks"></a>Notes

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**ispunct**|\<ctype.h>|
|**iswpunct**|\<ctype.h> ou \<wchar.h>|
|**_ispunct_l**|\<ctype.h>|
|**_iswpunct_l**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
