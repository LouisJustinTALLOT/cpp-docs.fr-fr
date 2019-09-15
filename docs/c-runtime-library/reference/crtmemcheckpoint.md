---
title: _CrtMemCheckpoint
ms.date: 11/04/2016
api_name:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
ms.openlocfilehash: edf91cd8c76fd080326e2e5eeac98f7f81ab90cf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942365"
---
# <a name="_crtmemcheckpoint"></a>_CrtMemCheckpoint

Obtient l’état actuel du tas de débogage et stocke dans une structure _ **crtmemstate** fournie par l’application (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>Paramètres

*state*<br/>
Pointeur vers la structure _ **crtmemstate** à remplir avec le point de contrôle de mémoire.

## <a name="remarks"></a>Notes

La fonction **_CrtMemCheckpoint** crée un instantané de l’état actuel du tas de débogage à un moment donné. Cet instantané peut être utilisé par d’autres fonctions d’état du tas, comme [_CrtMemDifference](crtmemdifference.md) , pour aider à détecter les fuites de mémoire et d’autres problèmes. Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à _ **crtmemstate** sont supprimés lors du prétraitement.

L’application doit passer un pointeur vers une instance précédemment allouée de la structure _ **crtmemstate** , définie dans CRTDBG. h, dans le paramètre *State* . Si **_CrtMemCheckpoint** rencontre une erreur lors de la création du point de contrôle, la fonction génère un rapport de débogage **_CRT_WARN** décrivant le problème.

Pour plus d’informations sur les fonctions d’État du tas et la structure _ **crtmemstate** , consultez [fonctions de rapport d’État du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version Debug du tas de base, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

Si *State* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ont la valeur **EINVAL** et la fonction retourne.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>, \<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

**Bibliotheque** Versions de débogage de UCRT uniquement.

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
