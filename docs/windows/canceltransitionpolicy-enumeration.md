---
title: Canceltransitionpolicy, énumération | Documents Microsoft
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
ms.openlocfilehash: 64f588e67066fed690271aa7d78fcbe726c67177
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860344"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy, énumération
Indique la façon dont une opération asynchrone tentative du passage à un état terminal de terminée ou l’erreur doit se comporter en ce qui concerne un client a demandé l’état annulé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum CancelTransitionPolicy;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="values"></a>Valeurs  
  
|Nom|Description|  
|----------|-----------------|  
|`RemainCanceled`|Si l’opération asynchrone est actuellement dans un état annulé de demande du client, cela indique qu’il reste dans l’état annulé, par opposition à la transition vers un Terminal Server s’est terminée ou l’état d’erreur.|  
|`TransitionFromCanceled`|Si l’opération asynchrone est actuellement dans un état annulé de demande du client, cela indique qu’état doit passer à partir de ce à l’état terminal d’état d’annulation s’est terminée ou d’erreur tel que déterminé par l’appel qui utilise cet indicateur.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)