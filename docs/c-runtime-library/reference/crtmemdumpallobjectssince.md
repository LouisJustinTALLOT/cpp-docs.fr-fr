---
title: _CrtMemDumpAllObjectsSince | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24cf01facaba326c36454ea5410da8dbb05848f2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396867"
---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

Vide les informations sur les objets dans le tas à partir du début de l’exécution du programme ou d’un état de tas spécifié (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Paramètres

*état* pointeur vers l’état du tas pour commencer le vidage à partir d’ou **NULL**.

## <a name="remarks"></a>Notes

Le **_CrtMemDumpAllObjectsSince** fonction exporte les informations d’en-tête de débogage des objets alloués dans le tas sous une forme lisible par l’utilisateur. Les informations de vidage permettent à l’application d’effectuer le suivi des allocations et de détecter les problèmes de mémoire. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtMemDumpAllObjectsSince** sont supprimés lors du prétraitement.

**_CrtMemDumpAllObjectsSince** utilise la valeur de la *état* paramètre afin de déterminer où lancer l’opération de vidage. Pour commencer le vidage d’un état du tas spécifié, le *état* paramètre doit être un pointeur vers un **_CrtMemState** structure a été renseigné par [_CrtMemCheckpoint](crtmemcheckpoint.md) avant **_CrtMemDumpAllObjectsSince** a été appelée. Lorsque *état* est **NULL**, la fonction commence le dump à partir du début de l’exécution du programme.

Si l’application a installé une fonction de raccordement de vidage en appelant [_CrtSetDumpClient](crtsetdumpclient.md), puis chaque fois que **_CrtMemDumpAllObjectsSince** exporte les informations sur un **_CLIENT_BLOCK** type de bloc, il appelle la fonction de vidage de fournie par l’application ainsi. Par défaut, les blocs de runtime C internes (**_CRT_BLOCK**) ne sont pas inclus dans les opérations de vidage de mémoire. Le [_CrtSetDbgFlag](crtsetdbgflag.md) fonction peut être utilisée pour activer la **_CRTDBG_CHECK_CRT_DF** de **_crtDbgFlag** afin d’inclure ces blocs. En outre, les blocs marqués comme libérés ou ignorés (**_FREE_BLOCK**, **_IGNORE_BLOCK**) ne sont pas inclus dans le vidage de la mémoire.

Pour plus d’informations sur les fonctions d’état du tas et le **_CrtMemState** de la structure, consultez [fonctions de rapport état du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version Debug du tas de base, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple montrant comment utiliser **_CrtMemDumpAllObjectsSince**, consultez [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
