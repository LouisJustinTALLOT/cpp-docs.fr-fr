---
title: CCmdTarget, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb4d7a06d728bddfd4ba1ee355cb4d1e0b5b9fd6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221708"
---
# <a name="ccmdtarget-class"></a>CCmdTarget (classe)
La classe de base pour l’architecture de table des messages de bibliothèque Microsoft Foundation Class.  
  
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
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|Affiche le curseur sous la forme d’une forme de sablier.|  
|[CCmdTarget::DoOleVerb](#dooleverb)|Provoque une action spécifiée par un verbe OLE à effectuer.|  
|[CCmdTarget::EnableAutomation](#enableautomation)|Permet de OLE automation pour le `CCmdTarget` objet.|  
|[CCmdTarget::EnableConnections](#enableconnections)|Permet de déclenchement des événements sur les points de connexion.|  
|[CCmdTarget::EnableTypeLib](#enabletypelib)|Active la bibliothèque de types d’un objet.|  
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|Retourne le curseur précédente.|  
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|Énumère les verbes d’un objet OLE.|  
|[CCmdTarget::FromIDispatch](#fromidispatch)|Retourne un pointeur vers le `CCmdTarget` objet associé à la `IDispatch` pointeur.|  
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|Obtient l’ID d’interface de dispatch principale.|  
|[CCmdTarget::GetIDispatch](#getidispatch)|Retourne un pointeur vers le `IDispatch` objet associé à la `CCmdTarget` objet.|  
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|Récupère le nombre d’interfaces d’informations de type qui fournit un objet.|  
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|Récupère la description de type qui correspond au GUID spécifié.|  
|[CCmdTarget::GetTypeLib](#gettypelib)|Obtient un pointeur vers une bibliothèque de types.|  
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|Obtient le cache de bibliothèque de type.|  
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|Permet l’appel de méthode automation.|  
|[CCmdTarget::IsResultExpected](#isresultexpected)|Retourne zéro si une fonction d’automatisation doit retourner une valeur.|  
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|Achemine et distribue des messages de commande.|  
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|Nettoie après que la dernière référence OLE est libérée.|  
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|Restaure le curseur sablier.|  
  
## <a name="remarks"></a>Notes  
 Une table des messages achemine les commandes ou les messages vers les fonctions de membre que vous écrivez pour gérer les. (Une commande est un message à partir d’un élément de menu, un bouton de commande ou une touche d’accès rapide.)  
  
 Classes de framework clés dérivées de `CCmdTarget` incluent [CView](../../mfc/reference/cview-class.md), [CWinApp](../../mfc/reference/cwinapp-class.md), [CDocument](../../mfc/reference/cdocument-class.md), [CWnd](../../mfc/reference/cwnd-class.md), et [ CFrameWnd](../../mfc/reference/cframewnd-class.md). Si vous envisagez d’utiliser une nouvelle classe à traiter les messages, dérivez la classe d’un de ces `CCmdTarget`-classes dérivées. Vous serez rarement dérivez une classe de `CCmdTarget` directement.  
  
 Pour une vue d’ensemble des cibles de commande et `OnCmdMsg` routage, consultez [cibles de la commande](../../mfc/command-targets.md), [routage des commandes](../../mfc/command-routing.md), et [mappage de Messages](../../mfc/mapping-messages.md).  
  
 `CCmdTarget` inclut des fonctions de membre qui gèrent l’affichage de la forme de sablier. Affiche le curseur sablier lorsque vous attendez une commande permettant de réaliser un intervalle de temps considérable à exécuter.  
  
 Tables dispatch, similaires aux mappages de message, sont utilisées pour exposer OLE automation `IDispatch` fonctionnalité. En exposant cette interface, les autres applications (par exemple, Visual Basic) peuvent appeler dans votre application.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCmdTarget`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
  
##  <a name="beginwaitcursor"></a>  CCmdTarget::BeginWaitCursor  
 Appelez cette fonction pour afficher le curseur comme un sablier lorsque vous attendez une commande permettant de réaliser un intervalle de temps considérable à exécuter.  
  
```  
void BeginWaitCursor();
```  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction pour afficher l’utilisateur qu’il est occupé, par exemple quand un `CDocument` objet charge ou lui-même enregistre dans un fichier.  
  
 Les actions de `BeginWaitCursor` ne sont pas toujours efficace en dehors d’un gestionnaire de messages unique en tant qu’autres actions, telles que `OnSetCursor` gérant, Impossible de modifier le curseur.  
  
 Appelez `EndWaitCursor` pour restaurer le curseur précédent.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="ccmdtarget"></a>  CCmdTarget::CCmdTarget  
 Construit un objet `CCmdTarget`.  
  
```  
CCmdTarget();
```  
  
##  <a name="dooleverb"></a>  CCmdTarget::DoOleVerb  
 Provoque une action spécifiée par un verbe OLE à effectuer.  
  
```  
BOOL DoOleVerb(
    LONG iVerb,  
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Paramètres  
 *iVerb*  
 Identificateur numérique du verbe.  
  
 *lpMsg*  
 Pointeur vers le [MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958) structure décrivant l’événement (par exemple, un double-clic) qui a appelé le verbe.  
  
 *hWndParent*  
 Handle de la fenêtre de document contenant l'objet.  
  
 *lpRect*  
 Pointeur vers le [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) rectangle de cadre englobant de structure contenant les coordonnées, en pixels, qui définissent un objet *hwndParent*.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE en cas de réussite, sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est essentiellement une implémentation de [IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb). Les actions possibles sont énumérées par [CCmdTarget::EnumOleVerbs](#enumoleverbs).  
  
##  <a name="enableautomation"></a>  CCmdTarget::EnableAutomation  
 Appelez cette fonction pour activer l’automatisation OLE pour un objet.  
  
```  
void EnableAutomation();
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction est généralement appelée à partir du constructeur de votre objet et doit uniquement être appelée si une table de dispatch a été déclarée pour la classe. Pour plus d’informations sur l’automatisation, consultez les articles [Clients Automation](../../mfc/automation-clients.md) et [serveurs Automation](../../mfc/automation-servers.md).  
  
##  <a name="enableconnections"></a>  CCmdTarget::EnableConnections  
 Permet de déclenchement des événements sur les points de connexion.  
  
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
 Appelez cette fonction membre dans le constructeur de votre `CCmdTarget`-objet dérivé s’il fournit des informations de type. Pour plus d’informations, consultez l’article de la Base de connaissances Q185720, « comment faire : fournir des informations de Type à partir d’un serveur d’Automation MFC. » Articles de la Base de connaissances sont disponibles dans [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="endwaitcursor"></a>  CCmdTarget::EndWaitCursor  
 Appelez cette fonction après avoir appelé la `BeginWaitCursor` fonction membre à retourner à partir du curseur sablier jusqu’au curseur précédente.  
  
```  
void EndWaitCursor();
```  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle également cette fonction membre après l’appel la forme de sablier.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="enumoleverbs"></a>  CCmdTarget::EnumOleVerbs  
 Énumère les verbes d’un objet OLE.  
  
```  
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```  
  
### <a name="parameters"></a>Paramètres  
 *ppenumOleVerb*  
 Un pointeur vers un pointeur vers un [IEnumOLEVERB](/windows/desktop/api/oleidl/nn-oleidl-ienumoleverb) interface.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’objet prend en charge au moins un verbe OLE (auquel cas \* *ppenumOleVerb* pointe vers un `IEnumOLEVERB` interface d’énumération) ; sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est essentiellement une implémentation de [IOleObject::EnumVerbs](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumverbs).  
  
##  <a name="fromidispatch"></a>  CCmdTarget::FromIDispatch  
 Appelez cette fonction pour mapper un `IDispatch` pointeur, reçue des fonctions de membre d’automation d’une classe, dans le `CCmdTarget` objet qui implémente les interfaces de le `IDispatch` objet.  
  
```  
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpDispatch*  
 Pointeur vers un objet `IDispatch` .  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `CCmdTarget` objet associé *lpDispatch*. Cette fonction retourne NULL si le `IDispatch` objet n’est pas reconnu comme un Microsoft Foundation Class `IDispatch` objet.  
  
### <a name="remarks"></a>Notes  
 Le résultat de cette fonction est l’inverse d’un appel à la fonction membre `GetIDispatch`.  
  
##  <a name="getdispatchiid"></a>  CCmdTarget::GetDispatchIID  
 Obtient l’ID d’interface de dispatch principale.  
  
```  
virtual BOOL GetDispatchIID(IID* pIID);
```  
  
### <a name="parameters"></a>Paramètres  
 *pIID*  
 Un pointeur vers un ID d’interface (un [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931)).  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE en cas de réussite, sinon, FALSE. En cas de réussite, \* *pIID* est défini sur l’ID d’interface de dispatch principale.  
  
### <a name="remarks"></a>Notes  
 Les classes dérivées doivent remplacer cette fonction membre (si ne pas substituée, `GetDispatchIID` renvoie la valeur FALSE). Consultez [COleControl](../../mfc/reference/colecontrol-class.md).  
  
 Pour plus d’informations, consultez l’article de la Base de connaissances Q185720, « comment faire : fournir des informations de Type à partir d’un serveur d’Automation MFC. » Articles de la Base de connaissances sont disponibles dans [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="getidispatch"></a>  CCmdTarget::GetIDispatch  
 Appelez cette fonction membre pour récupérer le `IDispatch` pointeur à partir d’une méthode automation qui retourne un `IDispatch` pointeur ou prend une `IDispatch` pointeur par référence.  
  
```  
LPDISPATCH GetIDispatch(BOOL bAddRef);
```  
  
### <a name="parameters"></a>Paramètres  
 *bAddRef*  
 Spécifie s’il faut incrémenter le décompte de références pour l’objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Le `IDispatch` pointeur associé à l’objet.  
  
### <a name="remarks"></a>Notes  
 Pour les objets qui appellent `EnableAutomation` dans leurs constructeurs, ce qui les rend automation est activée, cette fonction retourne un pointeur vers l’implémentation de classe de base de `IDispatch` qui est utilisé par les clients qui communiquent via le `IDispatch` interface. Appel de cette fonction automatiquement ajoute une référence au pointeur, donc il n’est pas nécessaire effectuer un appel à [IUnknown::AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref).  
  
##  <a name="gettypeinfocount"></a>  CCmdTarget::GetTypeInfoCount  
 Récupère le nombre d’interfaces d’informations de type qui fournit un objet.  
  
```  
virtual UINT GetTypeInfoCount();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’interfaces d’informations de type.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente fondamentalement [IDispatch::GetTypeInfoCount](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount).  
  
 Classes dérivées doivent remplacer cette fonction pour retourner le nombre d’interfaces d’informations de type fourni (0 ou 1). Si ne pas substituée, `GetTypeInfoCount` retourne 0. Pour remplacer, utilisez le [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) macro, qui implémente également `GetTypeLib` et `GetTypeLibCache`.  
  
##  <a name="gettypeinfoofguid"></a>  CCmdTarget::GetTypeInfoOfGuid  
 Récupère la description de type qui correspond au GUID spécifié.  
  
```  
HRESULT GetTypeInfoOfGuid(
    LCID lcid,  
    const GUID& guid,  
    LPTYPEINFO* ppTypeInfo);
```  
  
### <a name="parameters"></a>Paramètres  
 *lcid*  
 Un identificateur de paramètres régionaux ( `LCID`).  
  
 *guid*  
 Le [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931) de la description de type.  
  
 *ppTypeInfo*  
 Pointeur vers un pointeur vers le `ITypeInfo` interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT indiquant la réussite ou l’échec de l’appel. En cas de réussite, \* *ppTypeInfo* pointe vers l’interface d’informations de type.  
  
##  <a name="gettypelib"></a>  CCmdTarget::GetTypeLib  
 Obtient un pointeur vers une bibliothèque de types.  
  
```  
virtual HRESULT GetTypeLib(
    LCID lcid,  
    LPTYPELIB* ppTypeLib);
```  
  
### <a name="parameters"></a>Paramètres  
 *lcid*  
 Identificateur de paramètres régionaux (LCID).  
  
 *ppTypeLib*  
 Un pointeur vers un pointeur vers le `ITypeLib` interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT indiquant la réussite ou l’échec de l’appel. En cas de réussite, \* *ppTypeLib* pointe vers l’interface de bibliothèque de type.  
  
### <a name="remarks"></a>Notes  
 Les classes dérivées doivent remplacer cette fonction membre (si ne pas substituée, `GetTypeLib` retourne TYPE_E_CANTLOADLIBRARY). Utilisez le [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) macro, qui implémente également `GetTypeInfoCount` et `GetTypeLibCache`.  
  
##  <a name="gettypelibcache"></a>  CCmdTarget::GetTypeLibCache  
 Obtient le cache de bibliothèque de type.  
  
```  
virtual CTypeLibCache* GetTypeLibCache();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CTypeLibCache` objet.  
  
### <a name="remarks"></a>Notes  
 Les classes dérivées doivent remplacer cette fonction membre (si ne pas substituée, `GetTypeLibCache` renvoie la valeur NULL). Utilisez le [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib) macro, qui implémente également `GetTypeInfoCount` et `GetTypeLib`.  
  
##  <a name="isinvokeallowed"></a>  CCmdTarget::IsInvokeAllowed  
 Cette fonction est appelée par l’implémentation MFC de `IDispatch::Invoke` pour déterminer si une méthode automation donné (identifié par *dispid*) peuvent être appelées.  
  
```  
virtual BOOL IsInvokeAllowed(DISPID dispid);
```  
  
### <a name="parameters"></a>Paramètres  
 *DISPID*  
 Un ID de distribution.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la méthode peut être appelée ; sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Si `IsInvokeAllowed` retourne la valeur TRUE, `Invoke` passe à appeler la méthode ; sinon, `Invoke` échoue et génère E_UNEXPECTED.  
  
 Classes dérivées peuvent substituer cette fonction pour retourner des valeurs appropriées (si ne pas substituée, `IsInvokeAllowed` retourne la valeur TRUE). Consultez en particulier [COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed).  
  
##  <a name="isresultexpected"></a>  CCmdTarget::IsResultExpected  
 Utilisez `IsResultExpected` afin de déterminer si un client attend une valeur de retour d’un appel à une fonction d’automatisation.  
  
```  
BOOL IsResultExpected();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si une fonction d’automatisation doit retourner une valeur ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 L’interface OLE fournit des informations à MFC si le client est à l’aide d’ou en ignorant le résultat d’un appel de fonction, et MFC à son tour utilise ces informations pour déterminer le résultat d’un appel à `IsResultExpected`. Si la production d’une valeur de retour est le temps - ou gourmandes en ressources, vous pouvez augmenter l’efficacité en appelant cette fonction avant de calculer la valeur de retour.  
  
 Une seule fois afin que vous obtiendrez les valeurs de retour valides à partir d’autres fonctions d’automation si vous les appelez à partir de la fonction d’automatisation que le client a appelé la fonction renvoie 0.  
  
 `IsResultExpected` Retourne une valeur différente de zéro si elle est appelée lorsqu’un appel de fonction automation n’est pas en cours.  
  
##  <a name="oncmdmsg"></a>  CCmdTarget::OnCmdMsg  
 Appelé par l’infrastructure de router et distribuer des messages de commande et de gérer la mise à jour des objets d’interface utilisateur de commande.  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Paramètres  
 *nID*  
 Contient l’ID de commande.  
  
 *nCode*  
 Identifie le code de notification de commande. Consultez **remarques** pour plus d’informations sur les valeurs de *nCode*.  
  
 *pExtra*  
 Utilisé en fonction de la valeur de *nCode*. Consultez **remarques** pour plus d’informations sur *pExtra*.  
  
 *pHandlerInfo*  
 Si non NULL, `OnCmdMsg` renseigne le *pTarget* et *pmf* membres de la *pHandlerInfo* structure au lieu de la distribution de la commande. En règle générale, ce paramètre doit être NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le message est géré ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Il s’agit de la routine principale d’implémentation de l’architecture de commande de framework.  
  
 Au moment de l’exécution, `OnCmdMsg` distribue une commande à d’autres objets ou gère la commande elle-même en appelant la classe racine `CCmdTarget::OnCmdMsg`, qui effectue la recherche réelle de table des messages. Pour obtenir une description complète du routage de commande par défaut, consultez [gestion des messages et mappage des](../../mfc/message-handling-and-mapping.md).  
  
 Dans de rares occasions, voulez-vous remplacer cette fonction membre pour étendre l’infrastructure routage des commandes standard. Reportez-vous à [Note technique 21](../../mfc/tn021-command-and-message-routing.md) pour plus d’informations avancées de l’architecture de routage des commandes.  
  
 Si vous substituez `OnCmdMsg`, vous devez fournir la valeur appropriée pour *nCode*, le code de notification de commande, et *pExtra*, qui dépend de la valeur de *nCode* . Le tableau suivant répertorie les valeurs correspondantes :  
  
|*nCode* valeur|*pExtra* valeur|  
|-------------------|--------------------|  
|CAS|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|  
|CN_EVENT|AFX_EVENT\*|  
|CN_UPDATE_COMMAND_UI|CCmdUI\*|  
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|  
|CN_OLE_UNREGISTER|NULL|  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]  
  
##  <a name="onfinalrelease"></a>  CCmdTarget::OnFinalRelease  
 Appelé par l’infrastructure lors de la dernière référence OLE vers ou à partir de l’objet est libérée.  
  
```  
virtual void OnFinalRelease();
```  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour fournir une gestion spéciale pour cette situation. L’implémentation par défaut supprime l’objet.  
  
##  <a name="restorewaitcursor"></a>  CCmdTarget::RestoreWaitCursor  
 Appelez cette fonction pour restaurer le curseur sablier approprié une fois que le curseur du système a changé (par exemple, une fois une boîte de message ouverts et fermés puis au milieu d’une opération longue).  
  
```  
void RestoreWaitCursor();
```  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC ACDUAL](../../visual-cpp-samples.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CCmdUI, classe](../../mfc/reference/ccmdui-class.md)   
 [CDocument (classe)](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)   
 [CWinApp (classe)](../../mfc/reference/cwinapp-class.md)   
 [CWnd, classe](../../mfc/reference/cwnd-class.md)   
 [CView (classe)](../../mfc/reference/cview-class.md)   
 [CFrameWnd (classe)](../../mfc/reference/cframewnd-class.md)   
 [COleDispatchDriver, classe](../../mfc/reference/coledispatchdriver-class.md)
