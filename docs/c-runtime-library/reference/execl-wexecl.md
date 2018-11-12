---
title: _execl, _wexecl
ms.date: 11/04/2016
apiname:
- _execl
- _wexecl
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
- _execl
- _wexecl
- wexecl
helpviewer_keywords:
- _execl function
- wexecl function
- _wexecl function
- execl function
ms.assetid: 81fefb8a-0a06-4221-b2bc-be18e38e89f4
ms.openlocfilehash: 3d736849f90782425e6e1c1cff04536972318c91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530306"
---
# <a name="execl-wexecl"></a>_execl, _wexecl

Charge et exécute les nouveaux processus enfant.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _execl(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL
);
intptr_t _wexecl(
   const wchar_t *cmdname,
   const wchar_t *arg0,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>Paramètres

*CmdName*<br/>
Chemin d'accès du fichier à exécuter.

*arg0*,... *argn*<br/>
Liste des pointeurs désignant les paramètres.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, ces fonctions ne retournent pas au processus appelant. Une valeur de retour de -1 indique une erreur, auquel cas la **errno** variable globale est définie.

|Valeur de la variable errno|Description|
|-----------------|-----------------|
|**E2BIG**|L’espace requis pour les arguments et les paramètres d’environnement dépasse 32 Ko.|
|**EACCES**|Le fichier spécifié possède un verrou ou une violation de partage.|
|**EINVAL**|Paramètre non valide (un ou plusieurs des paramètres étaient un pointeur null ou une chaîne vide).|
|**EMFILE**|Trop de fichiers ouverts (le fichier spécifié doit être ouvert pour déterminer s'il est exécutable).|
|**ENOENT**|Fichier ou chemin d’accès introuvable.|
|**ENOEXEC**|Le fichier spécifié n'est pas exécutable ou a un format de fichier exécutable non valide.|
|**ENOMEM**|Mémoire insuffisante pour exécuter le nouveau processus ; la mémoire disponible est endommagée ; ou il existe un bloc non valide, indiquant que le processus appelant n'a pas été alloué correctement.|

## <a name="remarks"></a>Notes

Chacune de ces fonctions charge et exécute un nouveau processus, passant chaque argument de ligne de commande en tant que paramètre distinct. Le premier argument est la commande ou le nom du fichier exécutable, tandis que le deuxième argument doit être le même que le premier. Il devient `argv[0]` dans le processus exécuté. Le troisième argument est le premier argument, `argv[1]`, du processus en cours d’exécution.

Le **_execl** fonctions valident leurs paramètres. Si *cmdname* ou *arg0* est un pointeur null ou une chaîne vide, ces fonctions appellent le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md) si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retournent -1. Aucun nouveau processus n'est exécuté.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|En-tête facultatif|
|--------------|---------------------|---------------------|
|**_execl**|\<process.h>|\<errno.h>|
|**_wexecl**|\<process.h> ou \<wchar.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple dans [_exec, _wexec, fonctions](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec, fonctions](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
