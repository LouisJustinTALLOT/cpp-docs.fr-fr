---
title: IAxWinHostWindow Interface
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
ms.openlocfilehash: ebecc611660a788ce59bb11beb95bd60eacaf01b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330000"
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow Interface

Cette interface fournit des méthodes pour manipuler un contrôle et son objet hôte.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AttachControl (en)](#attachcontrol)|Attache un contrôle existant à l’objet hôte.|
|[CreateControl](#createcontrol)|Crée un contrôle et le fixe à l’objet hôte.|
|[CreateControlEx](#createcontrolex)|Crée un contrôle, l’attache à l’objet hôte et installe en option un gestionnaire d’événements.|
|[QueryControl](#querycontrol)|Retourne un pointeur d’interface au contrôle hébergé.|
|[SetExternalDispatch SetExternalDispatch SetExternalDispatch SetEx](#setexternaldispatch)|Définit l’interface externe. `IDispatch`|
|[SetExternalUIHandler SetExternalUIHandler SetExternalUIHandler SetEx](#setexternaluihandler)|Définit l’interface externe. `IDocHostUIHandlerDispatch`|

## <a name="remarks"></a>Notes

Cette interface est exposée par les objets d’hébergement de contrôle ActiveX d’ATL. Appelez les méthodes de cette interface pour créer et/ou attacher un contrôle à l’objet hôte, pour obtenir une interface à partir d’un contrôle hébergé, ou pour définir le dispinterface externe ou le gestionnaire d’interface utilisateur pour une utilisation lors de l’hébergement du navigateur Web.

## <a name="requirements"></a>Spécifications

La définition de cette interface est disponible sous forme d’IDL ou de C, comme indiqué ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (également inclus dans ATLBase.h)|

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHostWindow::AttachControl

Attache un contrôle existant (et précédemment initialisé) à l’objet hôte à l’aide de la fenêtre identifiée par *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*pUnkControl (en)*<br/>
[dans] Un pointeur `IUnknown` à l’interface du contrôle à attacher à l’objet hôte.

*hWnd*<br/>
[dans] Une poignée à la fenêtre à utiliser pour l’hébergement.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHostWindow::CreateControl

Crée un contrôle, l’initialise, et l’héberge dans la fenêtre identifiée par *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*lpTricsData (en)*<br/>
[dans] Une chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), ProgID, URL, ou HTML brut (préfixé par **MSHTML:**).

*hWnd*<br/>
[dans] Une poignée à la fenêtre à utiliser pour l’hébergement.

*pStream*<br/>
[dans] Un pointeur d’interface pour un flux contenant des données d’initialisation pour le contrôle. Sa valeur peut être NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fenêtre sera sous-classée par l’objet hôte exposant cette interface afin que les messages puissent être réfléchis au contrôle et que d’autres fonctionnalités de conteneur fonctionneront.

Appeler cette méthode équivaut à appeler [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Pour créer un contrôle ActiveX sous licence, voir [IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

Crée un contrôle ActiveX, l’initialise, et l’héberge dans la fenêtre spécifiée, similaire à [IAxWinHostWindow::CreateControl](#createcontrol).

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

*lpTricsData (en)*<br/>
[dans] Une chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), ProgID, URL, ou HTML brut (préfixé avec **MSHTML:**).

*hWnd*<br/>
[dans] Une poignée à la fenêtre à utiliser pour l’hébergement.

*pStream*<br/>
[dans] Un pointeur d’interface pour un flux contenant des données d’initialisation pour le contrôle. Sa valeur peut être NULL.

*ppUnk*<br/>
[out] L’adresse d’un pointeur qui recevra l’interface `IUnknown` du contrôle créé. Sa valeur peut être NULL.

*riidAdvise*<br/>
[dans] L’identifiant d’interface d’une interface sortante sur l’objet contenu. Peut être IID_NULL.

*punkAdvise (en)*<br/>
[dans] Un pointeur `IUnknown` à l’interface de l’objet de l’évier `iidSink`à connecter au point de connexion sur l’objet contenu spécifié par .

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Contrairement `CreateControl` à `CreateControlEx` la méthode, vous permet également de recevoir un pointeur d’interface pour le contrôle nouvellement créé et mettre en place un évier d’événement pour recevoir des événements tirés par le contrôle.

Pour créer un contrôle ActiveX sous licence, voir [IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHostWindow::QueryControl

Retourne le pointeur d’interface spécifié fourni par le contrôle hébergé.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
[dans] L’ID d’une interface sur le contrôle demandé.

*ppvObject*<br/>
[out] L’adresse d’un pointeur qui recevra l’interface spécifiée du contrôle créé.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

Définit le dispinterface externe, qui est disponible pour les contrôles contenus par le [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) méthode.

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
[dans] Un pointeur `IDispatch` à une interface.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler

Appelez cette fonction pour définir l’interface externe [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) pour l’objet. `CAxWindow`

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
[dans] Un pointeur `IDocHostUIHandlerDispatch` à une interface.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction est utilisée par les contrôles (tels que le contrôle du `IDocHostUIHandlerDispatch` navigateur Web) qui interrogent le site de l’hôte pour l’interface.

## <a name="see-also"></a>Voir aussi

[IAxWinAmbientDispatch Interface](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
