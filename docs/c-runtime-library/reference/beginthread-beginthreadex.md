---
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 2d2851a7e76a43501145b1e55e8028b72c2a8afb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348672"
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
Adresse de début d'une routine qui commence l'exécution d'un nouveau thread. Pour **_beginthread,** la convention d’appel est soit [__cdecl](../../cpp/cdecl.md) (pour le code natif) ou [__clrcall](../../cpp/clrcall.md) (pour le code géré); pour **_beginthreadex,** il est soit [__stdcall](../../cpp/stdcall.md) (pour le code natif) ou [__clrcall](../../cpp/clrcall.md) (pour le code géré).

*stack_size*<br/>
Taille de la pile d'un nouveau thread ou 0.

*Arglist*<br/>
Liste d’arguments à passer à un nouveau thread, ou **NULL**.

*Sécurité*<br/>
Pointeur vers une structure [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui détermine si le handle retourné peut être hérité par des processus enfants. Si *la sécurité* est **NULL**, la poignée ne peut pas être héritée. Doit être **NULL** pour les applications Windows 95.

*initflag*<br/>
Indicateurs qui contrôlent l'état initial d'un nouveau thread. Définissez *l’initflag* à 0 pour fonctionner immédiatement, ou pour **CREATE_SUSPENDED** pour créer le fil dans un état suspendu ; utiliser [ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread) pour exécuter le thread. Définissez *l’initflag* pour **STACK_SIZE_PARAM_IS_A_RESERVATION** drapeau pour utiliser *stack_size* comme la taille initiale de la réserve de la pile dans les octets; si ce drapeau n’est pas spécifié, *stack_size* spécifie la taille du commit.

*thrdaddr*<br/>
Pointe vers une variable 32 bits qui reçoit l'identificateur du thread. Si c’est **NULL**, il n’est pas utilisé.

## <a name="return-value"></a>Valeur de retour

En cas de succès, chacune de ces fonctions renvoie une poignée au fil nouvellement créé; toutefois, si le thread nouvellement créé sort trop rapidement, **_beginthread** pourrait ne pas retourner une poignée valide. (Voir la discussion dans la section Remarques.) Sur une erreur, **_beginthread** renvoie -1L, et **errno** est réglé à **EAGAIN** s’il ya trop de fils, à **EINVAL** si l’argument est invalide ou la taille de la pile est incorrecte, ou à **EACCES** s’il ya des ressources insuffisantes (comme la mémoire). Sur une erreur, **_beginthreadex** renvois 0, et **errno** et **_doserrno** sont fixés.

Si *start_address* est **NULL**, le gestionnaire de paramètres invalides est invoqué, tel que décrit dans [La validation des paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions **définies errno** à **EINVAL** et retour -1.

Pour plus d’informations sur ces codes de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pour plus d’informations sur **uintptr_t**, voir [Standard Types](../../c-runtime-library/standard-types.md).

## <a name="remarks"></a>Notes

La fonction **_beginthread** crée un fil qui commence l’exécution d’une routine à *start_address*. La routine à *start_address* doit utiliser le **__cdecl** (pour le code natif) ou **__clrcall** (pour le code géré) convention d’appel et ne devrait avoir aucune valeur de retour. Lorsque le thread retourne de cette routine, il est terminé automatiquement. Pour plus d’informations sur les threads, consultez [Prise en charge du multithreading pour le code plus ancien (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

**_beginthreadex** ressemble plus étroitement à l’API Win32 [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) **qu'_beginthread.** **_beginthreadex** diffère de **_beginthread** de la façon suivante :

- **_beginthreadex** a trois paramètres supplémentaires: *initflag*, *Sécurité*, et **threadaddr**. Le nouveau thread peut être créé dans un état suspendu, avec une sécurité spécifiée, et peut être consulté en utilisant *thrdaddr*, qui est l’identifiant de fil.

- La routine à *start_address* qui est passé à **_beginthreadex** doit utiliser le **__stdcall** (pour le code natif) ou **__clrcall** (pour le code géré) convention d’appel et doit retourner un code de sortie de fil.

- **_beginthreadex** revient 0 sur l’échec, plutôt que -1L.

- Un fil qui est créé en utilisant **_beginthreadex** est terminé par un appel à [_endthreadex](endthread-endthreadex.md).

La fonction **_beginthreadex** vous donne plus de contrôle sur la façon dont le thread est créé que **_beginthread** ne. La fonction **_endthreadex** est également plus flexible. Par exemple, avec **_beginthreadex,** vous pouvez utiliser des informations de sécurité, définir l’état initial du thread (en cours d’exécution ou suspendu), et obtenir l’identifiant de thread du fil nouvellement créé. Vous pouvez également utiliser la poignée de fil qui est retourné par **_beginthreadex** avec les API de synchronisation, que vous ne pouvez pas faire avec **_beginthread**.

Il est plus sûr d’utiliser **_beginthreadex** que **_beginthread**. Si le fil généré par **_beginthread** sort rapidement, la poignée qui est retournée à l’appelant de **_beginthread** peut être invalide ou pointer vers un autre thread. Cependant, la poignée qui est retournée par **_beginthreadex** doit être fermée par l’appelant de **_beginthreadex**, de sorte qu’il est garanti d’être une poignée valide si **_beginthreadex** n’a pas retourné une erreur.

Vous pouvez appeler [_endthread](endthread-endthreadex.md) ou **_endthreadex** explicitement pour mettre fin à un thread; cependant, **_endthread** ou **_endthreadex** est appelé automatiquement lorsque le thread revient de la routine qui est passé comme un paramètre. La fin d’un thread avec un appel pour **_endthread** ou **_endthreadex** permet d’assurer une récupération correcte des ressources qui sont allouées pour le thread.

**_endthread** ferme automatiquement la poignée de fil, alors que **_endthreadex** ne le fait pas. Par conséquent, lorsque vous utilisez **_beginthread** et **_endthread**, ne fermez pas explicitement le manche de thread en appelant l’API Win32 [CloseHandle.](/windows/win32/api/handleapi/nf-handleapi-closehandle) Ce comportement diffère de l’API [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) Win32.

> [!NOTE]
> Pour un fichier exécutable lié à Libcmt.lib, n’appelez pas l’API Win32 **ExitThread** afin de ne pas empêcher le système de temps de répartition de récupérer les ressources allouées. **_endthread** et **_endthreadex** récupérer les ressources de thread allouées, puis appeler **ExitThread**.

Le système d’exploitation gère l’allocation de la pile **lorsqu’on appelle _beginthread** ou **_beginthreadex;** vous n’avez pas à passer l’adresse de la pile de thread à l’une ou l’autre de ces fonctions. En outre, *l’argument stack_size* peut être 0, auquel cas le système d’exploitation utilise la même valeur que la pile qui est spécifiée pour le thread principal.

*arglist* est un paramètre à transmettre au fil nouvellement créé. En général, il s'agit de l'adresse d'un élément de donnée, tel qu'une chaîne de caractères. *arglist* peut être **NULL** si elle n’est pas nécessaire, mais **_beginthread** et **_beginthreadex** doit être donné une certaine valeur pour passer au nouveau thread. Tous les threads sont terminés si un thread appelle [abort](abort.md), **sortie**, **_exit**, ou **ExitProcess**.

Le local du nouveau thread est parasémenté en utilisant les informations locales actuelles globales par processus. Si le local par thread est activé par un appel à [_configthreadlocale](configthreadlocale.md) (soit globalement ou pour de nouveaux threads seulement), le thread peut changer son local indépendamment des autres threads en appelant **setlocale** ou **_wsetlocale**. Les fils qui n’ont pas l’ensemble de drapeau local par fil peuvent affecter les informations locales dans tous les autres threads qui n’ont pas non plus l’ensemble de drapeau local par fil, ainsi que tous les fils nouvellement créés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Pour le code **/clr,** **_beginthread** et **_beginthreadex** ont chacun deux surcharges. L’un prend un pointeur de fonction d’appel-convention natif, et l’autre prend un pointeur de fonction **__clrcall.** La première surcharge n'est pas sécurisée au niveau du domaine d'application et ne le sera jamais. Si vous écrivez **/clr** code, vous devez vous assurer que le nouveau thread entre dans le domaine d’application correcte avant d’accéder aux ressources gérées. Pour cela, vous pouvez par exemple utiliser la [fonction call_in_appdomain](../../dotnet/call-in-appdomain-function.md). La deuxième surcharge est la sécurité du domaine d’application; le fil nouvellement créé se retrouvera toujours dans le domaine d’application de l’appelant de **_beginthread** ou **_beginthreadex**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions multithread des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md) .

Pour utiliser **_beginthread** ou **_beginthreadex,** l’application doit être reliée à l’une des bibliothèques multithreaded C run-time.

## <a name="example"></a>Exemple

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

## <a name="example"></a>Exemple

Le code d’échantillon suivant montre comment vous pouvez utiliser la poignée de fil qui est retournée par **_beginthreadex** avec la synchronisation API [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject). Le thread principal attend que le second thread se termine avant de continuer. Lorsque le deuxième thread appelle **_endthreadex,** il provoque son objet de fil pour aller à l’état signalé. Le thread principal peut ainsi continuer à s'exécuter. Cela ne peut pas être fait avec **_beginthread** et **_endthread**, parce que **_endthread** appelle **CloseHandle**, qui détruit l’objet de fil avant qu’il ne puisse être réglé à l’état signalé.

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

- [Contrôle des processus et de l’environnement](../../c-runtime-library/process-and-environment-control.md)
- [_endthread, _endthreadex](endthread-endthreadex.md)
- [abort](abort.md)
- [exit, _Exit, _exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
