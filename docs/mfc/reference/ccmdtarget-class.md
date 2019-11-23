---
title: CCmdTarget, classe
ms.date: 11/04/2016
f1_keywords:
- CCmdTarget
- AFXWIN/CCmdTarget
- AFXWIN/CCmdTarget::CCmdTarget
- AFXWIN/CCmdTarget::BeginWaitCursor
- AFXWIN/CCmdTarget::DoOleVerb
- AFXWIN/CCmdTarget::EnableAutomation
- AFXWIN/CCmdTarget::EnableConnections
- AFXWIN/CCmdTarget::EnableTypeLib
- AFXWIN/CCmdTarget::EndWaitCursor
- AFXWIN/CCmdTarget::EnumOleVerbs
- AFXWIN/CCmdTarget::FromIDispatch
- AFXWIN/CCmdTarget::GetDispatchIID
- AFXWIN/CCmdTarget::GetIDispatch
- AFXWIN/CCmdTarget::GetTypeInfoCount
- AFXWIN/CCmdTarget::GetTypeInfoOfGuid
- AFXWIN/CCmdTarget::GetTypeLib
- AFXWIN/CCmdTarget::GetTypeLibCache
- AFXWIN/CCmdTarget::IsInvokeAllowed
- AFXWIN/CCmdTarget::IsResultExpected
- AFXWIN/CCmdTarget::OnCmdMsg
- AFXWIN/CCmdTarget::OnFinalRelease
- AFXWIN/CCmdTarget::RestoreWaitCursor
helpviewer_keywords:
- CCmdTarget [MFC], CCmdTarget
- CCmdTarget [MFC], BeginWaitCursor
- CCmdTarget [MFC], DoOleVerb
- CCmdTarget [MFC], EnableAutomation
- CCmdTarget [MFC], EnableConnections
- CCmdTarget [MFC], EnableTypeLib
- CCmdTarget [MFC], EndWaitCursor
- CCmdTarget [MFC], EnumOleVerbs
- CCmdTarget [MFC], FromIDispatch
- CCmdTarget [MFC], GetDispatchIID
- CCmdTarget [MFC], GetIDispatch
- CCmdTarget [MFC], GetTypeInfoCount
- CCmdTarget [MFC], GetTypeInfoOfGuid
- CCmdTarget [MFC], GetTypeLib
- CCmdTarget [MFC], GetTypeLibCache
- CCmdTarget [MFC], IsInvokeAllowed
- CCmdTarget [MFC], IsResultExpected
- CCmdTarget [MFC], OnCmdMsg
- CCmdTarget [MFC], OnFinalRelease
- CCmdTarget [MFC], RestoreWaitCursor
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
ms.openlocfilehash: 583b685295bf77910ef134776c1c4fa39baf93ad
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816340"
---
# <a name="ccmdtarget-class"></a>CCmdTarget, classe

Classe de base de l’architecture de la bibliothèque MFC (Microsoft Foundation Class) de la table des messages.

## <a name="syntax"></a>Syntaxe

