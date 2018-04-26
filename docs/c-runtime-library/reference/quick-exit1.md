---
title: quick_exit1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- quick_exit
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
- quick_exit
- process/quick_exit
- stdlib/quick_exit
dev_langs:
- C++
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fde06fc83b27b8bba43e3fa929cc8b97bb68dd06
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="quickexit"></a>quick_exit

Provoque l’arrêt normal du programme.

## <a name="syntax"></a>Syntaxe

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>Paramètres

*status*<br/>
Code d’état à retourner à l’environnement hôte.

## <a name="return-value"></a>Valeur de retour

Le **quick_exit** fonction ne peut pas retourner à son appelant.

## <a name="remarks"></a>Notes

Le **quick_exit** fonction provoque l’arrêt normal du programme. Il n’appelle aucune fonction inscrite par **atexit**, **_onexit** ou manipulateurs de signaux inscrits par le **signal** (fonction). Comportement n’est pas défini si **quick_exit** est appelée plusieurs fois ou si le **quitter** fonction est également appelée.

Le **quick_exit** dans le dernier entré, premier sorti (LIFO) commande, les fonctions inscrites par les appels de fonction **at_quick_exit**, sauf pour les fonctions déjà appelées lorsque la fonction a été inscrit.  Le comportement n’est pas défini si un appel [longjmp](longjmp.md) est effectué pendant un appel à une fonction inscrite qui terminerait l’appel à la fonction.

Une fois que les fonctions inscrites ont été appelées, **quick_exit** appelle **_Exit** à l’aide de la *état* valeur pour retourner le contrôle à l’environnement hôte.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**quick_exit**|\<process.h> ou \<stdlib.h>|

Pour plus d'informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec, fonctions](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn, fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
