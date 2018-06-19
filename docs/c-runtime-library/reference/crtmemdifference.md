---
title: _CrtMemDifference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtMemDifference
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
apitype: DLLExport
f1_keywords:
- _CrtMemDifference
- CrtMemDifference
dev_langs:
- C++
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66bb770c2f24c0312277d23c14beef09e2265f88
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398045"
---
# <a name="crtmemdifference"></a>_CrtMemDifference

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
Pointeur vers un **_CrtMemState** structure qui est utilisé pour stocker les différences entre les États de deux mémoire (retournés).

*oldState*<br/>
Pointeur vers un état antérieur de la mémoire (**_CrtMemState** structure).

*newState*<br/>
Pointeur vers un état ultérieur de la mémoire (**_CrtMemState** structure).

## <a name="return-value"></a>Valeur de retour

Si les États de la mémoire sont très différents, **_CrtMemDifference** retourne la valeur TRUE. Dans le cas contraire, la fonction retourne FALSE.

## <a name="remarks"></a>Notes

Le **_CrtMemDifference** fonction compare *oldState* et *newState* et stocke leurs différences dans *stateDiff*, lequel peut ensuite utilisé par l’application pour détecter les fuites de mémoire et d’autres problèmes de mémoire. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtMemDifference** sont supprimés lors du prétraitement.

*newState* et *oldState* doivent chacune être un pointeur valide vers une **_CrtMemState** structure, définie dans Crtdbg.h, qui a été renseigné par [_CrtMemCheckpoint](crtmemcheckpoint.md)avant d’appeler **_CrtMemDifference**. *stateDiff* doit être un pointeur vers une instance précédemment allouée de la **_CrtMemState** structure. Si *stateDiff*, *newState*, ou *oldState* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [ Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a la valeur **EINVAL** et la fonction retourne FALSE.

**_CrtMemDifference** compare le **_CrtMemState** champ valeurs des blocs dans *oldState* à ceux de *newState* et stocke le résultat dans *stateDiff*. Quand le nombre de types de bloc alloués ou le nombre total de blocs alloués pour chaque type diffère entre les deux états de la mémoire, ces états sont considérés comme très différents. La différence entre la quantité maximale allouée à la fois pour les deux États et la différence entre les allocations totales pour les deux États sont également stockées dans *stateDiff*.

Par défaut, les blocs de runtime C internes (**_CRT_BLOCK**) ne sont pas inclus dans les opérations d’état de mémoire. Le [_CrtSetDbgFlag](crtsetdbgflag.md) fonction peut être utilisée pour activer la **_CRTDBG_CHECK_CRT_DF** de **_crtDbgFlag** à inclure ces blocs dans la détection des fuites et l’état de la mémoire opérations. Blocs de mémoire libérés (**_FREE_BLOCK**) ne provoquent pas **_CrtMemDifference** pour retourner la valeur TRUE.

Pour plus d’informations sur les fonctions d’état du tas et le **_CrtMemState** de la structure, consultez [fonctions de rapport état du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

**Bibliothèques :** uniquement les versions de débogage des [fonctions de bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
