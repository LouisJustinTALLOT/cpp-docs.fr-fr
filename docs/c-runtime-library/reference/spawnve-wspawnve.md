---
title: _spawnve, _wspawnve | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _spawnve
- _wspawnve
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
- wspawnve
- _spawnve
- _wspawnve
- spawnve
dev_langs:
- C++
helpviewer_keywords:
- _spawnve function
- spawnve function
- wspawnve function
- processes, creating
- _wspawnve function
- processes, executing new
- process creation
ms.assetid: 26d1713d-b551-4f21-a07b-e9891a2ae6cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39d048d1d79135cd40e7821a71e57aa83b286d28
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411859"
---
# <a name="spawnve-wspawnve"></a>_spawnve, _wspawnve

Crée et exécute un nouveau processus.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _spawnve(
   int mode,
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wspawnve(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Paramètres

*mode*<br/>
Mode d’exécution pour un processus appelant.

*CmdName*<br/>
Chemin d'accès du fichier à exécuter.

*argv*<br/>
Tableau de pointeurs vers les arguments. L’argument *argv*[0] est généralement un pointeur vers un chemin d’accès en mode réel ou le nom du programme en mode protégé, et *argv*[1] via *argv*[**n**] sont des pointeurs vers les chaînes de caractères formant la nouvelle liste d’arguments. L’argument *argv*[**n** + 1] doit être un **NULL** pointeur pour marquer la fin de la liste d’arguments.

*envp*<br/>
Tableau de pointeurs vers les paramètres d'environnement.

## <a name="return-value"></a>Valeur de retour

La valeur de retour à partir d’une commande synchrone **_spawnve** ou **_wspawnve** (**_P_WAIT** spécifié pour *mode*) est l’état de sortie du nouveau processus . La valeur de retour à partir d’une commande asynchrone **_spawnve** ou **_wspawnve** (**_P_NOWAIT** ou **_P_NOWAITO** spécifiée pour  *mode*) est le handle du processus. L'état de sortie est 0 si le processus s'est terminé normalement. Vous pouvez définir l’état de sortie une valeur différente de zéro si le processus engendré appelle spécifiquement la **quitter** routine avec un argument différent de zéro. Si le nouveau processus ne définissait pas explicitement un état de sortie positif, un état de sortie positif indique une sortie anormale avec arrêt ou interruption. Une valeur de retour de -1 indique une erreur (le nouveau processus n’est pas lancé). Dans ce cas, **errno** est définie à une des valeurs suivantes.

|||
|-|-|
**E2BIG**|La liste des arguments dépasse 1024 octets.
**EINVAL**|*mode* argument n’est pas valide.
**ENOENT**|Fichier ou chemin d'accès introuvable.
**ENOEXEC**|Le fichier spécifié n'est pas exécutable ou a un format de fichier exécutable non valide.
**ENOMEM**|Mémoire insuffisante pour exécuter le nouveau processus.

Pour plus d'informations sur ces codes de retour et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chacune de ces fonctions crée et exécute un nouveau processus, passant un tableau de pointeurs vers des arguments de ligne de commande et un tableau de pointeurs vers des paramètres d’environnement.

Ces fonctions valident leurs paramètres. Si le paramètre *cmdname* ou *argv* est un pointeur null, ou si *argv* pointe vers un pointeur null ou *argv*[0] est une chaîne vide, non valide Gestionnaire de paramètres est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL**et retournent -1. Aucun nouveau processus généré.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_spawnve**|\<stdio.h > ou \<process.h >|
|**_wspawnve**|\<stdio.h> ou \<wchar.h>|

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