```
class CCmdTarget : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCmdTarget::CCmdTarget](#ccmdtarget)|Construit un objet `CCmdTarget`.|

### <a name="public-methods"></a>Méthodes publiques

|Nom|Description|
|----------|-----------------|
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|Affiche le curseur sous la forme d’un curseur en forme de sablier.|
|[CCmdTarget::DoOleVerb](#dooleverb)|Provoque l’exécution d’une action spécifiée par un verbe OLE.|
|[CCmdTarget::EnableAutomation](#enableautomation)|Autorise l’automatisation OLE pour l’objet `CCmdTarget`.|
|[CCmdTarget::EnableConnections](#enableconnections)|Active le déclenchement des événements sur les points de connexion.|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Active la bibliothèque de types d’un objet.|
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Retourne au curseur précédent.|
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Énumère les verbes OLE d’un objet.|
|[CCmdTarget::FromIDispatch](#fromidispatch)|Retourne un pointeur vers l’objet `CCmdTarget` associé au pointeur `IDispatch`.|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Obtient l’ID d’interface de dispatch principal.|
|[CCmdTarget::GetIDispatch](#getidispatch)|Retourne un pointeur vers l’objet `IDispatch` associé à l’objet `CCmdTarget`.|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Récupère le nombre d’interfaces d’informations de type fourni par un objet.|
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Récupère la description de type qui correspond au GUID spécifié.|
|[CCmdTarget::GetTypeLib](#gettypelib)|Obtient un pointeur vers une bibliothèque de types.|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Obtient le cache de la bibliothèque de types.|
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Active l’appel de la méthode Automation.|
|[CCmdTarget :: IsResultExpected](#isresultexpected)|Retourne une valeur différente de zéro si une fonction Automation doit retourner une valeur.|
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Achemine et distribue les messages de commande.|
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Nettoie après la publication de la dernière référence OLE.|
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Restaure le curseur de sablier.|

## <a name="remarks"></a>Notes

Une table des messages achemine les commandes ou les messages vers les fonctions membres que vous écrivez pour les gérer. (Une commande est un message d’un élément de menu, d’un bouton de commande ou d’une touche d’accès rapide.)

Les classes d’infrastructure clés dérivées de `CCmdTarget` incluent [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md)et [CFrameWnd](../../mfc/reference/cframewnd-class.md). Si vous souhaitez qu’une nouvelle classe gère les messages, dérivez la classe à partir de l’une de ces classes dérivées de `CCmdTarget`. Vous allez rarement dériver une classe de `CCmdTarget` directement.

Pour obtenir une vue d’ensemble des cibles de commande et du routage de `OnCmdMsg`, consultez [cibles de commande](../../mfc/command-targets.md), [routage des commandes](../../mfc/command-routing.md)et mappage de [messages](../../mfc/mapping-messages.md).

`CCmdTarget` comprend des fonctions membres qui gèrent l’affichage d’un curseur sablier. Affichez le curseur en forme de sablier quand vous vous attendez à ce que l’exécution d’une commande prenne un intervalle de temps notable.

Les tables de dispatch, similaires aux tables des messages, sont utilisées pour exposer les fonctionnalités de `IDispatch` OLE Automation. En exposant cette interface, les autres applications (telles que Visual Basic) peuvent appeler votre application.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="beginwaitcursor"></a>  CCmdTarget::BeginWaitCursor

Appelez cette fonction pour afficher le curseur sous la forme d’un sablier lorsque vous vous attendez à ce qu’une commande prenne un intervalle de temps notable pour s’exécuter.

```
void BeginWaitCursor();
```

### <a name="remarks"></a>Notes

L’infrastructure appelle cette fonction pour montrer à l’utilisateur qu’elle est occupée, par exemple quand un objet `CDocument` se charge ou s’enregistre lui-même dans un fichier.

Les actions des `BeginWaitCursor` ne sont pas toujours effectives en dehors d’un gestionnaire de messages unique, car d’autres actions, telles que la gestion des `OnSetCursor`, peuvent modifier le curseur.

Appelez `EndWaitCursor` pour restaurer le curseur précédent.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="ccmdtarget"></a>  CCmdTarget::CCmdTarget

Construit un objet `CCmdTarget`.

```
CCmdTarget();
```

##  <a name="dooleverb"></a>  CCmdTarget::DoOleVerb

Provoque l’exécution d’une action spécifiée par un verbe OLE.

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*iVerb*<br/>
Identificateur numérique du verbe.

*lpMsg*<br/>
Pointeur vers la structure [MSG](/windows/win32/api/winuser/ns-winuser-msg) décrivant l’événement (par exemple, un double-clic) qui a appelé le verbe.

*hWndParent*<br/>
Handle de la fenêtre de document contenant l'objet.

*lpRect*<br/>
Pointeur vers la structure [Rect](/previous-versions/dd162897\(v=vs.85\)) contenant les coordonnées, en pixels, qui définissent le rectangle englobant d’un objet dans *hwndParent*.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite ; sinon, FALSe.

### <a name="remarks"></a>Notes

Cette fonction membre est fondamentalement une implémentation de [IOleObject ::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb). Les actions possibles sont énumérées par [CCmdTarget :: EnumOleVerbs](#enumoleverbs).

##  <a name="enableautomation"></a>  CCmdTarget::EnableAutomation

Appelez cette fonction pour activer OLE Automation pour un objet.

```
void EnableAutomation();
```

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée à partir du constructeur de votre objet et doit être appelée uniquement si un mappage de dispatch a été déclaré pour la classe. Pour plus d’informations sur Automation, consultez les articles [clients Automation](../../mfc/automation-clients.md) et [Serveurs Automation](../../mfc/automation-servers.md).

##  <a name="enableconnections"></a>  CCmdTarget::EnableConnections

Active le déclenchement des événements sur les points de connexion.

```
void EnableConnections();
```

### <a name="remarks"></a>Notes

Pour activer les points de connexion, appelez cette fonction membre dans le constructeur de votre classe dérivée.

##  <a name="enabletypelib"></a>  CCmdTarget::EnableTypeLib

Active la bibliothèque de types d’un objet.

```
void EnableTypeLib();
```

### <a name="remarks"></a>Notes

Appelez cette fonction membre dans le constructeur de votre objet dérivé de `CCmdTarget`si elle fournit des informations de type.

##  <a name="endwaitcursor"></a>  CCmdTarget::EndWaitCursor

Appelez cette fonction après avoir appelé la fonction membre `BeginWaitCursor` pour retourner du curseur sablier au curseur précédent.

```
void EndWaitCursor();
```

### <a name="remarks"></a>Notes

Le Framework appelle également cette fonction membre après avoir appelé le curseur sablier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="enumoleverbs"></a>  CCmdTarget::EnumOleVerbs

Énumère les verbes OLE d’un objet.

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>Paramètres

*ppenumOleVerb*<br/>
Pointeur vers un pointeur vers une interface [IEnumOLEVERB](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb) .

### <a name="return-value"></a>Valeur de retour

TRUE si l’objet prend en charge au moins un verbe OLE (auquel cas \* *ppenumOleVerb* pointe vers une interface d’énumérateur `IEnumOLEVERB`); sinon, false.

### <a name="remarks"></a>Notes

Cette fonction membre est fondamentalement une implémentation de [IOleObject :: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs).

##  <a name="fromidispatch"></a>  CCmdTarget::FromIDispatch

Appelez cette fonction pour mapper un pointeur `IDispatch`, reçu des fonctions membres Automation d’une classe, à l’objet `CCmdTarget` qui implémente les interfaces de l’objet `IDispatch`.

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>Paramètres

*lpDispatch*<br/>
Pointeur vers un objet `IDispatch` .

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet `CCmdTarget` associé à *lpDispatch*. Cette fonction retourne la valeur NULL si l’objet `IDispatch` n’est pas reconnu comme un objet Microsoft Foundation Class `IDispatch`.

### <a name="remarks"></a>Notes

Le résultat de cette fonction est l’inverse d’un appel à la fonction membre `GetIDispatch`.

##  <a name="getdispatchiid"></a>  CCmdTarget::GetDispatchIID

Obtient l’ID d’interface de dispatch principal.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>Paramètres

*pIID*<br/>
Pointeur vers un ID d’interface ( [GUID](/previous-versions/cc317743(v%3dmsdn.10)).

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite ; sinon, FALSe. En cas de réussite, \* *pIID* est défini sur l’ID d’interface de dispatch principal.

### <a name="remarks"></a>Notes

Les classes dérivées doivent remplacer cette fonction membre (si elles ne sont pas substituées, `GetDispatchIID` retourne la valeur FALSe). Voir [COleControl](../../mfc/reference/colecontrol-class.md).

##  <a name="getidispatch"></a>  CCmdTarget::GetIDispatch

Appelez cette fonction membre pour récupérer le pointeur `IDispatch` à partir d’une méthode Automation qui retourne un pointeur `IDispatch` ou prend un pointeur `IDispatch` par référence.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>Paramètres

*bAddRef*<br/>
Spécifie s’il faut incrémenter le décompte de références pour l’objet.

### <a name="return-value"></a>Valeur de retour

Pointeur `IDispatch` associé à l’objet.

### <a name="remarks"></a>Notes

Pour les objets qui appellent `EnableAutomation` dans leurs constructeurs, ce qui rend l’automatisation activée, cette fonction retourne un pointeur vers l’implémentation de la classe de base de `IDispatch` utilisée par les clients qui communiquent via l’interface `IDispatch`. L’appel de cette fonction ajoute automatiquement une référence au pointeur, il n’est donc pas nécessaire d’effectuer un appel à [IUnknown :: AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref).

##  <a name="gettypeinfocount"></a>  CCmdTarget::GetTypeInfoCount

Récupère le nombre d’interfaces d’informations de type fourni par un objet.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre d’interfaces d’informations de type.

### <a name="remarks"></a>Notes

Cette fonction membre implémente fondamentalement [IDispatch :: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).

Les classes dérivées doivent remplacer cette fonction pour retourner le nombre d’interfaces d’informations de type fournies (0 ou 1). S’il n’est pas substitué, `GetTypeInfoCount` retourne 0. Pour remplacer, utilisez la macro [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) , qui implémente également `GetTypeLib` et `GetTypeLibCache`.

##  <a name="gettypeinfoofguid"></a>  CCmdTarget::GetTypeInfoOfGuid

Récupère la description de type qui correspond au GUID spécifié.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>Paramètres

*lcid*<br/>
Identificateur de paramètres régionaux (`LCID`).

*guid*<br/>
[GUID](/previous-versions/cc317743(v%3dmsdn.10)) de la description de type.

*ppTypeInfo*<br/>
Pointeur vers un pointeur vers l’interface `ITypeInfo`.

### <a name="return-value"></a>Valeur de retour

HRESULT indiquant la réussite ou l’échec de l’appel. En cas de réussite, \* *ppTypeInfo* pointe vers l’interface d’informations de type.

##  <a name="gettypelib"></a>  CCmdTarget::GetTypeLib

Obtient un pointeur vers une bibliothèque de types.

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>Paramètres

*lcid*<br/>
Identificateur de paramètres régionaux (LCID).

*ppTypeLib*<br/>
Pointeur vers un pointeur vers l’interface `ITypeLib`.

### <a name="return-value"></a>Valeur de retour

HRESULT indiquant la réussite ou l’échec de l’appel. En cas de réussite, \* *ppTypeLib* pointe vers l’interface de la bibliothèque de types.

### <a name="remarks"></a>Notes

Les classes dérivées doivent remplacer cette fonction membre (si elles ne sont pas substituées, `GetTypeLib` retourne TYPE_E_CANTLOADLIBRARY). Utilisez la macro [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) , qui implémente également `GetTypeInfoCount` et `GetTypeLibCache`.

##  <a name="gettypelibcache"></a>  CCmdTarget::GetTypeLibCache

Obtient le cache de la bibliothèque de types.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CTypeLibCache` .

