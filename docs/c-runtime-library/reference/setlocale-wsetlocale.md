---
title: setlocale, _wsetlocale
ms.date: 11/04/2016
apiname:
- _wsetlocale
- setlocale
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
ms.openlocfilehash: 618b3e58a52e89561439fe76bf1b30e3cbbce001
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356203"
---
# <a name="setlocale-wsetlocale"></a>setlocale, _wsetlocale

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

*category*<br/>
Catégorie affectée par les paramètres régionaux.

*locale*<br/>
Spécificateur de paramètres régionaux.

## <a name="return-value"></a>Valeur de retour

Si une commande valide *paramètres régionaux* et *catégorie* sont fournies, retourne un pointeur vers la chaîne associée spécifié *paramètres régionaux* et *catégorie*. Si le *paramètres régionaux* ou *catégorie* n’est pas valide, retourne un pointeur null et les paramètres régionaux actuels du programme ne sont pas modifiés.

Par exemple, l'appel

```C
setlocale( LC_ALL, "en-US" );
```

définit toutes les catégories, en retournant uniquement la chaîne

```Output
en-US
```

Vous pouvez copier la chaîne retournée par **setlocale** pour restaurer cette partie des informations de paramètres régionaux du programme. Global ou thread stockage local est utilisé pour la chaîne retournée par **setlocale**. Appels ultérieurs à **setlocale** remplacent la chaîne, ce qui invalide les pointeurs de chaîne renvoyés par les appels antérieurs.

## <a name="remarks"></a>Notes

Utilisez le **setlocale** fonction permettant de définir, modifier ou interroger certaines ou toutes les informations de paramètres régionaux de programme actuel spécifiées par *paramètres régionaux* et *catégorie*. *paramètres régionaux* fait référence à la localité (pays/région et langue) pour lequel vous pouvez personnaliser certains aspects de votre programme. Certaines catégories dépendent des paramètres régionaux, notamment la mise en forme des dates et le format d'affichage des valeurs monétaires. Si vous définissez *paramètres régionaux* à la chaîne par défaut pour une langue qui a plusieurs formes prises en charge sur votre ordinateur, vous devez vérifier le **setlocale** retourner de valeur pour connaître la langue en vigueur. Par exemple, si vous définissez *paramètres régionaux* à « chinois » la valeur de retour peut être « chinois simplifié » ou « chinois traditionnel ».

**_wsetlocale** est une version à caractères larges de **setlocale**; le *paramètres régionaux* argument et valeur de retour de **_wsetlocale** sont des chaînes à caractères larges. **_wsetlocale** et **setlocale** se comportent de façon identique dans le cas contraire.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**setlocale**|**setlocale**|**_wsetlocale**|

Le *catégorie* argument spécifie les parties d’informations de paramètres régionaux d’un programme qui sont affectées. Les macros utilisées pour *catégorie* et les parties du programme qu’ils affectent sont les suivantes :

|*catégorie* indicateur|Affecte|
|-|-|
| **LC_ALL** | Toutes les catégories, comme indiqué ci-dessous. |
| **LC_COLLATE** | Le **strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_ strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**, et **wcsxfrm** fonctions. |
| **LC_CTYPE** | Les fonctions de gestion de caractères (sauf **isdigit**, **isxdigit**, **mbstowcs**, et **mbtowc**, qui ne sont pas affecté). |
| **LC_MONETARY** | Informations de mise en forme monétaire retournées par la **localeconv** (fonction). |
| **LC_NUMERIC** | Caractère pour les routines de sortie mise en forme de virgule décimale (tel que **printf**), pour les routines de conversion de données et pour les informations de mise en forme non monétaire retournées par **localeconv**. Outre le caractère de virgule décimale, **LC_NUMERIC** séparateur de milliers de jeux et le contrôle de regroupement chaîne retournée par [localeconv](localeconv.md). |
| **LC_TIME** | Le **strftime** et **wcsftime** fonctions. |

Cette fonction valide le paramètre de catégorie. Si le paramètre de catégorie ne fait pas partie des valeurs fournies dans le tableau précédent, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction définit **errno** à **EINVAL** et retourne **NULL**.

