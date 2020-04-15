---
title: _spawnv, _wspawnv
ms.date: 4/2/2020
api_name:
- _wspawnv
- _spawnv
- _o__spawnv
- _o__wspawnv
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
- wspawnv
- _spawnv
- _wspawnv
helpviewer_keywords:
- wspawnv function
- processes, creating
- _spawnv function
- processes, executing new
- process creation
- _wspawnv function
- spawnv function
ms.assetid: 72360ef4-dfa9-44c1-88c1-b3ecb660aa7d
ms.openlocfilehash: f4a4d695e265c28efd1b9da8588752d8b2635163
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355896"
---
# <a name="_spawnv-_wspawnv"></a>_spawnv, _wspawnv

Crée et exécute un nouveau processus.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _spawnv(
   int mode,
   const char *cmdname,
   const char *const *argv
);
intptr_t _wspawnv(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>Paramètres

*mode*<br/>
Mode d'exécution du processus appelant.

*cmdname*<br/>
Chemin d'accès du fichier à exécuter.

*argv argv*<br/>
Tableau de pointeurs vers les arguments. *L’argument argv*[0] est généralement un pointeur à un chemin en mode réel ou au nom du programme en mode protégé, et *argv*[1] par *argv*[**n**] sont des pointeurs aux chaînes de caractère formant la nouvelle liste d’arguments. *L’argument argv***[n** '1] doit être un pointeur **NULL** pour marquer la fin de la liste d’arguments.

## <a name="return-value"></a>Valeur de retour

La valeur de retour d’un **_spawnv** synchrone ou **d’une _wspawnv** **(_P_WAIT** spécifiée pour le *mode*) est l’état de sortie du nouveau processus. La valeur de retour d’un **_spawnv** ou **d’une _wspawnv** asynchrone **(_P_NOWAIT** ou **_P_NOWAITO** spécifiée pour le *mode*) est la poignée de processus. L'état de sortie est 0 si le processus s'est terminé normalement. Vous pouvez définir le statut de sortie à une valeur non zéro si le processus engendré appelle spécifiquement la routine **de sortie** avec un argument non zéro. Si le nouveau processus ne définissait pas explicitement un état de sortie positif, un état de sortie positif indique une sortie anormale avec arrêt ou interruption. Une valeur de rendement de -1 indique une erreur (le nouveau processus n’est pas commencé). Dans ce cas, **errno** est réglé sur l’une des valeurs suivantes.

|||
|-|-|
| **E2BIG** | La liste des arguments dépasse 1024 octets. |
| **EINVAL (EN)** | *l’argument du mode* est invalide. |
| **ENOENT (ENOENT)** | Fichier ou chemin d'accès introuvable. |
| **ENOEXEC** | Le fichier spécifié n'est pas exécutable ou a un format de fichier exécutable non valide. |
| **ENOMEM (ENOMEM)** | Mémoire insuffisante pour exécuter le nouveau processus. |

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chacune de ces fonctions crée et exécute un nouveau processus, passant un tableau de pointeurs à des arguments de ligne de commande.

Ces fonctions valident leurs paramètres. Si l’un ou *l’autre cmdname* ou *argv* est un pointeur nul, ou si *argv* pointe à pointeur nul, ou *argv*[0] est une chaîne vide, le gestionnaire de paramètre invalide est invoqué, comme décrit dans [la validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions **définies errno** à **EINVAL**, et le retour -1. Aucun nouveau processus généré.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_spawnv**|\<stdio.h > ou \<process.h >|
|**_wspawnv**|\<stdio.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple dans [_spawn, _wspawn Functions](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Voir aussi

[Contrôle des processus et de l’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, fonctions _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, fonctions _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
