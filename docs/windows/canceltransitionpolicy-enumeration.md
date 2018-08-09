---
title: Canceltransitionpolicy, énumération | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
dev_langs:
- C++
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bd203ee0413b60bc7aa713e7923fd4d69bde665e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642956"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy, énumération
Indique la façon dont une opération asynchrone tentative du passage à un état terminal de terminé ou erreur doit se comporter en ce qui concerne un client a demandé l’état annulé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum CancelTransitionPolicy;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="values"></a>Valeurs  
  
|Nom|Description|  
|----------|-----------------|  
|`RemainCanceled`|Si l’opération asynchrone est en cours d’un client a demandé l’état annulé, cela indique qu’il reste à l’état annulé par opposition à la transition vers un terminal terminée ou l’état d’erreur.|  
|`TransitionFromCanceled`|Si l’opération asynchrone est en cours d’un client a demandé l’état annulé, cela indique qu’état doit passer de celle état annulé à l’état terminal de terminé ou erreur, tel que déterminé par l’appel qui utilise cet indicateur.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)