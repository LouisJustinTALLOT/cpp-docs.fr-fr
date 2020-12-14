---
description: 'En savoir plus sur : quitter, _Exit, _exit'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b2d5a95f8a110e467016be828418050d77caa984
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236033"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

Termine le processus appelant. La fonction **Exit** se termine après le nettoyage ; **_exit** et **_Exit** l’arrêter immédiatement.

> [!NOTE]
> N’utilisez pas cette méthode pour arrêter une application plateforme Windows universelle (UWP), sauf dans les scénarios de test ou de débogage. Les méthodes de programmation ou d’interface utilisateur pour fermer une application du Windows Store ne sont pas autorisées selon les [stratégies de Microsoft Store](/legal/windows/agreements/store-policies). Pour plus d’informations, consultez la page relative au [cycle de vie des applications UWP](/windows/uwp/launch-resume/app-lifecycle). Pour plus d’informations sur les applications Windows 10, consultez [Guides de procédures pour les applications Windows 10](https://developer.microsoft.com/windows/apps).

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

Les fonctions **Exit**, **_Exit** et **_exit** terminent le processus appelant. La fonction **Exit** appelle des destructeurs pour les objets locaux de thread, puis appelle, dans l’ordre LIFO (dernier entré, premier sorti), les fonctions inscrites par **atexit** et **_onexit**, puis vide toutes les mémoires tampons de fichiers avant de mettre fin au processus. Les fonctions **_Exit** et **_exit** terminent le processus sans détruire les objets locaux de thread ou traiter des fonctions **atexit** ou **_onexit** , et sans vider les mémoires tampons de flux.

Bien que les appels **Exit**, **_Exit** et **_exit** ne retournent pas de valeur, la valeur de *Status* est mise à la disposition de l’environnement hôte ou du processus appelant en attente, le cas échéant, une fois le processus terminé. En règle générale, l’appelant définit la valeur d' *État* sur 0 pour indiquer une sortie normale, ou sur une autre valeur pour indiquer une erreur. La valeur d' *État* est disponible pour la commande de traitement par lots du système d’exploitation **ERRORLEVEL** et est représentée par l’une des deux constantes suivantes : **EXIT_SUCCESS**, qui représente la valeur 0, ou **EXIT_FAILURE**, qui représente la valeur 1.

Les fonctions **Exit**, **_Exit**, **_exit**, **quick_exit**, **_cexit** et **_c_exit** se comportent comme suit.

|Fonction|Description|
|--------------|-----------------|
|**exit**|Exécute les procédures d’arrêt complètes de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|**_Exit**|Exécute les procédures d’arrêt minimales de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|**_exit**|Exécute les procédures d’arrêt minimales de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|**quick_exit**|Exécute les procédures d’arrêt rapides de la bibliothèque C, termine le processus et indique le code d’état fourni à l’environnement hôte.|
|**_cexit**|Exécute les procédures d’arrêt complètes de la bibliothèque C et retourne à l’appelant. Ne termine pas le processus.|
|**_c_exit**|Exécute les procédures d’arrêt minimales de la bibliothèque C et retourne à l’appelant. Ne termine pas le processus.|

Quand vous appelez la fonction **Exit**,  **_Exit** ou **_exit** , les destructeurs pour les objets temporaires ou automatiques qui existent au moment de l’appel ne sont pas appelés. Un objet automatique est un objet local non statique défini dans une fonction. Un objet temporaire est un objet créé par le compilateur, tel qu’une valeur retournée par un appel de fonction. Pour détruire un objet automatique avant d’appeler **Exit**, **_Exit** ou **_exit**, appelez explicitement le destructeur de l’objet, comme illustré ici :

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

N’utilisez pas **DLL_PROCESS_ATTACH** pour appeler **Exit** à partir de **DllMain**. Pour quitter la fonction **DllMain** , retournez la **valeur false** à partir de **DLL_PROCESS_ATTACH**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**Exit**, **_Exit**, **_exit**|\<process.h> ou \<stdlib.h>|

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
[_exec, _wexec fonctions](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, _wspawn fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
