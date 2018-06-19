---
title: _CrtGetAllocHook | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtGetAllocHook
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
- CrtGetAllocHook
- _CrtGetAllocHook
dev_langs:
- C++
helpviewer_keywords:
- _CrtGetAllocHook function
- CrtGetAllocHook function
ms.assetid: 036acf7c-547a-4b3f-a636-80451070d7ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb811353d0ac252411cc5bfc8beb408b6e707089
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394520"
---
# <a name="crtgetallochook"></a>_CrtGetAllocHook

Récupère la fonction d’allocation définie par le client pour le raccordement au processus d’allocation de mémoire de débogage du runtime C (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
_CRT_ALLOC_HOOK _CrtGetAllocHook( void );
```

## <a name="return-value"></a>Valeur de retour

Retourne la fonction de raccordement d’allocation définie.

## <a name="remarks"></a>Notes

**_CrtGetAllocHook** récupère de la fonction de raccordement d’application définies par le client en cours pour le processus d’allocation mémoire bibliothèque C Runtime debug.

Pour plus d’informations sur l’utilisation d’autres fonctions d’exécution compatibles avec le raccordement et sur l’écriture de vos propres fonctions de raccordement définies par le client, consultez [Écriture de fonctions de raccordement de débogage](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtGetAllocHook**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetAllocHook](crtsetallochook.md)<br/>
