---
title: Classe de IPropertyNotifySinkCP | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9612cf65479e474b9a6e89a8f5a57ca078c9ed0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361624"
---
# <a name="ipropertynotifysinkcp-class"></a>Classe de IPropertyNotifySinkCP
Cette classe expose [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interface comme une interface sortante sur un objet connectable.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T, class CDV = CComDynamicUnkArray>  
class IPropertyNotifySinkCP 
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```    
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IPropertyNotifySinkCP`.  
  
 `CDV`  
 Une classe qui gère les connexions entre un point de connexion et ses récepteurs. La valeur par défaut est [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), ce qui permet un nombre illimité de connexions. Vous pouvez également utiliser [CComUnkArray](../../atl/reference/ccomunkarray-class.md), qui spécifie un nombre fixe de connexions.  
  
## <a name="remarks"></a>Notes  
 `IPropertyNotifySinkCP` hérite de toutes les méthodes via sa classe de base, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).  
  
 Le [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interface permet à un objet sink de recevoir des notifications sur les modifications apportées aux propriétés. Classe `IPropertyNotifySinkCP` expose cette interface comme une interface sortante sur un objet connectable. Le client doit implémenter le `IPropertyNotifySink` méthodes sur le récepteur.  
  
 Dérivez votre classe de `IPropertyNotifySinkCP` lorsque vous souhaitez créer un point de connexion qui représente le `IPropertyNotifySink` interface.  
  
 Pour plus d’informations sur l’utilisation de points de connexion dans les ATL, consultez l’article [Points de connexion](../../atl/atl-connection-points.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)   
 [Classe de IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
