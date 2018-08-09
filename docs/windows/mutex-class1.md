---
title: Mutex, Classe1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d65d7e2a1087dcce8eaee2fa132ae80d14073dda
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014937"
---
# <a name="mutex-class1"></a>Mutex, Classe1
Représente un objet de synchronisation qui contrôle exclusivement une ressource partagée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class Mutex : public HandleT<HandleTraits::MutexTraits>  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`SyncLock`|Un synonyme pour une classe qui prend en charge les verrous synchrones.|  
  
### <a name="public-constructor"></a>Constructeur public  
  
|Name|Description|  
|----------|-----------------|  
|[Mutex::mutex, constructeur](../windows/mutex-mutex-constructor.md)|Initialise une nouvelle instance de la **Mutex** classe.|  
  
### <a name="public-members"></a>Membres publics  
  
|Name|Description|  
|----------|-----------------|  
|[Mutex::lock, méthode](../windows/mutex-lock-method.md)|Attend jusqu'à ce que l’objet actuel, ou le **Mutex** objet associé au handle spécifié, versions le mutex ou l’intervalle de délai d’attente spécifié se soit écoulé.|  
  
### <a name="public-operator"></a>Opérateur public  
  
|Name|Description|  
|----------|-----------------|  
|[Mutex::operator=, opérateur](../windows/mutex-operator-assign-operator.md)|Assigne le texte spécifié (déplace) **Mutex** objet actuel **Mutex** objet.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Mutex`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)