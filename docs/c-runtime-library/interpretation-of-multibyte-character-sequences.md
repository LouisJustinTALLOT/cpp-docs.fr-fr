---
description: 'En savoir plus sur : l’interprétation des séquences de caractères multioctets'
title: Interprétation des séquences de caractères multioctets
ms.date: 10/22/2019
f1_keywords:
- c.character.multibyte
helpviewer_keywords:
- MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
ms.openlocfilehash: 86ef62637e87fd204233ab87fa337c99c5d47a2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246700"
---
# <a name="interpretation-of-multibyte-character-sequences"></a>Interprétation des séquences de caractères multioctets

La plupart des routines de caractères multioctets dans la bibliothèque Runtime Microsoft reconnaissent les séquences de caractères multioctets relatives à une page de codes multioctets. La valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_L** utilisent les paramètres régionaux actuels pour ce comportement dépendant des paramètres régionaux. Les versions avec le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux à la place des paramètres régionaux actuels.

## <a name="locale-dependent-multibyte-routines"></a>Routines multioctets dépendantes des paramètres régionaux

|Routine|Utilisation|
|-------------|---------|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Valider et retourner le nombre d'octets dans un caractère multioctet|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Pour les chaînes de caractères multioctets : valider chaque caractère de la chaîne ; retourner la longueur de la chaîne. Pour les chaînes de caractères larges : retourne la longueur de chaîne.|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Convertir une séquence de caractères multioctets en une séquence correspondante de caractères larges|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Convertir un caractère multioctet en un caractère large correspondant|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Convertir une séquence de caractères larges en une séquence correspondante de caractères multioctets|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Convertir un caractère large en un caractère multioctet correspondant|

## <a name="locale-independent-multibyte-routines"></a>Routines multioctets indépendantes des paramètres régionaux

|Routine|Utilisation|
|-------------|---------|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Convertir un caractère UTF-8 multioctet en un caractère équivalent UTF-16 ou UTF-32|
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Convertir le caractère UTF-16 ou UTF-32 en caractère multioctet UTF-8 équivalent|

## <a name="see-also"></a>Voir aussi

[Internationalisation](../c-runtime-library/internationalization.md)\
[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)
