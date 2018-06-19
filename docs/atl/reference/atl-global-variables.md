---
title: Les Variables globales ATL | Documents Microsoft
ms.custom: ''
ms.date: 12/06/2017
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATLBASE/_pAtlModule
dev_langs:
- C++
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4664c99eb49b57f258be399c042fa14b60bbecdf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356477"
---
# <a name="atl-global-variables"></a>Variables globales ATL

## <a name="patlmodule"></a>_pAtlModule  
Une variable globale, le stockage d’un pointeur vers le module actuel.  

```cpp  
__declspec(selectany) CAtlModule * _pAtlModule  
```  
### <a name="remarks"></a>Notes  
Les méthodes sur cette variable globale peuvent être utilisés pour fournir les fonctionnalités fournie par la classe (obsolète) CComModule dans Visual C++ 6.0.

### <a name="example"></a>Exemple  

```cpp  
LONG lLocks = _pAtlModule->GetLockCount();  
```  
### <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  

