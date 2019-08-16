---
title: IOleInPlaceObjectWindowlessImpl, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
ms.openlocfilehash: fdd660daae109ac2a656519131dd9869ceaeaf4e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495752"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl, classe

Cette classe implémente `IUnknown` et fournit des méthodes qui permettent à un contrôle sans fenêtre de recevoir des messages de fenêtre et de participer à des opérations de glisser-déplacer.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée `IOleInPlaceObjectWindowlessImpl`de.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Active l’aide contextuelle. L’implémentation ATL retourne E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Fournit l' `IDropTarget` interface pour un objet actif sur place, sans fenêtre, qui prend en charge le glisser-déplacer. L’implémentation ATL retourne E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Obtient un handle de fenêtre.|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Désactive un contrôle sur place actif.|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Distribue un message du conteneur à un contrôle sans fenêtre qui est actif sur place.|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Réactive un contrôle précédemment désactivé. L’implémentation ATL retourne E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Indique la partie du contrôle sur place qui est visible.|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Désactive et supprime l’interface utilisateur qui prend en charge l’activation sur place.|

## <a name="remarks"></a>Notes

L’interface [IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) gère la réactivation et la désactivation des contrôles sur place et détermine la quantité de contrôle qui doit être visible. L’interface [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) permet à un contrôle sans fenêtre de recevoir des messages de fenêtre et de participer à des opérations de glisser-déplacer. La `IOleInPlaceObjectWindowlessImpl` classe fournit une implémentation par `IOleInPlaceObject` défaut `IOleInPlaceObjectWindowless` de et et `IUnknown` implémente en envoyant des informations à l’appareil de vidage dans les versions Debug.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlctl. h

##  <a name="contextsensitivehelp"></a>  IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

Retourne E_NOTIMPL.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Notes

Consultez [IOleWindow:: ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) dans le SDK Windows.

##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget

Retourne E_NOTIMPL.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceObjectWindowless:: GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) dans le SDK Windows.

##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow

Le conteneur appelle cette fonction pour recevoir le handle de fenêtre du contrôle.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Notes

Certains conteneurs ne fonctionnent pas avec un contrôle qui n’a pas de fenêtre, même s’il est actuellement fenêtre. Dans l’implémentation d’ATL, si le membre `m_bWasOnceWindowless` de données de la classe de contrôle a la valeur true, la fonction retourne E_FAIL. Sinon, si *phwnd* n’est pas null `GetWindow` , \* définit *phwnd* sur les données membres `m_hWnd` de la classe de contrôle et retourne S_OK.

Consultez [IOleWindow:: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) dans le SDK Windows.

##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

Appelé par le conteneur pour désactiver un contrôle actif sur place.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Notes

Cette méthode effectue une désactivation complète ou partielle en fonction de l’état du contrôle. Si nécessaire, l’interface utilisateur du contrôle est désactivée et la fenêtre du contrôle, le cas échéant, est détruite. Le conteneur est informé que le contrôle n’est plus actif sur place. L' `IOleInPlaceUIWindow` interface utilisée par le conteneur pour négocier les menus et l’espace de bordure est libérée.

Consultez [IOleInPlaceObject:: InPlaceDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) dans le SDK Windows.

##  <a name="onwindowmessage"></a>  IOleInPlaceObjectWindowlessImpl::OnWindowMessage

Distribue un message d’un conteneur à un contrôle sans fenêtre qui est actif sur place.

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceObjectWindowless:: OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) dans le SDK Windows.

##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

Retourne E_NOTIMPL.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceObject:: ReactivateAndUndo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) dans le SDK Windows.

##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects

Appelé par le conteneur pour informer le contrôle que sa taille et/ou sa position a changé.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Notes

Met à jour les données membres `m_rcPos` du contrôle et l’affichage du contrôle. Seule la partie du contrôle qui croise la zone de découpage est affichée. Si l’affichage d’un contrôle a été précédemment tronqué mais que le découpage a été supprimé, cette fonction peut être appelée pour redessiner une vue complète du contrôle.

Consultez [IOleInPlaceObject:: SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) dans le SDK Windows.

##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate

Désactive et supprime l’interface utilisateur du contrôle qui prend en charge l’activation sur place.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Notes

Affecte la valeur false au membre `m_bUIActive` de données de la classe de contrôle. L’implémentation ATL de cette fonction retourne toujours S_OK.

Consultez [IOleInPlaceObject:: UIDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