Le *paramètres régionaux* argument est un pointeur vers une chaîne qui spécifie les paramètres régionaux. Pour plus d’informations sur le format de la *paramètres régionaux* argument, consultez [noms de paramètres régionaux, langues et chaînes de pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Si *locale* pointe vers une chaîne vide, les paramètres régionaux sont donnés par l'environnement défini lors de l'implémentation. La valeur **C** Spécifie l’environnement de conformation minimal ANSI pour la conversion en C. Le **C** paramètres régionaux part du principe que tous les **char** types de données sont de 1 octet et que leur valeur est toujours inférieure à 256.

Au démarrage du programme, l'équivalent de l'instruction suivante est exécuté :

`setlocale( LC_ALL, "C" );`

Le *paramètres régionaux* argument peut prendre un nom de paramètres régionaux, une chaîne de langage, une chaîne de langue et code de pays/région, une page de codes, ou une chaîne de langue, code de pays/région et page de codes. L'ensemble des noms de paramètres régionaux, des langages, des pays ou codes zone, et de pages de codes disponibles inclut tous ceux pris en charge par l'API Windows NLS, à l'exception des pages de codes qui requièrent plus de deux octets par caractère, telles que UTF-7 et UTF-8. Si vous fournissez une valeur de page de code de UTF-7 ou UTF-8, **setlocale** échoue et génère **NULL**. L’ensemble des noms de paramètres régionaux pris en charge par **setlocale** sont décrites dans [noms de paramètres régionaux, langues et chaînes de pays/région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). L’ensemble de chaînes de langue et de pays/région pris en charge par **setlocale** sont répertoriés dans [chaînes de langue](../../c-runtime-library/language-strings.md) et [chaînes pays/région](../../c-runtime-library/country-region-strings.md). Nous recommandons d'utiliser la forme de nom des paramètres régionaux pour des questions de performance et de maintenance des chaînes de paramètres régionaux incorporées dans le code ou sérialisées du stockage. Les chaînes de nom des paramètres régionaux sont moins susceptibles d'être modifiées par une mise à niveau du système d'exploitation que la forme de nom de la langue et du pays ou de la région.

Un pointeur null est passé en tant que le *paramètres régionaux* argument indique à **setlocale** à interroger au lieu de définir l’environnement international. Si le *paramètres régionaux* argument est un pointeur null, les paramètres régionaux actuels du programme ne sont pas modifié. Au lieu de cela, **setlocale** retourne un pointeur désignant la chaîne qui est associée à la *catégorie* des paramètres régionaux actuels du thread. Si le *catégorie* argument est **LC_ALL**, la fonction retourne une chaîne qui indique le paramètre actuel de chaque catégorie, séparé par des points-virgules. Par exemple, la séquence d'appels

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

qui est la chaîne qui est associée à la **LC_ALL** catégorie.

Les exemples suivants se rapportent à la **LC_ALL** catégorie. Les deux chaînes « .OCP » et « .ACP » peuvent être utilisées à la place du numéro de page de codes pour spécifier, respectivement, l'utilisation de la page de codes OEM utilisateur par défaut et la page de codes ANSI utilisateur par défaut.

- `setlocale( LC_ALL, "" );`

   Définit les paramètres régionaux à la valeur par défaut, qui est la page de codes ANSI utilisateur par défaut obtenue du système d'exploitation.

- `setlocale( LC_ALL, ".OCP" );`

   Définit explicitement les paramètres régionaux à la page de codes OEM actuelle fournie par le système d'exploitation.

- `setlocale( LC_ALL, ".ACP" );`

   Définit les paramètres régionaux à la page de codes ANSI fournie par le système d'exploitation.

- `setlocale( LC_ALL, "<localename>" );`

   Définit les paramètres régionaux en fonction du nom de paramètres régionaux indiqué par *\<localename>*.

- `setlocale( LC_ALL, "<language>_<country>" );`

   Définit les paramètres régionaux en fonction de la langue et du pays/région indiqués par *\<language>* et *\<country>* et en tenant compte de la page de codes par défaut obtenue du système d’exploitation hôte.

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Définit les paramètres régionaux de la langue, le pays/région et la page de codes indiqué par le  *\<langue >*,  *\<pays >*, et  *\<code_page >* chaînes. Vous pouvez utiliser différentes combinaisons de langues, pays/région et page de codes. Par exemple, cet appel définit les paramètres régionaux à français du Canada avec la page de codes 1252 :

   `setlocale( LC_ALL, "French_Canada.1252" );`

   Cet appel définit les paramètres régionaux à français du Canada avec la page de codes ANSI par défaut :

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   Cet appel définit les paramètres régionaux à français du Canada avec la page de codes OEM par défaut :

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Définit les paramètres régionaux en fonction de la langue indiquée par *\<language>* et utilise le pays/région par défaut de la langue spécifiée et la page de codes ANSI utilisateur par défaut pour le pays/région en question obtenus du système d’exploitation hôte. Par exemple, les appels suivants à **setlocale** sont fonctionnellement équivalents :

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   Nous recommandons la première forme pour des questions de performances et de maintenance.

- `setlocale( LC_ALL, ".<code_page>" );`

   Définit la page de codes en fonction de la valeur indiquée par *<code_page>*, ainsi que du pays/région et de la langue par défaut (tels que définis par le système d’exploitation hôte) pour la page de codes spécifiée.

La catégorie doit être **LC_ALL** ou **LC_CTYPE** pour effectuer un changement de page de codes. Par exemple, si le pays/région par défaut et la langue du système d’exploitation hôte sont « États-Unis » et « Anglais », les deux appels suivants à **setlocale** sont fonctionnellement équivalents :

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Pour plus d’informations, consultez la directive pragma [setlocale](../../preprocessor/setlocale.md) dans [Référence du préprocesseur C/C++](../../preprocessor/c-cpp-preprocessor-reference.md).

La fonction [_configthreadlocale](configthreadlocale.md) est utilisée pour déterminer si **setlocale** affecte les paramètres régionaux de tous les threads dans un programme ou uniquement les paramètres régionaux du thread appelant.

## <a name="requirements"></a>Configuration requise

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

[Chaînes relatives aux noms des paramètres régionaux, aux langues et au pays/à la région](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
