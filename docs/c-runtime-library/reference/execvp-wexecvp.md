---
title: _execvp, _wexecvp
ms.date: 11/04/2016
api_name:
- _execvp
- _wexecvp
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
- _execvp
- wexecvp
- _wexecvp
helpviewer_keywords:
- _execvp function
- _wexecvp function
- wexecvp function
- execvp function
ms.assetid: a4db15df-b204-4987-be7c-de84c3414380
ms.openlocfilehash: 60de62a61c78152cd4a2d8053da41a37a4091424
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941786"
---
# <a name="_execvp-_wexecvp"></a>_execvp, _wexecvp

Charge et exécute les nouveaux processus enfant.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _execvp(
   const char *cmdname,
   const char *const *argv
);
intptr_t _wexecvp(
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>Paramètres

*cmdname*<br/>
Chemin d’accès du fichier à exécuter.

*argv*<br/>
Tableau de pointeurs vers les paramètres.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, ces fonctions ne retournent pas au processus appelant. Une valeur de retour de-1 indique une erreur, auquel cas la variable globale **errno** est définie.

|valeur **errno**|Description|
|-------------------|-----------------|
|**E2BIG**|L’espace requis pour les arguments et les paramètres d’environnement dépasse 32 Ko.|
|**EACCES**|Le fichier spécifié possède un verrou ou une violation de partage.|
|**EINVAL**|Paramètre non valide.|
|**EMFILE**|Trop de fichiers ouverts (le fichier spécifié doit être ouvert pour déterminer s'il est exécutable).|
|**ENOENT**|Fichier ou chemin d’accès introuvable.|
|**ENOEXEC**|Le fichier spécifié n'est pas exécutable ou a un format de fichier exécutable non valide.|
|**ENOMEM**|Mémoire insuffisante pour exécuter le nouveau processus ; la mémoire disponible est endommagée ; ou il existe un bloc non valide, indiquant que le processus appelant n'a pas été alloué correctement.|

Pour plus d'informations sur ces codes de retour et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chacune de ces fonctions charge et exécute un nouveau processus, passant un tableau de pointeurs à des arguments de ligne de commande et utilisant la variable **d’environnement PATH** pour rechercher le fichier à exécuter.

Les fonctions **_execvp** valident leurs paramètres. Si le *CmdName* est un pointeur null, si *argv* est un pointeur null, un pointeur vers un tableau vide ou si le tableau contient une chaîne vide comme premier argument, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre. ](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** sur **EINVAL** et retournent-1. Aucun processus lancé.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|En-tête facultatif|
|--------------|---------------------|---------------------|
|**_execvp**|\<process.h>|\<errno.h>|
|**_wexecvp**|\<process.h> ou \<wchar.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

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
