---
description: 'En savoir plus sur : __CxxFrameHandler'
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
ms.openlocfilehash: 3ebd4cefb303661b4b0293f3b4b3d42a915ddd56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326361"
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

## <a name="return-value"></a>Valeur renvoyée

Une des valeurs *d'expression de filtre* utilisées par [l’instruction try-except](../cpp/try-except-statement.md).

## <a name="remarks"></a>Notes

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|__CxxFrameHandler|excpt.h, ehdata.h|
