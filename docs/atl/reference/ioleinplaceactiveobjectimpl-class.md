---
description: 'En savoir plus sur : classe IOleInPlaceActiveObjectImpl'
title: IOleInPlaceActiveObjectImpl, classe
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
ms.openlocfilehash: 02f74e462dca2aac2749b8602281f40c8eacd0eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158190"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl, classe

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
Votre classe, dérivée de `IOleInPlaceActiveObjectImpl` .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Active l’aide contextuelle. L’implémentation ATL retourne E_NOTIMPL.|
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Active les boîtes de dialogue non modales. L’implémentation ATL retourne S_OK.|
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Obtient un handle de fenêtre.|
|[IOleInPlaceActiveObjectImpl :: OnDocWindowActivate](#ondocwindowactivate)|Notifie le contrôle lorsque la fenêtre de document du conteneur est activée ou désactivée. L’implémentation ATL retourne S_OK.|
|[IOleInPlaceActiveObjectImpl :: OnFrameWindowActivate](#onframewindowactivate)|Notifie le contrôle lorsque la fenêtre frame de niveau supérieur du conteneur est activée ou désactivée. L’implémentation ATL retourne|
|[IOleInPlaceActiveObjectImpl :: ResizeBorder](#resizeborder)|Informe le contrôle dont il a besoin pour redimensionner ses bordures. L’implémentation ATL retourne S_OK.|
|[IOleInPlaceActiveObjectImpl :: TranslateAccelerator](#translateaccelerator)|Traite les messages de touche d’accès rapide de menu à partir du conteneur. L’implémentation ATL retourne E_NOTIMPL.|

## <a name="remarks"></a>Notes

L’interface [IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) aide à la communication entre un contrôle sur place et son conteneur. par exemple, en communiquant l’état actif du contrôle et du conteneur, et en informant le contrôle, il doit se redimensionner lui-même. `IOleInPlaceActiveObjectImpl`La classe fournit une implémentation par défaut de `IOleInPlaceActiveObject` et prend en charge `IUnknown` en envoyant des informations à l’appareil de vidage dans les versions Debug.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

## <a name="ioleinplaceactiveobjectimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a> IOleInPlaceActiveObjectImpl::ContextSensitiveHelp

Active l’aide contextuelle.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Consultez [IOleWindow :: ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) dans le SDK Windows.

## <a name="ioleinplaceactiveobjectimplenablemodeless"></a><a name="enablemodeless"></a> IOleInPlaceActiveObjectImpl::EnableModeless

Active les boîtes de dialogue non modales.

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceActiveObject :: EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) dans le SDK Windows.

## <a name="ioleinplaceactiveobjectimplgetwindow"></a><a name="getwindow"></a> IOleInPlaceActiveObjectImpl::GetWindow

Le conteneur appelle cette fonction pour recevoir le handle de fenêtre du contrôle.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Notes

Certains conteneurs ne fonctionnent pas avec un contrôle qui n’a pas de fenêtre, même s’il est actuellement fenêtre. Dans l’implémentation d’ATL, si le `CComControl::m_bWasOnceWindowless` membre de données a la valeur true, la fonction retourne E_FAIL. Sinon, si \* *phwnd* n’a pas la valeur null, `GetWindow` assigne *phwnd* au membre de données de la classe de contrôle `m_hWnd` et retourne S_OK.

Consultez [IOleWindow :: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) dans le SDK Windows.

## <a name="ioleinplaceactiveobjectimplondocwindowactivate"></a><a name="ondocwindowactivate"></a> IOleInPlaceActiveObjectImpl :: OnDocWindowActivate

Notifie le contrôle lorsque la fenêtre de document du conteneur est activée ou désactivée.

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceActiveObject :: OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) dans le SDK Windows.

## <a name="ioleinplaceactiveobjectimplonframewindowactivate"></a><a name="onframewindowactivate"></a> IOleInPlaceActiveObjectImpl :: OnFrameWindowActivate

Notifie le contrôle lorsque la fenêtre frame de niveau supérieur du conteneur est activée ou désactivée.

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceActiveObject :: OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate) dans le SDK Windows.

## <a name="ioleinplaceactiveobjectimplresizeborder"></a><a name="resizeborder"></a> IOleInPlaceActiveObjectImpl :: ResizeBorder

Informe le contrôle dont il a besoin pour redimensionner ses bordures.

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceActiveObject :: ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) dans le SDK Windows.

## <a name="ioleinplaceactiveobjectimpltranslateaccelerator"></a><a name="translateaccelerator"></a> IOleInPlaceActiveObjectImpl :: TranslateAccelerator

Traite les messages de touche d’accès rapide de menu à partir du conteneur.

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>Valeur renvoyée

Cette méthode prend en charge les valeurs de retour suivantes :

S_OK si le message a été correctement traduit.

S_FALSE si le message n’a pas été traduit.

### <a name="remarks"></a>Notes

Consultez [IOleInPlaceActiveObject :: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de contrôles ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
