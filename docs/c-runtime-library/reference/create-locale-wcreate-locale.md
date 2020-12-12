---
description: 'En savoir plus sur : _create_locale, _wcreate_locale'
title: _create_locale, _wcreate_locale
ms.date: 4/2/2020
api_name:
- _create_locale
- __create_locale
- _wcreate_locale
- _o__create_locale
- _o__wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- create_locale
- _create_locale
- __create_locale
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
ms.openlocfilehash: feb2fee7befbaf3f798dc36466674eaa4aec55fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341518"
---
# <a name="_create_locale-_wcreate_locale"></a>_create_locale, _wcreate_locale

Crée un objet de paramètres régionaux.

## <a name="syntax"></a>Syntaxe

```C
_locale_t _create_locale(
   int category,
   const char *locale
);
_locale_t _wcreate_locale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Paramètres

*category*<br/>
Catégorie.

*locale*<br/>
Spécificateur de paramètres régionaux.

## <a name="return-value"></a>Valeur renvoyée

Si *des paramètres régionaux et* une *catégorie* valides sont fournis, retourne les paramètres régionaux spécifiés en tant qu’objet **_locale_t** . Les paramètres régionaux actuels du programme ne sont pas modifiés.

## <a name="remarks"></a>Notes

La fonction **_create_locale** vous permet de créer un objet qui représente certains paramètres spécifiques à une région, à utiliser dans les versions spécifiques aux paramètres régionaux de nombreuses fonctions CRT (fonctions avec le suffixe **_L** ). Le comportement est similaire à **setlocale**, sauf qu’au lieu d’appliquer les paramètres régionaux spécifiés à l’environnement actuel, les paramètres sont enregistrés dans une structure **_locale_t** retournée. La structure **_locale_t** doit être libérée à l’aide de [_free_locale](free-locale.md) lorsqu’elle n’est plus nécessaire.

**_wcreate_locale** est une version à caractères larges de **_create_locale**; l’argument de *paramètres régionaux* pour **_wcreate_locale** est une chaîne de caractères larges. dans le cas contraire, **_wcreate_locale** et **_create_locale** se comportent de la même façon.

L’argument *Category* spécifie les parties du comportement spécifique aux paramètres régionaux qui sont affectées. Les indicateurs utilisés pour la *catégorie* et les parties du programme qu’elles affectent sont comme indiqué dans le tableau suivant :

| indicateur de *catégorie* | Éléments affectés |
|-----------------|---------|
| **LC_ALL** |Toutes les catégories, comme indiqué ci-dessous. |
| **LC_COLLATE** |Les fonctions **strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll** et **wcsxfrm** . |
| **LC_CTYPE** | Fonctions de gestion de caractères (à l’exception de **IsDigit**, **isxdigit**, **mbstowcs** et **mbtowc**, qui ne sont pas affectées). |
| **LC_MONETARY** | Informations de mise en forme monétaire retournées par la fonction **localeconv** . |
| **LC_NUMERIC** | Caractère de virgule décimale pour les routines de sortie mises en forme (telles que **printf**), pour les routines de conversion de données et pour les informations de mise en forme non monétaire retournées par **localeconv**. Outre le caractère de virgule décimale, **LC_NUMERIC** définit le séparateur des milliers et la chaîne de contrôle de regroupement retournée par [localeconv](localeconv.md). |
| **LC_TIME** | Fonctions **strftime** et **wcsftime** . |

Cette fonction valide les paramètres de *catégorie* et de paramètres *régionaux* . Si le paramètre Category ne fait pas partie des valeurs indiquées dans le tableau précédent ou si les *paramètres régionaux* ont la **valeur null**, la fonction retourne la **valeur null**.

L’argument de *paramètres régionaux* est un pointeur vers une chaîne qui spécifie les paramètres régionaux. Pour plus d’informations sur le format de l’argument de *paramètres régionaux* , consultez [noms de paramètres régionaux, langues et chaînes de pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

L’argument des *paramètres régionaux* peut accepter un nom de paramètres régionaux, une chaîne de langue, une chaîne de langue et un pays/région, une page de codes ou une chaîne de langue, un pays/région et une page de codes. L’ensemble des noms de paramètres régionaux, des langues, des codes de pays/région et des pages de codes disponibles comprend tous les pris en charge par l’API NLS Windows. Le jeu de noms de paramètres régionaux pris en charge par **_create_locale** est décrit dans les [chaînes de noms, de langues et de pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). L’ensemble de chaînes de langue et de pays/région prises en charge par **_create_locale** sont répertoriés dans [chaînes de langue](../../c-runtime-library/language-strings.md) et [chaînes de pays/région](../../c-runtime-library/country-region-strings.md).

Pour plus d’informations sur les paramètres régionaux, consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md).

Le nom précédent de cette fonction, **__create_locale** (avec deux traits de soulignement de début), est déconseillé.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_create_locale**|\<locale.h>|
|**_wcreate_locale**|\<locale.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_create_locale.c
// Sets the current locale to "de-CH" using the
// setlocale function and demonstrates its effect on the strftime
// function.

#include <stdio.h>
#include <locale.h>
#include <time.h>

int main(void)
{
    time_t ltime;
    struct tm thetime;
    unsigned char str[100];
    _locale_t locale;

    // Create a locale object representing the German (Switzerland) locale
    locale = _create_locale(LC_ALL, "de-CH");
    time (&ltime);
    _gmtime64_s(&thetime, &ltime);

    // %#x is the long date representation, appropriate to
    // the current locale
    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In de-CH locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);

    // Create a locale object representing the default C locale
    locale = _create_locale(LC_ALL, "C");
    time(&ltime);
    _gmtime64_s(&thetime, &ltime);

    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In 'C' locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);
}
```

```Output
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'
```

## <a name="see-also"></a>Voir aussi

[Chaînes de noms de paramètres régionaux, de langues et de pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Chaînes de langue](../../c-runtime-library/language-strings.md)<br/>
[Chaînes pays/région](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
