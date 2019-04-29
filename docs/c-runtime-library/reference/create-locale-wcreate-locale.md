---
title: _create_locale, _wcreate_locale
ms.date: 11/04/2016
apiname:
- _create_locale
- __create_locale
- _wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 109a1d93692d0c65269b40fd0559381907ce1cab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340356"
---
# <a name="createlocale-wcreatelocale"></a>_create_locale, _wcreate_locale

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

## <a name="return-value"></a>Valeur de retour

Si une commande valide *paramètres régionaux* et *catégorie* sont fournis, retourne les paramètres régionaux spécifiés comme un **_locale_t** objet. Les paramètres régionaux actuels du programme ne sont pas modifiés.

## <a name="remarks"></a>Notes

Le **_create_locale** fonction vous permet de créer un objet qui représente certains paramètres spécifiques à une région, pour une utilisation dans les versions spécifiques de nombreuses fonctions CRT (fonctions avec le **_l** suffixe ). Le comportement est similaire à **setlocale**, sauf qu’au lieu d’appliquer les paramètres régionaux spécifiés à l’environnement actuel, les paramètres sont enregistrés dans un **_locale_t** structure qui est retournée. Le **_locale_t** structure doit être libérée à l’aide de [_free_locale](free-locale.md) quand il n’est plus nécessaire.

**_wcreate_locale** est une version à caractères larges de **_create_locale**; le *paramètres régionaux* l’argument de **_wcreate_locale** est une chaîne de caractères larges. **_wcreate_locale** et **_create_locale** se comportent de façon identique dans le cas contraire.

Le *catégorie* argument spécifie les parties du comportement spécifique de paramètres régionaux qui sont affectées. Les indicateurs utilisés pour *catégorie* et les parties du programme qu’ils affectent sont comme indiqué dans ce tableau :

| *catégorie* indicateur | Affecte |
|-----------------|---------|
| **LC_ALL** |Toutes les catégories, comme indiqué ci-dessous. |
| **LC_COLLATE** |Le **strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_ strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**, et **wcsxfrm** fonctions. |
| **LC_CTYPE** | Les fonctions de gestion de caractères (sauf **isdigit**, **isxdigit**, **mbstowcs**, et **mbtowc**, qui ne sont pas affecté). |
| **LC_MONETARY** | Informations de mise en forme monétaire retournées par la **localeconv** (fonction). |
| **LC_NUMERIC** | Caractère pour les routines de sortie mise en forme de virgule décimale (tel que **printf**), pour les routines de conversion de données et pour les informations de mise en forme non monétaire retournées par **localeconv**. Outre le caractère de virgule décimale, **LC_NUMERIC** séparateur de milliers de jeux et le contrôle de regroupement chaîne retournée par [localeconv](localeconv.md). |
| **LC_TIME** | Le **strftime** et **wcsftime** fonctions. |

Cette fonction valide le *catégorie* et *paramètres régionaux* paramètres. Si le paramètre de catégorie ne fait pas partie des valeurs fournies dans le tableau précédent ou si *paramètres régionaux* est **NULL**, la fonction retourne **NULL**.

Le *paramètres régionaux* argument est un pointeur vers une chaîne qui spécifie les paramètres régionaux. Pour plus d’informations sur le format de la *paramètres régionaux* argument, consultez [noms de paramètres régionaux, langues et chaînes de pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

Le *paramètres régionaux* argument peut prendre un nom de paramètres régionaux, une chaîne de langage, une chaîne de langue et code de pays/région, une page de codes, ou une chaîne de langue, code de pays/région et page de codes. L’ensemble des noms de paramètres régionaux, des langues, des pays ou codes zone, et de pages de codes disponibles inclut tous ceux qui sont pris en charge par l’API Windows NLS, à l’exception des pages de codes qui requièrent plus de deux octets par caractère, par exemple, UTF-7 et UTF-8. Si vous fournissez une page de codes comme UTF-7 ou UTF-8, **_create_locale** échouent et retournent **NULL**. L’ensemble des noms de paramètres régionaux pris en charge par **_create_locale** sont décrites dans [noms de paramètres régionaux, langues et chaînes de pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). L’ensemble de chaînes de langue et de pays/région pris en charge par **_create_locale** sont répertoriés dans [chaînes de langue](../../c-runtime-library/language-strings.md) et [chaînes pays/région](../../c-runtime-library/country-region-strings.md).

Pour plus d’informations sur les paramètres régionaux, consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md).

Le nom précédent de cette fonction, **__create_locale** (avec deux début des traits de soulignement), a été déconseillé.

## <a name="requirements"></a>Configuration requise

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

[Chaînes relatives aux noms des paramètres régionaux, aux langues et au pays/à la région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Chaînes de langue](../../c-runtime-library/language-strings.md)<br/>
[Country/Region Strings](../../c-runtime-library/country-region-strings.md)<br/>
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
