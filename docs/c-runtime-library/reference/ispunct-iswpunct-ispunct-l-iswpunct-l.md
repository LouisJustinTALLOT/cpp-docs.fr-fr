---
title: ispunct, iswpunct, _ispunct_l, _iswpunct_l
ms.date: 11/04/2016
api_name:
- ispunct
- _iswpunct_l
- iswpunct
- _ispunct_l
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
ms.openlocfilehash: 54c51c612cf3b491b49d7e141df34ed5b4415520
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953701"
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

*c*<br/>
Entier à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne une valeur différente de zéro si *c* est une représentation particulière d’un caractère de ponctuation. **ispunct** retourne une valeur différente de zéro pour tout caractère imprimable qui n’est pas un espace ou un caractère pour lequel **isalnum** est différent de zéro. **iswpunct** retourne une valeur différente de zéro pour tout caractère élargi imprimable qui n’est ni le caractère grand espace ni un caractère élargi pour lequel **iswalnum** est différent de zéro. Chacune de ces routines retourne 0 si *c* ne satisfait pas la condition de test.

Le résultat de la condition de test pour la fonction **ispunct** dépend du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations [, consultez setlocale, _wsetlocale](setlocale-wsetlocale.md) . Les versions de ces fonctions qui n’ont pas le suffixe **_L** utilisent les paramètres régionaux actuels pour tout comportement dépendant des paramètres régionaux ; les versions qui ont le suffixe **_L** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Le comportement de **ispunct** et **_ispunct_l** n’est pas défini si *c* n’est pas EOF ni dans la plage 0 à 0xFF, inclus. Quand une bibliothèque CRT de débogage est utilisée et que *c* n’est pas l’une de ces valeurs, les fonctions déclenchent une assertion.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istpunct**|**ispunct**|[_ismbcpunct](ismbcgraph-functions.md)|**iswpunct**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**ispunct**|\<ctype.h>|
|**iswpunct**|\<ctype.h> ou \<wchar.h>|
|**_ispunct_l**|\<ctype.h>|
|**_iswpunct_l**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