### <a name="remarks"></a>Notes

Les classes dérivées doivent remplacer cette fonction membre (si elles ne sont pas substituées, `GetTypeLibCache` retourne la valeur NULL). Utilisez la macro [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) , qui implémente également `GetTypeInfoCount` et `GetTypeLib`.

##  <a name="isinvokeallowed"></a>  CCmdTarget::IsInvokeAllowed

Cette fonction est appelée par l’implémentation de `IDispatch::Invoke` par MFC pour déterminer si une méthode Automation donnée (identifiée par *DISPID*) peut être appelée.

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
ID de dispatch.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode peut être appelée, sinon FALSe.

### <a name="remarks"></a>Notes

Si `IsInvokeAllowed` retourne la valeur TRUE, `Invoke` poursuit l’appel à la méthode ; dans le cas contraire, `Invoke` échoue, en retournant E_UNEXPECTED.

Les classes dérivées peuvent substituer cette fonction pour retourner des valeurs appropriées (si elles ne sont pas substituées, `IsInvokeAllowed` retourne la valeur TRUE). Consultez en particulier [COleControl :: IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).

##  <a name="isresultexpected"></a>  CCmdTarget::IsResultExpected

Utilisez `IsResultExpected` pour déterminer si un client attend une valeur de retour de son appel à une fonction d’automatisation.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si une fonction Automation doit retourner une valeur ; Sinon, 0.

