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
ms.openlocfilehash: 5ee4101302322a5212a80b32f095cdd13d9769e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352291"
---
# <a name="ccmdtarget-class"></a>CCmdTarget, classe

La classe de base de l’architecture de carte de message Microsoft Foundation Class Library.

## <a name="syntax"></a>Syntaxe

```
class CCmdTarget : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCmdTarget::CCmdTarget](#ccmdtarget)|Construit un objet `CCmdTarget`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|Affiche le curseur comme un curseur de sablier.|
|[CCmdTarget::DoOleVerb](#dooleverb)|Provoque l’exécution d’une action spécifiée par un verbe OLE.|
|[CCmdTarget::EnableAutomation](#enableautomation)|Permet l’automatisation `CCmdTarget` OLE pour l’objet.|
|[CCmdTarget::EnableConnections](#enableconnections)|Permet le tir événementiel sur les points de connexion.|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Permet la bibliothèque de type d’objet.|
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Retourne au curseur précédent.|
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Énumère les verbes OLE d’un objet.|
|[CCmdTarget::DeIDispatch](#fromidispatch)|Retourne un pointeur à `CCmdTarget` `IDispatch` l’objet associé au pointeur.|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Obtient l’id principal d’interface de répartition.|
|[CCmdTarget::GetIDispatch](#getidispatch)|Retourne un pointeur à `IDispatch` `CCmdTarget` l’objet associé à l’objet.|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Récupère le nombre d’interfaces d’information de type qu’un objet fournit.|
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Récupère la description de type qui correspond au GUID spécifié.|
|[CCmdTarget::GetTypeLib](#gettypelib)|Obtient un pointeur à une bibliothèque de type.|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Obtient le cache de bibliothèque de type.|
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Permet l’invocation de la méthode d’automatisation.|
|[CCmdTarget::IsResultExpected](#isresultexpected)|Retourne nonzero si une fonction d’automatisation doit retourner une valeur.|
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Itinéraires et envois de messages de commande.|
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Nettoyage après la sortie de la dernière référence OLE.|
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Restaure le curseur de sablier.|

## <a name="remarks"></a>Notes

Une carte de message achemine les commandes ou les messages vers les fonctions membres que vous écrivez pour les manipuler. (Une commande est un message à partir d’un élément de menu, d’un bouton de commande ou d’une clé d’accélérateur.)

Les principales classes-cadres `CCmdTarget` dérivées de [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md), et [CFrameWnd](../../mfc/reference/cframewnd-class.md). Si vous avez l’intention d’une nouvelle classe `CCmdTarget`pour gérer les messages, puisez la classe de l’une de ces classes dérivées. Vous tirerez rarement `CCmdTarget` une classe directement.

Pour un aperçu des `OnCmdMsg` cibles de commande et de l’itinéraire, voir [cibles de commandement](../../mfc/command-targets.md), itinéraire de [commande,](../../mfc/command-routing.md)et [messages de cartographie](../../mfc/mapping-messages.md).

`CCmdTarget`comprend des fonctions de membre qui gèrent l’affichage d’un curseur de sablier. Affichez le curseur de sablier lorsque vous vous attendez à ce qu’une commande prenne un intervalle de temps notable pour exécuter.

Les cartes d’expédition, semblables aux cartes `IDispatch` de message, sont utilisées pour exposer les fonctionnalités d’automatisation OLE. En exposant cette interface, d’autres applications (telles que Visual Basic) peuvent appeler dans votre application.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="ccmdtargetbeginwaitcursor"></a><a name="beginwaitcursor"></a>CCmdTarget::BeginWaitCursor

Appelez cette fonction pour afficher le curseur comme un sablier lorsque vous vous attendez à ce qu’une commande prenne un intervalle de temps notable pour exécuter.

```
void BeginWaitCursor();
```

### <a name="remarks"></a>Notes

Le cadre appelle cette fonction pour montrer à l’utilisateur qu’il est occupé, par exemple lorsqu’un `CDocument` objet se charge ou s’enregistre à un fichier.

Les actions `BeginWaitCursor` de ne sont pas toujours efficaces en `OnSetCursor` dehors d’un seul gestionnaire de message que d’autres actions, telles que la manipulation, pourrait changer le curseur.

Appelez `EndWaitCursor` pour restaurer le curseur précédent.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetccmdtarget"></a><a name="ccmdtarget"></a>CCmdTarget::CCmdTarget

Construit un objet `CCmdTarget`.

```
CCmdTarget();
```

## <a name="ccmdtargetdooleverb"></a><a name="dooleverb"></a>CCmdTarget::DoOleVerb

Provoque l’exécution d’une action spécifiée par un verbe OLE.

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*iVerb (en)*<br/>
Identifiant numérique du verbe.

*lpMsg*<br/>
Pointeur vers la structure [MSG](/windows/win32/api/winuser/ns-winuser-msg) décrivant l’événement (comme un double clic) qui invoquait le verbe.

*hWndParent*<br/>
Handle de la fenêtre de document contenant l'objet.

*lpRect*<br/>
Pointeur vers la structure [RECT](/previous-versions/dd162897\(v=vs.85\)) contenant les coordonnées, en pixels, qui définissent le rectangle de délimitation d’un objet dans *hwndParent*.

### <a name="return-value"></a>Valeur de retour

VRAI en cas de succès, sinon FALSE.

### <a name="remarks"></a>Notes

Cette fonction de membre est essentiellement une implémentation de [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb). Les actions possibles sont énumérées par [CCmdTarget::EnumOleVerbs](#enumoleverbs).

## <a name="ccmdtargetenableautomation"></a><a name="enableautomation"></a>CCmdTarget::EnableAutomation

Appelez cette fonction pour activer l’automatisation OLE pour un objet.

```
void EnableAutomation();
```

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée à partir du constructeur de votre objet et ne doit être appelée que si une carte de répartition a été déclarée pour la classe. Pour plus d’informations sur l’automatisation voir les articles [Automation Clients](../../mfc/automation-clients.md) et [Automation Servers](../../mfc/automation-servers.md).

## <a name="ccmdtargetenableconnections"></a><a name="enableconnections"></a>CCmdTarget::EnableConnections

Permet le tir événementiel sur les points de connexion.

```
void EnableConnections();
```

### <a name="remarks"></a>Notes

Pour activer les points de connexion, appelez cette fonction de membre dans le constructeur de votre classe dérivée.

## <a name="ccmdtargetenabletypelib"></a><a name="enabletypelib"></a>CCmdTarget::EnableTypeLib

Permet la bibliothèque de type d’objet.

```
void EnableTypeLib();
```

### <a name="remarks"></a>Notes

Appelez cette fonction de membre `CCmdTarget`dans le constructeur de votre objet dérivé s’il fournit des informations de type.

## <a name="ccmdtargetendwaitcursor"></a><a name="endwaitcursor"></a>CCmdTarget::EndWaitCursor

Appelez cette fonction après `BeginWaitCursor` avoir appelé la fonction membre pour revenir du curseur de sablier au curseur précédent.

```
void EndWaitCursor();
```

### <a name="remarks"></a>Notes

Le cadre appelle également cette fonction de membre après qu’il ait appelé le curseur de sablier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetenumoleverbs"></a><a name="enumoleverbs"></a>CCmdTarget::EnumOleVerbs

Énumère les verbes OLE d’un objet.

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>Paramètres

*ppenumOleVerb*<br/>
Un pointeur à un pointeur à une interface [IEnumOLEVERB.](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb)

### <a name="return-value"></a>Valeur de retour

VRAI si l’objet prend en charge au \* moins un verbe OLE (auquel cas *ppenumOleVerb* pointe vers une interface d’enumérateur), `IEnumOLEVERB` sinon FALSE.

### <a name="remarks"></a>Notes

Cette fonction de membre est essentiellement une implémentation de [IOleObject:EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs).

## <a name="ccmdtargetfromidispatch"></a><a name="fromidispatch"></a>CCmdTarget::DeIDispatch

Appelez cette fonction `IDispatch` pour cartographier un pointeur, reçu des `CCmdTarget` fonctions des membres d’automatisation d’une classe, dans l’objet qui implémente les interfaces de l’objet. `IDispatch`

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>Paramètres

*lpDispatch*<br/>
Pointeur vers un objet `IDispatch` .

### <a name="return-value"></a>Valeur de retour

Un pointeur `CCmdTarget` à l’objet associé à *lpDispatch*. Cette fonction renvoie `IDispatch` NULL si l’objet `IDispatch` n’est pas reconnu comme un objet Microsoft Foundation Class.

### <a name="remarks"></a>Notes

Le résultat de cette fonction est l’inverse `GetIDispatch`d’un appel à la fonction membre .

## <a name="ccmdtargetgetdispatchiid"></a><a name="getdispatchiid"></a>CCmdTarget::GetDispatchIID

Obtient l’id principal d’interface de répartition.

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>Paramètres

*pIID (en)*<br/>
Un pointeur à un ID d’interface (un [GUID](/previous-versions/cc317743(v%3dmsdn.10)).

### <a name="return-value"></a>Valeur de retour

VRAI en cas de succès, sinon FALSE. En cas \* de succès, *pIID* est réglé sur l’id principal de l’interface de répartition.

### <a name="remarks"></a>Notes

Les classes dérivées devraient remplacer cette fonction `GetDispatchIID` de membre (si elle n’est pas dépassée, retourne FALSE). Voir [COleControl](../../mfc/reference/colecontrol-class.md).

## <a name="ccmdtargetgetidispatch"></a><a name="getidispatch"></a>CCmdTarget::GetIDispatch

Appelez cette fonction de `IDispatch` membre pour récupérer le `IDispatch` pointeur d’une méthode d’automatisation qui renvoie un pointeur ou prend un `IDispatch` pointeur par référence.

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>Paramètres

*bAddRef (en)*<br/>
Précise s’il faut incrémenter le nombre de références pour l’objet.

### <a name="return-value"></a>Valeur de retour

Le `IDispatch` pointeur associé à l’objet.

### <a name="remarks"></a>Notes

Pour les `EnableAutomation` objets qui font appel à leurs constructeurs, ce qui les `IDispatch` rend automatisés, cette `IDispatch` fonction renvoie un pointeur à la mise en œuvre de la classe de fondation qui est utilisé par les clients qui communiquent via l’interface. Appeler cette fonction ajoute automatiquement une référence au pointeur, il n’est donc pas nécessaire de faire un appel à [IUnknown::AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref).

## <a name="ccmdtargetgettypeinfocount"></a><a name="gettypeinfocount"></a>CCmdTarget::GetTypeInfoCount

Récupère le nombre d’interfaces d’information de type qu’un objet fournit.

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre d’interfaces d’information de type.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente essentiellement [IDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).

Les classes dérivées devraient remplacer cette fonction pour retourner le nombre d’interfaces d’information de type fournies (0 ou 1). S’il n’est pas remplacé, `GetTypeInfoCount` retourne 0. Pour remplacer, utilisez le [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) macro, qui `GetTypeLib` met `GetTypeLibCache`également en œuvre et .

## <a name="ccmdtargetgettypeinfoofguid"></a><a name="gettypeinfoofguid"></a>CCmdTarget::GetTypeInfoOfGuid

Récupère la description de type qui correspond au GUID spécifié.

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>Paramètres

*lcid*<br/>
Un identificateur local ( `LCID`).

*Guid*<br/>
Le [GUID](/previous-versions/cc317743(v%3dmsdn.10)) de la description de type.

*ppTypeInfo*<br/>
Pointeur à un `ITypeInfo` pointeur à l’interface.

### <a name="return-value"></a>Valeur de retour

Un HRESULT indiquant le succès ou l’échec de l’appel. En cas \* de succès, *ppTypeInfo* indique l’interface d’information type.

## <a name="ccmdtargetgettypelib"></a><a name="gettypelib"></a>CCmdTarget::GetTypeLib

Obtient un pointeur à une bibliothèque de type.

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>Paramètres

*lcid*<br/>
Identificateur de paramètres régionaux (LCID).

*ppTypeLib*<br/>
Un pointeur à `ITypeLib` un pointeur de l’interface.

### <a name="return-value"></a>Valeur de retour

Un HRESULT indiquant le succès ou l’échec de l’appel. En cas \* de succès, *ppTypeLib* indique l’interface de bibliothèque de type.

### <a name="remarks"></a>Notes

Les classes dérivées devraient remplacer cette fonction `GetTypeLib` de membre (si elle n’est pas dépassée, les retours TYPE_E_CANTLOADLIBRARY). Utilisez le [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) macro, qui met `GetTypeInfoCount` `GetTypeLibCache`également en œuvre et .

## <a name="ccmdtargetgettypelibcache"></a><a name="gettypelibcache"></a>CCmdTarget::GetTypeLibCache

Obtient le cache de bibliothèque de type.

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CTypeLibCache`.

