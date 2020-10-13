---
title: Multithreading et paramètres régionaux
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], multithreading
- multithreading [C++], locales
- threading [C++], locales
- per-thread locale
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
ms.openlocfilehash: 82b410c592e5b68737514dda5a864c7bd15f6dc3
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008590"
---
# <a name="multithreading-and-locales"></a>Multithreading et paramètres régionaux

La bibliothèque Runtime C et la bibliothèque C++ standard prennent en charge la modification des paramètres régionaux de votre programme. Cette rubrique décrit les problèmes qui surviennent lors de l’utilisation des fonctionnalités de paramètres régionaux des deux bibliothèques dans une application multithread.

## <a name="remarks"></a>Notes

Avec la bibliothèque Runtime C, vous pouvez créer des applications multithread à l’aide `_beginthread` des `_beginthreadex` fonctions et. Cette rubrique traite uniquement des applications multithread créées à l’aide de ces fonctions. Pour plus d’informations, consultez [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md).

Pour modifier les paramètres régionaux à l’aide de la bibliothèque Runtime C, utilisez la fonction [setlocale](../preprocessor/setlocale.md) . Dans les versions précédentes de Visual C++, cette fonction modifiait toujours les paramètres régionaux dans toute l’application. Il existe désormais une prise en charge de la définition des paramètres régionaux pour chaque thread. Cette opération s’effectue à l’aide de la fonction [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) . Pour spécifier que [setlocale](../preprocessor/setlocale.md) doit uniquement changer les paramètres régionaux dans le thread actuel, appelez `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` dans ce thread. Inversement, l’appel à `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` entraîne l’utilisation par ce thread des paramètres régionaux globaux, et tout appel à [setlocale](../preprocessor/setlocale.md) dans ce thread modifie les paramètres régionaux dans tous les threads qui n’ont pas explicitement activé les paramètres régionaux par thread.