### <a name="remarks"></a>Notes

L’interface OLE fournit aux MFC des informations indiquant si le client utilise ou ignore le résultat d’un appel de fonction, et MFC à son tour utilise ces informations pour déterminer le résultat d’un appel à `IsResultExpected`. Si la production d’une valeur de retour est gourmande en temps ou en ressources, vous pouvez augmenter l’efficacité en appelant cette fonction avant de calculer la valeur de retour.

Cette fonction retourne 0 une seule fois pour que vous obteniez des valeurs de retour valides à partir d’autres fonctions d’automatisation si vous les appelez à partir de la fonction Automation appelée par le client.

`IsResultExpected` retourne une valeur différente de zéro si elle est appelée lorsqu’un appel de fonction Automation n’est pas en cours.

##  <a name="oncmdmsg"></a>  CCmdTarget::OnCmdMsg

Appelé par le Framework pour acheminer et distribuer des messages de commande et pour gérer la mise à jour des objets d’interface utilisateur de commande.

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Contient l’ID de commande.

*nCode*<br/>
Identifie le code de notification de commande. Pour plus d’informations sur les valeurs de *nCode*, consultez la **section Notes** .

*pExtra*<br/>
Utilisé en fonction de la valeur de *nCode*. Pour plus d’informations sur *pExtra*, consultez la **section Notes** .

