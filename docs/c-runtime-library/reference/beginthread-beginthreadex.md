---
description: 'En savoir plus sur : _beginthread, _beginthreadex'
title: _beginthread, _beginthreadex
ms.date: 4/2/2020
api_name:
- _beginthread
- _beginthreadex
- _o__beginthread
- _o__beginthreadex
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- beginthread
- _beginthread
- beginthreadex
- _beginthreadex
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
ms.openlocfilehash: f4357186a970914e70116650bd1c218521327f99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171905"
---
# <a name="_beginthread-_beginthreadex"></a>_beginthread, _beginthreadex

Crée un thread.

## <a name="syntax"></a>Syntaxe

```cpp
uintptr_t _beginthread( // NATIVE CODE
   void( __cdecl *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthread( // MANAGED CODE
   void( __clrcall *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthreadex( // NATIVE CODE
   void *security,
   unsigned stack_size,
   unsigned ( __stdcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
uintptr_t _beginthreadex( // MANAGED CODE
   void *security,
   unsigned stack_size,
   unsigned ( __clrcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
```

### <a name="parameters"></a>Paramètres

*start_address*<br/>
Adresse de début d'une routine qui commence l'exécution d'un nouveau thread. Par **_beginthread**, la Convention d’appel est [__cdecl](../../cpp/cdecl.md) (pour le code natif) ou [__clrcall](../../cpp/clrcall.md) (pour le code managé); pour **_beginthreadex**, il s’agit soit d' [__stdcall](../../cpp/stdcall.md) (pour le code natif), soit de [__clrcall](../../cpp/clrcall.md) (pour le code managé).

*stack_size*<br/>
Taille de la pile d'un nouveau thread ou 0.

*arglist*<br/>
Liste d’arguments à passer à un nouveau thread ou **null**.

