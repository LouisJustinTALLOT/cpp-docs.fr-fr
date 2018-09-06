---
title: Variables globales ATL | Microsoft Docs
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
ms.openlocfilehash: 55844390b872cb0d94ff991ab79b8519388d009f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762458"
---
# <a name="atl-global-variables"></a>Variables globales ATL

## <a name="patlmodule"></a>_pAtlModule

Une variable globale stocker un pointeur vers le module actuel.  

```cpp  
__declspec(selectany) CAtlModule * _pAtlModule  
```  
### <a name="remarks"></a>Notes

Méthodes sur cette variable globale peuvent être utilisés pour fournir les fonctionnalités fournie par la classe (obsolète) CComModule dans Visual C++ 6.0.

### <a name="example"></a>Exemple

```cpp  
LONG lLocks = _pAtlModule->GetLockCount();  
```  
### <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h  

