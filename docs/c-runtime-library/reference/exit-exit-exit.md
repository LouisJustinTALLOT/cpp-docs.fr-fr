---
title: exit, _Exit, _exit
ms.date: 4/2/2020
api_name:
- _exit
- exit
- _o__exit
- _o_exit
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
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
ms.openlocfilehash: 5bdb5ff5c8309e03a49f9518f65a45d5757e9bfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347636"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

Termine le processus appelant. La fonction **de sortie** le met fin après le nettoyage; **_exit** et **_Exit** y mettre fin immédiatement.

> [!NOTE]
> N’utilisez pas cette méthode pour arrêter une application Universal Windows Platform (UWP), sauf dans les scénarios de test ou de débogage. Les moyens programmatiques ou d’interface utilisateur de fermer une application Store ne sont pas autorisés selon les politiques du [Microsoft Store](/legal/windows/agreements/store-policies). Pour plus d’informations, voir [le cycle de vie de l’application UWP](/windows/uwp/launch-resume/app-lifecycle). Pour plus d’informations sur les applications Windows 10, consultez [Guides de procédures pour les applications Windows 10](https://developer.microsoft.com/windows/apps).

## <a name="syntax"></a>Syntaxe

```C
void exit(
   int const status
);
void _Exit(
   int const status
);
void _exit(
   int const status
);
```

### <a name="parameters"></a>Paramètres

*statut*<br/>
Code d’état de sortie.

## <a name="remarks"></a>Notes

La **sortie,** **_Exit** et les fonctions **_exit** mettre fin au processus d’appel. La fonction **de sortie** appelle destructeurs pour les objets thread-local, puis appelle- dans le dernier-en-premier-out (LIFO) ordre -les fonctions qui sont enregistrées par **atexit** et **_onexit,** puis chasse tous les tampons de fichier avant qu’il ne termine le processus. Les fonctions **_Exit** et **_exit** terminent le processus sans détruire les objets de thread-local ou le traitement des fonctions **d’exposition** ou **de _onexit,** et sans tampons de flux de rinçage.

Bien que la **sortie,** **_Exit** et **_exit** appels ne retournent pas une valeur, la valeur dans le *statut* est mise à la disposition de l’environnement hôte ou du processus d’appel d’attente, si l’on existe, après la sortie du processus. En règle générale, l’appelant définit la valeur *de statut* à 0 pour indiquer une sortie normale, ou à une autre valeur pour indiquer une erreur. La valeur *d’état* est disponible pour la commande de lot de système d’exploitation **ERRORLEVEL** et est représentée par l’une des deux constantes : **EXIT_SUCCESS**, qui représente une valeur de 0, ou **EXIT_FAILURE**, ce qui représente une valeur de 1.

La **sortie**, **_Exit**, **_exit**, **quick_exit**, **_cexit**, et les fonctions **_c_exit** se comportent comme suit.

|Fonction|Description|
|--------------|-----------------|
|**Sortie**|Exécute les procédures d’arrêt complètes de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|**_Exit**|Exécute les procédures d’arrêt minimales de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|**_exit**|Exécute les procédures d’arrêt minimales de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|**quick_exit**|Exécute les procédures d’arrêt rapides de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|**_cexit**|Exécute les procédures d’arrêt complètes de la bibliothèque C et retourne à l’appelant. Ne termine pas le processus.|
|**_c_exit**|Exécute les procédures d’arrêt minimales de la bibliothèque C et retourne à l’appelant. Ne termine pas le processus.|

Lorsque vous appelez la **sortie,** **_Exit** ou **_exit** fonction, les destructeurs pour tout objet temporaire ou automatique qui existent au moment de l’appel ne sont pas appelés. Un objet automatique est un objet local non statique défini dans une fonction. Un objet temporaire est un objet qui est créé par le compilateur, comme une valeur retournée par un appel de fonction. Pour détruire un objet automatique avant d’appeler **la sortie,** **_Exit**, ou **_exit**, appelez explicitement le destructeur de l’objet, comme indiqué ici:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

N’utilisez pas **DLL_PROCESS_ATTACH** pour appeler **la sortie** de **DllMain**. Pour quitter la fonction **DLLMain,** retournez **FALSE** de **DLL_PROCESS_ATTACH**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**sortie**, **_Exit**, **_exit**|\<process.h> ou \<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_exit.c
// This program returns an exit code of 1. The
// error code could be tested in a batch file.

#include <stdlib.h>

int main( void )
{
   exit( 1 );
}
```

## <a name="see-also"></a>Voir aussi

[Contrôle des processus et de l’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, fonctions _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, fonctions _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
