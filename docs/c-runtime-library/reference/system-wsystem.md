---
title: system, _wsystem
ms.date: 4/2/2020
api_name:
- system
- _wsystem
- _o__wsystem
- _o_system
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tsystem
- _wsystem
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
ms.openlocfilehash: 21ce04d30da80a40a1162dce06ff378150008766
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362792"
---
# <a name="system-_wsystem"></a>system, _wsystem

Exécute une commande.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Commande*<br/>
Commande à exécuter.

## <a name="return-value"></a>Valeur de retour

Si *la commande* est **NULL** et que l’interprète de commande est trouvé, renvoie une valeur non zéro. Si l’interprète de commande n’est pas trouvé, retourne 0 et définit **errno** à **ENOENT**. Si *la commande n’est* pas **NULL**, le **système** renvoie la valeur qui est retournée par l’interprète de commande. Elle retourne la valeur 0 uniquement si l'interpréteur de commande retourne la valeur 0. Une valeur de rendement de - 1 indique une erreur, et **errno** est réglé à l’une des valeurs suivantes:

|||
|-|-|
| **E2BIG** | La liste d’arguments (qui est dépendante du système) est trop grande. |
| **ENOENT (ENOENT)** | L'interpréteur de commande est introuvable. |
| **ENOEXEC** | Le fichier interpréteur de commande ne peut pas être exécuté, car le format n'est pas valide. |
| **ENOMEM (ENOMEM)** | Mémoire insuffisante pour exécuter la commande ; la mémoire disponible est endommagée ; ou il existe un bloc non valide, ce qui indique que le processus qui effectue l'appel n'a pas été alloué correctement. |

Pour plus d’informations sur ces codes de retour, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **système** passe *la commande* à l’interprète de commande, qui exécute la chaîne comme une commande de système d’exploitation. **utilise** les variables de l’environnement **COMSPEC** et **PATH** pour localiser le fichier de commande-interprète CMD.exe. Si *la commande* est **NULL**, la fonction vérifie simplement si l’interprète de commande existe.

Vous devez explicitement rincer, en utilisant [fflush](fflush.md) ou [_flushall](flushall.md), ou fermer n’importe quel flux avant d’appeler **le système**.

**_wsystem** est une version à caractère large du **système**; l’argument *de commande* pour **_wsystem** est une corde de caractère large. Ces fonctions se comportent sinon de façon identique.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**système**|**système**|**_wsystem**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**système**|\<process.h> ou \<stdlib.h>|
|**_wsystem**|\<process.h> ou \<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Cet exemple utilise **le système** pour TYPE un fichier texte.

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crt_systemtxt"></a>Entrée : crt_system.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Voir aussi

[Contrôle des processus et de l’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, fonctions _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn, fonctions _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
