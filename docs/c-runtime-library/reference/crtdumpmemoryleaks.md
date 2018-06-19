---
title: _CrtDumpMemoryLeaks | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDumpMemoryLeaks
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
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
dev_langs:
- C++
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68a187283eedadcd2f435b0900fde648a5010368
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396964"
---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

Vide tous les blocs de mémoire dans le tas de débogage quand une fuite de mémoire s’est produite (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>Valeur de retour

**_CrtDumpMemoryLeaks** retourne la valeur TRUE si une fuite de mémoire est trouvée. Dans le cas contraire, la fonction retourne FALSE.

## <a name="remarks"></a>Notes

Le **_CrtDumpMemoryLeaks** fonction détermine si une fuite de mémoire a eu lieu depuis le début de l’exécution du programme. Quand une fuite est détectée, les informations d’en-tête de débogage pour tous les objets du tas sont exportées dans un format lisible par l’utilisateur. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtDumpMemoryLeaks** sont supprimés lors du prétraitement.

**_CrtDumpMemoryLeaks** est fréquemment appelée à la fin de l’exécution du programme pour vérifier que toute mémoire allouée par l’application a été libérée. La fonction peut être appelée automatiquement à l’arrêt du programme en activant le **_CRTDBG_LEAK_CHECK_DF** champ de bits de le [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) indicateur à l’aide de la [_CrtSetDbgFlag](crtsetdbgflag.md)(fonction).

**_CrtDumpMemoryLeaks** appelle [_CrtMemCheckpoint](crtmemcheckpoint.md) pour obtenir l’état actuel du segment de mémoire, puis vérifie l’état pour les blocs qui n’ont pas été libérés. Lorsqu’un bloc non libéré est rencontré, **_CrtDumpMemoryLeaks** appelle [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) aux informations de vidage pour tous les objets alloués dans le tas à partir du début de l’exécution du programme.

Par défaut, les blocs de runtime C internes (**_CRT_BLOCK**) ne sont pas inclus dans les opérations de vidage de mémoire. Le [_CrtSetDbgFlag](crtsetdbgflag.md) fonction peut être utilisée pour activer la **_CRTDBG_CHECK_CRT_DF** de **_crtDbgFlag** à inclure ces blocs dans le processus de détection des fuites.

Pour plus d’informations sur les fonctions d’état du tas et le **_CrtMemState** de la structure, consultez [fonctions de rapport état du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version Debug du tas de base, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple montrant comment utiliser **_CrtDumpMemoryLeaks**, consultez [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
