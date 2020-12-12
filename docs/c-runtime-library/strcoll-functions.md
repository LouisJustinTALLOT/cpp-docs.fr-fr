---
description: 'En savoir plus sur les fonctions suivantes : strcoll'
title: strcoll, fonctions
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcoll
helpviewer_keywords:
- code pages, using for string comparisons
- string comparison [C++], culture-specific
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
ms.openlocfilehash: 8a0b146bff2eab8927733923367b0ae49ecea4c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235682"
---
# <a name="strcoll-functions"></a>strcoll, fonctions

Chacune des fonctions `strcoll` et `wcscoll` compare deux chaînes en fonction du paramètre de catégorie `LC_COLLATE` de la page de codes des paramètres régionaux en cours d’utilisation. Chacune des fonctions `_mbscoll` compare deux chaînes en fonction de la page de codes multioctets en cours d’utilisation. Utilisez les fonctions `coll` pour les comparaisons de chaînes s’il existe une différence entre l’ordre du jeu de caractères et l’ordre lexicographique des caractères dans la page de codes actuelle, et si cette différence présente un intérêt pour la comparaison. Utilisez les fonctions `cmp` correspondantes pour tester uniquement pour l’égalité des chaînes.

### <a name="strcoll-functions"></a>strcoll, fonctions

|SBCS|Unicode|MBCS|Description|
|----------|-------------|----------|-----------------|
|[strcoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[_mbscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Assembler deux chaînes|
|[_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_mbsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Assembler deux chaînes (sensible à la casse)|
|[_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_mbsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|Assembler les premiers caractères `count` de deux chaînes|
|[_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_mbsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Assembler les premiers caractères `count` de deux chaînes (qui ne respectent pas la casse)|

## <a name="remarks"></a>Notes

Les versions jeu de caractères codés sur un octet (SBCS) de ces fonctions (`strcoll`, `stricoll`, `_strncoll` et `_strnicoll`) comparent `string1` et `string2` conformément au paramètre de catégorie `LC_COLLATE` des paramètres régionaux actuels. Ces fonctions diffèrent des fonctions `strcmp` correspondantes en cela que les fonctions `strcoll` utilisent les informations de page de code de paramètres régionaux qui fournissent des séquences de classement. Pour les comparaisons de chaînes dans les paramètres régionaux dans lesquelles l’ordre du jeu de caractères et celui de l’ordre lexicographique des caractères diffèrent, les fonctions `strcoll` doivent être utilisées à la place des fonctions `strcmp` correspondantes. Pour plus d’informations sur `LC_COLLATE` , consultez [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

Pour certaines pages de codes et les jeux de caractères correspondants, l’ordre des caractères dans le jeu de caractères peut différer de l’ordre lexicographique des caractères. Dans les paramètres régionaux « C », ce n’est pas le cas : l’ordre des caractères dans le jeu de caractères ASCII est le même que l’ordre lexicographique des caractères. Cependant, dans certaines pages de code européennes, par exemple, le caractère « a » (valeur 0x61) précède le caractère « ä » (valeur 0xE4) dans le jeu de caractères, alors que d’un point de vue lexicographique, le caractère « ä » précède le caractère « a ». Pour effectuer une comparaison lexicographique dans un cas comme celui-ci, utilisez `strcoll` plutôt que `strcmp`. Vous pouvez aussi utiliser `strxfrm` sur les chaînes d'origine, puis utiliser `strcmp` sur les chaînes résultantes.

`strcoll`, `stricoll`, `_strncoll` et `_strnicoll` gèrent automatiquement les chaînes de caractères multioctets en fonction de la page de codes des paramètres régionaux en cours d’utilisation, comme le font leurs équivalents à caractères larges (Unicode). Les versions de jeu de caractères multioctets (MBCS) de ces fonctions cependant, assemblent les chaînes caractère par caractère en fonction de la page de codes multioctets en cours d’utilisation.

Étant donné que les fonctions `coll` assemblent des chaînes de façon lexicographique en vue des comparer, alors que les fonctions `cmp` testent simplement l’égalité des chaînes, les fonctions `coll` sont beaucoup plus lentes que les versions `cmp` correspondantes. Ainsi, les fonctions `coll` ne doivent être utilisées que s’il existe une différence entre l’ordre du jeu de caractères et l’ordre lexicographique des caractères dans la page de codes actuelle, et si cette différence présente un intérêt pour la comparaison de chaînes.

## <a name="see-also"></a>Voir aussi

[Paramètres régionaux](../c-runtime-library/locale.md)<br/>
[Manipulation de chaînes](../c-runtime-library/string-manipulation-crt.md)<br/>
[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)
