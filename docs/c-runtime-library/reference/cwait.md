---
title: _cwait
description: Informations de référence sur l’API pour la fonction runtime Microsoft Visual C `_cwait()` .
ms.date: 10/23/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 5b4c4db3c40645b947583b722d345c2e80dcaa8e
ms.sourcegitcommit: faecabcdd12ff53eb79dc0df193fc3567f2f037c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92639105"
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

*`termstat`*\
Pointeur vers une mémoire tampon où le code de résultat du processus spécifié sera stocké ou **`NULL`** .

*`procHandle`*\
Handle vers le processus à attendre (autrement dit, le processus qui doit se terminer avant que **_cwait** puisse retourner).

*`action`*\
**`NULL`** : Ignoré par les applications du système d’exploitation Windows ; pour d’autres applications : code d’action à effectuer sur *`procHandle`* .

## <a name="return-value"></a>Valeur de retour

Quand le processus spécifié s’est terminé avec succès, retourne le handle du processus spécifié et définit *`termstat`* sur le code de résultat retourné par le processus spécifié. Sinon, retourne-1 et définit **`errno`** comme suit.

|Valeur|Description|
|-----------|-----------------|
|**`ECHILD`**|Aucun processus spécifié n’existe, *`procHandle`* n’est pas valide ou l’appel à l' [`GetExitCodeProcess`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess) [`WaitForSingleObject`](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) API ou a échoué.|
|**`EINVAL`**|*`action`* n’est pas valide.|

Pour plus d’informations sur ces codes de retour et d’autres, consultez [`errno, _doserrno, _sys_errlist, and _sys_nerr`](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Notes

La **`_cwait`** fonction attend la fin de l’ID de processus du processus spécifié fourni par *`procHandle`* . La valeur de *`procHandle`* passée à **`_cwait`** doit être la valeur retournée par l’appel à la [`_spawn`](../../c-runtime-library/spawn-wspawn-functions.md) fonction qui a créé le processus spécifié. Si l’ID de processus se termine avant que **`_cwait`** ne soit appelé, est **`_cwait`** retourné immédiatement. **`_cwait`** peut être utilisé par n’importe quel processus pour attendre tout autre processus connu pour lequel il existe un handle valide ( *`procHandle`* ).

*`termstat`* pointe vers une mémoire tampon où le code de retour du processus spécifié sera stocké. La valeur de *`termstat`* indique si le processus spécifié s’est terminé normalement en appelant l' [`ExitProcess`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) API Windows. **`ExitProcess`** est appelé en interne si le processus spécifié appelle **`exit`** ou **`_exit`** , retourne à partir de **`main`** ou atteint la fin de **`main`** . Pour plus d’informations sur la valeur retournée par le biais de *`termstat`* , consultez [GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess). Si **`_cwait`** est appelé à l’aide d’une **`NULL`** valeur pour *`termstat`* , le code de retour du processus spécifié n’est pas stocké.

Le *`action`* paramètre est ignoré par le système d’exploitation Windows, car les relations parent-enfant ne sont pas implémentées dans ces environnements.

À moins que *`procHandle`* ne soit-1 ou-2 (Handles vers le processus ou le thread actuel), le handle est fermé. Dans ce cas, n’utilisez pas le handle retourné.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**`_cwait`**|\<process.h>|\<errno.h>|

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
    intptr_t hProcess;
    char    name[40];
} process[4] = { { 0, "Ann" }, { 0, "Beth" }, { 0, "Carl" }, { 0, "Dave" } };

int main(int argc, char* argv[])
{
    int termstat, c;
    unsigned int number;

    srand((unsigned)time(NULL));    // Seed randomizer

    // If no arguments, this is the calling process
    if (argc == 1)
    {
        // Spawn processes in numeric order
        for (c = 0; c < 4; c++) {
            _flushall();
            process[c].hProcess = _spawnl(_P_NOWAIT, argv[0], argv[0],
                process[c].name, NULL);
        }

        // Wait for randomly specified process, and respond when done
        c = getrandom(0, 3);
        printf("Come here, %s.\n", process[c].name);
        _cwait(&termstat, process[c].hProcess, _WAIT_CHILD);
        printf("Thank you, %s.\n", process[c].name);

    }
    // If there are arguments, this must be a spawned process
    else
    {
        // Delay for a period that's determined by process number
        Sleep((argv[1][0] - 'A' + 1) * 1000L);
        printf("Hi, Dad. It's %s.\n", argv[1]);
    }
}
```

L’ordre des sorties varie selon l’exécution.

```Output
Hi, Dad. It's Ann.
Come here, Ann.
Thank you, Ann.
Hi, Dad. It's Beth.
Hi, Dad. It's Carl.
Hi, Dad. It's Dave.
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)\
[_spawn, _wspawn fonctions](../../c-runtime-library/spawn-wspawn-functions.md)
