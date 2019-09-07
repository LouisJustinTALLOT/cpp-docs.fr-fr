---
title: _CrtMemDumpStatistics
ms.date: 11/04/2016
apiname:
- _CrtMemDumpStatistics
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
- CrtMemDumpStatistics
- _CrtMemDumpStatistics
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
ms.openlocfilehash: 66eb58b65f3fa20e01ad16d68f3fe1baafd8cd04
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739812"
---
# <a name="_crtmemdumpstatistics"></a>_CrtMemDumpStatistics

Vide les informations d’en-tête de débogage pour l’état du tas spécifié sous une forme lisible par l’utilisateur (version Debug uniquement).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemDumpStatistics(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Paramètres

*state*<br/>
Pointeur vers l’état du tas à vider.

## <a name="remarks"></a>Notes

La fonction **_CrtMemDumpStatistics** vide les informations d’en-tête de débogage pour un état spécifié du tas sous une forme lisible par l’utilisateur. Les statistiques de vidage permettent à l’application d’effectuer le suivi des allocations, et de détecter les problèmes de mémoire. L’état de la mémoire peut contenir un état de tas spécifique, ou la différence entre deux états. Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtMemDumpStatistics** sont supprimés lors du prétraitement.

Le paramètre d' *État* doit être un pointeur vers une structure _ **crtmemstate** qui a été remplie par [_CrtMemCheckpoint](crtmemcheckpoint.md) ou retournée par [_CrtMemDifference](crtmemdifference.md) avant l’appel de **_CrtMemDumpStatistics** . Si *State* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et aucune action n’est effectuée. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pour plus d’informations sur les fonctions d’État du tas et la structure _ **crtmemstate** , consultez [fonctions de rapport d’État du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version Debug du tas de base, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

**Bibliotheque** Versions de débogage des fonctionnalités de la [bibliothèque CRT](../../c-runtime-library/crt-library-features.md) uniquement.

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