*pHandlerInfo*<br/>
Si la valeur n’est pas NULL, `OnCmdMsg` remplit les membres *pTarget* et *PMF* de la structure *pHandlerInfo* au lieu de distribuer la commande. En général, ce paramètre doit avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le message est géré ; Sinon, 0.

### <a name="remarks"></a>Notes

Il s’agit de la principale routine d’implémentation de l’architecture de la commande Framework.

Au moment de l’exécution, `OnCmdMsg` distribue une commande à d’autres objets ou gère la commande elle-même en appelant la classe racine `CCmdTarget::OnCmdMsg`, qui effectue la recherche de la table des messages réelle. Pour obtenir une description complète du routage des commandes par défaut, consultez rubriques sur la [gestion et le mappage des messages](../../mfc/message-handling-and-mapping.md).

Dans de rares occasions, vous souhaiterez peut-être remplacer cette fonction membre pour étendre le routage des commandes standard du Framework. Reportez-vous à la [note technique 21](../../mfc/tn021-command-and-message-routing.md) pour obtenir des détails avancés sur l’architecture de routage des commandes.

Si vous remplacez `OnCmdMsg`, vous devez fournir la valeur appropriée pour *nCode*, le code de notification de commande et *pExtra*, qui dépend de la valeur de *nCode*. Le tableau suivant répertorie les valeurs correspondantes :

|valeur *nCode*|valeur *pExtra*|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

##  <a name="onfinalrelease"></a>  CCmdTarget::OnFinalRelease

Appelé par le Framework lorsque la dernière référence OLE à ou à partir de l’objet est libérée.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Notes

Remplacez cette fonction pour fournir un traitement spécial pour cette situation. L’implémentation par défaut supprime l’objet.

##  <a name="restorewaitcursor"></a>  CCmdTarget::RestoreWaitCursor

Appelez cette fonction pour restaurer le curseur de sablier approprié une fois que le curseur système a changé (par exemple, une fois qu’une boîte de message s’est ouverte, puis fermée au milieu d’une opération de longue durée).

```
void RestoreWaitCursor();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC ACDual](../../overview/visual-cpp-samples.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdUI, classe](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate, classe](../../mfc/reference/cdoctemplate-class.md)<br/>
[CWinApp, classe](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[COleDispatchDriver, classe](../../mfc/reference/coledispatchdriver-class.md)
