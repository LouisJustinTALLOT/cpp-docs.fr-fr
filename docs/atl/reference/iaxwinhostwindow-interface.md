---
title: Interface IAxWinHostWindow
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindow
- ATLIFACE/ATL::IAxWinHostWindow
- ATLIFACE/ATL::AttachControl
- ATLIFACE/ATL::CreateControl
- ATLIFACE/ATL::CreateControlEx
- ATLIFACE/ATL::QueryControl
- ATLIFACE/ATL::SetExternalDispatch
- ATLIFACE/ATL::SetExternalUIHandler
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
ms.openlocfilehash: 44681b94e0bd1dfd757ebfa19f83074785dd95f5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833372"
---
# <a name="iaxwinhostwindow-interface"></a>Interface IAxWinHostWindow

Cette interface fournit des méthodes pour manipuler un contrôle et son objet hôte.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Nom|Description|
|-|-|
|[AttachControl](#attachcontrol)|Attache un contrôle existant à l’objet hôte.|
|[CreateControl](#createcontrol)|Crée un contrôle et l’attache à l’objet hôte.|
|[CreateControlEx](#createcontrolex)|Crée un contrôle, l’attache à l’objet hôte et configure éventuellement un gestionnaire d’événements.|
|[QueryControl](#querycontrol)|Retourne un pointeur d’interface vers le contrôle hébergé.|
|[SetExternalDispatch](#setexternaldispatch)|Définit l' `IDispatch` interface externe.|
|[SetExternalUIHandler](#setexternaluihandler)|Définit l' `IDocHostUIHandlerDispatch` interface externe.|

## <a name="remarks"></a>Notes

Cette interface est exposée par les objets hébergeant le contrôle ActiveX de l’ATL. Appelez les méthodes sur cette interface pour créer et/ou attacher un contrôle à l’objet hôte, pour obtenir une interface à partir d’un contrôle hébergé ou pour définir la dispinterface externe ou le gestionnaire d’interface utilisateur à utiliser lors de l’hébergement du navigateur Web.

## <a name="requirements"></a>Configuration requise

La définition de cette interface est disponible en tant que IDL ou C++, comme indiqué ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|MIDL|ATLIFace. idl|
|C++|ATLIFace. h (également inclus dans ATLBase. h)|

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a> IAxWinHostWindow::AttachControl

Joint un contrôle existant (et précédemment initialisé) à l’objet hôte à l’aide de la fenêtre identifiée par *HWND*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*pUnkControl*<br/>
dans Pointeur vers l' `IUnknown` interface du contrôle à attacher à l’objet hôte.

*hWnd*<br/>
dans Handle de la fenêtre à utiliser pour l’hébergement.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a> IAxWinHostWindow :: CreateControl

Crée un contrôle, l’initialise et l’héberge dans la fenêtre identifiée par *HWND*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*lpTricsData*<br/>
dans Chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), ProgID, URL ou HTML brut (préfixé par **MSHTML :**).

*hWnd*<br/>
dans Handle de la fenêtre à utiliser pour l’hébergement.

*pStream*<br/>
dans Pointeur d’interface pour un flux contenant des données d’initialisation pour le contrôle. Sa valeur peut être NULL.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fenêtre sera sous-classée par l’objet hôte exposant cette interface afin que les messages puissent être reflétés dans le contrôle et que d’autres fonctionnalités de conteneur fonctionnent.

L’appel de cette méthode équivaut à appeler [IAxWinHostWindow :: CreateControlEx](#createcontrolex).

Pour créer un contrôle ActiveX sous licence, consultez [IAxWinHostWindowLic :: CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a> IAxWinHostWindow::CreateControlEx

Crée un contrôle ActiveX, l’initialise et l’héberge dans la fenêtre spécifiée, similaire à [IAxWinHostWindow :: CreateControl](#createcontrol).

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>Paramètres

*lpTricsData*<br/>
dans Chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), ProgID, URL ou HTML brut (avec le préfixe **MSHTML :**).

*hWnd*<br/>
dans Handle de la fenêtre à utiliser pour l’hébergement.

*pStream*<br/>
dans Pointeur d’interface pour un flux contenant des données d’initialisation pour le contrôle. Sa valeur peut être NULL.

*ppUnk*<br/>
à Adresse d’un pointeur qui recevra l' `IUnknown` interface du contrôle créé. Sa valeur peut être NULL.

*riidAdvise*<br/>
dans Identificateur d’interface d’une interface sortante sur l’objet contenu. Peut être IID_NULL.

*punkAdvise*<br/>
dans Pointeur vers l' `IUnknown` interface de l’objet récepteur à connecter au point de connexion sur l’objet contenu spécifié par `iidSink` .

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Contrairement à la `CreateControl` méthode, `CreateControlEx` vous permet également de recevoir un pointeur d’interface vers le contrôle nouvellement créé et de configurer un récepteur d’événements pour recevoir des événements déclenchés par le contrôle.

Pour créer un contrôle ActiveX sous licence, consultez [IAxWinHostWindowLic :: CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a> IAxWinHostWindow::QueryControl

Retourne le pointeur d’interface spécifié fourni par le contrôle hébergé.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
dans ID d’une interface sur le contrôle demandé.

*ppvObject*<br/>
à Adresse d’un pointeur qui recevra l’interface spécifiée du contrôle créé.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a> IAxWinHostWindow::SetExternalDispatch

Définit la dispinterface externe, qui est disponible pour les contrôles contenus par le biais de la méthode [IDocHostUIHandlerDispatch :: GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) .

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
dans Pointeur vers une `IDispatch` interface.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a> IAxWinHostWindow::SetExternalUIHandler

Appelez cette fonction pour définir l’interface [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) externe de l' `CAxWindow` objet.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
dans Pointeur vers une `IDocHostUIHandlerDispatch` interface.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction est utilisée par les contrôles (tels que le contrôle de navigateur Web) qui interrogent le site de l’hôte pour l' `IDocHostUIHandlerDispatch` interface.

## <a name="see-also"></a>Voir aussi

[Interface IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
