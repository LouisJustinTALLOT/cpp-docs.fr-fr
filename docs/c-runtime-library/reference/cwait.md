---
title: _cwait
ms.date: 4/2/2020
api_name:
- _cwait
- _o__cwait
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
- api-ms-win-crt-process-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: d54f62c8ce391b2c8ead92a0a73ac48e6f2b3cb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348149"
---
# <a name="_cwait"></a>_cwait

Attend la fin d'un autre processus.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _cwait(
   int *termstat,
   intptr_t procHandle,
   int action
);
```

### <a name="parameters"></a>Paramètres

*termstat*<br/>
Pointeur vers un tampon où le code de résultat du processus spécifié sera stocké, ou **NULL**.

*procHandle (procHandle)*<br/>
La poignée du processus à attendre (c’est-à-dire le processus qui doit se terminer avant **_cwait** peut revenir).

*action*<br/>
NULL: Ignoré par les applications du système d’exploitation Windows; pour d’autres applications: code d’action à effectuer sur *procHandle*.

## <a name="return-value"></a>Valeur de retour

Lorsque le processus spécifié est terminé avec succès, renvoie la poignée du processus spécifié et définit le *termstat* au code de résultat qui est retourné par le processus spécifié. Sinon, retourne -1 et définit **errno** comme suit.

|Valeur|Description|
|-----------|-----------------|
|**ECHILD**|Aucun processus spécifié n’existe, *procHandle* est invalide, ou l’appel à [l’API GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess) ou [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) a échoué.|
|**EINVAL (EN)**|*l’action* est invalide.|

Pour plus d’informations sur ces codes de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_cwait** attend la fin de l’ID processus du processus spécifié qui est fourni par *procHandle*. La valeur du *procHandle* qui est passé à **_cwait** devrait être la valeur qui est retournée par l’appel à la fonction [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) qui a créé le processus spécifié. Si l’ID du processus se termine avant **_cwait** est appelé, **_cwait** revient immédiatement. **_cwait** peut être utilisé par n’importe quel processus pour attendre tout autre processus connu pour lequel une poignée valide (*procHandle*) existe.

*termstat* indique un tampon où le code de retour du processus spécifié sera stocké. La valeur du *termstat* indique si le processus spécifié a pris fin normalement en appelant l’API Windows [ExitProcess.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) **ExitProcess** est appelé en interne si le processus spécifié appelle **la sortie** ou **_exit**, retourne de **la main**, ou atteint la fin de la **principale**. Pour plus d’informations sur la valeur qui est passée en arrière par *termstat*, voir [GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess). Si **_cwait** est appelé en utilisant une valeur **NULL** pour *termstat*, le code de retour du processus spécifié n’est pas stocké.

Le paramètre *d’action* est ignoré par le système d’exploitation Windows parce que les relations parent-enfant ne sont pas implémentées dans ces environnements.

Sauf si *procHandle* est de -1 ou -2 (poignées au processus ou au fil en cours), la poignée sera fermée. Ainsi, dans ce cas, n'utilisez pas le handle retourné.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_cwait.c
// compile with: /c
// This program launches several processes and waits
// for a specified process to finish.

#define _CRT_RAND_S

#include <windows.h>
#include <process.h>
#include <stdlib.h>
#include <stdio.h>
#include <time.h>

// Macro to get a random integer within a specified range
#define getrandom( min, max ) (( (rand_s (&number), number) % (int)((( max ) + 1 ) - ( min ))) + ( min ))

struct PROCESS
{
   int     nPid;
   char    name[40];
} process[4] = { { 0, "Ann" }, { 0, "Beth" }, { 0, "Carl" }, { 0, "Dave" } };

int main( int argc, char *argv[] )
{
   int termstat, c;
   unsigned int number;

   srand( (unsigned)time( NULL ) );    // Seed randomizer

   // If no arguments, this is the calling process
   if ( argc == 1 )
   {
      // Spawn processes in numeric order
      for ( c = 0; c < 4; c++ ) {
         _flushall();
         process[c].nPid = _spawnl( _P_NOWAIT, argv[0], argv[0],
                                    process[c].name, NULL );
      }

      // Wait for randomly specified process, and respond when done
      c = getrandom( 0, 3 );
      printf( "Come here, %s.\n", process[c].name );
      _cwait( &termstat, process[c].nPid, _WAIT_CHILD );
      printf( "Thank you, %s.\n", process[c].name );

   }
   // If there are arguments, this must be a spawned process
   else
   {
      // Delay for a period that's determined by process number
      Sleep( (argv[1][0] - 'A' + 1) * 1000L );
      printf( "Hi, Dad. It's %s.\n", argv[1] );
   }
}
```

```Output
Hi, Dad. It's Ann.
Come here, Ann.
Thank you, Ann.
Hi, Dad. It's Beth.
Hi, Dad. It's Carl.
Hi, Dad. It's Dave.
```

## <a name="see-also"></a>Voir aussi

[Contrôle des processus et de l’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, fonctions _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
