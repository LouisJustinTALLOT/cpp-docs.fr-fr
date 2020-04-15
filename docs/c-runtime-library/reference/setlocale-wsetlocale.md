---
title: setlocale, _wsetlocale
description: Décrit les fonctions de bibliothèque Microsoft C setlocale _wsetlocaleruntime (CRT) et .
ms.date: 4/2/2020
api_name:
- _wsetlocale
- setlocale
- _o__wsetlocale
- _o_setlocale
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
- _wsetlocale
- _tsetlocale
- setlocale
helpviewer_keywords:
- wsetlocale function
- setlocale function
- tsetlocale function
- locales, defining
- _tsetlocale function
- defining locales
- _wsetlocale function
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
no-loc:
- setlocale
- _wsetlocale
ms.openlocfilehash: 2834229839153c3154caadf71e5fb30d84ed2f1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353721"
---
# <a name="setlocale-_wsetlocale"></a>setlocale, _wsetlocale

Définit ou extrait les paramètres régionaux d'exécution.

## <a name="syntax"></a>Syntaxe

```C
char *setlocale(
   int category,
   const char *locale
);
wchar_t *_wsetlocale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Paramètres

*Catégorie*\
Catégorie affectée par les paramètres régionaux.

*locale*\
Spécificateur de paramètres régionaux.

## <a name="return-value"></a>Valeur retournée

Si un *local* et une *catégorie* valides sont donnés, renvoie un pointeur à la chaîne associée à la *localisation* et à la *catégorie*spécifiées. Si le *lieu* ou la *catégorie* n’est pas valide, renvoie un pointeur nul, et les paramètres locaux actuels du programme sont inchangés.

Par exemple, l'appel

```C
setlocale( LC_ALL, "en-US" );
```

définit toutes les catégories, en retournant uniquement la chaîne

```Output
en-US
```

Vous pouvez copier la chaîne retournée par **setlocale** pour restaurer cette partie des informations locales du programme. Le stockage local global ou de fil est utilisé pour la chaîne retournée par **setlocale**. Plus tard, les appels à **setlocale** sursoument la chaîne, ce qui invalide les pointeurs de cordes retournés par des appels antérieurs.

## <a name="remarks"></a>Notes

Utilisez la fonction **setlocale** pour définir, modifier ou interroger une partie ou la totalité des informations locales actuelles du programme spécifiées par *local* et *catégorie*. *local* se réfère à la localité (pays/région et langue) pour laquelle vous pouvez personnaliser certains aspects de votre programme. Certaines catégories dépendent des paramètres régionaux, notamment la mise en forme des dates et le format d'affichage des valeurs monétaires. Si vous *définissez local* à la chaîne par défaut pour une langue qui a plusieurs formulaires pris en charge sur votre ordinateur, vous devez vérifier la valeur de retour **setlocale** pour voir quelle langue est en vigueur. Par exemple, si vous *définissez local* à «chinois», la valeur de retour pourrait être soit «chinois-simplifié» ou «chinois-traditionnel».

**_wsetlocale** est une version à caractère large de **setlocale**; l’argument *local* et la valeur de retour de **_wsetlocale** sont des cordes de caractère large. **_wsetlocale** et **setlocale** se comportent de façon identique autrement.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**setlocale setlocale setlocale setloc**|**setlocale setlocale setlocale setloc**|**_wsetlocale**|

*L’argument* de la catégorie spécifie les parties de l’information locale d’un programme qui sont touchées. Les macros utilisées pour la *catégorie* et les parties du programme qu’elles affectent sont les suivantes :

|drapeau *de catégorie*|Éléments affectés|
|-|-|
| **Lc_all** | Toutes les catégories, comme indiqué ci-dessous. |
| **LC_COLLATE** | Le **strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**, et **wcsxfrm** fonctions. |
| **LC_CTYPE** | Les fonctions de manipulation des personnages (sauf **isdigit**, **isxdigit**, **mbstowcs**, et **mbtowc**, qui ne sont pas affectés). |
| **LC_MONETARY** | Informations de formatage monétaire retournées par la fonction **localconv.** |
| **LC_NUMERIC** | Caractère décimal pour les routines de sortie formatées (comme **l’impression),** pour les routines de conversion de données, et pour les informations de formatage non monétaire retournées par **localconv**. En plus du caractère décimal-point, **LC_NUMERIC** définit le séparateur de milliers et la chaîne de contrôle de groupe retourné par [localconv](localeconv.md). |
| **LC_TIME** | Le **strftime** et **wcsftime** fonctionne. |

Cette fonction valide le paramètre de catégorie. Si le paramètre de catégorie n’est pas l’une des valeurs données dans le tableau précédent, le gestionnaire de paramètres invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction définit **errno** à **EINVAL** et retourne **NULL**.

*L’argument local* est un pointeur d’une chaîne qui spécifie le lieu. Pour plus d’informations sur le format de l’argument *local,* voir [Noms locaux, langues et cordes pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Si *locale* pointe vers une chaîne vide, les paramètres régionaux sont donnés par l'environnement défini lors de l'implémentation. Une valeur de **C** spécifie l’environnement minimal DE conformité ANSI pour la traduction C. Le **local C** suppose que tous les types de données **d’omble sont** 1 byte et que leur valeur est toujours inférieure à 256.

Au démarrage du programme, l'équivalent de l'instruction suivante est exécuté :

`setlocale( LC_ALL, "C" );`

*L’argument local* peut prendre un nom local, une chaîne de langue, une chaîne de langue et un code pays/région, une page de code, ou une chaîne de langue, un code pays/région et une page de code. L’ensemble des noms locaux disponibles, les langues, les codes pays/région et les pages de code comprend tous ceux pris en charge par l’API Windows NLS. L’ensemble des noms locaux pris en charge par **setlocale** sont décrits dans [les noms locaux, les langues et les chaînes pays/région .](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) L’ensemble des chaînes linguistiques et pays/régions supportées par **setlocale** sont répertoriés dans [les cordes linguistiques](../../c-runtime-library/language-strings.md) et [les cordes pays/région.](../../c-runtime-library/country-region-strings.md) Nous recommandons d'utiliser la forme de nom des paramètres régionaux pour des questions de performance et de maintenance des chaînes de paramètres régionaux incorporées dans le code ou sérialisées du stockage. Les chaînes de nom des paramètres régionaux sont moins susceptibles d'être modifiées par une mise à niveau du système d'exploitation que la forme de nom de la langue et du pays ou de la région.

Un pointeur nul qui est passé que l’argument *local* dit **setlocale** à la question au lieu de définir l’environnement international. Si l’argument *local* est un pointeur nul, le cadre local actuel du programme n’est pas changé. Au lieu de cela, **setlocale** retourne un pointeur à la chaîne qui est associée à la *catégorie* de l’emplacement actuel du thread. Si l’argument de la *catégorie* est **LC_ALL,** la fonction renvoie une chaîne qui indique le réglage actuel de chaque catégorie, séparée par des semi-colons. Par exemple, la séquence d'appels

```C
// Set all categories and return "en-US"
setlocale(LC_ALL, "en-US");
// Set only the LC_MONETARY category and return "fr-FR"
setlocale(LC_MONETARY, "fr-FR");
printf("%s\n", setlocale(LC_ALL, NULL));
```

retourne

```Output
LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US
```

qui est la chaîne qui est associée à la **catégorie LC_ALL.**

Les exemples suivants concernent la catégorie **LC_ALL.** L’une ou l’autre des cordes ". OCP" et ". ACP" peut être utilisé au lieu d’un numéro de page de code pour spécifier l’utilisation de la page de code OEM par défaut de l’utilisateur et de la page de code ANSI par défaut pour ce nom local, respectivement.

- `setlocale( LC_ALL, "" );`

   Définit les paramètres régionaux à la valeur par défaut, qui est la page de codes ANSI utilisateur par défaut obtenue du système d'exploitation. Le nom local est réglé à la valeur retournée par [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). La page de code est définie à la valeur retournée par [GetACP](/windows/win32/api/winnls/nf-winnls-getacp).

- `setlocale( LC_ALL, ".OCP" );`

   Définit le lieu à la page de code OEM actuelle obtenue à partir du système d’exploitation. Le nom local est réglé à la valeur retournée par [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). La page de code est définie à la valeur [LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants) pour le nom local par défaut de l’utilisateur par [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, ".ACP" );`

   Définit les paramètres régionaux à la page de codes ANSI fournie par le système d'exploitation. Le nom local est réglé à la valeur retournée par [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). La page de code est définie à la valeur [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) pour le nom local par défaut de l’utilisateur par [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<localename>" );`

   Définit le lieu au nom local qui est indiqué par * \<localname>*. La page de code est définie à la valeur [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) pour le nom local spécifié par [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<language>_<country>" );`

   Définit le lieu à la langue * \<* et le pays/région indiqué par la langue>et * \<le pays>*, ainsi que la page de code par défaut obtenue à partir du système d’exploitation hôte. La page de code est définie à la valeur [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) pour le nom local spécifié par [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Définit le lieu à la langue, pays/région, * \< *et la page de code indiquée par la langue>, * \<pays>*, et * \<code_page>* cordes. Vous pouvez utiliser différentes combinaisons de langues, pays/région et page de codes. Par exemple, cet appel définit les paramètres régionaux à français du Canada avec la page de codes 1252 :

   `setlocale( LC_ALL, "French_Canada.1252" );`

   Cet appel définit les paramètres régionaux à français du Canada avec la page de codes ANSI par défaut :

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   Cet appel définit les paramètres régionaux à français du Canada avec la page de codes OEM par défaut :

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Définit le lieu à la langue * \< *qui est indiquée par la langue>, et utilise le pays/région par défaut pour la langue spécifiée et la page de code ANSI par défaut de l’utilisateur pour ce pays / région comme obtenu à partir du système d’exploitation hôte. Par exemple, les appels suivants à **setlocale** sont fonctionnellement équivalents :

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   Nous recommandons la première forme pour des questions de performances et de maintenance.

- `setlocale( LC_ALL, ".<code_page>" );`

   Définit la page de codes en fonction de la valeur indiquée par *<code_page>*, ainsi que du pays/région et de la langue par défaut (tels que définis par le système d’exploitation hôte) pour la page de codes spécifiée.

La catégorie doit être **LC_ALL** ou **LC_CTYPE** pour effectuer un changement de page de code. Par exemple, si le pays/région par défaut et la langue du système d’exploitation hôte sont « États-Unis » et « anglais », les deux appels suivants à **setlocale** sont fonctionnellement équivalents :

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Pour plus d’informations, consultez la directive pragma [setlocale](../../preprocessor/setlocale.md) dans [Référence du préprocesseur C/C++](../../preprocessor/c-cpp-preprocessor-reference.md).

La fonction [_configthreadlocale](configthreadlocale.md) est utilisée pour contrôler si **setlocale** affecte le local de tous les threads dans un programme ou seulement le lieu du fil d’appel.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**setlocale**|\<locale.h>|
|**_wsetlocale**|\<locale.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_setlocale.c
//
// This program demonstrates the use of setlocale when
// using two independent threads.
//

#include <locale.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date in the current
// locale's format.
int get_date(unsigned char* str)
{
    __time64_t ltime;
    struct tm  thetime;

    // Retrieve the current time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // "%#x" is the long date representation in the
    // current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm *)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to the argument
// and prints the date.
uintptr_t __stdcall SecondThreadFunc( void* pArguments )
{
    unsigned char str[BUFF_SIZE];
    char * locale = (char *)pArguments;

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, locale));

    // Retrieve the date string from the helper function
    if (get_date(str) == 0)
    {
        printf("The date in %s locale is: '%s'\n", locale, str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread sets the locale to English
// and then spawns a second thread (above) and prints the date.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the locale of the main thread to US English.
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "en-US"));

    // Create the second thread with a German locale.
    // Our thread function takes an argument of the locale to use.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      "de-DE", 0, &threadID );

    if (get_date(str) == 0)
    {
        // Retrieve the date string from the helper function
        printf("The date in en-US locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to en-US.
The time in en-US locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to de-DE.
The time in de-DE locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>Voir aussi

[Noms locaux, langues et cordes pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[_configthreadlocale](configthreadlocale.md)\
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)\
[Local](../../c-runtime-library/locale.md)\
[localconv](localeconv.md)\
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)\
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)\
[_setmbcp](setmbcp.md)\
[fonctions strcoll](../../c-runtime-library/strcoll-functions.md)\
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)\
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)\
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)\
[wctomb, _wctomb_l](wctomb-wctomb-l.md)
