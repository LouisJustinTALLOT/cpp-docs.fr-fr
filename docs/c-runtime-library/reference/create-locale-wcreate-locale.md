---
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 611eaf342776b9a0f57c4f55c52a841c3fd13fb5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348252"
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

*Catégorie*<br/>
Catégorie.

*locale*<br/>
Spécificateur de paramètres régionaux.

## <a name="return-value"></a>Valeur de retour

Si un *local* et une *catégorie* valides sont donnés, renvoie les paramètres locaux spécifiés comme objet **_locale_t.** Les paramètres régionaux actuels du programme ne sont pas modifiés.

## <a name="remarks"></a>Notes

La fonction **_create_locale** vous permet de créer un objet qui représente certains paramètres spécifiques à la région, pour une utilisation dans des versions locales spécifiques à de nombreuses fonctions CRT (fonctions avec le **_l** suffixe). Le comportement est similaire à **setlocale**, sauf qu’au lieu d’appliquer les paramètres locaux spécifiés à l’environnement actuel, les paramètres sont enregistrés dans une structure **_locale_t** qui est retourné. La **structure _locale_t** doit être libérée à [l’aide de _free_locale](free-locale.md) lorsqu’elle n’est plus nécessaire.

**_wcreate_locale** est une version à caractère large de **_create_locale**; l’argument *local* pour **_wcreate_locale** est une corde de caractère large. **_wcreate_locale** et **_create_locale** se comportent de façon identique autrement.

*L’argument* de catégorie spécifie les parties du comportement local-spécifique qui sont affectées. Les drapeaux utilisés pour la *catégorie* et les parties du programme qu’ils affectent sont comme indiqué dans ce tableau :

| drapeau *de catégorie* | Éléments affectés |
|-----------------|---------|
| **Lc_all** |Toutes les catégories, comme indiqué ci-dessous. |
| **LC_COLLATE** |Le **strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**, et **wcsxfrm** fonctions. |
| **LC_CTYPE** | Les fonctions de manipulation des personnages (sauf **isdigit**, **isxdigit**, **mbstowcs**, et **mbtowc**, qui ne sont pas affectés). |
| **LC_MONETARY** | Informations de formatage monétaire retournées par la fonction **localconv.** |
| **LC_NUMERIC** | Caractère décimal pour les routines de sortie formatées (comme **l’impression),** pour les routines de conversion de données, et pour les informations de formatage non monétaire retournées par **localconv**. En plus du caractère décimal-point, **LC_NUMERIC** définit le séparateur de milliers et la chaîne de contrôle de groupe retourné par [localconv](localeconv.md). |
| **LC_TIME** | Le **strftime** et **wcsftime** fonctionne. |

Cette fonction valide les paramètres *de catégorie* et *de localité.* Si le paramètre de la catégorie n’est pas l’une des valeurs données dans le tableau précédent ou si *le local* est **NULL**, la fonction renvoie **NULL**.

*L’argument local* est un pointeur d’une chaîne qui spécifie le lieu. Pour plus d’informations sur le format de l’argument *local,* voir [Noms locaux, langues et cordes pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

*L’argument local* peut prendre un nom local, une chaîne de langue, une chaîne de langue et un code pays/région, une page de code, ou une chaîne de langue, un code pays/région et une page de code. L’ensemble des noms locaux disponibles, les langues, les codes pays/région et les pages de code comprend tous ceux qui sont pris en charge par l’API Windows NLS. L’ensemble des noms locaux pris en charge par **_create_locale** sont décrits dans [les noms locaux, les langues et les chaînes pays/région .](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) L’ensemble des chaînes linguistiques et pays/régions soutenues par **_create_locale** sont répertoriés dans [les cordes linguistiques](../../c-runtime-library/language-strings.md) et les cordes [pays/région.](../../c-runtime-library/country-region-strings.md)

Pour plus d’informations sur les paramètres régionaux, consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md).

Le nom précédent de cette fonction, **__create_locale** (avec deux soulignes de premier plan), a été déprécié.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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

[Noms locaux, langues et cordes pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Language Strings](../../c-runtime-library/language-strings.md)<br/>
[Chaînes pays/région](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale setlocale setlocale setloc](../../preprocessor/setlocale.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[fonctions strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
