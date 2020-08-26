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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 15e4637d709fdf4600ecb4c66c7d4a75c4fa07eb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844975"
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

*command*<br/>
Commande à exécuter.

## <a name="return-value"></a>Valeur renvoyée

Si la *commande* a la valeur **null** et que l’interpréteur de commande est trouvé, retourne une valeur différente de zéro. Si l’interpréteur de commande est introuvable, retourne 0 et définit **errno** sur **ENOENT**. Si la *commande* n’est pas **null**, **System** retourne la valeur retournée par l’interpréteur de commande. Elle retourne la valeur 0 uniquement si l'interpréteur de commande retourne la valeur 0. Une valeur de retour de-1 indique une erreur et **errno** est défini sur l’une des valeurs suivantes :

| Valeur | Description |
|-|-|
| **E2BIG** | La liste d’arguments (qui est dépendante du système) est trop grande. |
| **ENOENT** | L'interpréteur de commande est introuvable. |
| **ENOEXEC** | Le fichier interpréteur de commande ne peut pas être exécuté, car le format n'est pas valide. |
| **ENOMEM** | Mémoire insuffisante pour exécuter la commande ; la mémoire disponible est endommagée ; ou il existe un bloc non valide, ce qui indique que le processus qui effectue l'appel n'a pas été alloué correctement. |

Pour plus d’informations sur ces codes de retour, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **système** passe la *commande* à l’interpréteur de commande, qui exécute la chaîne en tant que commande du système d’exploitation. le **système** utilise les variables d’environnement **COMSPEC** et **path** pour localiser le fichier de l’interpréteur de commandes CMD.exe. Si la *commande* a la **valeur null**, la fonction vérifie simplement si l’interpréteur de commandes existe.

Vous devez explicitement vider, en utilisant [fflush](fflush.md) ou [_flushall](flushall.md), ou fermer un flux avant d’appeler **System**.

**_wsystem** est une version à caractères larges du **système**. l’argument de *commande* pour **_wsystem** est une chaîne de caractères larges. Ces fonctions se comportent sinon de façon identique.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**système**|**système**|**_wsystem**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**système**|\<process.h> ou \<stdlib.h>|
|**_wsystem**|\<process.h> ou \<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Cet exemple utilise le **système** pour taper un fichier texte.

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

### <a name="output"></a>Sortie

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec fonctions](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn, _wspawn fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
