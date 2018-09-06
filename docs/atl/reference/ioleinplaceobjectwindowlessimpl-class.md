---
title: Ioleinplaceobjectwindowlessimpl, classe | Microsoft Docs
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
ms.openlocfilehash: 4fd6c2ddfaef8c298696ea33537ea7bfd754330f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762607"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>Ioleinplaceobjectwindowlessimpl, classe

Cette classe implémente `IUnknown` et fournit des méthodes qui permettent un contrôle sans fenêtre pour recevoir des messages de fenêtre et participer aux opérations de glisser-déplacer.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>Paramètres

*T*  
Votre classe, dérivée de `IOleInPlaceObjectWindowlessImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Permet à l’aide contextuelle. L’implémentation de ATL retourne E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Fournit le `IDropTarget` interface pour un objet sur place sans fenêtre et actif qui prend en charge glisser -déplacer. L’implémentation de ATL retourne E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Obtient un handle de fenêtre.|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Désactive un contrôle sur place actif.|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Distribue un message à partir du conteneur à un contrôle sans fenêtre qui est actif en place.|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Réactive un contrôle précédemment désactivé. L’implémentation de ATL retourne E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Indique quelle partie du contrôle sur place est visible.|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Désactive et supprime l’interface utilisateur qui prend en charge l’activation sur place.|

## <a name="remarks"></a>Notes

Le [IOleInPlaceObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceobject) interface gère la réactivation la désactivation de la place les contrôles et détermine la quantité du contrôle doit être visible. Le [IOleInPlaceObjectWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) interface permet à un contrôle sans fenêtre pour recevoir des messages de fenêtre et participer aux opérations de glisser-déplacer. Classe `IOleInPlaceObjectWindowlessImpl` fournit une implémentation par défaut de `IOleInPlaceObject` et `IOleInPlaceObjectWindowless` et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.

**Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

##  <a name="contextsensitivehelp"></a>  IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

Retourne E_NOTIMPL.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Notes

Consultez [IOleWindow::ContextSensitiveHelp](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) dans le Kit de développement logiciel Windows.

##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget

Retourne E_NOTIMPL.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceObjectWindowless::GetDropTarget](/windows/desktop/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) dans le Kit de développement logiciel Windows.

##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow

Le conteneur appelle cette fonction pour obtenir le handle de fenêtre du contrôle.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Notes

Certains conteneurs ne fonctionnent pas avec un contrôle qui a été sans fenêtre, même si elle est actuellement avec fenêtres. Dans l’implémentation d’ATL, si membre de données de la classe de contrôle `m_bWasOnceWindowless` a la valeur TRUE, la fonction retourne E_FAIL. Sinon, si *phwnd* n’est pas NULL, `GetWindow` définit \* *phwnd* au membre de données de la classe de contrôle `m_hWnd` et retourne S_OK.

Consultez [IOleWindow::GetWindow](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-getwindow) dans le Kit de développement logiciel Windows.

##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

Appelé par le conteneur pour désactiver un contrôle actif sur place.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Notes

Cette méthode effectue une désactivation complète ou partielle selon l’état du contrôle. Si nécessaire, l’interface du contrôle utilisateur est désactivé, et la fenêtre du contrôle, le cas échéant, est détruite. Le conteneur est averti que le contrôle n’est plus actif en place. Le `IOleInPlaceUIWindow` interface utilisée par le conteneur pour négocier des menus et de bordure d’espace est libéré.

Consultez [IOleInPlaceObject::InPlaceDeactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) dans le Kit de développement logiciel Windows.

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

Consultez [IOleInPlaceObjectWindowless::OnWindowMessage](/windows/desktop/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) dans le Kit de développement logiciel Windows.

##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

Retourne E_NOTIMPL.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceObject::ReactivateAndUndo](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) dans le Kit de développement logiciel Windows.

##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects

Appelé par le conteneur pour informer le contrôle que sa taille et/ou la position a changé.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Notes

Met à jour le contrôle `m_rcPos` membre de données et l’affichage de contrôle. Seule la partie du contrôle qui entre en intersection avec la zone de découpage est affichée. Si l’affichage d’un contrôle a été attachée précédemment, mais la capture a été supprimée, cette fonction peut être appelée pour une vue complète du contrôle de redessiner.

Consultez [IOleInPlaceObject::SetObjectRects](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) dans le Kit de développement logiciel Windows.

##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate

Désactive et supprime l’interface utilisateur du contrôle qui prend en charge l’activation sur place.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Notes

Définit le membre de données de la classe de contrôle `m_bUIActive` sur FALSE. L’ATL implémentation de cette fonction retourne toujours S_OK.

Consultez [IOleInPlaceObject::UIDeactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)   
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
