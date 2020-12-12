---
description: 'En savoir plus sur : _CrtDumpMemoryLeaks'
title: _CrtDumpMemoryLeaks
ms.date: 11/04/2016
api_name:
- _CrtDumpMemoryLeaks
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
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
ms.openlocfilehash: 83b3effdc4f3e8afdad24057ab55123aee924d60
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319776"
---
# <a name="_crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

Vide tous les blocs de mémoire dans le tas de débogage quand une fuite de mémoire s’est produite (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>Valeur de retour

**_CrtDumpMemoryLeaks** retourne la valeur true si une fuite de mémoire est détectée. Dans le cas contraire, la fonction retourne FALSE.

## <a name="remarks"></a>Notes

La fonction **_CrtDumpMemoryLeaks** détermine si une fuite de mémoire s’est produite depuis le début de l’exécution du programme. Quand une fuite est détectée, les informations d’en-tête de débogage pour tous les objets du tas sont exportées dans un format lisible par l’utilisateur. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtDumpMemoryLeaks** sont supprimés lors du prétraitement.

**_CrtDumpMemoryLeaks** est fréquemment appelé à la fin de l’exécution du programme pour vérifier que toute la mémoire allouée par l’application a été libérée. La fonction peut être appelée automatiquement au moment de l’arrêt du programme en activant le champ de bits **_CRTDBG_LEAK_CHECK_DF** de l’indicateur de [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) à l’aide de la fonction [_CrtSetDbgFlag](crtsetdbgflag.md) .

**_CrtDumpMemoryLeaks** appelle [_CrtMemCheckpoint](crtmemcheckpoint.md) pour obtenir l’état actuel du tas, puis analyse l’état des blocs qui n’ont pas été libérés. Lorsqu’un bloc non libéré est rencontré, **_CrtDumpMemoryLeaks** appelle [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) pour vider les informations de tous les objets alloués dans le tas à partir du début de l’exécution du programme.

Par défaut, les blocs Runtime C internes (**_CRT_BLOCK**) ne sont pas inclus dans les opérations de vidage de la mémoire. La fonction [_CrtSetDbgFlag](crtsetdbgflag.md) peut être utilisée pour activer le **_CRTDBG_CHECK_CRT_DF** **_crtDbgFlag** d’inclure ces blocs dans le processus de détection des fuites.

Pour plus d’informations sur les fonctions d’État du tas et la structure **_CrtMemState** , consultez [fonctions de rapport d’État du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version Debug du tas de base, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **_CrtDumpMemoryLeaks**, consultez [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
