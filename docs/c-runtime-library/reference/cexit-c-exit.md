---
title: _cexit, _c_exit
ms.date: 11/04/2016
apiname:
- _c_exit
- _cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
ms.openlocfilehash: a075e8a8e965a195765b86ffa21fed0915dbf5ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335488"
---
# <a name="cexit-cexit"></a>_cexit, _c_exit

Effectue des opérations de nettoyage et retourne le contrôle sans mettre fin au processus.

## <a name="syntax"></a>Syntaxe

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Notes

Le **_cexit** appels de fonctions, dans le dernier entré, premier sorti (LIFO) ordre, les fonctions inscrites par **atexit** et **_onexit**. Puis **_cexit** vide toutes les mémoires tampons d’e/s et ferme tous les flux ouverts avant de retourner. **_c_exit** est identique à **_exit** mais retourne au processus appelant sans traitement **atexit** ou **_onexit** ou vider les mémoires tampons de flux de données. Le comportement de **quitter**, **_exit**, **_cexit**, et **_c_exit** est indiqué dans le tableau suivant.

|Fonction|Comportement|
|--------------|--------------|
|**exit**|Exécute les procédures d’arrêt complètes de la bibliothèque C, termine le processus et quitte avec le code d’état fourni.|
|**_exit**|Exécute les procédures d’arrêt rapides de la bibliothèque C, termine le processus et quitte avec le code d’état fourni.|
|**_cexit**|Exécute les procédures d’arrêt complètes de la bibliothèque C et retourne à l’appelant, mais ne termine pas le processus.|
|**_c_exit**|Exécute les procédures d’arrêt rapides de la bibliothèque C et retourne à l’appelant, mais ne termine pas le processus.|

Lorsque vous appelez le **_cexit** ou **_c_exit** fonctions, les destructeurs pour les objets temporaires ou automatiques qui existent au moment de l’appel ne sont pas appelées. Un objet automatique est un objet défini dans une fonction où l’objet n’est pas déclaré comme statique. Un objet temporaire est un objet créé par le compilateur. Pour détruire un objet automatique avant d’appeler **_cexit** ou **_c_exit**, explicitement appelle le destructeur pour l’objet, comme suit :

```cpp
myObject.myClass::~myClass( );
```

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec, fonctions](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
