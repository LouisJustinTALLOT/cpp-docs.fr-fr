---
title: _CrtMemDumpStatistics | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 688cef94721ac7ea3a36ccd375185b922b23a15f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395602"
---
# <a name="crtmemdumpstatistics"></a>_CrtMemDumpStatistics

Vide les informations d’en-tête de débogage pour l’état du tas spécifié sous une forme lisible par l’utilisateur (version Debug uniquement).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemDumpStatistics(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Paramètres

*état* pointeur vers l’état du tas à vider.

## <a name="remarks"></a>Notes

Le **_CrtMemDumpStatistics** fonction exporte les informations d’en-tête de débogage pour un état spécifié du segment de mémoire sous une forme lisible par l’utilisateur. Les statistiques de vidage permettent à l’application d’effectuer le suivi des allocations, et de détecter les problèmes de mémoire. L’état de la mémoire peut contenir un état de tas spécifique, ou la différence entre deux états. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtMemDumpStatistics** sont supprimés lors du prétraitement.

Le *état* paramètre doit être un pointeur vers un **_CrtMemState** structure a été renseigné par [_CrtMemCheckpoint](crtmemcheckpoint.md) ou retournée par [_ CrtMemDifference](crtmemdifference.md) avant **_CrtMemDumpStatistics** est appelée. Si *état* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et aucune action n’est effectuée. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pour plus d’informations sur les fonctions d’état du tas et le **_CrtMemState** de la structure, consultez [fonctions de rapport état du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version Debug du tas de base, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

**Bibliothèques :** uniquement les versions de débogage des [fonctions de bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
