---
description: 'En savoir plus sur : IsBlank, iswblank, _isblank_l, _iswblank_l'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a2731468cda3a2d3bf059133f116b22fa2b019f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321111"
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

*c*<br/>
Entier à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

Chacune de ces routines retourne une valeur différente de zéro si *c* est une représentation particulière d’un espace ou d’un caractère de tabulation horizontale, ou est l’un des jeux de caractères spécifiques aux paramètres régionaux utilisés pour séparer les mots dans une ligne de texte. **ISBLANK** retourne une valeur différente de zéro si *c* est un espace (0x20) ou un caractère de tabulation horizontale (0x09). Le résultat de la condition de test pour les fonctions **ISBLANK** dépend du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md). Les versions de ces fonctions qui n’ont pas le suffixe **_L** utilisent les paramètres régionaux actuels pour tout comportement dépendant des paramètres régionaux ; les versions qui ont le suffixe **_L** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

**iswblank** retourne une valeur différente de zéro si *c* est un caractère élargi qui correspond à un espace standard ou un caractère de tabulation horizontale.

Le comportement de **ISBLANK** et **_isblank_l** n’est pas défini si *c* n’est pas EOF ni dans la plage 0 à 0xFF, inclus. Quand une bibliothèque CRT de débogage est utilisée et que *c* n’est pas l’une de ces valeurs, les fonctions déclenchent une assertion.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**IsBlank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="remarks"></a>Notes

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**IsBlank**|\<ctype.h>|
|**iswblank**|\<ctype.h> ou \<wchar.h>|
|**_isblank_l**|\<ctype.h>|
|**_iswblank_l**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification des caractères](../../c-runtime-library/character-classification.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[is, ISW, routines](../../c-runtime-library/is-isw-routines.md)<br/>
