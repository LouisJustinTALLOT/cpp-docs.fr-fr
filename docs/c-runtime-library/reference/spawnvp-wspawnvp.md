---
title: _spawnvp, _wspawnvp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wspawnvp
- _spawnvp
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
- _wspawnvp
- _spawnvp
- wspawnvp
dev_langs:
- C++
helpviewer_keywords:
- wspawnvp function
- processes, creating
- _wspawnvp function
- processes, executing new
- spawnvp function
- process creation
- _spawnvp function
ms.assetid: 8d8774ec-6ad4-4680-a5aa-440cde1e0249
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e31cb0d21b6ac626dcf00c6a80e50b924adac285
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411911"
---
# <a name="spawnvp-wspawnvp"></a>_spawnvp, _wspawnvp

Crée un processus et l'exécute.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _spawnvp(
   int mode,
   const char *cmdname,
   const char *const *argv
);
intptr_t _wspawnvp(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>Paramètres

*mode*<br/>
Mode d'exécution de l'appel du processus.

*CmdName*<br/>
Chemin d'accès du fichier à exécuter.

*argv*<br/>
Tableau de pointeurs vers les arguments. L’argument *argv*[0] est généralement un pointeur vers un chemin d’accès en mode réel ou le nom du programme en mode protégé, et *argv*[1] via *argv*[**n**] sont des pointeurs vers les chaînes de caractères qui forment la nouvelle liste d’arguments. L’argument *argv*[**n** + 1] doit être un **NULL** pointeur pour marquer la fin de la liste d’arguments.

## <a name="return-value"></a>Valeur de retour

La valeur de retour à partir d’une commande synchrone **_spawnvp** ou **_wspawnvp** (**_P_WAIT** spécifié pour *mode*) est l’état de sortie du nouveau processus . La valeur de retour à partir d’une commande asynchrone **_spawnvp** ou **_wspawnvp** (**_P_NOWAIT** ou **_P_NOWAITO** spécifiée pour  *mode*) est le handle du processus. L'état de sortie est 0 si le processus s'est terminé normalement. Vous pouvez définir l’état de sortie une valeur différente de zéro si le processus engendré utilise spécifiquement un argument différent de zéro pour appeler le **quitter** routine. Si le nouveau processus ne définissait pas explicitement un état de sortie positif, un état de sortie positif indique une sortie anormale avec arrêt ou interruption. Une valeur de retour de -1 indique une erreur (le nouveau processus n’est pas lancé). Dans ce cas, **errno** est définie à une des valeurs suivantes :

|||
|-|-|
**E2BIG**|La liste des arguments dépasse 1024 octets.
**EINVAL**|*mode* argument n’est pas valide.
**ENOENT**|Fichier ou chemin d'accès introuvable.
**ENOEXEC**|Le fichier spécifié n'est pas exécutable ou a un format de fichier exécutable non valide.
**ENOMEM**|Mémoire insuffisante pour exécuter le nouveau processus.

Pour plus d’informations sur ces codes de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chacune de ces fonctions crée un nouveau processus et l’exécute et passe un tableau de pointeurs à des arguments de ligne de commande et utilise le **chemin d’accès** variable d’environnement pour rechercher le fichier à exécuter.

Ces fonctions valident leurs paramètres. Si le paramètre *cmdname* ou *argv* est un pointeur null, ou si *argv* pointe vers un pointeur null ou *argv*[0] est une chaîne vide, non valide Gestionnaire de paramètres est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL**et retournent -1. Aucun nouveau processus généré.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_spawnvp**|\<stdio.h > ou \<process.h >|
|**_wspawnvp**|\<stdio.h> ou \<wchar.h>|

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
