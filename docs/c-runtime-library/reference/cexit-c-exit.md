---
title: _cexit, _c_exit
ms.date: 4/2/2020
api_name:
- _c_exit
- _cexit
- _o__cexit
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
ms.openlocfilehash: 78675ef91c2ab68e18f6111b4908886017ae1f79
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917148"
---
# <a name="_cexit-_c_exit"></a>_cexit, _c_exit

Effectue des opérations de nettoyage et retourne le contrôle sans mettre fin au processus.

## <a name="syntax"></a>Syntaxe

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Notes 

La fonction **_cexit** appelle, dans l’ordre LIFO (dernier entré, premier sorti), les fonctions inscrites par **atexit** et **_onexit**. Ensuite **_cexit** vide toutes les mémoires tampons d’e/s et ferme tous les flux ouverts avant de retourner. **_c_exit** est identique à **_exit** mais retourne au processus appelant sans traitement de **atexit** ou **_onexit** ou en vidant des tampons de flux. Le tableau suivant indique le comportement de **Exit**, **_exit**, **_cexit**et **_c_exit** .

|Function|Comportement|
|--------------|--------------|
|**exit**|Exécute les procédures d’arrêt complètes de la bibliothèque C, termine le processus et quitte avec le code d’état fourni.|
|**_exit**|Exécute les procédures d’arrêt rapides de la bibliothèque C, termine le processus et quitte avec le code d’état fourni.|
|**_cexit**|Exécute les procédures d’arrêt complètes de la bibliothèque C et retourne à l’appelant, mais ne termine pas le processus.|
|**_c_exit**|Exécute les procédures d’arrêt rapides de la bibliothèque C et retourne à l’appelant, mais ne termine pas le processus.|

Quand vous appelez les fonctions **_cexit** ou **_c_exit** , les destructeurs pour les objets temporaires ou automatiques qui existent au moment de l’appel ne sont pas appelés. Un objet automatique est un objet défini dans une fonction où l’objet n’est pas déclaré comme statique. Un objet temporaire est un objet créé par le compilateur. Pour détruire un objet automatique avant d’appeler **_cexit** ou **_c_exit**, appelez explicitement le destructeur de l’objet, comme suit :

```cpp
myObject.myClass::~myClass( );
```

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec fonctions](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
