---
title: CAxWindow, classe
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
ms.openlocfilehash: 6f5c178090a970906209e41da9298be61a61c639
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864729"
---
# <a name="caxwindow-class"></a>CAxWindow, classe

Cette classe fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAxWindow : public CWindow
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[AttachControl](#attachcontrol)|Attache un contrôle ActiveX existant à l’objet `CAxWindow`.|
|[CAxWindow](#caxwindow)|Construit un objet `CAxWindow`.|
|[CreateControl](#createcontrol)|Crée un contrôle ActiveX, l’initialise et l’héberge dans la fenêtre de `CAxWindow`.|
|[CreateControlEx](#createcontrolex)|Crée un contrôle ActiveX et récupère un pointeur d’interface (ou des pointeurs) du contrôle.|
|[GetWndClassName](#getwndclassname)|Statique Récupère le nom de classe prédéfini de l’objet `CAxWindow`.|
|[QueryControl](#querycontrol)|Récupère le `IUnknown` du contrôle ActiveX hébergé.|
|[QueryHost](#queryhost)|Récupère le pointeur `IUnknown` de l’objet `CAxWindow`.|
|[SetExternalDispatch](#setexternaldispatch)|Définit l’interface de dispatch externe utilisée par l’objet `CAxWindow`.|
|[SetExternalUIHandler](#setexternaluihandler)|Définit l’interface de `IDocHostUIHandler` externe utilisée par l’objet `CAxWindow`.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur =](#operator_eq)|Assigne un HWND à un objet `CAxWindow` existant.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX. L’hébergement est fourni par « **AtlAxWin80 »** , qui est encapsulé par `CAxWindow`.

La classe `CAxWindow` est implémentée comme une spécialisation de la classe `CAxWindowT`. Cette spécialisation est déclarée comme suit :

`typedef CAxWindowT<CWindow> CAxWindow;`

Si vous avez besoin de modifier la classe de base, vous pouvez utiliser `CAxWindowT` et spécifier la nouvelle classe de base comme argument de modèle.

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="attachcontrol"></a>CAxWindow::AttachControl

Crée un objet hôte s’il n’en existe pas déjà un et joint le contrôle spécifié à l’hôte.

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
dans Pointeur vers le `IUnknown` du contrôle.

*ppUnkContainer*<br/>
à Pointeur vers l' `IUnknown` de l’hôte (l’objet `AxWin`).

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’objet de contrôle qui est attaché doit être correctement initialisé avant l’appel de `AttachControl`.

##  <a name="caxwindow"></a>CAxWindow::CAxWindow

Construit un objet `CAxWindow` à l’aide d’un handle d’objet de fenêtre existant.

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Handle d’un objet Window existant.

##  <a name="createcontrol"></a>CAxWindow :: CreateControl

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

*lpszName*<br/>
Pointeur vers une chaîne pour créer le contrôle. Doit être mis en forme de l’une des manières suivantes :

- Un ProgID comme `"MSCAL.Calendar.7"`

- Un CLSID comme `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Une URL telle que `"<https://www.microsoft.com>"`

- Référence à un document actif tel que `"file://\\\Documents\MyDoc.doc"`

- Fragment de code HTML tel que `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` doit précéder le fragment HTML afin qu’il soit désigné comme un flux MSHTML. Seuls les ProgID et CLSID sont pris en charge dans les plateformes Windows Mobile. Windows CE plateformes incorporées, autres que Windows Mobile avec prise en charge pour CE IE, prennent en charge tous les types, notamment ProgID, CLSID, URL, référence à un document actif et fragment de code HTML.

*pStream*<br/>
dans Pointeur vers un flux utilisé pour initialiser les propriétés du contrôle. Sa valeur peut être NULL.

*ppUnkContainer*<br/>
à Adresse d’un pointeur qui recevra le `IUnknown` du conteneur. Sa valeur peut être NULL.

*dwResID*<br/>
ID de ressource d’une ressource HTML. Le contrôle WebBrowser sera créé et chargé avec la ressource spécifiée.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si la deuxième version de cette méthode est utilisée, un contrôle HTML est créé et lié à la ressource identifiée par *dwResID*.

Cette méthode donne le même résultat que l’appel de :

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

Consultez [CAxWindow2T :: CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) pour créer, initialiser et héberger un contrôle ActiveX sous licence.

### <a name="example"></a>Exemple

Consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `CreateControl`.

##  <a name="createcontrolex"></a>CAxWindow::CreateControlEx

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

*lpszName*<br/>
Pointeur vers une chaîne pour créer le contrôle. Doit être mis en forme de l’une des manières suivantes :

- Un ProgID comme `"MSCAL.Calendar.7"`

- Un CLSID comme `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Une URL telle que `"<https://www.microsoft.com>"`

- Référence à un document actif tel que `"file://\\\Documents\MyDoc.doc"`

- Fragment de code HTML tel que `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` doit précéder le fragment HTML afin qu’il soit désigné comme un flux MSHTML. Seuls les ProgID et CLSID sont pris en charge dans les plateformes Windows Mobile. Windows CE plateformes incorporées, autres que Windows Mobile avec prise en charge pour CE IE, prennent en charge tous les types, notamment ProgID, CLSID, URL, référence à un document actif et fragment de code HTML.

*pStream*<br/>
dans Pointeur vers un flux utilisé pour initialiser les propriétés du contrôle. Sa valeur peut être NULL.

*ppUnkContainer*<br/>
à Adresse d’un pointeur qui recevra le `IUnknown` du conteneur. Sa valeur peut être NULL.

*ppUnkControl*<br/>
à Adresse d’un pointeur qui recevra le `IUnknown` du contrôle. Sa valeur peut être NULL.

*iidSink*<br/>
dans Identificateur d’interface d’une interface sortante sur l’objet contenu. Peut être IID_NULL.

*punkSink*<br/>
dans Pointeur vers l’interface `IUnknown` de l’objet récepteur à connecter au point de connexion sur l’objet contenu spécifié par *iidSink*.

*dwResID*<br/>
dans ID de ressource d’une ressource HTML. Le contrôle WebBrowser sera créé et chargé avec la ressource spécifiée.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode est similaire à [CAxWindow :: CreateControl](#createcontrol), mais contrairement à cette méthode, `CreateControlEx` vous permet également de recevoir un pointeur d’interface vers le contrôle nouvellement créé et de configurer un récepteur d’événements pour recevoir des événements déclenchés par le contrôle.

Consultez [CAxWindow2T :: CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) pour créer, initialiser et héberger un contrôle ActiveX sous licence.

### <a name="example"></a>Exemple

Consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `CreateControlEx`.

##  <a name="getwndclassname"></a>CAxWindow::GetWndClassName

Récupère le nom de la classe de fenêtre.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une chaîne contenant le nom de la classe de fenêtre qui peut héberger des contrôles ActiveX sans licence.

##  <a name="operator_eq"></a>CAxWindow :: Operator =

Assigne un HWND à un objet `CAxWindow` existant.

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Handle d’une fenêtre existante.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à l'objet `CAxWindow` actif.

##  <a name="querycontrol"></a>CAxWindow::QueryControl

Récupère l’interface spécifiée du contrôle hébergé.

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans Spécifie l’IID de l’interface du contrôle.

*ppUnk*<br/>
à Pointeur vers l’interface du contrôle. Dans la version de modèle de cette méthode, il n’est pas nécessaire d’utiliser un ID de référence tant qu’une interface typée avec un UUID associé est passée.

*Q*<br/>
dans Interface en cours d’interrogation.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="queryhost"></a>CAxWindow::QueryHost

Retourne l’interface spécifiée de l’hôte.

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans Spécifie l’IID de l’interface du contrôle.

*ppUnk*<br/>
à Pointeur vers l’interface sur l’hôte. Dans la version de modèle de cette méthode, il n’est pas nécessaire d’utiliser un ID de référence tant qu’une interface typée avec un UUID associé est passée.

*Q*<br/>
dans Interface en cours d’interrogation.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’interface de l’hôte autorise l’accès à la fonctionnalité sous-jacente du code d’hébergement de fenêtres, implémentée par `AxWin`.

##  <a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch

Définit l’interface de dispatch externe pour l’objet `CAxWindow`.

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
dans Pointeur vers une interface de `IDispatch`.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

##  <a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler

Définit l’interface [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) externe pour l’objet `CAxWindow`.

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>Paramètres

*pUIHandler*<br/>
dans Pointeur vers une interface de `IDocHostUIHandlerDispatch`.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’interface de `IDocHostUIHandlerDispatch` externe est utilisée par les contrôles qui interrogent le site de l’hôte pour l’interface `IDocHostUIHandlerDispatch`. Le contrôle WebBrowser est un contrôle qui le fait.

## <a name="see-also"></a>Voir aussi

[ATLCON, exemple](../../overview/visual-cpp-samples.md)<br/>
[CWindow, classe](../../atl/reference/cwindow-class.md)<br/>
[Notions de base des contrôles composites](../../atl/atl-composite-control-fundamentals.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[FAQ sur la relation contenant-contenu des contrôles](../../atl/atl-control-containment-faq.md)