Pour modifier les paramètres régionaux à l’aide de la bibliothèque Runtime C++, utilisez la [classe locale](../standard-library/locale-class.md). En appelant la méthode [locale :: Global](../standard-library/locale-class.md#global) , vous modifiez les paramètres régionaux dans chaque thread qui n’a pas explicitement activé les paramètres régionaux par thread. Pour modifier les paramètres régionaux d’un thread unique ou d’une partie d’une application, il vous suffit de créer une instance d’un `locale` objet dans ce thread ou cette partie de code.

> [!NOTE]
> L’appel de [paramètres régionaux :: Global](../standard-library/locale-class.md#global) modifie les paramètres régionaux de la bibliothèque standard C++ et de la bibliothèque Runtime C. Toutefois, l’appel de [setlocale](../preprocessor/setlocale.md) modifie uniquement les paramètres régionaux de la bibliothèque Runtime C ; la bibliothèque C++ standard n’est pas affectée.

Les exemples suivants montrent comment utiliser la fonction [setlocale](../preprocessor/setlocale.md) , la [classe locale](../standard-library/locale-class.md)et la fonction [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) pour modifier les paramètres régionaux d’une application dans différents scénarios.

## <a name="example-change-locale-with-per-thread-locale-enabled"></a>Exemple : modifier les paramètres régionaux avec les paramètres régionaux par thread activés

Dans cet exemple, le thread principal génère deux threads enfants. Le premier thread, thread A, active les paramètres régionaux par thread en appelant `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . Le deuxième thread, thread B, ainsi que le thread principal, n’activent pas les paramètres régionaux par thread. Le thread A entreprend alors de modifier les paramètres régionaux à l’aide de la fonction [setlocale](../preprocessor/setlocale.md) de la bibliothèque Runtime C.

Étant donné que les paramètres régionaux par thread sont activés pour le thread A, seules les fonctions de la bibliothèque Runtime C dans le thread A commencent à utiliser les paramètres régionaux « français ». Les fonctions de la bibliothèque Runtime C dans le thread B et dans le thread principal continuent à utiliser les paramètres régionaux « C ». En outre, étant donné que [setlocale](../preprocessor/setlocale.md) n’affecte pas les paramètres régionaux de la bibliothèque c++ standard, tous les objets de la bibliothèque c++ standard continuent à utiliser les paramètres régionaux « C ».

```cpp
// multithread_locale_1.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "C"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "C"
```

## <a name="example-change-global-locale-with-per-thread-locale-enabled"></a>Exemple : modifier les paramètres régionaux globaux avec les paramètres régionaux par thread activés

Dans cet exemple, le thread principal génère deux threads enfants. Le premier thread, thread A, active les paramètres régionaux par thread en appelant `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . Le deuxième thread, thread B, ainsi que le thread principal, n’activent pas les paramètres régionaux par thread. Le thread A entreprend alors de modifier les paramètres régionaux à l’aide de la méthode [locale :: Global](../standard-library/locale-class.md#global) de la bibliothèque C++ standard.

Étant donné que les paramètres régionaux par thread sont activés pour le thread A, seules les fonctions de la bibliothèque Runtime C dans le thread A commencent à utiliser les paramètres régionaux « français ». Les fonctions de la bibliothèque Runtime C dans le thread B et dans le thread principal continuent à utiliser les paramètres régionaux « C ». Toutefois, étant donné que la méthode [locale :: Global](../standard-library/locale-class.md#global) modifie les paramètres régionaux « globalement », tous les objets de la bibliothèque C++ standard de tous les threads commencent par les paramètres régionaux « français ».

```cpp
// multithread_locale_2.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "French_France.1252"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="example-change-locale-without-per-thread-locale-enabled"></a>Exemple : modifier les paramètres régionaux sans les paramètres régionaux par thread activés

Dans cet exemple, le thread principal génère deux threads enfants. Le premier thread, thread A, active les paramètres régionaux par thread en appelant `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . Le deuxième thread, thread B, ainsi que le thread principal, n’activent pas les paramètres régionaux par thread. Le thread B procède ensuite à la modification des paramètres régionaux à l’aide de la fonction [setlocale](../preprocessor/setlocale.md) de la bibliothèque Runtime C.

Étant donné que les paramètres régionaux par thread ne sont pas activés pour le thread B, les fonctions de la bibliothèque Runtime C dans le thread B et dans le thread principal commencent par les paramètres régionaux « français ». Les fonctions de la bibliothèque Runtime C dans le thread A continuent à utiliser les paramètres régionaux « C », car le thread a a des paramètres régionaux par thread activés. En outre, étant donné que [setlocale](../preprocessor/setlocale.md) n’affecte pas les paramètres régionaux de la bibliothèque c++ standard, tous les objets de la bibliothèque c++ standard continuent à utiliser les paramètres régionaux « C ».

```cpp
// multithread_locale_3.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "C"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "C"
```

## <a name="example-change-global-locale-without-per-thread-locale-enabled"></a>Exemple : modifier les paramètres régionaux globaux sans les paramètres régionaux par thread activés

Dans cet exemple, le thread principal génère deux threads enfants. Le premier thread, thread A, active les paramètres régionaux par thread en appelant `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . Le deuxième thread, thread B, ainsi que le thread principal, n’activent pas les paramètres régionaux par thread. Le thread B procède ensuite à la modification des paramètres régionaux à l’aide de la méthode [locale :: Global](../standard-library/locale-class.md#global) de la bibliothèque C++ standard.

Étant donné que les paramètres régionaux par thread ne sont pas activés pour le thread B, les fonctions de la bibliothèque Runtime C dans le thread B et dans le thread principal commencent par les paramètres régionaux « français ». Les fonctions de la bibliothèque Runtime C dans le thread A continuent à utiliser les paramètres régionaux « C », car le thread a a des paramètres régionaux par thread activés. Toutefois, étant donné que la méthode [locale :: Global](../standard-library/locale-class.md#global) modifie les paramètres régionaux « globalement », tous les objets de la bibliothèque C++ standard de tous les threads commencent par les paramètres régionaux « français ».

```cpp
// multithread_locale_4.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "French_France.1252"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="see-also"></a>Voir aussi

[Prise en charge du multithreading pour le code plus ancien (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)<br/>
[setlocale](../preprocessor/setlocale.md)<br/>
[Internationalisation](../c-runtime-library/internationalization.md)<br/>
[Paramètres régionaux](../c-runtime-library/locale.md)<br/>
[\<clocale>](../standard-library/clocale.md)<br/>
[\<locale>](../standard-library/locale.md)<br/>
[locale, classe](../standard-library/locale-class.md)
