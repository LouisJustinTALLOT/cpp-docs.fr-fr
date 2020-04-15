---
title: Classe IOleInPlaceActiveObjectImpl
ms.date: 11/04/2016
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
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
ms.openlocfilehash: b39ba2845a5483444dac53d1616654e902969c77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326586"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>Classe IOleInPlaceActiveObjectImpl

Cette classe fournit des méthodes pour aider à la communication entre un contrôle sur place et son conteneur.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IOleInPlaceActiveObjectImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Permet une aide sensible au contexte. La mise en œuvre d’ATL E_NOTIMPL.|
|[IOleInPlaceActiveObjectImpl::EnableModeless IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Permet des boîtes de dialogue sans mode. La mise en œuvre d’ATL S_OK.|
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Obtient un handle de fenêtre.|
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Informe le contrôle lorsque la fenêtre de document du conteneur est activée ou désactivée. La mise en œuvre d’ATL S_OK.|
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Informe le contrôle lorsque la fenêtre de cadre de haut niveau du conteneur est activée ou désactivée. Les retours de mise en œuvre atL|
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Informe le contrôle dont il a besoin pour resize ses frontières. La mise en œuvre d’ATL S_OK.|
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator IOleInPlaceActiveObjectImpl::TranslateAccelerator IOleInPlaceActiveObjectImpl::TranslateAccelerator IOle](#translateaccelerator)|Traite les messages clés de l’accélérateur du menu à partir du conteneur. La mise en œuvre d’ATL E_NOTIMPL.|

## <a name="remarks"></a>Notes

[L’interface IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) aide la communication entre un contrôle en place et son conteneur ; par exemple, communiquer l’état actif du contrôle et du conteneur, et informer le contrôle dont il a besoin pour se resize. La `IOleInPlaceActiveObjectImpl` classe fournit `IOleInPlaceActiveObject` une `IUnknown` mise en œuvre par défaut et des supports en envoyant des informations à l’appareil de décharge dans les constructions de débogé.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="ioleinplaceactiveobjectimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlaceActiveObjectImpl::ContextSensitiveHelp

Permet une aide sensible au contexte.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Voir [IOleWindow::ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) dans le Windows SDK.

## <a name="ioleinplaceactiveobjectimplenablemodeless"></a><a name="enablemodeless"></a>IOleInPlaceActiveObjectImpl::EnableModeless IOleInPlaceActiveObjectImpl::EnableModeless

Permet des boîtes de dialogue sans mode.

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Voir [IOleInPlaceActiveObject:EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) in the Windows SDK.

## <a name="ioleinplaceactiveobjectimplgetwindow"></a><a name="getwindow"></a>IOleInPlaceActiveObjectImpl::GetWindow

Le conteneur appelle cette fonction pour obtenir la poignée de fenêtre du contrôle.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Notes

Certains conteneurs ne fonctionneront pas avec un contrôle qui a été sans fenêtre, même s’il est actuellement mis en fenêtre. Dans la mise en œuvre d’ATL, si le membre des `CComControl::m_bWasOnceWindowless` données est VRAI, la fonction revient E_FAIL. Sinon, \* si *le phwnd n’est* pas `GetWindow` NULL, attribue le `m_hWnd` *phwnd* au membre des données de la classe de contrôle et renvoie S_OK.

Voir [IOleWindow::GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) dans le Windows SDK.

## <a name="ioleinplaceactiveobjectimplondocwindowactivate"></a><a name="ondocwindowactivate"></a>IOleInPlaceActiveObjectImpl::OnDocWindowActivate

Informe le contrôle lorsque la fenêtre de document du conteneur est activée ou désactivée.

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Voir [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) in the Windows SDK.

## <a name="ioleinplaceactiveobjectimplonframewindowactivate"></a><a name="onframewindowactivate"></a>IOleInPlaceActiveObjectImpl::OnFrameWindowActivate

Informe le contrôle lorsque la fenêtre de cadre de haut niveau du conteneur est activée ou désactivée.

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Voir [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate) in the Windows SDK.

## <a name="ioleinplaceactiveobjectimplresizeborder"></a><a name="resizeborder"></a>IOleInPlaceActiveObjectImpl::ResizeBorder

Informe le contrôle dont il a besoin pour resize ses frontières.

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Voir [IOleInPlaceActiveObject:ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) dans le Windows SDK.

## <a name="ioleinplaceactiveobjectimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IOleInPlaceActiveObjectImpl::TranslateAccelerator IOleInPlaceActiveObjectImpl::TranslateAccelerator IOleInPlaceActiveObjectImpl::TranslateAccelerator IOle

Traite les messages clés de l’accélérateur du menu à partir du conteneur.

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>Valeur de retour

Cette méthode prend en charge les valeurs de retour suivantes :

S_OK si le message a été traduit avec succès.

S_FALSE si le message n’a pas été traduit.

### <a name="remarks"></a>Notes

Voir [IOleInPlaceActiveObject:TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[Classe CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX contrôle les interfaces](/windows/win32/com/activex-controls-interfaces)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
