---
title: Conversion de données
ms.date: 03/21/2018
f1_keywords:
- c.conversions
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
ms.openlocfilehash: 37c969ea327325ea84ce22c8d993a9332f6ddc9d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416707"
---
# <a name="data-conversion"></a>Conversion de données

Ces routines convertissent les données d’une forme à une autre. Ces routines s’exécutent en général plus rapidement que les conversions que vous écrivez. Chaque routine qui commence par un préfixe *to* est implémentée sous la forme d’une fonction et d’une macro. Pour plus d’informations sur le choix de l’implémentation, consultez [Choix entre fonctions et macros](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

## <a name="data-conversion-routines"></a>Routines de conversion de données

|Routine|Utilisez|
|-------------|---------|
|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Rechercher la valeur absolue d’un entier|
|[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convertir une chaîne en **float**|
|[atoi, _atoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Convertir une chaîne en **int**|
|[_atoi64, _atoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Convertir une chaîne en **__int64** ou **long long**|
|[atol, _atol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Convertir une chaîne en entier **long**|
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Convertir un caractère UTF-16 ou UTF-32 en caractère multioctet équivalent|
|[_ecvt](../c-runtime-library/reference/ecvt.md), [_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Convertir **double** en chaine de longueur spécifiée|
|[_fcvt](../c-runtime-library/reference/fcvt.md), [_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Convertir **double** en chaîne avec le nombre spécifié de chiffres après la virgule|
|[_gcvt](../c-runtime-library/reference/gcvt.md), [_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Convertir un nombre **double** en chaîne ; stocker la chaîne dans la mémoire tampon|
|[_itoa, _ltoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, ultow, _i64tow, _ui64tow](../c-runtime-library/reference/itoa-itow.md), [_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s, _ui64tow_s](../c-runtime-library/reference/itoa-s-itow-s.md)|Convertir les types d’entier en chaîne|
|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Rechercher la valeur absolue d’un entier **long**|
|[llabs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Rechercher la valeur absolue d’un entier **long long**|
|[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|Convertir un caractère multioctet sur 1 octet en caractère multioctet sur 2 octets correspondant|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Convertir des caractères JIS (Japan Industry Standard) en caractères JMS(Microsoft Japan).|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Convertir un caractère JMS en caractère JIS|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Convertir un caractère multioctet en code hiragana sur 1 octet|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Convertir un caractère multioctet en code katakana sur 1 octet|
|[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|Convertir un caractère multioctet sur 2 octets en caractère multioctet sur 1 octet correspondant|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Convertir un caractère multioctet en caractère UTF-16 ou UTF-32 équivalent|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Convertir une séquence de caractères multioctets en une séquence correspondante de caractères larges|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Convertir un caractère multioctet en un caractère large correspondant|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Convertir une chaîne en **double**|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Convertir une chaîne en entier **long**|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Convertir une chaîne en entier **long non signé**|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Classer une chaîne en fonction des informations spécifiques des paramètres régionaux|
|[toascii, __toascii](../c-runtime-library/reference/toascii-toascii.md)|Convertir le caractère en code ASCII|
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Vérifier le caractère et le convertir en minuscule s’il est actuellement en majuscule|
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|Convertir un caractère en minuscule sans condition|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Vérifier le caractère et le convertir en majuscule s’il est actuellement en minuscule|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|Convertir un caractère en majuscule sans condition|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Convertir une séquence de caractères larges en une séquence correspondante de caractères multioctets|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Convertir un caractère large en un caractère multioctet correspondant|
|[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convertir une chaîne de caractères larges en **double**|
|[_wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Convertir une chaîne de caractères larges en **int**|
|[_wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Convertir une chaîne de caractères larges en **__int64** ou **long long**|
|[_wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Convertir une chaîne de caractères larges en **long**|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
