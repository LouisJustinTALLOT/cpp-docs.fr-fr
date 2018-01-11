---
title: exit, _Exit, _exit | Microsoft Docs
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dbb54b756363da2069bbc4bface4e971fcab91e4
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="exit-exit-exit"></a>exit, _Exit, _exit

Termine le processus appelant. La fonction `exit` le termine après nettoyage ; `_exit` et `_Exit` le terminent immédiatement.

> [!NOTE]
> N’utilisez pas cette méthode pour arrêter une application de plateforme Windows universelle (UWP), à l’exception de test ou de scénarios de débogage. Méthodes de programmation ou l’interface utilisateur pour fermer une application de magasin ne sont pas autorisées en fonction de la [des stratégies Microsoft Store](/legal/windows/agreements/store-policies). Pour plus d’informations, consultez [cycle de vie application UWP](/windows/uwp/launch-resume/app-lifecycle). Pour plus d’informations sur les applications Windows 10, consultez [Guides de procédures pour les applications Windows 10](http://go.microsoft.com/fwlink/p/?linkid=619133).

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

_status_  
Code d’état de sortie.

## <a name="remarks"></a>Notes

Les fonctions `exit`, `_Exit` et `_exit` terminent le processus appelant. La fonction `exit` appelle des destructeurs pour les objets locaux de thread, puis appelle, selon un ordre dernier entré premier sorti (LIFO), les fonctions qui sont inscrites par `atexit` et `_onexit`, puis vide toutes les mémoires tampons de fichiers avant de terminer le processus. Les fonctions `_Exit` et `_exit` terminent le processus sans détruire les objets locaux de thread ou sans traiter les fonctions `atexit` ou `_onexit` , et sans vider les mémoires tampons des flux.

Bien que le `exit`, `_Exit` et `_exit` appels ne retournent pas de valeur, la valeur dans _état_ est accessible à l’environnement hôte ou le processus d’appel en attente, s’il en existe, une fois que le processus s’arrête. En règle générale, l’appelant définit le _état_ sur 0 pour indiquer une sortie normale, ou sur une autre valeur pour indiquer une erreur. Le _état_ valeur n’est disponible pour la commande batch du système d’exploitation `ERRORLEVEL` et est représenté par une des deux constantes : `EXIT_SUCCESS`, qui représente la valeur 0, ou `EXIT_FAILURE`, qui représente la valeur 1.

Les fonctions `exit`, `_Exit`, `_exit`, `quick_exit`, `_cexit`et `_c_exit` se comportent comme suit.

|Fonction|Description|
|--------------|-----------------|
|`exit`|Exécute les procédures d’arrêt complètes de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|`_Exit`|Exécute les procédures d’arrêt minimales de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|`_exit`|Exécute les procédures d’arrêt minimales de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|`quick_exit`|Exécute les procédures d’arrêt rapides de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|`_cexit`|Exécute les procédures d’arrêt complètes de la bibliothèque C et retourne à l’appelant. Ne termine pas le processus.|
|`_c_exit`|Exécute les procédures d’arrêt minimales de la bibliothèque C et retourne à l’appelant. Ne termine pas le processus.|

Quand vous appelez la fonction `exit`,  `_Exit` ou `_exit` , les destructeurs pour les objets temporaires ou automatiques qui existent au moment de l’appel ne sont pas appelés. Un objet automatique est un objet local non statique défini dans une fonction. Un objet temporaire est un objet qui est créé par le compilateur, telles qu’une valeur retournée par un appel de fonction. Pour détruire un objet automatique avant d’appeler `exit`, `_Exit`, ou `_exit`explicitement appelle le destructeur pour l’objet, comme indiqué ici :

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

N’utilisez pas `DLL_PROCESS_ATTACH` pour appeler `exit` depuis `DllMain`. Pour quitter le `DLLMain` de fonction, retour `FALSE` de `DLL_PROCESS_ATTACH`.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|`exit`, `_Exit`, `_exit`|\<process.h> ou \<stdlib.h>|

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

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)  
[abort](../../c-runtime-library/reference/abort.md)  
[atexit](../../c-runtime-library/reference/atexit.md)  
[_cexit, _c_exit](../../c-runtime-library/reference/cexit-c-exit.md)  
[_exec, _wexec, fonctions](../../c-runtime-library/exec-wexec-functions.md)  
[_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)  
[quick_exit](../../c-runtime-library/reference/quick-exit1.md)  
[_spawn, _wspawn, fonctions](../../c-runtime-library/spawn-wspawn-functions.md)  
[system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)  
