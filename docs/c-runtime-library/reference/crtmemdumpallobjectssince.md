---
description: 'En savoir plus sur : _CrtMemDumpAllObjectsSince'
title: _CrtMemDumpAllObjectsSince
ms.date: 11/04/2016
api_name:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
ms.openlocfilehash: e833543d3119b39a21b596af412a97f6991e4ef0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319636"
---
# <a name="_crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

Vide les informations sur les objets dans le tas à partir du début de l’exécution du programme ou d’un état de tas spécifié (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Paramètres

*state*<br/>
Pointeur désignant l’état de tas à partir duquel commencer le vidage ou **NULL**.

## <a name="remarks"></a>Notes

La fonction **_CrtMemDumpAllObjectsSince** vide les informations d’en-tête de débogage des objets alloués dans le tas sous une forme lisible par l’utilisateur. Les informations de vidage permettent à l’application d’effectuer le suivi des allocations et de détecter les problèmes de mémoire. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtMemDumpAllObjectsSince** sont supprimés lors du prétraitement.

**_CrtMemDumpAllObjectsSince** utilise la valeur du paramètre *State* pour déterminer où initier l’opération de vidage. Pour commencer à vider à partir d’un état de tas spécifié, le paramètre d' *État* doit être un pointeur vers une structure **_CrtMemState** qui a été remplie par [_CrtMemCheckpoint](crtmemcheckpoint.md) avant l’appel de **_CrtMemDumpAllObjectsSince** . Quand *State* a la **valeur null**, la fonction commence le vidage depuis le début de l’exécution du programme.

Si l’application a installé une fonction de raccordement de vidage en appelant [_CrtSetDumpClient](crtsetdumpclient.md), chaque fois que **_CrtMemDumpAllObjectsSince** vide les informations relatives à un type de bloc **_CLIENT_BLOCK** , il appelle également la fonction de vidage fournie par l’application. Par défaut, les blocs Runtime C internes (**_CRT_BLOCK**) ne sont pas inclus dans les opérations de vidage de la mémoire. La fonction [_CrtSetDbgFlag](crtsetdbgflag.md) peut être utilisée pour activer le **_CRTDBG_CHECK_CRT_DF** de **_crtDbgFlag** pour inclure ces blocs. En outre, les blocs marqués comme libérés ou ignorés (**_FREE_BLOCK**, **_IGNORE_BLOCK**) ne sont pas inclus dans le vidage de la mémoire.

Pour plus d’informations sur les fonctions d’État du tas et la structure **_CrtMemState** , consultez [fonctions de rapport d’État du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version Debug du tas de base, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtMemDumpAll ObjectsSince**|\<crtdbg.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **_CrtMemDumpAllObjectsSince**, consultez [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