### <a name="remarks"></a>Notes

Les classes dérivées devraient remplacer cette fonction `GetTypeLibCache` de membre (si elle n’est pas dépassée, retourne NULL). Utilisez le [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) macro, qui met `GetTypeInfoCount` `GetTypeLib`également en œuvre et .

## <a name="ccmdtargetisinvokeallowed"></a><a name="isinvokeallowed"></a>CCmdTarget::IsInvokeAllowed

Cette fonction est appelée par la `IDispatch::Invoke` mise en œuvre de MFC pour déterminer si une méthode d’automatisation donnée (identifiée par *dispid)* peut être invoquée.

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
Une carte d’identité.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode peut être invoquée, sinon FALSE.

### <a name="remarks"></a>Notes

Si `IsInvokeAllowed` vous `Invoke` retournez TRUE, procède à l’appel de la méthode; sinon, `Invoke` échouera, retournant E_UNEXPECTED.

Les classes dérivées peuvent remplacer cette fonction pour retourner `IsInvokeAllowed` les valeurs appropriées (si elles ne sont pas remplacées, retourne VRAI). Voir en particulier [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).

## <a name="ccmdtargetisresultexpected"></a><a name="isresultexpected"></a>CCmdTarget::IsResultExpected

Utilisez-le `IsResultExpected` pour vérifier si un client s’attend à une valeur de retour de son appel à une fonction d’automatisation.

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si une fonction d’automatisation doit retourner une valeur; sinon 0.

