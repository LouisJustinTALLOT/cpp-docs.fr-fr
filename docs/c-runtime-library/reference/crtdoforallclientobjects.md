---
title: _CrtDoForAllClientObjects | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
dev_langs:
- C++
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 889c3c4060098927df08d785e85b64e7e7becc2c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

Appelle une fonction fournie par l’application pour toutes les **_CLIENT_BLOCK** types dans le tas (version debug uniquement).

## <a name="syntax"></a>Syntaxe

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>Paramètres

*pfn* pointeur vers la fonction de rappel fournie par l’application de fonction. Le premier paramètre de cette fonction pointe vers les données. Le deuxième paramètre est le pointeur de contexte qui est passé à l’appel à **_CrtDoForAllClientObjects**.

*contexte* pointeur vers le contexte fourni par l’application à passer à la fonction fournie par l’application.

## <a name="remarks"></a>Notes

Le **_CrtDoForAllClientObjects** fonction dans la liste du tas lié blocs de mémoire avec la **_CLIENT_BLOCK** type et appelle la fonction fournie par l’application quand un bloc de ce type est trouvé. Le bloc trouvé et le *contexte* paramètre sont passés comme arguments à la fonction fournie par l’application. Pendant le débogage, une application peut suivre un groupe spécifique d’allocations en appelant explicitement le débogage des fonctions de segment de mémoire à allouer la mémoire et en spécifiant que les blocs d’être assigné la **_CLIENT_BLOCK** type de bloc. Il est alors possible d'assurer le suivi de ces blocs séparément ainsi que de créer des rapports correspondants différents pendant la création de rapports sur la détection des fuites et l'état de la mémoire.

Si le **_CRTDBG_ALLOC_MEM_DF** champ de bits de le [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) indicateur n’est pas activé, **_CrtDoForAllClientObjects** retourne immédiatement. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtDoForAllClientObjects** sont supprimés lors du prétraitement.

Pour plus d’informations sur la **_CLIENT_BLOCK** de type et la manière dont il peut être utilisé par d’autres fonctions de débogage, consultez [Types de blocs sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

Si *pfn* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a la valeur **EINVAL** et la fonction retourne.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>, \<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

**Bibliothèques :** uniquement les versions de débogage des bibliothèques Runtime C.

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[Fonctions de création de rapports d’état du tas](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
