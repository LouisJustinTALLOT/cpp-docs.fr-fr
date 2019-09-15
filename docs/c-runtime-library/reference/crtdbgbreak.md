---
title: _CrtDbgBreak
ms.date: 11/04/2016
api_name:
- _CrtDbgBreak
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
- _CrtDbgBreak
- CrtDbgBreak
helpviewer_keywords:
- CrtDbgBreak function
- _CrtDbgBreak function
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
ms.openlocfilehash: 9471b1a93abd9777c3a53c54c2517e59896d8160
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942580"
---
# <a name="_crtdbgbreak"></a>_CrtDbgBreak

Définit un point d’arrêt sur une ligne de code particulière. (Utilisé en mode de débogage uniquement.)

## <a name="syntax"></a>Syntaxe

```C
void _CrtDbgBreak( void );
```

## <a name="return-value"></a>Valeur de retour

Il n'y a pas de valeur de retour.

## <a name="remarks"></a>Notes

La fonction **_CrtDbgBreak** définit un point d’arrêt de débogage sur la ligne de code spécifique où la fonction réside. Cette fonction est utilisée uniquement en mode débogage et dépend de **_ DEBUG** défini précédemment.

Pour plus d’informations sur l’utilisation d’autres fonctions d’exécution compatibles avec le raccordement et sur l’écriture de vos propres fonctions de raccordement définies par le client, consultez [Écriture de vos propres fonctions de raccordement de débogage](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtDbgBreak**|\<CRTDBG.h>|

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[__debugbreak](../../intrinsics/debugbreak.md)<br/>
