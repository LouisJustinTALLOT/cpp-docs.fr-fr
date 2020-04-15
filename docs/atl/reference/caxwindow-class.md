---
title: Classe CAxWindow
ms.date: 11/04/2016
f1_keywords:
- CAxWindow
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::AttachControl
- ATLWIN/ATL::CreateControl
- ATLWIN/ATL::CreateControlEx
- ATLWIN/ATL::GetWndClassName
- ATLWIN/ATL::QueryControl
- ATLWIN/ATL::QueryHost
- ATLWIN/ATL::SetExternalDispatch
- ATLWIN/ATL::SetExternalUIHandler
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
ms.openlocfilehash: 6f5629370bc1f821dac0a08cc76b5df1450f7a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318719"
---
# <a name="caxwindow-class"></a>Classe CAxWindow

Cette classe fournit des méthodes pour manipuler une fenêtre hébergeant un contrôle ActiveX.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAxWindow : public CWindow
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AttachControl (en)](#attachcontrol)|Attache un contrôle ActiveX `CAxWindow` existant à l’objet.|
|[CAxWindow](#caxwindow)|Construit un objet `CAxWindow`.|
|[CreateControl](#createcontrol)|Crée un contrôle ActiveX, l’initialise et `CAxWindow` l’héberge dans la fenêtre.|
|[CreateControlEx](#createcontrolex)|Crée un contrôle ActiveX et récupère un pointeur d’interface (ou pointeurs) du contrôle.|
|[GetWndClassName (en)](#getwndclassname)|(Statique) Récupère le nom de classe prédéfinie de l’objet. `CAxWindow`|
|[QueryControl](#querycontrol)|Récupère le `IUnknown` contrôle ActiveX hébergé.|
|[RequêteHost](#queryhost)|Récupère le `IUnknown` pointeur `CAxWindow` de l’objet.|
|[SetExternalDispatch SetExternalDispatch SetExternalDispatch SetEx](#setexternaldispatch)|Définit l’interface de `CAxWindow` répartition externe utilisée par l’objet.|
|[SetExternalUIHandler SetExternalUIHandler SetExternalUIHandler SetEx](#setexternaluihandler)|Définit l’interface `IDocHostUIHandler` externe `CAxWindow` utilisée par l’objet.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur](#operator_eq)|Assigne un HWND `CAxWindow` à un objet existant.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX. L’hébergement est fourni par **"AtlAxWin80"**, qui est enveloppé par `CAxWindow`.

La `CAxWindow` classe est mise en `CAxWindowT` œuvre comme une spécialisation de la classe. Cette spécialisation est déclarée comme :

`typedef CAxWindowT<CWindow> CAxWindow;`

Si vous avez besoin de changer `CAxWindowT` la classe de base, vous pouvez utiliser et spécifier la nouvelle classe de base comme argument de modèle.

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="caxwindowattachcontrol"></a><a name="attachcontrol"></a>CAxWindow::AttachControl

Crée un nouvel objet hôte si l’on n’est pas déjà présent et attache le contrôle spécifié à l’hôte.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
[dans] Un pointeur `IUnknown` au contrôle.

*ppUnkContainer*<br/>
[out] Un pointeur `IUnknown` à l’hôte (l’objet). `AxWin`

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’objet de commande attaché doit `AttachControl`être correctement initialisé avant d’appeler .

## <a name="caxwindowcaxwindow"></a><a name="caxwindow"></a>CAxWindow::CAxWindow

Construit un `CAxWindow` objet à l’aide d’une poignée d’objet de fenêtre existante.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Une poignée à un objet de fenêtre existant.

## <a name="caxwindowcreatecontrol"></a><a name="createcontrol"></a>CAxWindow::CreateControl

Crée un contrôle ActiveX, puis initialise et héberge ce dernier dans la fenêtre spécifiée.

```
HRESULT CreateControl(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);

HRESULT CreateControl(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une chaîne pour créer le contrôle. Doit être formaté de l’une des façons suivantes :

- Un ProgID tel que`"MSCAL.Calendar.7"`

- Un CLSID tel que`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Une URL telle que`"<https://www.microsoft.com>"`

- Une référence à un document actif tel que`"file://\\\Documents\MyDoc.doc"`

- Un fragment de HTML tel que`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`doit précéder le fragment HTML afin qu’il soit désigné comme étant un flux MSHTML. Seuls les ProgID et CLSID sont pris en charge sur les plateformes Windows Mobile. Windows CE plates-formes intégrées, autres que Windows Mobile avec la prise en charge de CE IE prendre en charge tous les types, y compris ProgID, CLSID, URL, référence au document actif, et fragment de HTML.

*pStream*<br/>
[dans] Un pointeur à un flux qui est utilisé pour initialiser les propriétés du contrôle. Sa valeur peut être NULL.

*ppUnkContainer*<br/>
[out] L’adresse d’un pointeur qui recevra le `IUnknown` du conteneur. Sa valeur peut être NULL.

*dwResID dwResID*<br/>
L’ID de ressource d’une ressource HTML. Le contrôle WebBrowser sera créé et chargé avec la ressource spécifiée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si la deuxième version de cette méthode est utilisée, un contrôle HTML est créé et lié à la ressource identifiée par *dwResID*.

Cette méthode vous donne le même résultat que l’appel:

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

Voir [CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) pour créer, initialiser et héberger un contrôle ActiveX sous licence.

### <a name="example"></a>Exemple

Voir [Hosting ActiveX Controls À l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon qui utilise `CreateControl`.

## <a name="caxwindowcreatecontrolex"></a><a name="createcontrolex"></a>CAxWindow::CreateControlEx

Crée un contrôle ActiveX, puis initialise et héberge ce dernier dans la fenêtre spécifiée.

```
HRESULT CreateControlEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);

HRESULT CreateControlEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une chaîne pour créer le contrôle. Doit être formaté de l’une des façons suivantes :

- Un ProgID tel que`"MSCAL.Calendar.7"`

- Un CLSID tel que`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Une URL telle que`"<https://www.microsoft.com>"`

- Une référence à un document actif tel que`"file://\\\Documents\MyDoc.doc"`

- Un fragment de HTML tel que`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`doit précéder le fragment HTML afin qu’il soit désigné comme étant un flux MSHTML. Seuls les ProgID et CLSID sont pris en charge sur les plateformes Windows Mobile. Windows CE plates-formes intégrées, autres que Windows Mobile avec la prise en charge de CE IE prendre en charge tous les types, y compris ProgID, CLSID, URL, référence au document actif, et fragment de HTML.

*pStream*<br/>
[dans] Un pointeur à un flux qui est utilisé pour initialiser les propriétés du contrôle. Sa valeur peut être NULL.

*ppUnkContainer*<br/>
[out] L’adresse d’un pointeur qui recevra le `IUnknown` du conteneur. Sa valeur peut être NULL.

*ppUnkControl*<br/>
[out] L’adresse d’un pointeur qui recevra le `IUnknown` du contrôle. Sa valeur peut être NULL.

*iidSink iidSink*<br/>
[dans] L’identifiant d’interface d’une interface sortante sur l’objet contenu. Peut être IID_NULL.

*punkSink punkSink*<br/>
[dans] Un pointeur `IUnknown` à l’interface de l’objet de l’évier à connecter au point de connexion sur l’objet contenu spécifié par *iidSink*.

*dwResID dwResID*<br/>
[dans] L’ID de ressource d’une ressource HTML. Le contrôle WebBrowser sera créé et chargé avec la ressource spécifiée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode est similaire à [CAxWindow::CreateControl](#createcontrol) `CreateControlEx` , mais contrairement à cette méthode, vous permet également de recevoir un pointeur d’interface pour le contrôle nouvellement créé et mettre en place un évier d’événement pour recevoir des événements tirés par le contrôle.

Voir [CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) pour créer, initialiser et héberger un contrôle ActiveX sous licence.

### <a name="example"></a>Exemple

Voir [Hosting ActiveX Controls À l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon qui utilise `CreateControlEx`.

## <a name="caxwindowgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow::GetWndClassName

Récupère le nom de la classe de fenêtre.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à une chaîne contenant le nom de la classe de fenêtre qui peut héberger des commandes ActiveX non autorisées.

## <a name="caxwindowoperator-"></a><a name="operator_eq"></a>CAxWindow::opérateur

Assigne un HWND `CAxWindow` à un objet existant.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Une poignée à une fenêtre existante.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à l'objet `CAxWindow` actif.

## <a name="caxwindowquerycontrol"></a><a name="querycontrol"></a>CAxWindow::QueryControl

Récupère l’interface spécifiée du contrôle hébergé.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Spécifie l’IID de l’interface du contrôle.

*ppUnk*<br/>
[out] Un pointeur à l’interface du contrôle. Dans la version modèle de cette méthode, il n’est pas nécessaire d’obtenir un ID de référence tant qu’une interface dactylographique avec un UUID associé est adoptée.

*Q*<br/>
[dans] L’interface qui est demandée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="caxwindowqueryhost"></a><a name="queryhost"></a>CAxWindow::QueryHost

Retourne l’interface spécifiée de l’hôte.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Spécifie l’IID de l’interface du contrôle.

*ppUnk*<br/>
[out] Un pointeur à l’interface sur l’hôte. Dans la version modèle de cette méthode, il n’est pas nécessaire d’obtenir un ID de référence tant qu’une interface dactylographique avec un UUID associé est adoptée.

*Q*<br/>
[dans] L’interface qui est demandée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’interface de l’hôte permet d’accéder à la fonctionnalité `AxWin`sous-jacente du code d’hébergement de fenêtre, implémenté par .

## <a name="caxwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch

Définit l’interface de `CAxWindow` répartition externe pour l’objet.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
[dans] Un pointeur `IDispatch` à une interface.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="caxwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler

Définit l’interface [externe IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) pour l’objet. `CAxWindow`

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Paramètres

*pUIHandler (en)*<br/>
[dans] Un pointeur `IDocHostUIHandlerDispatch` à une interface.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’interface externe `IDocHostUIHandlerDispatch` est utilisée par des contrôles qui `IDocHostUIHandlerDispatch` interrogent le site de l’hôte pour l’interface. Le contrôle WebBrowser est un contrôle qui fait cela.

## <a name="see-also"></a>Voir aussi

[Échantillon ATLCON](../../overview/visual-cpp-samples.md)<br/>
[Classe CWindow](../../atl/reference/cwindow-class.md)<br/>
[Notions de base des contrôles composites](../../atl/atl-composite-control-fundamentals.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[FAQ sur la relation contenant-contenu des contrôles](../../atl/atl-control-containment-faq.md)
