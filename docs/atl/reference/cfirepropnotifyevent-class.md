---
title: Classe de CFirePropNotifyEvent | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
dev_langs:
- C++
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 728f4e973a7ef74dcdbb44150375df235e0d990e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent (classe)
Cette classe fournit des méthodes de notification du récepteur du conteneur en ce qui concerne les modifications apportées aux propriétés de contrôle.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CFirePropNotifyEvent
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Statique) Notifie le récepteur du conteneur qu’une propriété de contrôle a changé.|  
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|(Statique) Notifie le récepteur du conteneur qui a une propriété de contrôle est sur le point de changer.|  
  
## <a name="remarks"></a>Notes  
 `CFirePropNotifyEvent` a deux méthodes pour avertir les récepteurs du conteneur qui a une propriété de contrôle a été modifié ou est sur le point de changer.  
  
 Si la classe qui implémente votre contrôle est dérivée `IPropertyNotifySink`, le `CFirePropNotifyEvent` les méthodes sont appelées lorsque vous appelez `FireOnRequestEdit` ou `FireOnChanged`. Si votre classe de contrôle n’est pas dérivée de `IPropertyNotifySink`, les appels à ces fonctions retournent `S_OK`.  
  
 Pour plus d’informations sur la création de contrôles, consultez la [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
##  <a name="fireonchanged"></a>  CFirePropNotifyEvent::FireOnChanged  
 Avertit tous connectés [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) (sur chaque point de connexion de l’objet), les interfaces que la propriété de l’objet spécifié a changé.  
  
```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>Paramètres  
 *pUnk*  
 [in] Pointeur vers le **IUnknown** de l’objet qui envoie la notification.  
  
 *dispID*  
 [in] Identificateur de la propriété qui a changé.  
  
### <a name="return-value"></a>Valeur de retour  
 Un de la norme `HRESULT` valeurs.  
  
### <a name="remarks"></a>Notes  
 Cette fonction peut appeler, même si votre contrôle ne prend pas en charge les points de connexion.  
  
##  <a name="fireonrequestedit"></a>  CFirePropNotifyEvent::FireOnRequestEdit  
 Avertit tous connectés [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) (sur chaque point de connexion de l’objet) des interfaces dont la propriété de l’objet spécifié est sur le point de changer.  
  
```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>Paramètres  
 *pUnk*  
 [in] Pointeur vers le **IUnknown** de l’objet qui envoie la notification.  
  
 *dispID*  
 [in] Identificateur de la propriété va être modifiée.  
  
### <a name="return-value"></a>Valeur de retour  
 Un de la norme `HRESULT` valeurs.  
  
### <a name="remarks"></a>Notes  
 Cette fonction peut appeler, même si votre contrôle ne prend pas en charge les points de connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
