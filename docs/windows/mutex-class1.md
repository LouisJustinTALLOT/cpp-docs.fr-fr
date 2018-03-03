---
title: Mutex Class1 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0e849d1fee7eca67f3b5765d31b54e0660eaa25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="mutex-class1"></a>Mutex Class1
Représente un objet de synchronisation qui contrôle exclusivement une ressource partagée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class Mutex : public HandleT<HandleTraits::MutexTraits>  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|**SyncLock**|Un synonyme pour une classe qui prend en charge les verrous synchrones.|  
  
### <a name="public-constructor"></a>Constructeur public  
  
|Name|Description|  
|----------|-----------------|  
|[Mutex::mutex, constructeur](../windows/mutex-mutex-constructor.md)|Initialise une nouvelle instance de la classe Mutex.|  
  
### <a name="public-members"></a>Membres publics  
  
|Name|Description|  
|----------|-----------------|  
|[Mutex::lock, méthode](../windows/mutex-lock-method.md)|Attend que l’objet actif ou l’objet Mutex associé au handle spécifié, libère le mutex ou l’intervalle de délai d’attente spécifié est écoulé.|  
  
### <a name="public-operator"></a>Opérateur public  
  
|Name|Description|  
|----------|-----------------|  
|[Mutex::operator=, opérateur](../windows/mutex-operator-assign-operator.md)|Affecte (se déplace) le Mutex spécifié de l’objet à l’objet Mutex actuel.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Mutex`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)