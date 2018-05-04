---
title: Classe de IOleInPlaceObjectWindowlessImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetDropTarget
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::OnWindowMessage
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::SetObjectRects
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::UIDeactivate
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5616258405eb8346132d32b8f7fd71d0b4794d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>Classe de IOleInPlaceObjectWindowlessImpl
Cette classe implémente **IUnknown** et fournit des méthodes qui permettent un contrôle sans fenêtre pour recevoir des messages de fenêtre et participer aux opérations de glisser-déplacer.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IOleInPlaceObjectWindowlessImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Permet à l’aide contextuelle. L’implémentation ATL retourne **E_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Fournit la `IDropTarget` interface pour un objet sur place actif, sans fenêtre qui prend en charge glisser -déplacer. L’implémentation ATL retourne **E_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Obtient un handle de fenêtre.|  
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Désactive un contrôle sur place actif.|  
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Distribue un message à partir du conteneur à un contrôle sans fenêtre qui est actif en place.|  
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Réactive un contrôle précédemment désactivé. L’implémentation ATL retourne **E_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Indique quelle partie du contrôle sur place est visible.|  
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Désactive et supprime l’interface utilisateur qui prend en charge l’activation sur place.|  
  
## <a name="remarks"></a>Notes  
 Le [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) interface gère la réactivation la désactivation de la place les contrôles et détermine la quantité du contrôle doit être visible. Le [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) interface permet à un contrôle sans fenêtre pour recevoir des messages de fenêtre et participer aux opérations de glisser-déplacer. Classe `IOleInPlaceObjectWindowlessImpl` fournit une implémentation par défaut de `IOleInPlaceObject` et `IOleInPlaceObjectWindowless` et implémente **IUnknown** en envoyant des informations pour le vidage de builds périphérique en mode débogage.  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IOleInPlaceObjectWindowless`  
  
 `IOleInPlaceObjectWindowlessImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>  IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp  
 Retourne **E_NOTIMPL**.  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) dans le Kit de développement logiciel Windows.  
  
##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget  
 Retourne **E_NOTIMPL**.  
  
```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleInPlaceObjectWindowless::GetDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms678535) dans le Kit de développement logiciel Windows.  
  
##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow  
 Le conteneur appelle cette fonction pour obtenir le handle de fenêtre du contrôle.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Notes  
 Certains conteneurs ne fonctionnera pas avec un contrôle qui a été sans fenêtre, même si elle est actuellement fenêtrée. Dans l’implémentation de d’ATL, si membre de données de la classe du contrôle `m_bWasOnceWindowless` est **TRUE**, la fonction retourne **E_FAIL**. Sinon, si *phwnd* n’est pas **NULL**, `GetWindow` définit \* *phwnd* au membre de données de la classe du contrôle `m_hWnd` et retourne `S_OK`.  
  
 Consultez [IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) dans le Kit de développement logiciel Windows.  
  
##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate  
 Appelée par le conteneur pour désactiver un contrôle actif sur place.  
  
```
HRESULT InPlaceDeactivate(HWND* phwnd);
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode effectue une désactivation complète ou partielle selon l’état du contrôle. Si nécessaire, l’interface utilisateur du contrôle est désactivé, et la fenêtre de contrôle, le cas échéant, est détruite. Le conteneur est averti que le contrôle n’est plus actif en place. Le **IOleInPlaceUIWindow** interface utilisée par le conteneur pour négocier des menus et de la bordure d’espace est libérée.  
  
 Consultez [IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700) dans le Kit de développement logiciel Windows.  
  
##  <a name="onwindowmessage"></a>  IOleInPlaceObjectWindowlessImpl::OnWindowMessage  
 Distribue un message à partir d’un conteneur à un contrôle sans fenêtre qui est actif en place.  
  
```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleInPlaceObjectWindowless::OnWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms693783) dans le Kit de développement logiciel Windows.  
  
##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo  
 Retourne **E_NOTIMPL**.  
  
```
HRESULT ReactivateAndUndo();
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleInPlaceObject::ReactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms691372) dans le Kit de développement logiciel Windows.  
  
##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects  
 Appelée par le conteneur pour informer le contrôle que sa taille et/ou la position a changé.  
  
```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```  
  
### <a name="remarks"></a>Notes  
 Met à jour du contrôle `m_rcPos` membre de données et l’affichage de contrôle. Seule la partie du contrôle qui entre en intersection avec la zone de découpage est affichée. Si l’affichage d’un contrôle a été attachée précédemment, mais la capture a été supprimée, cette fonction peut être appelée pour redessiner une vue complète du contrôle.  
  
 Consultez [IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767) dans le Kit de développement logiciel Windows.  
  
##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate  
 Désactive et supprime l’interface utilisateur du contrôle qui prend en charge l’activation sur place.  
  
```
HRESULT UIDeactivate();
```  
  
### <a name="remarks"></a>Notes  
 Définit le membre de données de la classe du contrôle `m_bUIActive` à **FALSE**. L’implémentation ATL de cette fonction toujours renvoie `S_OK`.  
  
 Consultez [IOleInPlaceObject::UIDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms693348) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
