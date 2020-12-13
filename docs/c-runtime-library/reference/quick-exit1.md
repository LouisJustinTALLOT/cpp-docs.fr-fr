---
description: 'En savoir plus sur : quick_exit'
title: quick_exit1
ms.date: 11/04/2016
api_name:
- quick_exit
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- quick_exit
- process/quick_exit
- stdlib/quick_exit
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 85640af902092d5cc60a1c718dfd8999c41406b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137096"
---
# <a name="quick_exit"></a>quick_exit

Provoque l’arrêt normal du programme.

## <a name="syntax"></a>Syntaxe

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>Paramètres

*statut*<br/>
Code d’état à retourner à l’environnement hôte.

## <a name="return-value"></a>Valeur renvoyée

La fonction **quick_exit** ne peut pas retourner à son appelant.

## <a name="remarks"></a>Notes

La fonction **quick_exit** provoque l’arrêt normal du programme. Elle n’appelle aucune fonction inscrite par **atexit**, **_onexit** ou des gestionnaires de signal enregistrés par la fonction **signal** . Le comportement n’est pas défini si **quick_exit** est appelé plusieurs fois, ou si la fonction **Exit** est également appelée.

La fonction **quick_exit** appelle, dans l’ordre LIFO (dernier entré, premier sorti), les fonctions inscrites par **at_quick_exit**, à l’exception des fonctions déjà appelées lorsque la fonction a été inscrite.  Le comportement n’est pas défini si un appel à [longjmp](longjmp.md) est effectué pendant un appel à une fonction inscrite qui terminerait l’appel à la fonction.

Une fois que les fonctions inscrites ont été appelées, **quick_exit** appelle **_Exit** à l’aide de la valeur d' *État* pour retourner le contrôle à l’environnement hôte.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**quick_exit**|\<process.h> ou \<stdlib.h>|

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
