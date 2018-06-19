---
title: Classe de IPointerInactiveImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
dev_langs:
- C++
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c28eb8d6db520bd1c2d5de5642098263508c0f6b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360330"
---
# <a name="ipointerinactiveimpl-class"></a>Classe de IPointerInactiveImpl
Cette classe implémente **IUnknown** et [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) méthodes d’interface.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class IPointerInactiveImpl
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IPointerInactiveImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Récupère la stratégie d’activation en cours de l’objet. L’implémentation ATL retourne **E_NOTIMPL**.|  
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Notifie l’objet que le pointeur de la souris a été déplacé, qui indique l’objet peut déclencher des événements de souris. L’implémentation ATL retourne **E_NOTIMPL**.|  
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Définit le pointeur de la souris pour l’objet inactif. L’implémentation ATL retourne **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Notes  
 Un objet inactif est celle qui est simplement chargé ou en cours d’exécution. Contrairement à un objet actif, un objet inactif ne peut pas recevoir les messages de clavier et souris Windows. Par conséquent, les objets inactifs utilisent moins de ressources et sont généralement plus efficaces.  
  
 Le [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) interface permet à un objet prendre en charge un niveau minimal d’interaction de la souris tout en restant inactif. Cette fonctionnalité est particulièrement utile pour les contrôles.  
  
 Classe `IPointerInactiveImpl` implémente la `IPointerInactive` méthodes par un retour **E_NOTIMPL**. Toutefois, il implémente **IUnknown** en envoyant des informations pour le vidage de builds périphérique en mode débogage.  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IPointerInactive`  
  
 `IPointerInactiveImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
##  <a name="getactivationpolicy"></a>  IPointerInactiveImpl::GetActivationPolicy  
 Récupère la stratégie d’activation en cours de l’objet.  
  
```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **E_NOTIMPL**.  
  
### <a name="remarks"></a>Notes  
 Consultez [IPointerInactive::GetActivationPolicy](http://msdn.microsoft.com/library/windows/desktop/ms692470) dans le Kit de développement logiciel Windows.  
  
##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove  
 Notifie l’objet que le pointeur de la souris a été déplacé, qui indique l’objet peut déclencher des événements de souris.  
  
```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **E_NOTIMPL**.  
  
### <a name="remarks"></a>Notes  
 Consultez [IPointerInactive::OnInactiveMouseMove](http://msdn.microsoft.com/library/windows/desktop/ms693374) dans le Kit de développement logiciel Windows.  
  
##  <a name="oninactivesetcursor"></a>  IPointerInactiveImpl::OnInactiveSetCursor  
 Définit le pointeur de la souris pour l’objet inactif.  
  
```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **E_NOTIMPL**.  
  
### <a name="remarks"></a>Notes  
 Consultez [IPointerInactive::OnInactiveSetCursor](http://msdn.microsoft.com/library/windows/desktop/ms694336) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
