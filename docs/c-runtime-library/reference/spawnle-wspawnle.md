---
title: _spawnle, _wspawnle
ms.date: 11/04/2016
api_name:
- _spawnle
- _wspawnle
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- spawnle
- _spawnle
- wspawnle
- _wspawnle
helpviewer_keywords:
- spawnle function
- processes, creating
- _wspawnle function
- processes, executing new
- process creation
- wspawnle function
- _spawnle function
ms.assetid: 80308892-2815-49b1-8cca-53894c366f5a
ms.openlocfilehash: a0225d007bfc69d88982b4c130410bc6be9abc06
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947962"
---
# <a name="_spawnle-_wspawnle"></a>_spawnle, _wspawnle

Crée et exécute un nouveau processus.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _spawnle(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wspawnle(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Paramètres

*mode*<br/>
Mode d'exécution du processus appelant.

*cmdname*<br/>
Chemin d'accès du fichier à exécuter.

*arg0*, *Arg1*,... *argN*<br/>
Liste des pointeurs vers les arguments. L’argument *arg0* est généralement un pointeur vers *CmdName*. Les arguments *Arg1* à *argN* sont des pointeurs vers les chaînes de caractères formant la nouvelle liste d’arguments. Après *argN*, il doit exister un pointeur **null** pour marquer la fin de la liste d’arguments.

*envp*<br/>
Tableau de pointeurs vers les paramètres d'environnement.

## <a name="return-value"></a>Valeur de retour

La valeur de retour d’un **_spawnle** ou d’un **_wspawnle** synchrone ( **_P_WAIT** spécifié pour le *mode*) est l’état de sortie du nouveau processus. La valeur de retour d’un **_spawnle** ou d’un **_wspawnle** asynchrone ( **_P_NOWAIT** ou **_P_NOWAITO** spécifié pour le *mode*) est le handle de processus. L'état de sortie est 0 si le processus s'est terminé normalement. Vous pouvez définir l’état de sortie à une valeur différente de zéro si le processus généré appelle spécifiquement la routine de **sortie** avec un argument différent de zéro. Si le nouveau processus ne définissait pas explicitement un état de sortie positif, un état de sortie positif indique une sortie anormale avec arrêt ou interruption. Une valeur de retour de-1 indique une erreur (le nouveau processus n’est pas démarré). Dans ce cas, **errno** est défini sur l’une des valeurs suivantes.

|||
|-|-|
| **E2BIG** | La liste des arguments dépasse 1024 octets. |
| **EINVAL** | l’argument *mode* n’est pas valide. |
| **ENOENT** | Fichier ou chemin d'accès introuvable. |
| **ENOEXEC** | Le fichier spécifié n'est pas exécutable ou a un format de fichier exécutable non valide. |
| **ENOMEM** | Mémoire insuffisante pour exécuter le nouveau processus. |

Pour plus d'informations sur ces codes de retour et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chacune de ces fonctions crée et exécute un nouveau processus, passant chaque argument de ligne de commande en tant que paramètre distinct et passant également un tableau de pointeurs aux paramètres d’environnement.

Ces fonctions valident leurs paramètres. Si *CmdName* ou *arg0* est une chaîne vide ou un pointeur null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** sur **EINVAL**et retournent-1. Aucun nouveau processus généré.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_spawnle**|\<process.h>|
|**_wspawnle**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l'exemple de [Fonctions _spawn, _wspawn](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn, fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec, fonctions](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
