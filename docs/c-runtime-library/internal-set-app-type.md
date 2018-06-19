---
title: __set_app_type | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __set_app_type
- _set_app_type
apilocation:
- msvcr90.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __set_app_type
dev_langs:
- C++
helpviewer_keywords:
- __set_app_type
ms.assetid: f0ac0f4d-70e6-4e96-9e43-eb9d1515490c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 854873987cd83b89efc5c9006c1e091023c91226
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389060"
---
# <a name="setapptype"></a>__set_app_type
Définit le type d’application actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __set_app_type (  
   int at  
   )  
```  
  
#### <a name="parameters"></a>Paramètres  
 `at`  
 Valeur qui indique le type d’application. Les valeurs possibles sont :  
  
|Value|Description|  
|-----------|-----------------|  
|_UNKNOWN_APP|Type d’application inconnu.|  
|_CONSOLE_APP|Application console (ligne de commande).|  
|_GUI_APP|Application GUI (Windows).|  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|__set_app_type|internal.h|