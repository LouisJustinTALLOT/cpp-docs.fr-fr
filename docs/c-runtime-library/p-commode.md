---
title: __p__commode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __p__commode
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __p__commode
dev_langs:
- C++
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e91c03f619be1d0f1d8ad23f3b8d60e1be30cfb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388063"
---
# <a name="pcommode"></a>__p__commode
Pointe vers la variable globale `_commode`, qui spécifie le *mode de validation de fichiers* par défaut pour les opérations d’E/S de fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
int * __p__commode(  
   );  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Pointeur vers la variable globale `_commode`.  
  
## <a name="remarks"></a>Notes  
 La fonction `__p__commode` est exclusivement réservée à un usage interne et ne doit pas être appelée à partir du code utilisateur.  
  
 Le mode de validation de fichiers spécifie quand les données critiques sont écrites sur le disque. Pour plus d’informations, consultez [fflush](../c-runtime-library/reference/fflush.md).  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|__p\__commode|internal.h|