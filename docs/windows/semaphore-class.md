---
title: Classe de sémaphore | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Semaphore class
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5feb954a5bba1bfc7c3a98b1324e75bd2aa058f1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015701"
---
# <a name="semaphore-class"></a>Semaphore (classe)
Représente un objet de synchronisation qui contrôle une ressource partagée prenant en charge un nombre limité d’utilisateurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`SyncLock`|Un synonyme pour une classe qui prend en charge les verrous synchrones.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Semaphore::Semaphore, constructeur](../windows/semaphore-semaphore-constructor.md)|Initialise une nouvelle instance de la **sémaphore** classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[InvokeHelper::Invoke, méthode](../windows/invokehelper-invoke-method.md)|Appelle le Gestionnaire d’événements dont la signature contient le nombre spécifié d’arguments.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Semaphore::Lock, méthode](../windows/semaphore-lock-method.md)|Attend que l’objet en cours ou l’objet associé au handle spécifié, est dans l’état signalé ou que l’intervalle de délai d’attente spécifié est écoulé.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Semaphore::operator=, opérateur](../windows/semaphore-operator-assign-operator.md)|Déplace le handle spécifié à partir d’un **sémaphore** objet actuel **sémaphore** objet.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Semaphore`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)