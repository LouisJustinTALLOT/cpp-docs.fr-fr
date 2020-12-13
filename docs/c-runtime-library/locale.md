---
description: 'En savoir plus sur : paramètres régionaux'
title: Paramètres régionaux
ms.date: 04/11/2018
f1_keywords:
- c.international
helpviewer_keywords:
- localization, locale
- country information
- language information routines
- setlocale function
- locale routines
ms.assetid: 442f8112-9288-44d7-be3c-15d22652093a
ms.openlocfilehash: 660a4fb0103de8c1ac06272c711e02fcd6d12289
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331073"
---
# <a name="locale"></a>Paramètres régionaux

Les *paramètres régionaux* font référence aux paramètres de pays/région et de langue que vous pouvez utiliser pour personnaliser votre programme. Certaines catégories dépendantes des paramètres régionaux incluent les formats d'affichage des dates et des valeurs monétaires. Pour plus d’informations, consultez [Catégories de paramètres régionaux](../c-runtime-library/locale-categories.md).

Utilisez la fonction [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) pour modifier ou interroger certaines ou toutes les informations relatives aux paramètres régionaux du programme ou thread actif, tout en utilisant les fonctions sans le suffixe **_l**. Les fonctions avec le suffixe **_l** utilisent le paramètre locale qui leur est passé pour ses paramètres régionaux, uniquement pendant l’exécution de cette fonction. Pour créer des paramètres régionaux à utiliser avec une fonction dotée d’un suffixe **_l**, utilisez [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md). Pour libérer ces paramètres régionaux, utilisez [_free_locale](../c-runtime-library/reference/free-locale.md). Pour obtenir les paramètres régionaux actuels, utilisez [_get_current_locale](../c-runtime-library/reference/get-current-locale.md).

Utilisez [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) pour déterminer si chaque thread possède ses propres paramètres régionaux, ou si tous les threads d’un programme partagent les mêmes paramètres régionaux. Pour plus d’informations, consultez [Paramètres régionaux et pages de codes](../text/locales-and-code-pages.md).

Des versions plus sécurisées des fonctions contenues dans le tableau suivant sont disponibles. Elles sont indiquées par le suffixe **_s** (« sécurisé »). Pour plus d'informations, consultez [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="locale-dependent-routines"></a>Routines dépendantes des paramètres régionaux

|Routine|Utilisation|Dépendance du paramètre de catégorie **setlocale**|
|-------------|---------|---------------------------------------------|
|[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convertir un caractère en valeur à virgule flottante|**LC_NUMERIC**|
|[atoi, _atoi_l, _wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Convertir un caractère en valeur entière|**LC_NUMERIC**|
|[_atoi64, _atoi64_l, _wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Convertir un caractère en valeur entière 64 bits|**LC_NUMERIC**|
|[atol, _atol_l, _wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Convertir un caractère en valeur de type long|**LC_NUMERIC**|
|[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Convertir un caractère en valeur de type long double|**LC_NUMERIC**|
|[is (routines)](../c-runtime-library/is-isw-routines.md)|Tester un entier donné pour une condition particulière.|**LC_CTYPE**|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Tester l'octet de tête|**LC_CTYPE**|
|[localeconv](../c-runtime-library/reference/localeconv.md)|Lire les valeurs appropriées pour mettre en forme des quantités numériques|`LC_MONETARY, LC_NUMERIC`|
|[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)|Longueur maximale en octets d'un caractère multioctet dans les paramètres régionaux actifs (macro définie dans STDLIB.H)|**LC_CTYPE**|
|[_mbccpy, _mbccpy_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md),[_mbccpy_s, _mbccpy_s_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|Copier un caractère multioctet|**LC_CTYPE**|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Valider et retourner le nombre d'octets dans un caractère multioctet|**LC_CTYPE**|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Pour les chaînes de caractères multioctets : valider chaque caractère de la chaîne ; retourner la longueur de la chaîne|**LC_CTYPE**|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md),[mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Convertir une séquence de caractères multioctets en une séquence correspondante de caractères larges|**LC_CTYPE**|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Convertir un caractère multioctet en un caractère large correspondant|**LC_CTYPE**|
|Fonctions [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|Écrire la sortie mise en forme|**LC_NUMERIC** (détermine la sortie de caractères de base)|
|Fonctions [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)|Lire l'entrée mise en forme|**LC_NUMERIC** (détermine la reconnaissance des caractères de base)|
|[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|Sélectionner les paramètres régionaux du programme|Non applicable|
|[strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Comparer les caractères de deux chaînes|**LC_COLLATE**|
|[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|Comparer deux chaînes sans tenir compte de la casse|**LC_CTYPE**|
|[_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Comparer les caractères de deux chaînes (qui ne respectent pas la casse)|**LC_COLLATE**|
|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|Comparer les **n** premiers caractères de deux chaînes|**LC_COLLATE**|
|[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|Comparer les caractères de deux chaînes sans tenir compte de la casse.|**LC_CTYPE**|
|[_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Comparer les **n** premiers caractères de deux chaînes (qui ne respectent pas la casse)|**LC_COLLATE**|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Mettre en forme une valeur de date et d’heure en fonction de l’argument **format** fourni|**LC_TIME**|
|[_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md),[_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|Convertir, sur place, chaque lettre majuscule d'une chaîne donnée en minuscules|**LC_CTYPE**|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Convertir une chaîne de caractères en **`double`** valeur|**LC_NUMERIC** (détermine la reconnaissance des caractères de base)|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Convertir une chaîne de caractères en **`long`** valeur|**LC_NUMERIC** (détermine la reconnaissance des caractères de base)|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Convertir une chaîne de caractères en une valeur de type long non signé|**LC_NUMERIC** (détermine la reconnaissance des caractères de base)|
|[_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md),[_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|Convertir, sur place, chaque lettre minuscule d'une chaîne en majuscules|**LC_CTYPE**|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Transformer une chaîne dans un format compilé en respectant les paramètres régionaux|**LC_COLLATE**|
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md),[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Convertir un caractère donné en un caractère minuscule correspondant|**LC_CTYPE**|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md),[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Convertir un caractère donné en une lettre majuscule correspondante|**LC_CTYPE**|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md),[wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Convertir une séquence de caractères larges en une séquence correspondante de caractères multioctets|**LC_CTYPE**|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md),[wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Convertir un caractère large en un caractère multioctet correspondant|**LC_CTYPE**|

> [!NOTE]
> Pour les routines multioctets, la page de codes multioctets doit être équivalente aux paramètres régionaux définis avec [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). [_setmbcp](../c-runtime-library/reference/setmbcp.md), avec l’argument **_MB_CP_LOCALE**, rend la page de codes multioctet identique à la page de codes **setlocale**.

## <a name="see-also"></a>Voir aussi

[Internationalisation](../c-runtime-library/internationalization.md)<br/>
[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
