---
title: _WAIT_CHILD, _WAIT_GRANDCHILD | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
dev_langs:
- C++
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84e0f195bebd43ced767f05a7c6073a6d6e9db61
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408019"
---
# <a name="waitchild-waitgrandchild"></a>_WAIT_CHILD, _WAIT_GRANDCHILD
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <process.h>  
  
```  
  
## <a name="remarks"></a>Notes  
 La fonction `_cwait` peut être utilisée par n’importe quel processus pour attendre un autre processus (si l’ID du processus est connu). L’argument action peut être une des valeurs suivantes :  
  
|Constante|Signification|  
|--------------|-------------|  
|`_WAIT_CHILD`|Le processus appelant attend jusqu'à l’arrêt du nouveau processus spécifié.|  
|`_WAIT_GRANDCHILD`|Le processus appelant attend jusqu'à l’arrêt du nouveau processus spécifié et de tous les processus qu’il crée.|  
  
## <a name="see-also"></a>Voir aussi  
 [_cwait](../c-runtime-library/reference/cwait.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)