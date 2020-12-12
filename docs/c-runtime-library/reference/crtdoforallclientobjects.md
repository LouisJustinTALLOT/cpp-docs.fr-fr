---
description: 'En savoir plus sur : _CrtDoForAllClientObjects'
title: _CrtDoForAllClientObjects
ms.date: 11/04/2016
api_name:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
ms.openlocfilehash: 73d2718aa4bfb68752a8424a385638a48aba2e36
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319789"
---
# <a name="_crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

Appelle une fonction fournie par l’application pour tous les types de **_CLIENT_BLOCK** dans le tas (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>Paramètres

*PFN*<br/>
Pointeur vers la fonction de rappel de la fonction fournie par l'application. Le premier paramètre de cette fonction pointe vers les données. Le deuxième paramètre est le pointeur de contexte qui est passé à l’appel à **_CrtDoForAllClientObjects**.

*context*<br/>
Pointeur vers le contexte fourni par l'application à passer à la fonction fournie par l'application.

## <a name="remarks"></a>Notes

La fonction **_CrtDoForAllClientObjects** recherche dans la liste liée du tas les blocs de mémoire avec le type **_CLIENT_BLOCK** et appelle la fonction fournie par l’application quand un bloc de ce type est trouvé. Le bloc trouvé et le paramètre de *contexte* sont passés comme arguments à la fonction fournie par l’application. Pendant le débogage, une application peut effectuer le suivi d’un groupe spécifique d’allocations en appelant de manière explicite les fonctions du tas de débogage pour allouer la mémoire et en spécifiant que le type de bloc **_CLIENT_BLOCK** doit être affecté aux blocs. Il est alors possible d'assurer le suivi de ces blocs séparément ainsi que de créer des rapports correspondants différents pendant la création de rapports sur la détection des fuites et l'état de la mémoire.

Si le champ de bits **_CRTDBG_ALLOC_MEM_DF** de l’indicateur de [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) n’est pas activé, **_CrtDoForAllClientObjects** retourne immédiatement. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtDoForAllClientObjects** sont supprimés lors du prétraitement.

Pour plus d’informations sur le type de **_CLIENT_BLOCK** et la manière dont il peut être utilisé par d’autres fonctions de débogage, consultez [types de blocs sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

Si *PFN* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a la valeur **EINVAL** et la fonction retourne.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>, \<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

**Bibliothèques :** uniquement les versions de débogage des bibliothèques Runtime C.

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[Fonctions de rapport d’État du tas](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
