---
description: 'En savoir plus sur : _CrtMemDumpStatistics'
title: _CrtMemDumpStatistics
ms.date: 11/04/2016
api_name:
- _CrtMemDumpStatistics
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
- CrtMemDumpStatistics
- _CrtMemDumpStatistics
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
ms.openlocfilehash: 2f02c35ff61dc2bc5ac7e8dfbe921fa48731c2b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319611"
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

La fonction **_CrtMemDumpStatistics** vide les informations d’en-tête de débogage pour un état spécifié du tas sous une forme lisible par l’utilisateur. Les statistiques de vidage permettent à l’application d’effectuer le suivi des allocations, et de détecter les problèmes de mémoire. L’état de la mémoire peut contenir un état de tas spécifique, ou la différence entre deux états. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtMemDumpStatistics** sont supprimés lors du prétraitement.

Le paramètre d' *État* doit être un pointeur vers une structure **_CrtMemState** qui a été remplie par [_CrtMemCheckpoint](crtmemcheckpoint.md) ou retournée par [_CrtMemDifference](crtmemdifference.md) avant l’appel de **_CrtMemDumpStatistics** . Si *State* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et aucune action n’est effectuée. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pour plus d’informations sur les fonctions d’État du tas et la structure **_CrtMemState** , consultez [fonctions de rapport d’État du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version Debug du tas de base, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

**Bibliothèques :** uniquement les versions de débogage des [fonctions de bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
