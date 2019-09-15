---
title: strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l
ms.date: 11/04/2016
api_name:
- wcscoll
- _mbscoll
- _mbscoll_l
- strcoll
- _strcoll_l
- _wcscoll_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcscoll
- _mbscoll
- _tcscoll
- _ftcscoll
helpviewer_keywords:
- code pages, using for string comparisons
- mbscoll function
- wcscoll_l function
- ftcscoll function
- wcscoll function
- _strcoll_l function
- tcscoll function
- _ftcscoll function
- _tcscoll function
- _wcscoll_l function
- _mbscoll function
- strcoll_l function
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
ms.openlocfilehash: 7519b8f41d77ed668bb7da1e8ced18ee13c0a5bf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957881"
---
# <a name="strcoll-wcscoll-_mbscoll-_strcoll_l-_wcscoll_l-_mbscoll_l"></a>strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l

Compare des chaînes en utilisant les paramètres régionaux actifs ou une catégorie d’état de conversion LC_COLLATE spécifiée.

> [!IMPORTANT]
> **_mbscoll** et **_mbscoll_l** ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int strcoll(
   const char *string1,
   const char *string2
);
int wcscoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _strcoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int wcscoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbscoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*string1*, *string2*<br/>
Chaîne terminée par Null à comparer.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne une valeur indiquant la relation de *Chaîne1* à *Chaîne2*, comme suit.

|Valeur de retour|Relation de chaîne1 à chaîne2|
|------------------|----------------------------------------|
|< 0|*Chaîne1* inférieure à *Chaîne2*|
|0|*Chaîne1* identique à *Chaîne2*|
|> 0|*Chaîne1* supérieure à *Chaîne2*|

Chacune de ces fonctions retourne **_NLSCMPERROR** en cas d’erreur. Pour utiliser **_NLSCMPERROR**, incluez l’une ou l’autre chaîne. H ou MBSTRING. Manutention. **wcscoll** peut échouer si *Chaîne1* ou *string2* a la **valeur null** ou contient des codes à caractères larges en dehors du domaine de la séquence de classement. Lorsqu’une erreur se produit, **wcscoll** peut définir **errno** sur **EINVAL**. Pour rechercher une erreur lors d’un appel à **wcscoll**, attribuez la valeur 0 à **errno** , puis activez la case à cocher **errno** après avoir appelé **wcscoll**.

## <a name="remarks"></a>Notes

Chacune de ces fonctions effectue une comparaison sensible à la casse de *string1* et *string2* , en fonction de la page de codes en cours d’utilisation. Ces fonctions ne doivent être utilisées que s’il existe une différence entre l’ordre du jeu de caractères et l’ordre lexicographique des caractères dans la page de codes actuelle, et si cette différence présente un intérêt pour la comparaison de chaînes.

Toutes ces fonctions valident leurs paramètres. Si *string1* ou *string2* est un pointeur null ou si *Count* est supérieur à **INT_MAX**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **_NLSCMPERROR** et attribuent à **errno** la valeur **EINVAL**.

La comparaison des deux chaînes est une opération dépendante des paramètres régionaux dans la mesure où les différents paramètres régionaux ont des règles de classement de caractères qui leur sont propres. Les versions de ces fonctions sans le suffixe **_L** utilisent les paramètres régionaux du thread actuel pour ce comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_L** sont identiques à la fonction correspondante sans suffixe, à ceci près qu’elles utilisent les paramètres régionaux passés en tant que paramètre à la place des paramètres régionaux actuels. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscoll**|**strcoll**|**_mbscoll**|**wcscoll**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**strcoll**|\<string.h>|
|**wcscoll**|\<wchar.h>, \<string.h>|
|**_mbscoll**, **_mbscoll_l**|\<mbstring.h>|
|**_strcoll_l**|\<string.h>|
|**_wcscoll_l**|\<wchar.h>, \<string.h>|

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
