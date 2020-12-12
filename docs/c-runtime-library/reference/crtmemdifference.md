---
description: 'En savoir plus sur : _CrtMemDifference'
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
ms.openlocfilehash: 076cead5f60df457171bbcdf2fd8690f0361870b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319649"
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
Pointeur vers une structure de **_CrtMemState** utilisée pour stocker les différences entre les deux États de la mémoire (retourné).

*oldState*<br/>
Pointeur vers un état antérieur de la mémoire (structure **_CrtMemState** ).

*newState*<br/>
Pointeur vers un état de mémoire ultérieur (structure **_CrtMemState** ).

## <a name="return-value"></a>Valeur renvoyée

Si les États de la mémoire sont très différents, **_CrtMemDifference** retourne la valeur true. Dans le cas contraire, la fonction retourne FALSE.

## <a name="remarks"></a>Notes

La fonction **_CrtMemDifference** compare *OldState* et *NewState* et stocke leurs différences dans *stateDiff*, qui peuvent ensuite être utilisées par l’application pour détecter les fuites de mémoire et autres problèmes de mémoire. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtMemDifference** sont supprimés lors du prétraitement.

*NewState* et *OldState* doivent tous être un pointeur valide vers une structure **_CrtMemState** , définie dans CRTDBG. h, qui a été rempli par [_CrtMemCheckpoint](crtmemcheckpoint.md) avant d’appeler **_CrtMemDifference**. *stateDiff* doit être un pointeur vers une instance précédemment allouée de la structure **_CrtMemState** . Si *stateDiff*, *NewState* ou *OldState* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) est défini sur **EINVAL** et la fonction retourne false.

**_CrtMemDifference** compare les valeurs de champ **_CrtMemState** des blocs dans *OldState* à celles de *NewState* et stocke le résultat dans *stateDiff*. Quand le nombre de types de bloc alloués ou le nombre total de blocs alloués pour chaque type diffère entre les deux états de la mémoire, ces états sont considérés comme très différents. La différence entre la plus grande quantité jamais allouée à la fois pour les deux États et la différence entre les allocations totales pour les deux États sont également stockées dans *stateDiff*.

Par défaut, les blocs Runtime C internes (**_CRT_BLOCK**) ne sont pas inclus dans les opérations d’état de la mémoire. La fonction [_CrtSetDbgFlag](crtsetdbgflag.md) peut être utilisée pour activer le **_CRTDBG_CHECK_CRT_DF** bit de **_crtDbgFlag** pour inclure ces blocs dans la détection des fuites et dans d’autres opérations d’état de la mémoire. Les blocs de mémoire libérés (**_FREE_BLOCK**) ne provoquent pas que **_CrtMemDifference** retourne la valeur true.

Pour plus d’informations sur les fonctions d’État du tas et la structure **_CrtMemState** , consultez [fonctions de rapport d’État du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

**Bibliothèques :** uniquement les versions de débogage des [fonctions de bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
