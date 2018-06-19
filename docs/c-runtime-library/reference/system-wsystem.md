---
title: system, _wsystem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- system
- _wsystem
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tsystem
- _wsystem
dev_langs:
- C++
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca44648ed378d4484b8e4c32a38a6780b3eddd53
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414700"
---
# <a name="system-wsystem"></a>system, _wsystem

Exécute une commande.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int system(
   const char *command
);
int _wsystem(
   const wchar_t *command
);
```

### <a name="parameters"></a>Paramètres

*command*<br/>
Commande à exécuter.

## <a name="return-value"></a>Valeur de retour

Si *commande* est **NULL** et l’interpréteur de commandes est trouvée, retourne une valeur différente de zéro. Si l’interpréteur de commandes est introuvable, retourne 0 et définit **errno** à **ENOENT**. Si *commande* n’est pas **NULL**, **système** retourne la valeur retournée par l’interpréteur de commandes. Elle retourne la valeur 0 uniquement si l'interpréteur de commande retourne la valeur 0. Une valeur de retour de - 1 indique une erreur et **errno** est définie à une des valeurs suivantes :

|||
|-|-|
**E2BIG**|La liste d’arguments (qui est dépendante du système) est trop grande.
**ENOENT**|L'interpréteur de commande est introuvable.
**ENOEXEC**|Le fichier interpréteur de commande ne peut pas être exécuté, car le format n'est pas valide.
**ENOMEM**|Mémoire insuffisante pour exécuter la commande ; la mémoire disponible est endommagée ; ou il existe un bloc non valide, ce qui indique que le processus qui effectue l'appel n'a pas été alloué correctement.

Pour plus d’informations sur ces codes de retour, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **système** fonction passe *commande* à l’interpréteur de commande qui exécute la chaîne comme une commande du système d’exploitation. **système** utilise le **COMSPEC** et **chemin d’accès** variables d’environnement pour localiser l’interpréteur de commandes CMD.exe de fichiers. Si *commande* est **NULL**, la fonction vérifie uniquement l’existence de l’interpréteur de commandes.

Vous devez explicitement vider, à l’aide de [fflush](fflush.md) ou [_flushall](flushall.md), ou fermer tout flux avant d’appeler **système**.

**_wsystem** est une version à caractères larges de **système**; le *commande* argument **_wsystem** est une chaîne à caractères larges. Ces fonctions se comportent sinon de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**system**|**system**|**_wsystem**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**system**|\<process.h> ou \<stdlib.h>|
|**_wsystem**|\<process.h> ou \<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Cet exemple utilise **système** vers le TYPE d’un fichier texte.

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crtsystemtxt"></a>Entrée : crt_system.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Sortie

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec, fonctions](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn, _wspawn, fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
