---
title: Classe de IQuickActivateImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
dev_langs:
- C++
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b87427408483a60cf33b46a1a670095d211b3d80
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362802"
---
# <a name="iquickactivateimpl-class"></a>Classe de IQuickActivateImpl
Cette classe combine l’initialisation du contrôle de conteneurs en un seul appel.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IQuickActivateImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Récupère la taille d’affichage actuel pour un contrôle en cours d’exécution.|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Effectue une initialisation de contrôles en cours de chargement rapide.|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Indique au contrôle de la quantité d’espace affichage le conteneur est affectée à ce dernier.|  
  
## <a name="remarks"></a>Notes  
 Le [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146) interface permet d’éviter les retards lors du chargement des contrôles en combinant l’initialisation dans un seul appel de conteneurs. Le `QuickActivate` méthode permet au conteneur passer un pointeur vers un [QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630) structure qui conserve des pointeurs à toutes les interfaces que le contrôle a besoin. En retour, le contrôle passe à nouveau un pointeur vers un [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) structure qui conserve des pointeurs vers ses propres interfaces qui sont utilisées par le conteneur. Classe `IQuickActivateImpl` fournit une implémentation par défaut de **IQuickActivate** et implémente **IUnknown** en envoyant des informations pour le vidage de builds périphérique en mode débogage.  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
##  <a name="getcontentextent"></a>  IQuickActivateImpl::GetContentExtent  
 Récupère la taille d’affichage actuel pour un contrôle en cours d’exécution.  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Notes  
 La taille est pour un rendu complet du contrôle et est spécifiée en unités HIMETRIC.  
  
 Consultez [IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792) dans le Kit de développement logiciel Windows.  
  
##  <a name="quickactivate"></a>  IQuickActivateImpl::QuickActivate  
 Effectue une initialisation de contrôles en cours de chargement rapide.  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>Notes  
 La structure contient des pointeurs vers les interfaces requises par le contrôle et les valeurs de certaines propriétés ambiantes. Au moment du retour, le contrôle passe un pointeur vers un [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) structure qui contient des pointeurs sur ses propres interfaces nécessitant le conteneur et d’autres informations d’état.  
  
 Consultez [IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421) dans le Kit de développement logiciel Windows.  
  
##  <a name="setcontentextent"></a>  IQuickActivateImpl::SetContentExtent  
 Indique au contrôle de la quantité d’espace affichage le conteneur est affectée à ce dernier.  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Notes  
 La taille est spécifiée en unités HIMETRIC.  
  
 Consultez [IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
