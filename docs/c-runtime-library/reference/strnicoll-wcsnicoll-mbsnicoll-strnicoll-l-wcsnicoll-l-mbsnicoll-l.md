---
title: _strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnicoll_l
- _mbsnicoll
- _wcsnicoll_l
- _strnicoll
- _strnicoll_l
- _wcsnicoll
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcshicoll_l
- _ftcsncicoll
- strnicoll_l
- _wcsnicoll
- mbsnicoll_l
- _strnicoll
- mbsnicoll
- _ftcsnicoll
- wcsnicoll
- _tcsnicoll
- _mbsnicoll
- strinicoll
- _tcsncicoll
dev_langs:
- C++
helpviewer_keywords:
- code pages, using for string comparisons
- ftcsncicoll function
- mbsnicoll_l function
- _ftcsnicoll function
- mbsnicoll function
- _tcsnicoll function
- _wcsnicoll_l function
- _mbsnicoll function
- tcsncicoll function
- strnicoll function
- _ftcsncicoll function
- wcsnicoll_l function
- _mbsnicoll_l function
- _tcsncicoll function
- strnicoll_l function
- wcsnicoll function
- _strnicoll_l function
- _wcsnicoll function
- ftcsnicoll function
- strings [C++], comparing by code page
- tcsnicoll function
- _strnicoll function
ms.assetid: abf0c569-725b-428d-9ff2-924f430104b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f8592f40dda312f138351526509b69eadf9647c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32416525"
---
# <a name="strnicoll-wcsnicoll-mbsnicoll-strnicolll-wcsnicolll-mbsnicolll"></a>_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l

Compare les chaînes à partir des informations propres aux paramètres régionaux.

> [!IMPORTANT]
> **_mbsnicoll** et **_mbsnicoll_l** ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _strnicoll(
   const char *string1,
   const char *string2,
   size_t count
);
int _wcsnicoll(
   const wchar_t *string1,
   const wchar_t *string2 ,
   size_t count
);
int _mbsnicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _strnicoll_l(
   const char *string1,
   const char *string2,
   size_t count,
   _locale_t locale
);
int _wcsnicoll_l(
   const wchar_t *string1,
   const wchar_t *string2 ,
   size_t count,
   _locale_t locale
);
int _mbsnicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*string1*, *chaîne2*<br/>
Chaînes se terminant par un caractères Null à comparer.

*count*<br/>
Nombre de caractères à comparer.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne une valeur qui indique la relation entre les sous-chaînes de *string1* et *chaîne2*, comme suit.

|Valeur de retour|Relation de chaîne1 à chaîne2|
|------------------|----------------------------------------|
|< 0|*string1* moins *chaîne2*|
|0|*string1* identique à *chaîne2*|
|> 0|*string1* supérieur *chaîne2*|

Chacune de ces fonctions retourne **_NLSCMPERROR**. Pour utiliser **_NLSCMPERROR**, inclure une chaîne. H ou MBSTRING. H. **_wcsnicoll** peut échouer si *string1* ou *chaîne2* contient les codes de caractères larges en dehors du domaine de la séquence de classement. Lorsqu’une erreur se produit, **_wcsnicoll** peuvent définir **errno** à **EINVAL**. Pour rechercher une erreur sur un appel à **_wcsnicoll**, définissez **errno** à 0, puis vérifiez **errno** après avoir appelé **_wcsnicoll**.

## <a name="remarks"></a>Notes

Chacune de ces fonctions effectue une comparaison respectant la casse de la première *nombre* caractères *string1* et *chaîne2* en fonction de la page de codes. Ces fonctions ne doivent être utilisées que s’il existe une différence entre l’ordre du jeu de caractères et l’ordre lexicographique des caractères dans la page de codes, et si cette différence présente un intérêt pour la comparaison de chaînes. Les versions de ces fonctions sans le **_l** suffixe utiliser la page de paramètres régionaux et le code en cours. Les versions avec le **_l** suffixe sont identiques, sauf qu’elles utilisent les paramètres régionaux passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Toutes ces fonctions valident leurs paramètres. Si le paramètre *string1* ou *chaîne2* est un pointeur null, ou si le nombre est supérieur à **INT_MAX**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [ Validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **_NLSCMPERROR** et **errno** à **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncicoll**|**_strnicoll**|**_mbsnbicoll**|**_wcsnicoll**|
|**_tcsnicoll**|**_strnicoll**|[_mbsnbicoll](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|**_wcsnicoll**|
|**_tcsnicoll_l**|**_strnicoll_l**|**_mbsnbicoll_l**|**_wcsnicoll_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_strnicoll**, **_strnicoll_l**|\<string.h>|
|**_wcsnicoll**, **_wcsnicoll_l**|\<wchar.h> ou \<string.h>|
|**_mbsnicoll**, **_mbsnicoll_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
