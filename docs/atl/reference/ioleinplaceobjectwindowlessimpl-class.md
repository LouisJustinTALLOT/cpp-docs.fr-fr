---
title: Classe IOleInPlaceObjectWindowlessImpl
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
ms.openlocfilehash: b0438692161f38445eb7cbed54edcc8a0ba8c0d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326577"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>Classe IOleInPlaceObjectWindowlessImpl

Cette classe `IUnknown` met en œuvre et fournit des méthodes qui permettent à un contrôle sans fenêtre de recevoir des messages de fenêtre et de participer à des opérations de drag-and-drop.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IOleInPlaceObjectWindowlessImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Permet une aide sensible au contexte. La mise en œuvre d’ATL E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Fournit `IDropTarget` l’interface pour un objet actif et sans fenêtre qui prend en charge la traînée et la chute. La mise en œuvre d’ATL E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Obtient un handle de fenêtre.|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate IOle](#inplacedeactivate)|Désactiver un contrôle actif sur place.|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Envoie un message du conteneur à un contrôle sans fenêtre qui est actif sur place.|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Réactive un contrôle précédemment désactivé. La mise en œuvre d’ATL E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Indique quelle partie du contrôle sur place est visible.|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate IOleInPlaceObjectWindowlessImpl::UIDeactivate IOleInPlaceObjectWindowlessImpl::UIDeactivate IOle](#uideactivate)|Désactiver et supprimer l’interface utilisateur qui prend en charge l’activation sur place.|

## <a name="remarks"></a>Notes

[L’interface IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) gère la réactivation et la désactivation des contrôles sur place et détermine la quantité de contrôle visible. [L’interface IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) permet à un contrôle sans fenêtre de recevoir des messages de fenêtre et de participer à des opérations de drag-and-drop. La `IOleInPlaceObjectWindowlessImpl` classe fournit `IOleInPlaceObject` une `IOleInPlaceObjectWindowless` mise `IUnknown` en œuvre par défaut et implémente en envoyant des informations à l’appareil de décharge dans les versions de débogé.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="ioleinplaceobjectwindowlessimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

Retourne E_NOTIMPL.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Notes

Voir [IOleWindow::ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) dans le Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplgetdroptarget"></a><a name="getdroptarget"></a>IOleInPlaceObjectWindowlessImpl::GetDropTarget

Retourne E_NOTIMPL.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Notes

Voir [IOleInPlaceObjectWindowless::GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) in the Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplgetwindow"></a><a name="getwindow"></a>IOleInPlaceObjectWindowlessImpl::GetWindow

Le conteneur appelle cette fonction pour obtenir la poignée de fenêtre du contrôle.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Notes

Certains conteneurs ne fonctionneront pas avec un contrôle qui a été sans fenêtre, même s’il est actuellement mis en fenêtre. Dans la mise en œuvre d’ATL, si le membre `m_bWasOnceWindowless` des données de la classe de contrôle est VRAI, la fonction revient E_FAIL. Sinon, si *le phwnd n’est* `GetWindow` pas NULL, fixe \* le *phwnd* au membre `m_hWnd` des données de la classe de contrôle et renvoie S_OK.

Voir [IOleWindow::GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) dans le Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplinplacedeactivate"></a><a name="inplacedeactivate"></a>IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate IOle

Appelé par le conteneur pour désactiver un contrôle actif sur place.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Notes

Cette méthode effectue une désactivation complète ou partielle en fonction de l’état du contrôle. Si nécessaire, l’interface utilisateur du contrôle est désactivée, et la fenêtre du contrôle, le cas échéant, est détruite. Le conteneur est averti que le contrôle n’est plus actif en place. L’interface `IOleInPlaceUIWindow` utilisée par le conteneur pour négocier les menus et l’espace frontalier est libérée.

Voir [IOleInPlaceObject:InPlaceDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) in the Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplonwindowmessage"></a><a name="onwindowmessage"></a>IOleInPlaceObjectWindowlessImpl::OnWindowMessage IOleInPlaceObjectWindowlessImpl::OnWindowMessage

Envoie un message d’un conteneur à un contrôle sans fenêtre qui est actif sur place.

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>Notes

Voir [IOleInPlaceObjectWindowless::OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) in the Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplreactivateandundo"></a><a name="reactivateandundo"></a>IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

Retourne E_NOTIMPL.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Notes

Voir [IOleInPlaceObject:ReactivateAndUndo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) dans le Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplsetobjectrects"></a><a name="setobjectrects"></a>IOleInPlaceObjectWindowlessImpl::SetObjectRects

Appelé par le conteneur pour informer le contrôle que sa taille et / ou la position a changé.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Notes

Mise à jour `m_rcPos` du membre des données du contrôle et de l’affichage de contrôle. Seule la partie du contrôle qui croise la région du clip s’affiche. Si l’affichage d’un contrôle a déjà été coupé mais que la coupure a été supprimée, cette fonction peut être appelée pour redessiner une vue complète du contrôle.

Voir [IOleInPlaceObject:SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) in the Windows SDK.

## <a name="ioleinplaceobjectwindowlessimpluideactivate"></a><a name="uideactivate"></a>IOleInPlaceObjectWindowlessImpl::UIDeactivate IOleInPlaceObjectWindowlessImpl::UIDeactivate IOleInPlaceObjectWindowlessImpl::UIDeactivate IOle

Désactiver et supprimer l’interface utilisateur du contrôle qui prend en charge l’activation sur place.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Notes

Définit le membre `m_bUIActive` des données de la classe de contrôle à FALSE. La mise en œuvre ATL de cette fonction revient toujours S_OK.

Voir [IOleInPlaceObject:UIDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[Classe CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