*Security*<br/>
Pointeur vers une structure [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui détermine si le handle retourné peut être hérité par des processus enfants. Si *Security* a la **valeur null**, le handle ne peut pas être hérité. Doit avoir la **valeur null** pour les applications Windows 95.

*initflag*<br/>
Indicateurs qui contrôlent l'état initial d'un nouveau thread. Affectez la valeur 0 à *initflag* pour qu’elle s’exécute immédiatement, ou pour **CREATE_SUSPENDED** pour créer le thread dans un état suspendu ; Utilisez [ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread) pour exécuter le thread. Affectez à *initflag* la valeur **STACK_SIZE_PARAM_IS_A_RESERVATION** indicateur pour utiliser *STACK_SIZE* comme taille de réserve initiale de la pile en octets ; Si cet indicateur n’est pas spécifié, *STACK_SIZE* spécifie la taille de validation.

*thrdaddr*<br/>
Pointe vers une variable 32 bits qui reçoit l'identificateur du thread. Si la **valeur est null**, elle n’est pas utilisée.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, chacune de ces fonctions retourne un handle au thread nouvellement créé. Toutefois, si le thread nouvellement créé s’arrête trop rapidement, **_beginthread** peut ne pas retourner un handle valide. (Voir la discussion dans la section Notes.) En cas d’erreur, **_beginthread** retourne-1L et **errno** a la valeur **EAGAIN** s’il y a trop de threads, à **EINVAL** si l’argument n’est pas valide ou que la taille de la pile est incorrecte, ou à **EACCES** si les ressources sont insuffisantes (telles que la mémoire). En cas d’erreur, **_beginthreadex** retourne 0, et **errno** et **_doserrno** sont définis.

Si *start_address* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** sur **EINVAL** et retournent-1.

Pour plus d’informations sur ces codes de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pour plus d’informations sur les **uintptr_t**, consultez [types standard](../../c-runtime-library/standard-types.md).

## <a name="remarks"></a>Notes

La fonction **_beginthread** crée un thread qui commence l’exécution d’une routine à *start_address*. La routine à *start_address* doit utiliser la **`__cdecl`** Convention d’appel (pour le code natif) ou **__clrcall** (pour le code managé) et ne doit pas avoir de valeur de retour. Lorsque le thread retourne de cette routine, il est terminé automatiquement. Pour plus d’informations sur les threads, consultez [Prise en charge du multithreading pour le code plus ancien (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

**_beginthreadex** ressemble à l’API [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) Win32 plus près que **_beginthread** . **_beginthreadex** diffère de **_beginthread** des manières suivantes :

- **_beginthreadex** a trois paramètres supplémentaires : *initflag*, *Security* et **threadaddr**. Le nouveau thread peut être créé dans un état suspendu, avec une sécurité spécifiée, et il est accessible à l’aide de *thrdaddr*, qui est l’identificateur de thread.

- La routine à *start_address* transmise à **_beginthreadex** doit utiliser la **`__stdcall`** Convention d’appel (pour le code natif) ou **__clrcall** (pour le code managé) et doit retourner un code de sortie de thread.

- **_beginthreadex** retourne 0 en cas d’échec, plutôt que-1L.

- Un thread créé à l’aide de **_beginthreadex** se termine par un appel à [_endthreadex](endthread-endthreadex.md).

La fonction **_beginthreadex** vous donne davantage de contrôle sur la façon dont le thread est créé que **_beginthread** . La fonction **_endthreadex** est également plus flexible. Par exemple, avec **_beginthreadex**, vous pouvez utiliser les informations de sécurité, définir l’état initial du thread (en cours d’exécution ou suspendu) et obtenir l’identificateur de thread du thread nouvellement créé. Vous pouvez également utiliser le handle de thread retourné par **_beginthreadex** avec les API de synchronisation, ce que vous ne pouvez pas faire avec **_beginthread**.

Il est plus sûr d’utiliser **_beginthreadex** que **_beginthread**. Si le thread généré par **_beginthread** s’arrête rapidement, le handle retourné à l’appelant de **_beginthread** peut être non valide ou pointer vers un autre thread. Toutefois, le handle retourné par **_beginthreadex** doit être fermé par l’appelant de **_beginthreadex**. il est donc garanti qu’il s’agit d’un handle valide si **_beginthreadex** n’a pas retourné d’erreur.

Vous pouvez appeler [_endthread](endthread-endthreadex.md) ou **_endthreadex** explicitement pour terminer un thread ; Toutefois, **_endthread** ou **_endthreadex** est appelé automatiquement lorsque le thread retourne de la routine passée en tant que paramètre. L’arrêt d’un thread avec un appel à **_endthread** ou **_endthreadex** permet de garantir une récupération correcte des ressources allouées pour le thread.

**_endthread** ferme automatiquement le handle de thread, contrairement à **_endthreadex** . Par conséquent, lorsque vous utilisez **_beginthread** et **_endthread**, ne fermez pas explicitement le handle du thread en appelant l’API [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) Win32. Ce comportement diffère de l’API [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) Win32.

> [!NOTE]
> Pour un fichier exécutable lié à LIBCMT. lib, n’appelez pas l’API **ExitThread** Win32 afin de ne pas empêcher le système Runtime de récupérer les ressources allouées. **_endthread** et **_endthreadex** récupérer les ressources de thread allouées, puis appeler **ExitThread**.

Le système d’exploitation gère l’allocation de la pile lors de l’appel de **_beginthread** ou **_beginthreadex** ; vous n’êtes pas obligé de passer l’adresse de la pile de threads à l’une de ces fonctions. En outre, l’argument *STACK_SIZE* peut être 0, auquel cas le système d’exploitation utilise la même valeur que la pile spécifiée pour le thread principal.

*arglist* est un paramètre à passer au thread nouvellement créé. En général, il s'agit de l'adresse d'un élément de donnée, tel qu'une chaîne de caractères. *arglist* peut être **null** si ce n’est pas nécessaire, mais **_beginthread** et **_beginthreadex** doivent recevoir une valeur à passer au nouveau thread. Tous les threads sont arrêtés si un thread appelle [Abort](abort.md), **Exit**, **_exit** ou **ExitProcess**.

Les paramètres régionaux du nouveau thread sont initialisés à l’aide des informations de paramètres régionaux actuels globaux par processus. Si les paramètres régionaux par thread sont activés par un appel à [_configthreadlocale](configthreadlocale.md) (globalement ou pour de nouveaux threads uniquement), le thread peut modifier ses paramètres régionaux indépendamment des autres threads en appelant **setlocale** ou **_wsetlocale**. Les threads qui n’ont pas l’indicateur de paramètres régionaux par thread défini peuvent affecter les informations de paramètres régionaux dans tous les autres threads qui n’ont pas non plus l’indicateur de paramètres régionaux par thread défini, ainsi que tous les threads nouvellement créés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Pour le code **/CLR** , **_beginthread** et **_beginthreadex** ont chacun deux surcharges. L’une utilise un pointeur de fonction de convention d’appel native, tandis que l’autre prend un pointeur de fonction **__clrcall** . La première surcharge n'est pas sécurisée au niveau du domaine d'application et ne le sera jamais. Si vous écrivez du code **/CLR** , vous devez vous assurer que le nouveau thread entre dans le domaine d’application correct avant d’accéder aux ressources managées. Pour cela, vous pouvez par exemple utiliser la [fonction call_in_appdomain](../../dotnet/call-in-appdomain-function.md). La deuxième surcharge est sécurisée au domaine d’application ; le thread nouvellement créé se terminera toujours dans le domaine d’application de l’appelant de **_beginthread** ou **_beginthreadex**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions multithread des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md) .

Pour utiliser **_beginthread** ou **_beginthreadex**, l’application doit être liée à l’une des bibliothèques Runtime C multithread.

## <a name="examples"></a>Exemples

L’exemple suivant utilise **_beginthread** et **_endthread**.

```C
// crt_BEGTHRD.C
// compile with: /MT /D "_X86_" /c
// processor: x86
#include <windows.h>
#include <process.h>    /* _beginthread, _endthread */
#include <stddef.h>
#include <stdlib.h>
#include <conio.h>

void Bounce( void * );
void CheckKey( void * );

// GetRandom returns a random integer between min and max.
#define GetRandom( min, max ) ((rand() % (int)(((max) + 1) - (min))) + (min))
// GetGlyph returns a printable ASCII character value
#define GetGlyph( val ) ((char)((val + 32) % 93 + 33))

BOOL repeat = TRUE;                 // Global repeat flag
HANDLE hStdOut;                     // Handle for console window
CONSOLE_SCREEN_BUFFER_INFO csbi;    // Console information structure

int main()
{
    int param = 0;
    int * pparam = &param;

    // Get display screen's text row and column information.
    hStdOut = GetStdHandle( STD_OUTPUT_HANDLE );
    GetConsoleScreenBufferInfo( hStdOut, &csbi );

    // Launch CheckKey thread to check for terminating keystroke.
    _beginthread( CheckKey, 0, NULL );

    // Loop until CheckKey terminates program or 1000 threads created.
    while( repeat && param < 1000 )
    {
        // launch another character thread.
        _beginthread( Bounce, 0, (void *) pparam );

        // increment the thread parameter
        param++;

        // Wait one second between loops.
        Sleep( 1000L );
    }
}

// CheckKey - Thread to wait for a keystroke, then clear repeat flag.
void CheckKey( void * ignored )
{
    _getch();
    repeat = 0;    // _endthread implied
}

// Bounce - Thread to create and control a colored letter that moves
// around on the screen.
//
// Params: parg - the value to create the character from
void Bounce( void * parg )
{
    char       blankcell = 0x20;
    CHAR_INFO  ci;
    COORD      oldcoord, cellsize, origin;
    DWORD      result;
    SMALL_RECT region;

    cellsize.X = cellsize.Y = 1;
    origin.X = origin.Y = 0;

    // Generate location, letter and color attribute from thread argument.
    srand( _threadid );
    oldcoord.X = region.Left = region.Right =
        GetRandom(csbi.srWindow.Left, csbi.srWindow.Right - 1);
    oldcoord.Y = region.Top = region.Bottom =
        GetRandom(csbi.srWindow.Top, csbi.srWindow.Bottom - 1);
    ci.Char.AsciiChar = GetGlyph(*((int *)parg));
    ci.Attributes = GetRandom(1, 15);

    while (repeat)
    {
        // Pause between loops.
        Sleep( 100L );

        // Blank out our old position on the screen, and draw new letter.
        WriteConsoleOutputCharacterA(hStdOut, &blankcell, 1, oldcoord, &result);
        WriteConsoleOutputA(hStdOut, &ci, cellsize, origin, &region);

        // Increment the coordinate for next placement of the block.
        oldcoord.X = region.Left;
        oldcoord.Y = region.Top;
        region.Left = region.Right += GetRandom(-1, 1);
        region.Top = region.Bottom += GetRandom(-1, 1);

        // Correct placement (and beep) if about to go off the screen.
        if (region.Left < csbi.srWindow.Left)
            region.Left = region.Right = csbi.srWindow.Left + 1;
        else if (region.Right >= csbi.srWindow.Right)
            region.Left = region.Right = csbi.srWindow.Right - 2;
        else if (region.Top < csbi.srWindow.Top)
            region.Top = region.Bottom = csbi.srWindow.Top + 1;
        else if (region.Bottom >= csbi.srWindow.Bottom)
            region.Top = region.Bottom = csbi.srWindow.Bottom - 2;

        // If not at a screen border, continue, otherwise beep.
        else
            continue;
        Beep((ci.Char.AsciiChar - 'A') * 100, 175);
    }
    // _endthread given to terminate
    _endthread();
}
```

Appuyez sur n'importe quelle touche pour fermer l'exemple d'application.

L’exemple de code suivant montre comment vous pouvez utiliser le handle de thread retourné par **_beginthreadex** avec l’API de synchronisation [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject). Le thread principal attend que le second thread se termine avant de continuer. Lorsque le deuxième thread appelle **_endthreadex**, il fait passer son objet thread à l’état signalé. Le thread principal peut ainsi continuer à s'exécuter. Cela ne peut pas être fait avec **_beginthread** et **_endthread**, car **_endthread** appelle **CloseHandle**, ce qui détruit l’objet thread avant de pouvoir le définir à l’état signalé.

```cpp
// crt_begthrdex.cpp
// compile with: /MT
#include <windows.h>
#include <stdio.h>
#include <process.h>

unsigned Counter;
unsigned __stdcall SecondThreadFunc( void* pArguments )
{
    printf( "In second thread...\n" );

    while ( Counter < 1000000 )
        Counter++;

    _endthreadex( 0 );
    return 0;
}

int main()
{
    HANDLE hThread;
    unsigned threadID;

    printf( "Creating second thread...\n" );

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc, NULL, 0, &threadID );

    // Wait until second thread terminates. If you comment out the line
    // below, Counter will not be correct because the thread has not
    // terminated, and Counter most likely has not been incremented to
    // 1000000 yet.
    WaitForSingleObject( hThread, INFINITE );
    printf( "Counter should be 1000000; it is-> %d\n", Counter );
    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
Creating second thread...
In second thread...
Counter should be 1000000; it is-> 1000000
```

## <a name="see-also"></a>Voir aussi

- [Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)
- [_endthread, _endthreadex](endthread-endthreadex.md)
- [abort](abort.md)
- [exit, _Exit, _exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
