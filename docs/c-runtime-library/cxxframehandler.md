---
title: __CxxFrameHandler
ms.date: 11/04/2016
api_name:
- __CxxFrameHandler
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __CxxFrameHandler
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
ms.openlocfilehash: b6350568bdba41da90609dfd5e2e60269e7d729f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217036"
---
# <a name="__cxxframehandler"></a>__CxxFrameHandler

Fonction CRT interne. Utilisée par la bibliothèque CRT pour gérer les frames d'exceptions structurées.

## <a name="syntax"></a>Syntaxe

```cpp
EXCEPTION_DISPOSITION __CxxFrameHandler(
      EHExceptionRecord  *pExcept,
      EHRegistrationNode *pRN,
      void               *pContext,
      DispatcherContext  *pDC
   )
```

#### <a name="parameters"></a>Paramètres

*pExcept*<br/>
Enregistrement d’exception qui est transmis aux **`catch`** instructions possibles.

*pRN*<br/>
Informations dynamiques sur le frame de pile utilisé pour gérer l'exception. Pour plus d'informations, voir ehdata.h.

*pContext*<br/>
Contexte. (Non utilisé sur les processeurs Intel.)

*Maîtres*<br/>
Informations supplémentaires sur l'entrée de la fonction et sur le frame de pile.

## <a name="return-value"></a>Valeur de retour

Une des valeurs *d'expression de filtre* utilisées par [l’instruction try-except](../cpp/try-except-statement.md).

## <a name="remarks"></a>Notes

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|__CxxFrameHandler|excpt.h, ehdata.h|
