---
title: quick_exit1
ms.date: 11/04/2016
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
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 50f1ee72cce04c2bebc8f7396a2b6fad98301dd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358032"
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

Le **quick_exit** fonction provoque l’arrêt normal du programme. Il n’appelle aucune fonction inscrite par **atexit**, **_onexit** ou manipulateurs de signaux inscrits par le **signal** (fonction). Comportement est indéfini si **quick_exit** est appelée plusieurs fois ou si le **quitter** fonction est également appelée.

Le **quick_exit** appels de fonctions, dans le dernier entré, premier sorti (LIFO) ordre, les fonctions inscrites par **at_quick_exit**, sauf pour les fonctions déjà appelées lorsque la fonction a été enregistrée.  Le comportement n’est pas défini si un appel à [longjmp](longjmp.md) est effectué pendant un appel à une fonction inscrite qui terminerait l’appel à la fonction.

Une fois que les fonctions inscrites ont été appelées, **quick_exit** appelle **_Exit** à l’aide de la *état* valeur pour retourner le contrôle à l’environnement hôte.

## <a name="requirements"></a>Configuration requise

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
