---
title: isprint, iswprint, _isprint_l, _iswprint_l
ms.date: 4/2/2020
api_name:
- iswprint
- isprint
- _isprint_l
- _iswprint_l
- _o_isprint
- _o_iswprint
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
- iswprint
- _istprint
- isprint
helpviewer_keywords:
- _istprint function
- iswprint function
- _iswprint_l function
- isprint_l function
- istprint function
- isprint function
- iswprint_l function
- _isprint_l function
ms.assetid: a8bbcdb0-e8d0-4d8c-ae4e-56d3bdee6ca3
ms.openlocfilehash: f09168e8e010fb59d748c109d4a41c533318e2eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342883"
---
# <a name="isprint-iswprint-_isprint_l-_iswprint_l"></a>isprint, iswprint, _isprint_l, _iswprint_l

Détermine si un entier représente un caractère imprimable.

## <a name="syntax"></a>Syntaxe

```C
int isprint(
   int c
);
int iswprint(
   wint_t c
);
int _isprint_l(
   int c,
   _locale_t locale
);
int _iswprint_l(
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

Chacune de ces routines retourne nonzero si *c* est une représentation particulière d’un caractère imprimable. **isprint renvoie** une valeur non zéro si *c* est un personnage imprimable, cela inclut le caractère spatial (0x20 - 0x7E). **iswprint** retourne une valeur non zéro si *c* est un personnage grand imprimable, cela inclut le caractère large de l’espace. Chacune de ces routines retourne 0 si *c* ne satisfait pas l’état d’essai.

Le résultat de l’état d’essai pour ces fonctions dépend de la **LC_CTYPE’établissement** de la catégorie du lieu; voir [setlocale, _wsetlocale](setlocale-wsetlocale.md) pour plus d’informations. Les versions de ces fonctions qui n’ont pas le **suffixe _l** utilisent le lieu actuel pour tout comportement local-dépendant; les versions qui ont le **suffixe _l** sont identiques, sauf qu’ils utilisent le lieu qui est passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Le comportement de **l’empreinte et** **de l'_isprint_l** n’est pas défini si *c* n’est pas EOF ou dans la gamme 0 à 0xFF, inclusive. Lorsqu’une bibliothèque CRT débagé est utilisée et *que c* n’est pas l’une de ces valeurs, les fonctions soulèvent une affirmation.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_unicode défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**-** **istprint**|**isprint**|[_ismbcprint](ismbcgraph-functions.md)|**iswprint**|

## <a name="remarks"></a>Notes

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**isprint**|\<ctype.h>|
|**iswprint**|\<ctype.h> ou \<wchar.h>|
|**_isprint_l**|\<ctype.h>|
|**_iswprint_l**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
