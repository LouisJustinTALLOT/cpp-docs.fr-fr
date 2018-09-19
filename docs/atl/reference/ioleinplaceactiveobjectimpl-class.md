---
title: Ioleinplaceactiveobjectimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::EnableModeless
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnDocWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnFrameWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ResizeBorder
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::TranslateAccelerator
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e74df913b22684a61ab4f45ade561e55db18544
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044507"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>Ioleinplaceactiveobjectimpl, classe

Cette classe fournit des méthodes d’assistance de communication entre un contrôle sur place et de son conteneur.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IOleInPlaceActiveObjectImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Permet à l’aide contextuelle. L’implémentation de ATL retourne E_NOTIMPL.|
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Permet de boîtes de dialogue non modale. L’implémentation de ATL retourne S_OK.|
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Obtient un handle de fenêtre.|
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Avertit le contrôle lors de la fenêtre de document du conteneur est activée ou désactivée. L’implémentation de ATL retourne S_OK.|
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Avertit le contrôle lors de la fenêtre de frame de niveau supérieur du conteneur est activée ou désactivée. Retourne l’implémentation de ATL|
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Indique au contrôle qu'il doit redimensionner ses bordures. L’implémentation de ATL retourne S_OK.|
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Traite les messages de touche d’accès rapide de menu à partir du conteneur. L’implémentation de ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

Le [IOleInPlaceActiveObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceactiveobject) interface facilite la communication entre un contrôle sur place et de son conteneur ; par exemple, communiquer l’état actif du contrôle et le conteneur et à informer le contrôle qu’il doit redimensionner lui-même. Classe `IOleInPlaceActiveObjectImpl` fournit une implémentation par défaut de `IOleInPlaceActiveObject` et prend en charge `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.

**Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

##  <a name="contextsensitivehelp"></a>  IOleInPlaceActiveObjectImpl::ContextSensitiveHelp

Permet à l’aide contextuelle.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleWindow::ContextSensitiveHelp](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) dans le Kit de développement logiciel Windows.

##  <a name="enablemodeless"></a>  IOleInPlaceActiveObjectImpl::EnableModeless

Permet de boîtes de dialogue non modale.

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) dans le Kit de développement logiciel Windows.

##  <a name="getwindow"></a>  IOleInPlaceActiveObjectImpl::GetWindow

Le conteneur appelle cette fonction pour obtenir le handle de fenêtre du contrôle.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Notes

Certains conteneurs ne fonctionnent pas avec un contrôle qui a été sans fenêtre, même si elle est actuellement avec fenêtres. Dans l’implémentation d’ATL, si le `CComControl::m_bWasOnceWindowless` membre de données a la valeur TRUE, la fonction retourne E_FAIL. Sinon, si \* *phwnd* n’est pas NULL, `GetWindow` attribue *phwnd* au membre de données de la classe de contrôle `m_hWnd` et retourne S_OK.

Consultez [IOleWindow::GetWindow](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-getwindow) dans le Kit de développement logiciel Windows.

##  <a name="ondocwindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnDocWindowActivate

Avertit le contrôle lors de la fenêtre de document du conteneur est activée ou désactivée.

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) dans le Kit de développement logiciel Windows.

##  <a name="onframewindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnFrameWindowActivate

Avertit le contrôle lors de la fenêtre de frame de niveau supérieur du conteneur est activée ou désactivée.

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate) dans le Kit de développement logiciel Windows.

##  <a name="resizeborder"></a>  IOleInPlaceActiveObjectImpl::ResizeBorder

Indique au contrôle qu'il doit redimensionner ses bordures.

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceActiveObject::ResizeBorder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) dans le Kit de développement logiciel Windows.

##  <a name="translateaccelerator"></a>  IOleInPlaceActiveObjectImpl::TranslateAccelerator

Traite les messages de touche d’accès rapide de menu à partir du conteneur.

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>Valeur de retour

Cette méthode prend en charge les valeurs de retour suivantes :

S_OK si le message a été converti avec succès.

S_FALSE si le message n’était pas traduit.

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceActiveObject::TranslateAccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de contrôles ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