### <a name="remarks"></a>Notes

L’interface OLE fournit des informations à MFC pour savoir si le client utilise ou ignore le résultat d’un appel de fonction, et MFC utilise à son tour ces informations pour déterminer le résultat d’un appel à `IsResultExpected`. Si la production d’une valeur de retour est à forte intensité de temps ou de ressources, vous pouvez augmenter l’efficacité en appelant cette fonction avant de calculer la valeur de retour.

Cette fonction ne renvoie 0 qu’une seule fois de sorte que vous obtiendrez des valeurs de retour valides à partir d’autres fonctions d’automatisation si vous les appelez à partir de la fonction d’automatisation que le client a appelé.

`IsResultExpected`retourne une valeur non zéro si appelé lorsqu’un appel de fonction d’automatisation n’est pas en cours.

## <a name="ccmdtargetoncmdmsg"></a><a name="oncmdmsg"></a>CCmdTarget::OnCmdMsg

Appelé par le cadre pour acheminer et envoyer des messages de commande et pour gérer la mise à jour des objets de commande utilisateur-interface.

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

*nCode (en)*<br/>
Identifie le code de notification de commande. Voir **Remarques** pour plus d’informations sur les valeurs pour *nCode*.

*pExtra*<br/>
Utilisé selon la valeur de *nCode*. Voir **Remarques** pour plus d’informations sur *pExtra*.

