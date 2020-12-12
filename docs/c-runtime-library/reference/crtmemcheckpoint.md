---
description: 'En savoir plus sur : _CrtMemCheckpoint'
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
ms.openlocfilehash: f7a88e63c99c063999f3de0d01e019fecd10496f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319675"
---
# <a name="_crtmemcheckpoint"></a>_CrtMemCheckpoint

Obtient l’état actuel du tas de débogage et stocke dans une structure de **_CrtMemState** fournie par l’application (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>Paramètres

*state*<br/>
Pointeur vers **_CrtMemState** structure à remplir avec le point de contrôle de la mémoire.

## <a name="remarks"></a>Notes

La fonction **_CrtMemCheckpoint** crée un instantané de l’état actuel du tas de débogage à un moment donné. Cet instantané peut être utilisé par d’autres fonctions d’état du tas, comme [_CrtMemDifference](crtmemdifference.md) , pour aider à détecter les fuites de mémoire et d’autres problèmes. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtMemState** sont supprimés lors du prétraitement.

L’application doit passer un pointeur vers une instance précédemment allouée de la structure **_CrtMemState** , définie dans CRTDBG. h, dans le paramètre *State* . Si **_CrtMemCheckpoint** rencontre une erreur lors de la création du point de contrôle, la fonction génère un rapport de débogage **_CRT_WARN** décrivant le problème.

Pour plus d’informations sur les fonctions d’État du tas et la structure **_CrtMemState** , consultez [fonctions de rapport d’État du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version Debug du tas de base, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

Si *State* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a la valeur **EINVAL** et la fonction retourne.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>, \<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

**Bibliothèques :** uniquement les versions Debug de la bibliothèque UCRT.

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
