---
title: __CxxFrameHandler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __CxxFrameHandler
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __CxxFrameHandler
dev_langs:
- C++
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53659b462f811bca79209dd141d90527401cbc95
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388282"
---
# <a name="cxxframehandler"></a>__CxxFrameHandler
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
 `pExcept`  
 Enregistrement d'exception qui est transmis aux instructions `catch` possibles.  
  
 `pRN`  
 Informations dynamiques sur le frame de pile utilisé pour gérer l'exception. Pour plus d'informations, voir ehdata.h.  
  
 `pContext`  
 Contexte. (Non utilisé sur les processeurs Intel.)  
  
 `pDC`  
 Informations supplémentaires sur l'entrée de la fonction et sur le frame de pile.  
  
## <a name="return-value"></a>Valeur de retour  
 Une des valeurs *d'expression de filtre* utilisées par [l’instruction try-except](../cpp/try-except-statement.md).  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|__CxxFrameHandler|excpt.h, ehdata.h|