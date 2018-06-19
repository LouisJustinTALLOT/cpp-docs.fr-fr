---
title: Classe de IConnectionPointContainerImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
dev_langs:
- C++
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af5e8b1bc1af0a515cc8fad0500c3f7d040b1eb9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361168"
---
# <a name="iconnectionpointcontainerimpl-class"></a>Classe de IConnectionPointContainerImpl
Cette classe implémente un conteneur de point de connexion pour gérer une collection de [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objets.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class ATL_NO_VTABLE IConnectionPointContainerImpl 
   : public IConnectionPointContainer
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IConnectionPointContainerImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Crée un énumérateur pour itérer sur les points de connexion pris en charge dans l’objet connectable.|  
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Récupère un pointeur d’interface vers le point de connexion qui prend en charge l’IID spécifié.|  
  
## <a name="remarks"></a>Notes  
 `IConnectionPointContainerImpl` implémente un conteneur de point de connexion pour gérer une collection de [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objets. `IConnectionPointContainerImpl` propose deux méthodes qu’un client peut appeler pour récupérer des informations sur un objet connectable :  
  
- `EnumConnectionPoints` permet au client déterminer quels sortant interfaces de l’objet prend en charge.  
  
- `FindConnectionPoint` permet au client déterminer si l’objet prend en charge une interface sortante spécifique.  
  
 Pour plus d’informations sur l’utilisation de points de connexion dans ATL, consultez l’article [Points de connexion](../../atl/atl-connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IConnectionPointContainer`  
  
 `IConnectionPointContainerImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
##  <a name="enumconnectionpoints"></a>  IConnectionPointContainerImpl::EnumConnectionPoints  
 Crée un énumérateur pour itérer sur les points de connexion pris en charge dans l’objet connectable.  
  
```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IConnectionPointContainer::EnumConnectionPoints](http://msdn.microsoft.com/library/windows/desktop/ms682460) dans le Kit de développement logiciel Windows.  
  
##  <a name="findconnectionpoint"></a>  IConnectionPointContainerImpl::FindConnectionPoint  
 Récupère un pointeur d’interface vers le point de connexion qui prend en charge l’IID spécifié.  
  
```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
