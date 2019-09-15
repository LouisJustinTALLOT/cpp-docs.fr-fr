---
title: _CrtMemDifference
ms.date: 11/04/2016
api_name:
- _CrtMemDifference
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtMemDifference
- CrtMemDifference
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
ms.openlocfilehash: 51bfa014d54f55843fcb112f318f143774abf8f3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938707"
---
# <a name="_crtmemdifference"></a>_CrtMemDifference

Compare deux états de la mémoire et retourne leurs différences (version Debug uniquement).

## <a name="syntax"></a>Syntaxe

```C
int _CrtMemDifference(
   _CrtMemState *stateDiff,
   const _CrtMemState *oldState,
   const _CrtMemState *newState
);
```

### <a name="parameters"></a>Paramètres

*stateDiff*<br/>
Pointeur vers une structure _ **crtmemstate** utilisée pour stocker les différences entre les deux États de la mémoire (retourné).

*oldState*<br/>
Pointeur vers un état antérieur de la mémoire (structure _**crtmemstate** ).

*newState*<br/>
Pointeur vers un état de mémoire ultérieur (structure _**crtmemstate** ).

## <a name="return-value"></a>Valeur de retour

Si les États de la mémoire sont très différents, **_CrtMemDifference** retourne la valeur true. Dans le cas contraire, la fonction retourne FALSE.

## <a name="remarks"></a>Notes

La fonction **_CrtMemDifference** compare *OldState* et *NewState* et stocke leurs différences dans *stateDiff*, qui peuvent ensuite être utilisées par l’application pour détecter les fuites de mémoire et autres problèmes de mémoire. Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtMemDifference** sont supprimés lors du prétraitement.

*NewState* et *OldState* doivent tous être un pointeur valide vers une structure _ **crtmemstate** , définie dans CRTDBG. h, qui a été rempli par [_CrtMemCheckpoint](crtmemcheckpoint.md) avant l’appel de **_CrtMemDifference**. *stateDiff* doit être un pointeur vers une instance précédemment allouée de la structure _ **crtmemstate** . Si *stateDiff*, *NewState*ou *OldState* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ont la valeur **EINVAL** et la fonction retourne false.

**_CrtMemDifference** compare les valeurs de champ _ **crtmemstate** des blocs de *OldState* à celles de *NewState* et stocke le résultat dans *stateDiff*. Quand le nombre de types de bloc alloués ou le nombre total de blocs alloués pour chaque type diffère entre les deux états de la mémoire, ces états sont considérés comme très différents. La différence entre la plus grande quantité jamais allouée à la fois pour les deux États et la différence entre les allocations totales pour les deux États sont également stockées dans *stateDiff*.

Par défaut, les blocs Runtime C internes (_**crt_block**) ne sont pas inclus dans les opérations d’état de la mémoire. La fonction _ [crtsetdbgflag](crtsetdbgflag.md) peut être utilisée pour activer le bit **_CRTDBG_CHECK_CRT_DF** de _ **crtdbgflag** afin d’inclure ces blocs dans la détection des fuites et d’autres opérations d’état de la mémoire. Les blocs de mémoire libérés ( **_FREE_BLOCK**) n’entraînent pas le renvoi de la valeur true par **_CrtMemDifference** .

Pour plus d’informations sur les fonctions d’État du tas et la structure _ **crtmemstate** , consultez [fonctions de rapport d’État du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

**Bibliotheque** Versions de débogage des fonctionnalités de la [bibliothèque CRT](../../c-runtime-library/crt-library-features.md) uniquement.

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
