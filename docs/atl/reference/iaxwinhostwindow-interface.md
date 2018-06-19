---
title: Interface de l’interface IAxWinHostWindow | Documents Microsoft
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
ms.openlocfilehash: d1d0d41439748cd0ddbc981ecb1d74194d5fbd59
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365124"
---
# <a name="iaxwinhostwindow-interface"></a>Interface de l’interface IAxWinHostWindow
Cette interface fournit des méthodes pour manipuler un contrôle et son objet ordinateur hôte.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
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
|[CreateControlEx](#createcontrolex)|Crée un contrôle, attache à l’objet hôte et définit éventuellement un gestionnaire d’événements.|  
|[QueryControl](#querycontrol)|Retourne un pointeur d’interface pour le contrôle hébergé.|  
|[SetExternalDispatch](#setexternaldispatch)|Définit les externes `IDispatch` interface.|  
|[SetExternalUIHandler](#setexternaluihandler)|Définit les externes `IDocHostUIHandlerDispatch` interface.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est exposée par le contrôle ActiveX de d’ATL qui héberge les objets. Appelez les méthodes sur cette interface pour créer ou joindre un contrôle à l’objet hôte, pour obtenir une interface à partir d’un contrôle hébergé, ou pour définir le dispinterface externe ou un gestionnaire d’interface utilisateur à utiliser lors de l’hébergement du navigateur Web.  
  
## <a name="requirements"></a>Spécifications  
 La définition de cette interface est disponible en tant que fichier IDL ou C++, comme indiqué ci-dessous.  
  
|Type de définition|Fichier|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (également inclus dans ATLBase.h)|  
  
##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl  
 Attache un contrôle existant (et précédemment initialisé) à l’objet hôte à l’aide de la fenêtre identifiée par `hWnd`.  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *pUnkControl*  
 [in] Un pointeur vers le **IUnknown** interface du contrôle à attacher à l’objet hôte.  
  
 `hWnd`  
 [in] Un handle de fenêtre à utiliser pour l’hébergement.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl  
 Crée un contrôle, il initialise et héberge ce dernier dans la fenêtre identifiée par `hWnd`.  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpTricsData`  
 [in] Chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), un ProgID, une URL ou un code HTML brut (précédé **MSHTML :**).  
  
 `hWnd`  
 [in] Un handle de fenêtre à utiliser pour l’hébergement.  
  
 `pStream`  
 [in] Un pointeur d’interface pour un flux contenant les données d’initialisation pour le contrôle. Peut être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Cette fenêtre est sous-classée par l’objet hôte qui expose cette interface afin que les messages peuvent être reflétées sur le contrôle et d’autres fonctionnalités de conteneur fonctionneront.  
  
 Appel de cette méthode équivaut à appeler la méthode [IAxWinHostWindow::CreateControlEx](#createcontrolex).  
  
 Pour créer un contrôle ActiveX sous licence, consultez [IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).  
  
##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx  
 Crée un contrôle ActiveX, il initialise et héberge ce dernier dans la fenêtre spécifiée, semblable à [IAxWinHostWindow::CreateControl](#createcontrol).  
  
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
 `lpTricsData`  
 [in] Chaîne identifiant le contrôle à créer. Peut être un CLSID (doit inclure les accolades), un ProgID, une URL ou un code HTML brut (avec le préfixe **MSHTML :**).  
  
 `hWnd`  
 [in] Un handle de fenêtre à utiliser pour l’hébergement.  
  
 `pStream`  
 [in] Un pointeur d’interface pour un flux contenant les données d’initialisation pour le contrôle. Peut être **NULL**.  
  
 `ppUnk`  
 [out] L’adresse d’un pointeur qui recevra le **IUnknown** interface du contrôle créé. Peut être **NULL**.  
  
 *riidAdvise*  
 [in] L’identificateur d’interface d’une interface sortante sur l’objet de relation contenant-contenu. Peut être **IID_NULL**.  
  
 *punkAdvise*  
 [in] Un pointeur vers le **IUnknown** interface de l’objet récepteur pour la connexion à un point de connexion de l’objet de relation contenant-contenu spécifié par `iidSink`.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Contrairement à la `CreateControl` méthode `CreateControlEx` permet également de recevoir un pointeur d’interface pour le contrôle qui vient d’être créé et configuré un récepteur d’événements pour recevoir les événements déclenchés par le contrôle.  
  
 Pour créer un contrôle ActiveX sous licence, consultez [IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex).  
  
##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl  
 Retourne le pointeur d’interface spécifié fourni par le contrôle hébergé.  
  
```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Paramètres  
 `riid`  
 [in] L’ID d’une interface sur le contrôle demandé.  
  
 `ppvObject`  
 [out] L’adresse d’un pointeur qui recevra l’interface spécifiée du contrôle créé.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch  
 Définit la dispinterface externe, qui est disponible pour les contrôles contenus par le biais du [IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) (méthode).  
  
```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDisp`  
 [in] Un pointeur vers un `IDispatch` interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler  
 Appelez cette fonction pour définir les externes [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) de l’interface pour le `CAxWindow` objet.  
  
```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDisp`  
 [in] Un pointeur vers un **IDocHostUIHandlerDispatch** interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est utilisée par les contrôles (par exemple, le contrôle de navigateur Web) qui interroge le site de l’ordinateur hôte pour le `IDocHostUIHandlerDispatch` interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface de IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)   
 [CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)









