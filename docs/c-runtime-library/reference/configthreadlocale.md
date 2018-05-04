---
title: _configthreadlocale | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _configthreadlocale
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
- _configthreadlocale
- configthreadlocale
dev_langs:
- C++
helpviewer_keywords:
- configthreadlocale function
- locales, per-thread
- _configthreadlocale function
- per-thread locale
- thread locale
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7531a5849bc1e86d469a12747b5c4648b76c9117
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="configthreadlocale"></a>_configthreadlocale

Configure les options de paramètres régionaux par thread.

## <a name="syntax"></a>Syntaxe

```C
int _configthreadlocale( int per_thread_locale_type );
```

### <a name="parameters"></a>Paramètres

*per_thread_locale_type*<br/>
Option à définir. Une des options répertoriées dans le tableau suivant.

## <a name="return-value"></a>Valeur de retour

L’état de paramètres régionaux par thread précédent (**_DISABLE_PER_THREAD_LOCALE** ou **_ENABLE_PER_THREAD_LOCALE**), ou -1 en cas d’échec.

## <a name="remarks"></a>Notes

Le **_configurethreadlocale** fonction est utilisée pour contrôler l’utilisation de paramètres régionaux du thread spécifique. Utilisez une de ces *per_thread_locale_type* options pour spécifier ou déterminer l’état de paramètres régionaux par thread :

|||
|-|-|
**_ENABLE_PER_THREAD_LOCALE**|Faites en sorte que le thread actuel utilise des paramètres régionaux spécifiques aux threads. Les appels suivants à **setlocale** dans ce thread affecte uniquement aux paramètres régionaux du thread.
**_DISABLE_PER_THREAD_LOCALE**|Faites en sorte que le thread actuel utilise les paramètres régionaux globaux. Les appels suivants à **setlocale** dans ce thread affecter les autres threads à l’aide des paramètres régionaux globaux.
**0**|Récupère le paramétrage actuel de ce thread particulier.

Ces fonctions affectent le comportement de **setlocale**, **_tsetlocale**, **_wsetlocale**, et **_setmbcp**. Lorsque les paramètres régionaux par thread sont désactivé, tous les appels à **setlocale** ou **_wsetlocale** modifie les paramètres régionaux de tous les threads qui utilisent des paramètres régionaux globaux. Lorsque les paramètres régionaux par thread sont activé, **setlocale** ou **_wsetlocale** affecte uniquement aux paramètres régionaux du thread actuel.

Si vous utilisez **_configurethreadlocale** pour activer les paramètres régionaux par thread, nous vous recommandons d’appeler **setlocale** ou **_wsetlocale** pour définir les paramètres régionaux par défaut dans ce thread immédiatement après.

Si *per_thread_locale_type* n’est pas une des valeurs répertoriées dans le tableau, cette fonction appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne -1.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_configthreadlocale**|\<locale.h>|

## <a name="example"></a>Exemple

```cpp
// crt_configthreadlocale.cpp
//
// This program demonstrates the use of _configthreadlocale when
// using two independent threads.
//
// Compile by using: cl /EHsc /W4 crt_configthreadlocale.cpp

#include <locale.h>
#include <mbctype.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date and time in the current
// locale's format.
int get_time(unsigned char* str)
{
    __time64_t  ltime;
    struct tm   thetime;

    // Retieve the time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // using %#x is the long date representation,
    // appropriate to the current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm*)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to German
// and prints the time.
unsigned __stdcall SecondThreadFunc( void* /*pArguments*/ )
{
    unsigned char str[BUFF_SIZE];

    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the thread code page
    _setmbcp(_MB_CP_ANSI);

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "German"));

    // Retrieve the time string from the helper function
    if (get_time(str) == 0)
    {
        printf("The time in German locale is: '%s'\n", str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread spawns a second thread (above) and then
// sets the locale to English and prints the time.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Retrieve the time string from the helper function
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "English"));

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      NULL, 0, &threadID );

    if (get_time(str) == 0)
    {
        // Retrieve the time string from the helper function
        printf("The time in English locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to English_United States.1252.
The time in English locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to German_Germany.1252.
The time in German locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>Voir aussi

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Multithreading et paramètres régionaux](../../parallel/multithreading-and-locales.md)<br/>