*pHandlerInfo (en anglais)*<br/>
Si ce `OnCmdMsg` n’est pas NULL, remplit les membres *pTarget* et *pmf* de la structure *pHandlerInfo* au lieu d’envoyer la commande. Typiquement, ce paramètre devrait être NULL.

### <a name="return-value"></a>Valeur de retour

Nonzero si le message est manipulé; sinon 0.

### <a name="remarks"></a>Notes

Il s’agit de la principale routine de mise en œuvre de l’architecture de commandement-cadre.

Au moment `OnCmdMsg` de l’exécution, envoie une commande à d’autres `CCmdTarget::OnCmdMsg`objets ou gère la commande elle-même en appelant la classe racine , qui fait le lookup message-carte réelle. Pour une description complète du routage de commande par défaut, voir [Les sujets de manipulation et de cartographie des messages](../../mfc/message-handling-and-mapping.md).

En de rares occasions, vous pouvez remplacer cette fonction de membre pour prolonger le tracé de commande standard du cadre. Consultez [la note technique 21](../../mfc/tn021-command-and-message-routing.md) pour obtenir des détails avancés sur l’architecture de routage de commande.

Si vous `OnCmdMsg`remplacez, vous devez fournir la valeur appropriée pour *nCode*, le code de notification de commande, et *pExtra*, qui dépend de la valeur de *nCode*. Le tableau suivant énumère leurs valeurs correspondantes :

|*nCode* valeur|*valeur pExtra*|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

## <a name="ccmdtargetonfinalrelease"></a><a name="onfinalrelease"></a>CCmdTarget::OnFinalRelease

Appelé par le cadre lorsque la dernière référence OLE à ou à partir de l’objet est libéré.

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Notes

Remplacer cette fonction pour fournir une manipulation spéciale pour cette situation. La implémentation par défaut supprime l’objet.

## <a name="ccmdtargetrestorewaitcursor"></a><a name="restorewaitcursor"></a>CCmdTarget::RestoreWaitCursor

Appelez cette fonction pour restaurer le curseur de sablier approprié après que le curseur du système a changé (par exemple, après qu’une boîte de message a ouvert puis fermé au milieu d’une longue opération).

```
void RestoreWaitCursor();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdUI, classe](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)<br/>
[Classe CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[CWinApp, classe](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Classe CView](../../mfc/reference/cview-class.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Classe COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)
