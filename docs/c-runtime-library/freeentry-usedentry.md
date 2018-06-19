---
title: _FREEENTRY, _USEDENTRY | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- USEDENTRY
- _USEDENTRY
- _FREEENTRY
- FREEENTRY
dev_langs:
- C++
helpviewer_keywords:
- _USEDENTRY constant
- _FREEENTRY constant
- FREEENTRY constant
- USEDENTRY constant
ms.assetid: 26f658e6-6846-4a4e-9984-262cfe392770
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d75dbc61ae2c9b0c30217a782519ba4e826d2b98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390776"
---
# <a name="freeentry-usedentry"></a>_FREEENTRY, _USEDENTRY
## <a name="syntax"></a>Syntaxe  
  
```  
#include <malloc.h>  
```  
  
## <a name="remarks"></a>Notes  
 Ces constantes représentent les valeurs affectées par les routines `_heapwalk` à l’élément **_useflag** de la structure **_HEAPINFO**. Ils indiquent l’état de l’entrée de tas.  
  
## <a name="see-also"></a>Voir aussi  
 [_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)