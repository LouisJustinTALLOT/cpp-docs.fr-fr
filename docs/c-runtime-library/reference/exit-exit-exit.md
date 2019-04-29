---
title: exit, _Exit, _exit
ms.date: 1/02/2018
apiname:
- _exit
- exit
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
ms.openlocfilehash: 7b2a22649d779f382bb4055b1e44c14312627ccd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339349"
---
# <a name="exit-exit-exit"></a>exit, _Exit, _exit

Termine le processus appelant. Le **quitter** fonction termine après nettoyage ; **_exit** et **_Exit** terminent immédiatement.

> [!NOTE]
> N’utilisez pas cette méthode pour arrêter une application Universal Windows Platform (UWP), à l’exception de test ou de scénarios de débogage. Méthodes de programmation ou l’interface utilisateur pour fermer une application de Store ne sont pas autorisées en fonction de la [les stratégies de Microsoft Store](/legal/windows/agreements/store-policies). Pour plus d’informations, consultez [cycle de vie application UWP](/windows/uwp/launch-resume/app-lifecycle). Pour plus d’informations sur les applications Windows 10, consultez [Guides de procédures pour les applications Windows 10](https://developer.microsoft.com/windows/apps).

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

*status*<br/>
Code d’état de sortie.

## <a name="remarks"></a>Notes

Le **quitter**, **_Exit** et **_exit** fonctions terminent le processus appelant. Le **quitter** fonction appelle des destructeurs pour les objets locaux de thread, puis appelle, par ordre dernier-in-first-out (LIFO), les fonctions qui sont inscrits par **atexit** et **_onexit**, puis vide toutes les mémoires tampons de fichiers avant de terminer le processus. Le **_Exit** et **_exit** fonctions mettre fin au processus sans détruire les objets locaux de thread ou traitement **atexit** ou **_onexit**fonctions et sans vider les mémoires tampons de flux de données.

Bien que le **quitter**, **_Exit** et **_exit** appels ne retournent pas de valeur, la valeur dans *état* est mis à disposition à l’environnement hôte ou en attente de processus appelant, s’il en existe, une fois que le processus se termine. En règle générale, l’appelant affecte la *état* valeur sur 0 pour indiquer une sortie normale, ou à une autre valeur pour indiquer une erreur. Le *état* valeur n’est disponible pour la commande batch du système d’exploitation **ERRORLEVEL** et est représenté par une des deux constantes : **EXIT_SUCCESS**, qui représente une valeur égale à 0, ou **EXIT_FAILURE**, qui représente une valeur de 1.

Le **quitter**, **_Exit**, **_exit**, **quick_exit**, **_cexit**, et **_c_exit** fonctions se comportent comme suit.

|Fonction|Description|
|--------------|-----------------|
|**exit**|Exécute les procédures d’arrêt complètes de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|**_Exit**|Exécute les procédures d’arrêt minimales de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|**_exit**|Exécute les procédures d’arrêt minimales de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|**quick_exit**|Exécute les procédures d’arrêt rapides de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|**_cexit**|Exécute les procédures d’arrêt complètes de la bibliothèque C et retourne à l’appelant. Ne termine pas le processus.|
|**_c_exit**|Exécute les procédures d’arrêt minimales de la bibliothèque C et retourne à l’appelant. Ne termine pas le processus.|

Lorsque vous appelez le **quitter**, **_Exit** ou **_exit** (fonction), les destructeurs pour les objets temporaires ou automatiques qui existent au moment de l’appel ne sont pas appelés. Un objet automatique est un objet local non statique défini dans une fonction. Un objet temporaire est un objet qui est créé par le compilateur, tel qu’une valeur retournée par un appel de fonction. Pour détruire un objet automatique avant d’appeler **quitter**, **_Exit**, ou **_exit**, explicitement appelle le destructeur pour l’objet, comme illustré ici :

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

N’utilisez pas **DLL_PROCESS_ATTACH** pour appeler **quitter** de **DllMain**. Pour quitter le **DLLMain** de fonction, retour **FALSE** de **DLL_PROCESS_ATTACH**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**exit**, **_Exit**, **_exit**|\<process.h> ou \<stdlib.h>|

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

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit, _c_exit](cexit-c-exit.md)<br/>
[_exec, _wexec, fonctions](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, _wspawn, fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
