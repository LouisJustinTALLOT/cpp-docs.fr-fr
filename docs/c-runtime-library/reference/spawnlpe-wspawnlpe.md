---
title: _spawnlpe, _wspawnlpe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _spawnlpe
- _wspawnlpe
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
- spawnlpe
- _wspawnlpe
- _spawnlpe
- wspawnlpe
dev_langs:
- C++
helpviewer_keywords:
- _wspawnlpe function
- wspawnlpe function
- processes, creating
- spawnlpe function
- _spawnlpe function
- processes, executing new
- process creation
ms.assetid: e171ebfa-70e7-4c44-8331-2a291fc17bd6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be8e86ddb6405c39f877bd9065a931b66238c2b6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413301"
---
# <a name="spawnlpe-wspawnlpe"></a>_spawnlpe, _wspawnlpe

Crée et exécute un nouveau processus.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _spawnlpe(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wspawnlpe(
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

*CmdName*<br/>
Chemin d'accès du fichier à exécuter.

*arg0*, *arg1*,... *argn*<br/>
Liste des pointeurs vers les arguments. Le *arg0* est généralement un pointeur vers *cmdname*. Les arguments *arg1* via *argn* sont des pointeurs vers les chaînes de caractères qui forment la nouvelle liste d’arguments. Suivant *argn*, il doit y avoir un **NULL** pointeur pour marquer la fin de la liste d’arguments.

*envp*<br/>
Tableau de pointeurs vers les paramètres d'environnement.

## <a name="return-value"></a>Valeur de retour

La valeur de retour à partir d’une commande synchrone **_spawnlpe** ou **_wspawnlpe** (**_P_WAIT** spécifié pour *mode*) est l’état de sortie de la nouvelle processus. La valeur de retour à partir d’une commande asynchrone **_spawnlpe** ou **_wspawnlpe** (**_P_NOWAIT** ou **_P_NOWAITO** spécifiée pour  *mode*) est le handle du processus. L'état de sortie est 0 si le processus s'est terminé normalement. Vous pouvez définir l’état de sortie une valeur différente de zéro si le processus engendré utilise spécifiquement un argument différent de zéro pour appeler le **quitter** routine. Si le nouveau processus ne définissait pas explicitement un état de sortie positif, un état de sortie positif indique une sortie anormale provoquée par un abandon ou une interruption. Une valeur de retour de -1 indique une erreur (le nouveau processus n’est pas lancé). Dans ce cas, **errno** est définie à une des valeurs suivantes.

|||
|-|-|
**E2BIG**|La liste des arguments dépasse 1024 octets.
**EINVAL**|*mode* argument n’est pas valide.
**ENOENT**|Fichier ou chemin d'accès introuvable.
**ENOEXEC**|Le fichier spécifié n'est pas exécutable ou a un format de fichier exécutable non valide.
**ENOMEM**|Mémoire insuffisante pour exécuter le nouveau processus.

Pour plus d’informations sur ces codes de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chacune de ces fonctions crée et exécute un nouveau processus, passe chaque argument de ligne de commande en tant que paramètre distinct et passe un tableau de pointeurs aux paramètres d’environnement. Ces fonctions utilisent la **chemin d’accès** variable d’environnement pour rechercher le fichier à exécuter.

Ces fonctions valident leurs paramètres. Si le paramètre *cmdname* ou *arg0* est une chaîne vide ou un pointeur null, le Gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL**et retournent -1. Aucun nouveau processus généré.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_spawnlpe**|\<process.h>|
|**_wspawnlpe**|\<stdio.h> ou \<wchar.h>|

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
