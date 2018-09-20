---
title: Multithreading et paramètres régionaux | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- locales [C++], multithreading
- multithreading [C++], locales
- threading [C++], locales
- per-thread locale
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d728bb8696a71eb733f15c236e42dc1859c5f135
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428783"
---
# <a name="multithreading-and-locales"></a>Multithreading et paramètres régionaux

La bibliothèque Runtime C et la bibliothèque Standard C++ fournissent la prise en charge pour la modification des paramètres régionaux de votre programme. Cette rubrique décrit les problèmes qui surviennent lors de l’utilisation de la fonctionnalité de paramètres régionaux des deux bibliothèques dans une application multithread.

## <a name="remarks"></a>Notes

Avec la bibliothèque Runtime C, vous pouvez créer des applications multithread à l’aide de la `_beginthread` et `_beginthreadex` fonctions. Cette rubrique couvre uniquement les applications multithread créées à l’aide de ces fonctions. Pour plus d’informations, consultez [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md).

Pour modifier les paramètres régionaux à l’aide de la bibliothèque Runtime C, utilisez la [setlocale](../preprocessor/setlocale.md) (fonction). Dans les versions précédentes de Visual C++, cette fonction est toujours modifier les paramètres régionaux dans toute l’application. Il est prennent désormais en charge pour la définition des paramètres régionaux par thread. Cette opération est effectuée à l’aide de la [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) (fonction). Pour spécifier que [setlocale](../preprocessor/setlocale.md) ne devez modifier les paramètres régionaux du thread actif, l’appel `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` dans ce thread. Inversement, l’appel `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` entraînera ce thread à utiliser les paramètres régionaux globaux et tout appel à [setlocale](../preprocessor/setlocale.md) dans ce thread modifiera les paramètres régionaux dans tous les threads qui n’ont pas explicitement activé de paramètres régionaux par thread.

Pour modifier les paramètres régionaux à l’aide de la bibliothèque Runtime C++, utilisez la [locale, classe](../standard-library/locale-class.md). En appelant le [locale::global](../standard-library/locale-class.md#global) (méthode), vous modifiez les paramètres régionaux dans chaque thread qui n’a pas explicitement activé de paramètres régionaux par thread. Pour modifier les paramètres régionaux dans un thread unique ou une partie d’une application, créez simplement une instance d’un `locale` objet dans ce thread ou d’une partie du code.

> [!NOTE]
> Appel [locale::global](../standard-library/locale-class.md#global) modifie les paramètres régionaux pour la bibliothèque C++ Standard et la bibliothèque Runtime C. Toutefois, l’appel [setlocale](../preprocessor/setlocale.md) modifie uniquement les paramètres régionaux de la bibliothèque Runtime C ; la bibliothèque Standard C++ n’est pas affectée.

Les exemples suivants montrent comment utiliser le [setlocale](../preprocessor/setlocale.md) (fonction), le [locale, classe](../standard-library/locale-class.md)et le [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) (fonction) pour modifier les paramètres régionaux d’une application dans différents scénarios.

## <a name="example"></a>Exemple

Dans cet exemple, le thread principal génère deux threads enfants. Le premier thread, Thread A, Active les paramètres régionaux par thread en appelant `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Le deuxième thread, Thread B, ainsi que le thread principal, n’activez pas les paramètres régionaux par thread. Thread A entreprend alors modifier les paramètres régionaux à l’aide de la [setlocale](../preprocessor/setlocale.md) fonction de la bibliothèque Runtime C.

Étant donné que le Thread A possède par thread activé les paramètres régionaux, uniquement les fonctions de bibliothèque Runtime C de lancer le Thread A à l’aide des paramètres régionaux « français ». Les fonctions de bibliothèque Runtime C dans Thread B et dans le thread principal continuent à utiliser les paramètres régionaux « C ». En outre, depuis [setlocale](../preprocessor/setlocale.md) n’affecte pas les paramètres régionaux à la bibliothèque Standard C++, bibliothèque Standard C++ tous les objets de continuent à utiliser les paramètres régionaux « C ».

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

## <a name="example"></a>Exemple

Dans cet exemple, le thread principal génère deux threads enfants. Le premier thread, Thread A, Active les paramètres régionaux par thread en appelant `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Le deuxième thread, Thread B, ainsi que le thread principal, n’activez pas les paramètres régionaux par thread. Thread A entreprend alors modifier les paramètres régionaux à l’aide de la [locale::global](../standard-library/locale-class.md#global) méthode de la bibliothèque Standard C++.

Étant donné que le Thread A possède par thread activé les paramètres régionaux, uniquement les fonctions de bibliothèque Runtime C de lancer le Thread A à l’aide des paramètres régionaux « français ». Les fonctions de bibliothèque Runtime C dans Thread B et dans le thread principal continuent à utiliser les paramètres régionaux « C ». Toutefois, étant donné que le [locale::global](../standard-library/locale-class.md#global) méthode modifie les paramètres régionaux « globalement », tous les objets de bibliothèque C++ Standard dans tous les threads commencent à utiliser les paramètres régionaux « français ».

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

## <a name="example"></a>Exemple

Dans cet exemple, le thread principal génère deux threads enfants. Le premier thread, Thread A, Active les paramètres régionaux par thread en appelant `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Le deuxième thread, Thread B, ainsi que le thread principal, n’activez pas les paramètres régionaux par thread. Thread B entreprend alors de modifier les paramètres régionaux à l’aide de la [setlocale](../preprocessor/setlocale.md) fonction de la bibliothèque Runtime C.

Étant donné que Thread B n’a pas activé les paramètres régionaux par thread, les fonctions de bibliothèque Runtime C dans Thread B et dans le thread principal commencer à utiliser les paramètres régionaux « français ». Les fonctions de la bibliothèque Runtime C dans Thread A continuent à utiliser les paramètres régionaux « C », car le Thread A a activé les paramètres régionaux par thread. En outre, depuis [setlocale](../preprocessor/setlocale.md) n’affecte pas les paramètres régionaux à la bibliothèque Standard C++, bibliothèque Standard C++ tous les objets de continuent à utiliser les paramètres régionaux « C ».

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

## <a name="example"></a>Exemple

Dans cet exemple, le thread principal génère deux threads enfants. Le premier thread, Thread A, Active les paramètres régionaux par thread en appelant `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Le deuxième thread, Thread B, ainsi que le thread principal, n’activez pas les paramètres régionaux par thread. Thread B entreprend alors de modifier les paramètres régionaux à l’aide de la [locale::global](../standard-library/locale-class.md#global) méthode de la bibliothèque Standard C++.

Étant donné que Thread B n’a pas activé les paramètres régionaux par thread, les fonctions de bibliothèque Runtime C dans Thread B et dans le thread principal commencer à utiliser les paramètres régionaux « français ». Les fonctions de la bibliothèque Runtime C dans Thread A continuent à utiliser les paramètres régionaux « C », car le Thread A a activé les paramètres régionaux par thread. Toutefois, étant donné que le [locale::global](../standard-library/locale-class.md#global) méthode modifie les paramètres régionaux « globalement », tous les objets de bibliothèque C++ Standard dans tous les threads commencent à utiliser les paramètres régionaux « français ».

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
[\<clocale >](../standard-library/clocale.md)<br/>
[\<locale>](../standard-library/locale.md)<br/>
[locale, classe](../standard-library/locale-class.md)