---
title: setlocale, _wsetlocale
description: Décrit les fonctions de la bibliothèque Microsoft C Runtime (CRT) setlocale et _wsetlocale .
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 812aab43667416a5892d8e24d03d0e67cad8d0ac
ms.sourcegitcommit: b51703a96ee35ee2376d5f0775b70f03ccbe6d9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88086992"
---
# <a name="no-locsetlocale-no-loc_wsetlocale"></a>setlocale, _wsetlocale

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

*catégorie*\
Catégorie affectée par les paramètres régionaux.

*locale*\
Spécificateur de paramètres régionaux.

## <a name="return-value"></a>Valeur retournée

Si des *paramètres régionaux* et une *catégorie* valides sont fournis, retourne un pointeur vers la chaîne associée aux *paramètres régionaux* et à la *catégorie*spécifiés. Si les paramètres *régionaux* ou la *catégorie* ne sont pas valides, retourne un pointeur null et les paramètres régionaux actuels du programme ne sont pas modifiés.

Par exemple, l'appel

```C
setlocale( LC_ALL, "en-US" );
```

définit toutes les catégories, en retournant uniquement la chaîne

```Output
en-US
```

Vous pouvez copier la chaîne retournée par `setlocale` pour restaurer cette partie des informations relatives aux paramètres régionaux du programme. Un stockage local des threads ou un stockage global est utilisé pour la chaîne retournée par `setlocale`. Les appels ultérieurs à `setlocale` remplacent la chaîne, ce qui rend les pointeurs de chaîne retournés par les appels antérieurs non valides.

## <a name="remarks"></a>Notes

Utilisez la `setlocale` fonction pour définir, modifier ou interroger certaines ou toutes les informations de paramètres régionaux du programme en cours spécifiées par les *paramètres régionaux* et la *catégorie*. les *paramètres régionaux* font référence à la localité (pays/région et langue) pour laquelle vous pouvez personnaliser certains aspects de votre programme. Certaines catégories dépendent des paramètres régionaux, notamment la mise en forme des dates et le format d'affichage des valeurs monétaires. Si vous définissez les *paramètres régionaux* sur la chaîne par défaut pour une langue qui a plusieurs formulaires pris en charge sur votre ordinateur, vous devez vérifier la `setlocale` valeur de retour pour connaître la langue en vigueur. Par exemple, si vous affectez à *paramètres régionaux* la valeur « chinois », la valeur de retour peut être « chinois simplifié » ou « chinois traditionnel ».

