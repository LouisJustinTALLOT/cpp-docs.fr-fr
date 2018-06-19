---
title: _cwait | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _cwait
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cwait
dev_langs:
- C++
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 878c1c08dabe52a31a2bdf377c3e0bb167a9ae5d
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450946"
---
# <a name="cwait"></a>_cwait

Attend la fin d'un autre processus.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Pointeur vers une mémoire tampon où le code de résultat du processus spécifié sera stocké, ou **NULL**.

*procHandle*<br/>
Le handle pour le processus à attendre (autrement dit, le processus qui doit se terminer avant **_cwait** peut retourner).

*action*<br/>
NULL : L’ignoré par les applications de système d’exploitation Windows ; pour d’autres applications : code d’action à effectuer sur *procHandle*.

## <a name="return-value"></a>Valeur de retour

Lorsque le processus spécifié terminé, retourne le handle du processus spécifié et définit *termstat* pour le code de résultat retourné par le processus spécifié. Sinon, retourne -1 et définit **errno** comme suit.

|Value|Description|
|-----------|-----------------|
|**ECHILD**|Aucun processus spécifié n’existe, *procHandle* n’est pas valide ou l’appel à la [GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx) ou [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx) échoué de l’API.|
|**EINVAL**|*action* n’est pas valide.|

Pour plus d’informations sur ces codes de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_cwait** fonction attend l’arrêt de l’ID de processus du processus spécifié qui est fournie par *procHandle*. La valeur de *procHandle* qui est passé à **_cwait** doit avoir la valeur retournée par l’appel à la [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) fonction qui a créé le processus spécifié. Si l’ID de processus se termine avant **_cwait** est appelée, **_cwait** retourne immédiatement. **_cwait** peut être utilisé par n’importe quel processus pour attendre tout autre processus connu pour lequel un handle valide (*procHandle*) existe.

*termstat* pointe vers une mémoire tampon où le code de retour du processus spécifié sera stocké. La valeur de *termstat* indique si le processus spécifié s’est terminé normalement en appelant les fenêtres [ExitProcess](http://msdn.microsoft.com/library/windows/desktop/ms682658.aspx) API. **ExitProcess** est appelée en interne si le processus spécifié appelle **quitter** ou **_exit**, quitte **principal**, ou atteint la fin de **principal** . Pour plus d’informations sur la valeur qui est passée par le biais de *termstat*, consultez [GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx). Si **_cwait** est appelée en utilisant un **NULL** valeur *termstat*, le code de retour du processus spécifié n’est pas stocké.

Le *action* paramètre est ignoré par le système d’exploitation Windows, car les relations parent-enfant ne sont pas implémentées dans ces environnements.

À moins que *procHandle* est -1 ou -2 (handles pour le processus en cours ou le thread), le handle est fermé. Ainsi, dans ce cas, n'utilisez pas le handle retourné.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn, fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
