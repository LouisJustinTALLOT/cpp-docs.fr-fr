---
title: IAxWinHostWindow, Interface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAxWinHostWindow
- ATLIFACE/ATL::IAxWinHostWindow
- ATLIFACE/ATL::AttachControl
- ATLIFACE/ATL::CreateControl
- ATLIFACE/ATL::CreateControlEx
- ATLIFACE/ATL::QueryControl
- ATLIFACE/ATL::SetExternalDispatch
- ATLIFACE/ATL::SetExternalUIHandler
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8cf8c27d118984422ec3a78f442a3f11f13e1c75
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766030"
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow, Interface

Cette interface fournit des méthodes pour manipuler un contrôle et son objet hôte.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AttachControl](#attachcontrol)|Attache un contrôle existant à l’objet hôte.|
|[CreateControl](#createcontrol)|Crée un contrôle et l’attache à l’objet hôte.|
|[CreateControlEx](#createcontrolex)|Crée un contrôle, attache à l’objet ordinateur hôte et éventuellement configure un gestionnaire d’événements.|
|[QueryControl](#querycontrol)|Retourne un pointeur d’interface pour le contrôle hébergé.|
|[SetExternalDispatch](#setexternaldispatch)|Définit l’externe `IDispatch` interface.|
|[SetExternalUIHandler](#setexternaluihandler)|Définit l’externe `IDocHostUIHandlerDispatch` interface.|

## <a name="remarks"></a>Notes

Cette interface est exposée par le contrôle ActiveX d’ATL hébergement d’objets. Appelez les méthodes sur cette interface à créer et/ou attacher un contrôle à l’objet hôte, pour obtenir une interface à partir d’un contrôle hébergé, ou pour définir la dispinterface externe ou un gestionnaire d’interface utilisateur pour une utilisation lors de l’hébergement de navigateur Web.

## <a name="requirements"></a>Configuration requise

La définition de cette interface est disponible en tant que fichier IDL ou C++, comme indiqué ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (également inclus dans ATLBase.h)|

##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl

Attache un contrôle existant (et précédemment initialisé) à l’objet hôte à l’aide de la fenêtre identifiée par *hWnd*.

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*pUnkControl*  
[in] Un pointeur vers le `IUnknown` interface du contrôle à joindre à l’objet hôte.

*hWnd*  
[in] Handle vers la fenêtre à utiliser pour l’hébergement.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl

Crée un contrôle, il initialise et héberge ce dernier dans la fenêtre identifiée par *hWnd*.

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*lpTricsData*  
[in] Chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), un ProgID, une URL ou un HTML brut (précédé **MSHTML :**).

*hWnd*  
[in] Handle vers la fenêtre à utiliser pour l’hébergement.

*pStream*  
[in] Un pointeur d’interface pour un flux contenant les données d’initialisation pour le contrôle. Peut être NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fenêtre est sous-classé par l’objet hôte exposer cette interface afin que les messages peuvent être reflétées au contrôle et d’autres fonctionnalités de conteneur fonctionneront.

Appel de cette méthode équivaut à appeler [IAxWinHostWindow::CreateControlEx](#createcontrolex).

Pour créer un contrôle ActiveX sous licence, consultez [IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx

Crée un contrôle ActiveX, il initialise et héberge ce dernier dans la fenêtre spécifiée, similaire à [IAxWinHostWindow::CreateControl](#createcontrol).

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

*lpTricsData*  
[in] Chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), un ProgID, une URL ou un HTML brut (avec le préfixe **MSHTML :**).

*hWnd*  
[in] Handle vers la fenêtre à utiliser pour l’hébergement.

*pStream*  
[in] Un pointeur d’interface pour un flux contenant les données d’initialisation pour le contrôle. Peut être NULL.

*ppUnk*  
[out] L’adresse d’un pointeur qui reçoit le `IUnknown` interface du contrôle créé. Peut être NULL.

*riidAdvise*  
[in] L’identificateur d’interface d’une interface sortante sur l’objet de relation contenant-contenu. Peut être IID_NULL.

*punkAdvise*  
[in] Un pointeur vers le `IUnknown` interface de l’objet de récepteur à être connectés au point de connexion sur l’objet de relation contenant-contenu spécifié par `iidSink`.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Contrairement à la `CreateControl` (méthode), `CreateControlEx` vous permet également de recevoir un pointeur d’interface au contrôle nouvellement créé et de configurer un récepteur d’événements pour recevoir des événements déclenchés par le contrôle.

Pour créer un contrôle ActiveX sous licence, consultez [IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).

##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl

Retourne le pointeur d’interface spécifié fourni par le contrôle hébergé.

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*  
[in] L’ID d’une interface sur le contrôle demandé.

*ppvObject*  
[out] L’adresse d’un pointeur qui reçoit l’interface spécifiée du contrôle créé.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch

Définit la dispinterface externe, qui est disponible pour les contrôles contenus par le biais du [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) (méthode).

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*argument pDisp*  
[in] Un pointeur vers un `IDispatch` interface.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler

Appelez cette fonction pour définir l’externe [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) interface pour le `CAxWindow` objet.

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*argument pDisp*  
[in] Un pointeur vers un `IDocHostUIHandlerDispatch` interface.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction est utilisée par les contrôles (par exemple, le contrôle de navigateur Web) qui interroge le site de l’hôte pour le `IDocHostUIHandlerDispatch` interface.

## <a name="see-also"></a>Voir aussi

[IAxWinAmbientDispatch, Interface](../../atl/reference/iaxwinambientdispatch-interface.md)   
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)