`_wsetlocale`est une version à caractères larges de `setlocale` ; l’argument de *paramètres régionaux* et la valeur de retour de `_wsetlocale` sont des chaînes à caractères larges. Sinon,`_wsetlocale` et `setlocale` se comportent de la même façon.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tsetlocale`|`setlocale`|`setlocale`|`_wsetlocale`|

L’argument *Category* spécifie les parties des informations relatives aux paramètres régionaux d’un programme qui sont affectées. Les macros utilisées pour la *catégorie* et les parties du programme qu’elles affectent sont les suivantes :

|indicateur de *catégorie*|Éléments affectés|
|-|-|
| `LC_ALL` | Toutes les catégories, comme indiqué ci-dessous. |
| `LC_COLLATE` | Les fonctions `strcoll`, `_stricoll`, `wcscoll`, `_wcsicoll`, `strxfrm`, `_strncoll`, `_strnicoll`, `_wcsncoll`, `_wcsnicoll` et `wcsxfrm`. |
| `LC_CTYPE` | Les fonctions de gestion de caractères (sauf `isdigit`, `isxdigit`, `mbstowcs`, et `mbtowc`, qui ne sont pas affectés). |
| `LC_MONETARY` | Les informations de mise en forme monétaire retournées par la fonction `localeconv`. |
| `LC_NUMERIC` | Le caractère de virgule décimale pour les routines de sortie mise en forme (comme `printf`), pour les routines de conversion de données, et pour les informations de mise en forme non monétaire retournées par `localeconv`. Outre le caractère de virgule décimale, `LC_NUMERIC` définit le séparateur de milliers et la chaîne de contrôle de regroupement retournés par [localeconv](localeconv.md). |
| `LC_TIME` | Les fonctions `strftime` et `wcsftime`. |

Cette fonction valide le paramètre de catégorie. Si le paramètre Category n’est pas l’une des valeurs indiquées dans le tableau précédent, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l'exécution est autorisée à se poursuivre, la fonction définit `errno` avec la valeur `EINVAL` et retourne `NULL`.

L’argument de *paramètres régionaux* est un pointeur vers une chaîne qui spécifie les paramètres régionaux. Pour plus d’informations sur le format de l’argument de *paramètres régionaux* , consultez [noms de paramètres régionaux, langues et chaînes de pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Si *locale* pointe vers une chaîne vide, les paramètres régionaux sont donnés par l'environnement défini lors de l'implémentation. Une valeur de `C` spécifie l'environnement de conformation minimal ANSI pour la conversion en C. Les paramètres régionaux de `C` supposent que tous les types de données de ``char`` sont de 1 octet et que leur valeur est toujours inférieure à 256.

Au démarrage du programme, l'équivalent de l'instruction suivante est exécuté :

`setlocale( LC_ALL, "C" );`

L’argument des *paramètres régionaux* peut accepter un nom de paramètres régionaux, une chaîne de langue, une chaîne de langue et un pays/région, une page de codes ou une chaîne de langue, un pays/région et une page de codes. L’ensemble des noms de paramètres régionaux, des langues, des codes de pays/région et des pages de codes disponibles comprend tous ceux pris en charge par l’API NLS Windows. L’ensemble des noms de paramètres régionaux pris en charge par `setlocale` est décrit dans [Chaînes relatives aux noms, aux langues, au pays et à la région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). L’ensemble des chaînes de langue et de pays/région prises en charge par `setlocale` est répertorié dans [Chaînes de langue](../../c-runtime-library/language-strings.md) et [Chaînes pays/région](../../c-runtime-library/country-region-strings.md). Nous recommandons d'utiliser la forme de nom des paramètres régionaux pour des questions de performance et de maintenance des chaînes de paramètres régionaux incorporées dans le code ou sérialisées du stockage. Les chaînes de nom des paramètres régionaux sont moins susceptibles d'être modifiées par une mise à niveau du système d'exploitation que la forme de nom de la langue et du pays ou de la région.

Un pointeur null passé comme argument de *paramètres régionaux* indique à d' `setlocale` interroger au lieu de définir l’environnement international. Si l’argument de *paramètres régionaux* est un pointeur null, les paramètres régionaux actuels du programme ne sont pas modifiés. Au lieu de cela, `setlocale` retourne un pointeur vers la chaîne associée à la *catégorie* des paramètres régionaux actuels du thread. Si l’argument *Category* est `LC_ALL` , la fonction retourne une chaîne qui indique le paramètre actuel de chaque catégorie, en les séparant par des points-virgules. Par exemple, la séquence d'appels

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

qui est la chaîne associée à la catégorie `LC_ALL`.

Les exemples suivants appartiennent à la catégorie `LC_ALL`. L’une ou l’autre des chaînes». OCP « and ». ACP» peut être utilisé à la place d’un numéro de page de codes pour spécifier l’utilisation de la page de codes OEM par défaut de l’utilisateur et de la page de codes ANSI utilisateur par défaut pour ce nom de paramètres régionaux, respectivement.

- `setlocale( LC_ALL, "" );`

   Définit les paramètres régionaux à la valeur par défaut, qui est la page de codes ANSI utilisateur par défaut obtenue du système d'exploitation. Le nom des paramètres régionaux est défini sur la valeur retournée par [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). La page de codes est définie sur la valeur retournée par [GetACP](/windows/win32/api/winnls/nf-winnls-getacp).

- `setlocale( LC_ALL, ".OCP" );`

   Définit les paramètres régionaux sur la page de codes OEM actuelle obtenue à partir du système d’exploitation. Le nom des paramètres régionaux est défini sur la valeur retournée par [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). La page de codes est définie sur la valeur [LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants) pour le nom de paramètres régionaux par défaut de l’utilisateur par [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, ".ACP" );`

   Définit les paramètres régionaux à la page de codes ANSI fournie par le système d'exploitation. Le nom des paramètres régionaux est défini sur la valeur retournée par [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). La page de codes est définie sur la valeur [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) pour le nom de paramètres régionaux par défaut de l’utilisateur par [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<localename>" );`

   Définit les paramètres régionaux en spécifiant le nom des paramètres régionaux indiqué par *\<localename>* . La page de codes est définie sur la valeur [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) pour le nom de paramètres régionaux spécifié par [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<language>_<country>" );`

   Définit les paramètres régionaux sur la langue et le pays/région indiqués par *\<language>* et *\<country>* , ainsi que la page de codes par défaut obtenue du système d’exploitation hôte. La page de codes est définie sur la valeur [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) pour le nom de paramètres régionaux spécifié par [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Définit les paramètres régionaux de la langue, du pays/de la région et de la page de codes indiqués par les *\<language>* *\<country>* chaînes, et *\<code_page>* . Vous pouvez utiliser différentes combinaisons de langues, pays/région et page de codes. Par exemple, cet appel définit les paramètres régionaux à français du Canada avec la page de codes 1252 :

   `setlocale( LC_ALL, "French_Canada.1252" );`

   Cet appel définit les paramètres régionaux à français du Canada avec la page de codes ANSI par défaut :

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   Cet appel définit les paramètres régionaux à français du Canada avec la page de codes OEM par défaut :

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Définit les paramètres régionaux sur la langue indiquée par *\<language>* et utilise le pays ou la région par défaut pour la langue spécifiée et la page de codes ANSI par défaut de l’utilisateur pour ce pays/cette région, telle qu’elle est obtenue à partir du système d’exploitation hôte. Par exemple, les appels suivants à `setlocale` sont fonctionnellement équivalents :

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   Nous recommandons la première forme pour des questions de performances et de maintenance.

- `setlocale( LC_ALL, ".<code_page>" );`

   Définit la page de codes en fonction de la valeur indiquée par *<code_page>*, ainsi que du pays/région et de la langue par défaut (tels que définis par le système d’exploitation hôte) pour la page de codes spécifiée.

La catégorie doit être `LC_ALL` ou `LC_CTYPE` pour effectuer un changement de page de codes. Par exemple, si le pays/la région et la langue par défaut du système d'exploitation hôte sont « États-Unis » et « anglais », les deux appels suivants à `setlocale` sont fonctionnellement équivalents :

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Pour plus d’informations, consultez la [setlocale](../../preprocessor/setlocale.md) directive pragma dans la [Référence du préprocesseur C/C++](../../preprocessor/c-cpp-preprocessor-reference.md).

La fonction [_configthreadlocale](configthreadlocale.md) est utilisée pour déterminer si `setlocale` affecte les paramètres régionaux de tous les threads d’un programme ou uniquement les paramètres régionaux du thread appelant.

## <a name="utf-8-support"></a>Prise en charge d’UTF-8

À compter de la build 17134 de Windows 10 (mise à jour d’avril 2018), le runtime C universel prend en charge l’utilisation d’une page de codes UTF-8. Cela signifie que `char` les chaînes passées aux fonctions runtime C attendent des chaînes dans l’encodage UTF-8. Pour activer le mode UTF-8, utilisez « UTF-8 » comme page de codes lors de l’utilisation de `setlocale` . Par exemple, `setlocale(LC_ALL, ".utf8")` utilise la page de codes ANSI par défaut Windows (ACP) pour les paramètres régionaux et UTF-8 pour la page de codes.

Après l’appel de `setlocale(LC_ALL, ".UTF8")` , vous pouvez passer « 😊 » à `mbtowcs` et il sera correctement traduit en une `wchar_t` chaîne, alors qu’il n’existait précédemment aucun paramètre de paramètres régionaux disponible pour cette opération.

Le mode UTF-8 est également activé pour les fonctions qui ont des chaînes traduites historiquement `char` à l’aide de la page de codes ANSI Windows par défaut (ACP). Par exemple, l’appel de [`_mkdir("😊")`](../reference/mkdir-wmkdir.md) lors de l’utilisation d’une page de codes UTF-8 génère correctement un répertoire avec cet Emoji comme nom de dossier, au lieu de demander à ce que l’ACP soit remplacé par UTF-8 avant d’exécuter votre programme. De même, [`_getcwd()`](../reference/getcwd-wgetcwd.md) l’appel à l’intérieur de ce dossier retourne une chaîne encodée en UTF-8. Pour des cas de compatibilité, l’ACP est toujours utilisé si la page de codes des paramètres régionaux C n’est pas définie sur UTF-8.

Les aspects suivants du runtime C qui ne sont pas en mesure d’utiliser UTF-8 parce qu’ils sont définis pendant le démarrage du programme et doivent utiliser la page de codes ANSI Windows par défaut (ACP) : [`__argv`](../argc-argv-wargv.md) , [`_acmdln`](../acmdln-tcmdln-wcmdln.md) et [`_pgmptr`](../pgmptr-wpgmptr.md) .

Avant ce [support, `mbrtoc16` `mbrtoc32` ,, ](../reference/mbrtoc16-mbrtoc323.md), [ `c16rtomb` et `c32rtomb` ](../reference/c16rtomb-c32rtomb1.md) existaient pour effectuer la conversion entre les chaînes de caractères UTF-8, UTF-16 (même encodage que sur les `wchar_t` plateformes Windows) et UTF-32. Pour des raisons de compatibilité, ces API ne traduisent toujours pas vers et à partir d’UTF-8, et non la page de codes définie via `setlocale` .

Pour utiliser cette fonctionnalité sur un système d’exploitation antérieur à Windows 10, tel que Windows 7, vous devez utiliser le [déploiement local](../../windows/universal-crt-deployment.md#local-deployment) de l’application ou le lier de manière statique à l’aide de la version 17134 du SDK Windows ou version ultérieure. Pour les systèmes d’exploitation Windows 10 antérieures à 17134, seule la liaison statique est prise en charge.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|`setlocale`|\<locale.h>|
|`_wsetlocale`|\<locale.h> ou \<wchar.h>|

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

[Chaînes de noms de paramètres régionaux, de langues et de pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[_configthreadlocale](configthreadlocale.md)\
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)\
[Paramètres régionaux](../../c-runtime-library/locale.md)\
[localeconv](localeconv.md)\
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)\
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)\
[_setmbcp](setmbcp.md)\
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)\
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)\
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)\
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)\
[wctomb, _wctomb_l](wctomb-wctomb-l.md)
