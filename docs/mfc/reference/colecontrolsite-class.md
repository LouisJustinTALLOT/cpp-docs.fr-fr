---
title: Classe de COleControlSite | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleControlSite
- AFXOCC/COleControlSite
- AFXOCC/COleControlSite::COleControlSite
- AFXOCC/COleControlSite::BindDefaultProperty
- AFXOCC/COleControlSite::BindProperty
- AFXOCC/COleControlSite::CreateControl
- AFXOCC/COleControlSite::DestroyControl
- AFXOCC/COleControlSite::DoVerb
- AFXOCC/COleControlSite::EnableDSC
- AFXOCC/COleControlSite::EnableWindow
- AFXOCC/COleControlSite::FreezeEvents
- AFXOCC/COleControlSite::GetDefBtnCode
- AFXOCC/COleControlSite::GetDlgCtrlID
- AFXOCC/COleControlSite::GetEventIID
- AFXOCC/COleControlSite::GetExStyle
- AFXOCC/COleControlSite::GetProperty
- AFXOCC/COleControlSite::GetStyle
- AFXOCC/COleControlSite::GetWindowText
- AFXOCC/COleControlSite::InvokeHelper
- AFXOCC/COleControlSite::InvokeHelperV
- AFXOCC/COleControlSite::IsDefaultButton
- AFXOCC/COleControlSite::IsWindowEnabled
- AFXOCC/COleControlSite::ModifyStyle
- AFXOCC/COleControlSite::ModifyStyleEx
- AFXOCC/COleControlSite::MoveWindow
- AFXOCC/COleControlSite::QuickActivate
- AFXOCC/COleControlSite::SafeSetProperty
- AFXOCC/COleControlSite::SetDefaultButton
- AFXOCC/COleControlSite::SetDlgCtrlID
- AFXOCC/COleControlSite::SetFocus
- AFXOCC/COleControlSite::SetProperty
- AFXOCC/COleControlSite::SetPropertyV
- AFXOCC/COleControlSite::SetWindowPos
- AFXOCC/COleControlSite::SetWindowText
- AFXOCC/COleControlSite::ShowWindow
- AFXOCC/COleControlSite::GetControlInfo
- AFXOCC/COleControlSite::m_bIsWindowless
- AFXOCC/COleControlSite::m_ctlInfo
- AFXOCC/COleControlSite::m_dwEventSink
- AFXOCC/COleControlSite::m_dwMiscStatus
- AFXOCC/COleControlSite::m_dwPropNotifySink
- AFXOCC/COleControlSite::m_dwStyle
- AFXOCC/COleControlSite::m_hWnd
- AFXOCC/COleControlSite::m_iidEvents
- AFXOCC/COleControlSite::m_nID
- AFXOCC/COleControlSite::m_pActiveObject
- AFXOCC/COleControlSite::m_pCtrlCont
- AFXOCC/COleControlSite::m_pInPlaceObject
- AFXOCC/COleControlSite::m_pObject
- AFXOCC/COleControlSite::m_pWindowlessObject
- AFXOCC/COleControlSite::m_pWndCtrl
- AFXOCC/COleControlSite::m_rect
dev_langs:
- C++
helpviewer_keywords:
- COleControlSite [MFC], COleControlSite
- COleControlSite [MFC], BindDefaultProperty
- COleControlSite [MFC], BindProperty
- COleControlSite [MFC], CreateControl
- COleControlSite [MFC], DestroyControl
- COleControlSite [MFC], DoVerb
- COleControlSite [MFC], EnableDSC
- COleControlSite [MFC], EnableWindow
- COleControlSite [MFC], FreezeEvents
- COleControlSite [MFC], GetDefBtnCode
- COleControlSite [MFC], GetDlgCtrlID
- COleControlSite [MFC], GetEventIID
- COleControlSite [MFC], GetExStyle
- COleControlSite [MFC], GetProperty
- COleControlSite [MFC], GetStyle
- COleControlSite [MFC], GetWindowText
- COleControlSite [MFC], InvokeHelper
- COleControlSite [MFC], InvokeHelperV
- COleControlSite [MFC], IsDefaultButton
- COleControlSite [MFC], IsWindowEnabled
- COleControlSite [MFC], ModifyStyle
- COleControlSite [MFC], ModifyStyleEx
- COleControlSite [MFC], MoveWindow
- COleControlSite [MFC], QuickActivate
- COleControlSite [MFC], SafeSetProperty
- COleControlSite [MFC], SetDefaultButton
- COleControlSite [MFC], SetDlgCtrlID
- COleControlSite [MFC], SetFocus
- COleControlSite [MFC], SetProperty
- COleControlSite [MFC], SetPropertyV
- COleControlSite [MFC], SetWindowPos
- COleControlSite [MFC], SetWindowText
- COleControlSite [MFC], ShowWindow
- COleControlSite [MFC], GetControlInfo
- COleControlSite [MFC], m_bIsWindowless
- COleControlSite [MFC], m_ctlInfo
- COleControlSite [MFC], m_dwEventSink
- COleControlSite [MFC], m_dwMiscStatus
- COleControlSite [MFC], m_dwPropNotifySink
- COleControlSite [MFC], m_dwStyle
- COleControlSite [MFC], m_hWnd
- COleControlSite [MFC], m_iidEvents
- COleControlSite [MFC], m_nID
- COleControlSite [MFC], m_pActiveObject
- COleControlSite [MFC], m_pCtrlCont
- COleControlSite [MFC], m_pInPlaceObject
- COleControlSite [MFC], m_pObject
- COleControlSite [MFC], m_pWindowlessObject
- COleControlSite [MFC], m_pWndCtrl
- COleControlSite [MFC], m_rect
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61544026f559e0c45cbd81735e76203a088d2d6b
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040871"
---
# <a name="colecontrolsite-class"></a>Classe de COleControlSite
Prend en charge les interfaces de contrôle côté client personnalisées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleControlSite : public CCmdTarget  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleControlSite::COleControlSite](#colecontrolsite)|Construit un objet `COleControlSite`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|Lie la propriété par défaut du contrôle hébergé à une source de données.|  
|[COleControlSite::BindProperty](#bindproperty)|Lie une propriété du contrôle hébergé à une source de données.|  
|[COleControlSite::CreateControl](#createcontrol)|Crée un contrôle ActiveX hébergé.|  
|[COleControlSite::DestroyControl](#destroycontrol)|Détruit le contrôle hébergé.|  
|[COleControlSite::DoVerb](#doverb)|Exécute un verbe spécifique du contrôle hébergé.|  
|[COleControlSite::EnableDSC](#enabledsc)|Permet d’un site de contrôle de source de données.|  
|[COleControlSite::EnableWindow](#enablewindow)|Permet le contrôle site.|  
|[COleControlSite::FreezeEvents](#freezeevents)|Spécifie si le site de contrôle accepte d’événements.|  
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|Récupère le code du bouton par défaut pour le contrôle hébergé.|  
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|Récupère l’identificateur du contrôle.|  
|[COleControlSite::GetEventIID](#geteventiid)|Récupère l’ID d’une interface d’événement pour un contrôle hébergé.|  
|[COleControlSite::GetExStyle](#getexstyle)|Récupère les styles étendus de contrôle.|  
|[COleControlSite::GetProperty](#getproperty)|Récupère une propriété spécifique du contrôle hébergé.|  
|[COleControlSite::GetStyle](#getstyle)|Récupère les styles de contrôle.|  
|[COleControlSite::GetWindowText](#getwindowtext)|Récupère le texte du contrôle hébergé.|  
|[COleControlSite::InvokeHelper](#invokehelper)|Appeler une méthode spécifique du contrôle hébergé.|  
|[COleControlSite::InvokeHelperV](#invokehelperv)|Appeler une méthode spécifique du contrôle hébergé avec une liste d’arguments de variables.|  
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|Détermine si le contrôle est le bouton par défaut dans la fenêtre.|  
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|Vérifie l’état visible du site de contrôle.|  
|[COleControlSite::ModifyStyle](#modifystyle)|Modifie l’étendue des styles de contrôle d’actuel.|  
|[COleControlSite::ModifyStyleEx](#modifystyleex)|Modifie les styles de contrôle en cours.|  
|[COleControlSite::MoveWindow](#movewindow)|Modifie la position de contrôle.|  
|[COleControlSite::QuickActivate](#quickactivate)|Rapide active le contrôle hébergé.|  
|[COleControlSite::SafeSetProperty](#safesetproperty)|Définit une propriété ou méthode du contrôle sans risque de lever une exception.|  
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|Définit le bouton par défaut dans la fenêtre.|  
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|Récupère l’identificateur du contrôle.|  
|[COleControlSite::SetFocus](#setfocus)|Définit le focus sur le site du contrôle.|  
|[COleControlSite::SetProperty](#setproperty)|Définit une propriété spécifique du contrôle hébergé.|  
|[COleControlSite::SetPropertyV](#setpropertyv)|Définit une propriété spécifique du contrôle hébergé avec une liste d’arguments de variables.|  
|[COleControlSite::SetWindowPos](#setwindowpos)|Définit la position de contrôle.|  
|[COleControlSite::SetWindowText](#setwindowtext)|Définit le texte du contrôle hébergé.|  
|[COleControlSite::ShowWindow](#showwindow)|Affiche ou masque le site du contrôle.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[COleControlSite::GetControlInfo](#getcontrolinfo)|Récupère les informations du clavier et les mnémoniques pour le contrôle hébergé.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|Détermine si le contrôle hébergé est un contrôle sans fenêtre.|  
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|Contient des informations sur la gestion du clavier pour le contrôle.|  
|[COleControlSite::m_dwEventSink](#m_dweventsink)|Le cookie du contrôle point de connexion.|  
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|Les divers états pour le contrôle hébergé.|  
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|Le `IPropertyNotifySink` cookie du contrôle.|  
|[COleControlSite::m_dwStyle](#m_dwstyle)|Les styles du contrôle hébergé.|  
|[COleControlSite::m_hWnd](#m_hwnd)|La poignée de contrôle.|  
|[COleControlSite::m_iidEvents](#m_iidevents)|ID de l’interface d’événement pour le contrôle hébergé.|  
|[COleControlSite::m_nID](#m_nid)|L’ID du contrôle hébergé.|  
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|Un pointeur vers le `IOleInPlaceActiveObject` objet du contrôle hébergé.|  
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|Le conteneur du contrôle hébergé.|  
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|Un pointeur vers le `IOleInPlaceObject` objet du contrôle hébergé.|  
|[COleControlSite::m_pObject](#m_pobject)|Un pointeur vers le `IOleObjectInterface` interface du contrôle.|  
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|Un pointeur vers le `IOleInPlaceObjectWindowless` interface du contrôle.|  
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|Pointeur vers l’objet de fenêtre pour le contrôle hébergé.|  
|[COleControlSite::m_rect](#m_rect)|Les dimensions du site de contrôle.|  
  
## <a name="remarks"></a>Notes  
 Cette prise en charge est le principal moyen par lequel un contrôle ActiveX incorporé obtient des informations sur l’emplacement et l’étendue de son site d’affichage, son moniker, son interface utilisateur, ses propriétés ambiantes et autres ressources fournies par son conteneur. `COleControlSite` implémente entièrement le [IOleControlSite](http://msdn.microsoft.com/library/windows/desktop/ms688502), [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586), [IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706), [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), `IBoundObjectSite`, `INotifyDBEvents`, [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md) interfaces. En outre, l’IDispatch interface (prise en charge pour les récepteurs d’événements et les propriétés ambiantes) est également implémentée.  
  
 Pour créer un site de contrôle ActiveX à l’aide `COleControlSite`, dérivez une classe de `COleControlSite`. Dans votre `CWnd`-classe dérivée pour le conteneur (par exemple, votre boîte de dialogue) remplacer le **CWnd::CreateControlSite** (fonction).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlSite`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxocc.h  
  
##  <a name="binddefaultproperty"></a>  COleControlSite::BindDefaultProperty  
 Lie par défaut simple propriété liée l’objet appelant, comme indiqué dans la bibliothèque de types, le curseur sous-jacent défini par les propriétés de source de données, nom d’utilisateur, mot de passe et SQL du contrôle de source de données.  
  
```  
virtual void BindDefaultProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    LPCTSTR szFieldName,  
    CWnd* pDSCWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDispID*  
 Spécifie le **DISPID** d’une propriété sur un contrôle lié aux données qui doit être lié à un contrôle de source de données.  
  
 *vtProp*  
 Spécifie le type de la propriété à lier, par exemple, **VT_BSTR**, **VT_VARIANT**, et ainsi de suite.  
  
 *szFieldName*  
 Spécifie le nom de la colonne, dans le curseur fourni par le contrôle de source de données auquel la propriété va être liée.  
  
 *pDSCWnd*  
 Un pointeur vers le `CWnd`-objet dérivé qui héberge le contrôle de source de données auquel la propriété va être liée.  
  
### <a name="remarks"></a>Notes  
 Le `CWnd` objet sur lequel vous appelez cette fonction doit être un contrôle lié aux données.  
  
##  <a name="bindproperty"></a>  COleControlSite::BindProperty  
 Lie la propriété de dépendant de l’objet appelant simple, comme indiqué dans la bibliothèque de types, le curseur sous-jacent défini par les propriétés de source de données, nom d’utilisateur, mot de passe et SQL du contrôle de source de données.  
  
```  
virtual void BindProperty(
    DISPID dwDispId,  
    CWnd* pWndDSC);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDispId*  
 Spécifie le **DISPID** d’une propriété sur un contrôle lié aux données qui doit être lié à un contrôle de source de données.  
  
 *pWndDSC*  
 Un pointeur vers le `CWnd`-objet dérivé qui héberge le contrôle de source de données auquel la propriété va être liée.  
  
### <a name="remarks"></a>Notes  
 Le `CWnd` objet sur lequel vous appelez cette fonction doit être un contrôle lié aux données.  
  
##  <a name="colecontrolsite"></a>  COleControlSite::COleControlSite  
 Construit un nouveau `COleControlSite` objet.  
  
```  
explicit COleControlSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>Paramètres  
 *pCtrlCont*  
 Pointeur vers le conteneur du contrôle (qui représente la fenêtre qui héberge le contrôle ActiveX).  
  
### <a name="remarks"></a>Notes  
 Cette fonction est appelée par le [COccManager::CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer) (fonction). Pour plus d’informations sur la personnalisation de la création de conteneurs, consultez [COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite).  
  
##  <a name="createcontrol"></a>  COleControlSite::CreateControl  
 Crée un contrôle ActiveX, hébergé par le `COleControlSite` objet.  
  
```  
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,  
    REFCLSID clsid,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    UINT nID,  
    CFile* pPersist = NULL,  
    BOOL bStorage = FALSE,  
    BSTR bstrLicKey = NULL);

 
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,  
    REFCLSID clsid,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const POINT* ppt,  
    const SIZE* psize,  
    UINT nID,  
    CFile* pPersist = NULL,  
    BOOL bStorage = FALSE,  
    BSTR bstrLicKey = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWndCtrl*  
 Pointeur vers l’objet de fenêtre qui représente le contrôle.  
  
 *clsid*  
 L’ID de classe unique du contrôle.  
  
 *lpszWindowName*  
 Pointeur vers le texte à afficher dans le contrôle. Définit la valeur de propriété de légende ou le texte de la winodw (le cas échéant).  
  
 *dwStyle*  
 Styles de Windows. Les styles disponibles sont répertoriés sous la **notes** section.  
  
 *Rect*  
 Spécifie la taille et la position du contrôle. Il peut être soit un `CRect` objet ou un `RECT` structure.  
  
 *nID*  
 Spécifie la fenêtre de l’enfant. du contrôle  
  
 *pPersist*  
 Un pointeur vers un `CFile` contenant l’état persistant pour le contrôle. La valeur par défaut est **NULL**, indiquant que le contrôle s’initialise sans restaurer son état à partir de n’importe quel stockage persistant. Si ce n’est pas **NULL**, il doit être un pointeur vers un `CFile`-objet qui contient les données du contrôle persistant, sous la forme d’un flux ou un stockage dérivé. Ces données pourraient ont été enregistrées dans l’activation d’une précédente du client. Le `CFile` peut contenir des autres données, mais doit avoir son pointeur en lecture-écriture au moment de l’appel à la valeur du premier octet de données persistantes `CreateControl`.  
  
 *bStorage*  
 Indique si les données de *pPersist* doivent être interprétées comme `IStorage` ou `IStream` données. Si les données de *pPersist* est un stockage, *bStorage* doit être **TRUE**. Si les données de *pPersist* est un flux de données, *bStorage* doit être **FALSE**. La valeur par défaut est **FALSE**.  
  
 *bstrLicKey*  
 Données de clé de licence facultatif. Ces données sont nécessaire uniquement pour la création de contrôles qui nécessitent une clé de licence d’exécution. Si le contrôle prend en charge le Gestionnaire de licences, vous devez fournir une clé de licence pour la création du contrôle réussisse. La valeur par défaut est **NULL**.  
  
 *ppt*  
 Un pointeur vers un **POINT** structure qui contient l’angle supérieur gauche du contrôle. La taille du contrôle est déterminée par la valeur de *psize*. Le *ppt* et *psize* valeurs sont une méthode facultative de spécification de la taille et position opf le contrôle.  
  
 *psize*  
 Un pointeur vers un **taille** structure qui contient la taille du contrôle. L’angle supérieur gauche est déterminé par la valeur de *ppt*. Le *ppt* et *psize* valeurs sont une méthode facultative de spécification de la taille et position opf le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Seul un sous-ensemble des fenêtres *dwStyle* indicateurs sont pris en charge par `CreateControl`:  
  
- **WS_VISIBLE** crée une fenêtre est visible initialement. Requis si vous souhaitez que le contrôle soit visible immédiatement, comme des fenêtres ordinaires.  
  
- **WS_DISABLED** crée une fenêtre qui est initialement désactivée. Une fenêtre désactivée ne peut pas recevoir d’entrée de l’utilisateur. Peut être définie si le contrôle a une propriété activé.  
  
- **WS_BORDER** crée une fenêtre avec une bordure de ligne dynamique. Peut être définie si le contrôle a une propriété BorderStyle.  
  
- **WS_GROUP** Spécifie le premier contrôle d’un groupe de contrôles. L’utilisateur peut modifier le focus clavier d’un contrôle dans le groupe à l’autre en utilisant les touches de direction. Tous les contrôles définis avec la **WS_GROUP** après le premier contrôle appartiennent au même groupe de style. Le contrôle suivant avec le **WS_GROUP** style met fin au groupe et démarre le groupe suivant.  
  
- **WS_TABSTOP** spécifie un contrôle qui peut recevoir le focus clavier lorsque l’utilisateur appuie sur la touche TAB. En appuyant sur la touche TAB modifie le focus clavier au contrôle suivant de la **WS_TABSTOP** style.  
  
 La deuxième surcharge permet de créer des contrôles de taille par défaut.  
  
##  <a name="destroycontrol"></a>  COleControlSite::DestroyControl  
 Détruit le `COleControlSite` objet.  
  
```  
virtual BOOL DestroyControl();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite, sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Une fois terminé, l’objet est libéré de la mémoire et tous les pointeurs à l’objet ne sont plus valides.  
  
##  <a name="doverb"></a>  COleControlSite::DoVerb  
 Exécute le verbe spécifié.  
  
```  
virtual HRESULT DoVerb(
    LONG nVerb,  
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *nVerb*  
 Spécifie le verbe à exécuter. Il peut inclure un des éléments suivants :  
  
|Value|Signification|Symbole|  
|-----------|-------------|------------|  
|0|Primary (verbe)|`OLEIVERB_PRIMARY`|  
|-1|Verbe secondaire|(Aucun)|  
|1|Affiche l’objet à modifier.|`OLEIVERB_SHOW`|  
|-2|Modifie l’élément dans une fenêtre distincte.|`OLEIVERB_OPEN`|  
|-3|Masque l’objet.|`OLEIVERB_HIDE`|  
|-4|Active un contrôle en place.|`OLEIVERB_UIACTIVATE`|  
|-5|Active un contrôle en place, sans les éléments d’interface utilisateur.|`OLEIVERB_INPLACEACTIVATE`|  
|-7|Afficher les propriétés du contrôle.|`OLEIVERB_PROPERTIES`|  
  
 *lpMsg*  
 Pointeur vers le message qui a provoqué l’élément d’être activées.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Cette fonction appelle directement par le biais du contrôle `IOleObject` interface pour exécuter le verbe spécifié. Si une exception est levée à la suite de cet appel de fonction, un `HRESULT` code d’erreur est retourné.  
  
 Pour plus d’informations, consultez [IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) dans le Kit de développement logiciel Windows.  
  
##  <a name="enabledsc"></a>  COleControlSite::EnableDSC  
 Active pour le site de contrôle de source de données.  
  
```  
virtual void EnableDSC();
```  
  
### <a name="remarks"></a>Notes  
 Appelé par l’infrastructure pour activer et initialiser pour le site de contrôle de source de données. Remplacez cette fonction pour fournir le comportement personnalisé.  
  
##  <a name="enablewindow"></a>  COleControlSite::EnableWindow  
 Active ou désactive la souris et clavier pour le site de contrôle.  
  
```  
virtual BOOL EnableWindow(BOOL bEnable);
```  
  
### <a name="parameters"></a>Paramètres  
 *bActivez*  
 Spécifie s’il faut activer ou désactiver la fenêtre : **TRUE** si l’entrée de la fenêtre est activée, sinon **FALSE**.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fenêtre a été précédemment désactivée, sinon, 0.  
  
##  <a name="freezeevents"></a>  COleControlSite::FreezeEvents  
 Spécifie si le site du contrôle sera gérer ou ignorer des événements déclenchés à partir d’un contrôle.  
  
```  
void FreezeEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>Paramètres  
 *bFreeze*  
 Spécifie si le site de contrôle souhaite cesser d'accepter des événements. Différent de zéro si le contrôle n’accepte pas d’événements ; Sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Si *bFreeze* est **TRUE**, le site de contrôle demande le contrôle à arrêter fring des événements. Si *bFreeze* est **FALSE**, le site de contrôle demande le contrôle pour poursuivre le déclenchement d’événements.  
  
> [!NOTE]
>  Le contrôle n’est pas nécessaire d’arrêter le déclenchement des événements si demandé par le site du contrôle. Il peut continuer, mais tous les événements suivants sont ignorées par le site du contrôle.  
  
##  <a name="getcontrolinfo"></a>  COleControlSite::GetControlInfo  
 Récupère des informations sur les touches mnémoniques et le comportement du clavier d’un contrôle.  
  
```  
void GetControlInfo();
```  
  
### <a name="remarks"></a>Notes  
 Les informations sont stockées dans [COleControlSite::m_ctlInfo](#m_ctlinfo).  
  
##  <a name="getdefbtncode"></a>  COleControlSite::GetDefBtnCode  
 Détermine si le contrôle est un bouton de commande par défaut.  
  
```  
DWORD GetDefBtnCode();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Peut avoir l'une des valeurs suivantes :  
  
- **DLGC_DEFPUSHBUTTON** contrôle est le bouton par défaut dans la boîte de dialogue.  
  
- **DLGC_UNDEFPUSHBUTTON** contrôle n’est pas le bouton par défaut dans la boîte de dialogue.  
  
- **0** contrôle n’est pas un bouton.  
  
##  <a name="getdlgctrlid"></a>  COleControlSite::GetDlgCtrlID  
 Récupère l’identificateur du contrôle.  
  
```  
virtual int GetDlgCtrlID() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’identificateur d’élément de boîte de dialogue du contrôle.  
  
##  <a name="geteventiid"></a>  COleControlSite::GetEventIID  
 Récupère un pointeur vers l’interface d’événement par défaut du contrôle.  
  
```  
BOOL GetEventIID(IID* piid);
```  
  
### <a name="parameters"></a>Paramètres  
 *piid*  
 Un pointeur vers l’ID d’interface.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite, sinon, 0. En cas de réussite, *piid* contient l’ID de l’interface d’événement par défaut du contrôle.  
  
##  <a name="getexstyle"></a>  COleControlSite::GetExStyle  
 Récupère les styles étendus de la fenêtre.  
  
```  
virtual DWORD GetExStyle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La fenêtre de contrôle de l’étendue des styles.  
  
### <a name="remarks"></a>Notes  
 Pour récupérer les styles régulières, appelez [COleControlSite::GetStyle](#getstyle).  
  
##  <a name="getproperty"></a>  COleControlSite::GetProperty  
 Obtient la propriété du contrôle spécifiée par *dwDispID*.  
  
```  
virtual void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDispID*  
 Identifie l’ID de dispatch de la propriété trouvée sur la valeur par défaut du contrôle `IDispatch` interface, doit être récupéré.  
  
 *vtProp*  
 Spécifie le type de la propriété à récupérer. Pour les valeurs possibles, consultez la section Notes pour [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *pvProp*  
 Adresse de la variable qui recevra la valeur de propriété. Il doit correspondre au type spécifié par *vtProp*.  
  
### <a name="remarks"></a>Notes  
 La valeur est retournée via *pvProp*.  
  
##  <a name="getstyle"></a>  COleControlSite::GetStyle  
 Récupère les styles de contrôle.  
  
```  
virtual DWORD GetStyle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Styles de la fenêtre.  
  
### <a name="remarks"></a>Notes  
 Pour obtenir la liste des valeurs possibles, consultez [Styles Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles). Pour récupérer les styles étendus de contrôle, appelez [COleControlSite::GetExStyle](#getexstyle).  
  
##  <a name="getwindowtext"></a>  COleControlSite::GetWindowText  
 Récupère le texte actuel du contrôle.  
  
```  
virtual void GetWindowText(CString& str) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *str*  
 Une référence à un `CString` objet qui contient le texte actuel du contrôle.  
  
### <a name="remarks"></a>Notes  
 Si le contrôle prend en charge la propriété stock Caption, cette valeur est retournée. Si la propriété stock Caption n’est pas pris en charge, la valeur de la propriété de texte est retournée.  
  
##  <a name="invokehelper"></a>  COleControlSite::InvokeHelper  
 Appelle la méthode ou la propriété spécifiée par *dwDispID*, dans le contexte spécifié par *wFlags*.  
  
```  
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,  
    WORD wFlags,  
    VARTYPE vtRet,  
    void* pvRet,  
    const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDispID*  
 Identifie l’ID de dispatch de la propriété ou méthode, trouvée dans le contrôle `IDispatch` interface, à appeler.  
  
 *wFlags*  
 Indicateurs décrivant le contexte de l’appel à IDispatch::Invoke. Pour possible *wFlags* valeurs, consultez `IDispatch::Invoke` dans le Kit de développement logiciel Windows.  
  
 *vtRet*  
 Spécifie le type de la valeur de retour. Pour les valeurs possibles, consultez la section Notes pour [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *pvRet*  
 Adresse de la variable qui recevra la valeur de propriété ou la valeur de retour. Il doit correspondre au type spécifié par *vtRet*.  
  
 *pbParamInfo*  
 Pointeur vers une chaîne se terminant par null d’octets spécifiant les types des paramètres suivant *pbParamInfo*. Pour les valeurs possibles, consultez la section Notes pour [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Liste des variables de paramètres, des types spécifiés dans *pbParamInfo*.  
  
### <a name="remarks"></a>Notes  
 Le *pbParamInfo* paramètre spécifie les types des paramètres passés à la méthode ou propriété. La liste variable d’arguments est représentée par... dans la déclaration de syntaxe.  
  
 Cette fonction convertit les paramètres **VARIANTARG** valeurs, puis appelle la `IDispatch::Invoke` méthode sur le contrôle. Si l’appel à `IDispatch::Invoke` échoue, cette fonction lève une exception. Si le code d’état retourné par `IDispatch::Invoke` est `DISP_E_EXCEPTION`, cette fonction lève un `COleDispatchException` objet, sinon elle lève une `COleException`.  
  
##  <a name="invokehelperv"></a>  COleControlSite::InvokeHelperV  
 Appelle la méthode ou la propriété spécifiée par *dwDispID*, dans le contexte spécifié par *wFlags*.  
  
```  
virtual void InvokeHelperV(
    DISPID dwDispID,  
    WORD wFlags,  
    VARTYPE vtRet,  
    void* pvRet,  
    const BYTE* pbParamInfo,  
    va_list argList);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDispID*  
 Identifie l’ID de dispatch de la propriété ou méthode, trouvée dans le contrôle `IDispatch` interface, à appeler.  
  
 *wFlags*  
 Indicateurs décrivant le contexte de l’appel à IDispatch::Invoke.  
  
 *vtRet*  
 Spécifie le type de la valeur de retour. Pour les valeurs possibles, consultez la section Notes pour [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *pvRet*  
 Adresse de la variable qui recevra la valeur de propriété ou la valeur de retour. Il doit correspondre au type spécifié par *vtRet*.  
  
 *pbParamInfo*  
 Pointeur vers une chaîne se terminant par null d’octets spécifiant les types des paramètres suivant *pbParamInfo*. Pour les valeurs possibles, consultez la section Notes pour [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *argList*  
 Pointeur vers une liste d’arguments variable.  
  
### <a name="remarks"></a>Notes  
 Le *pbParamInfo* paramètre spécifie les types des paramètres passés à la méthode ou propriété. Paramètres supplémentaires pour la méthode ou propriété appelée peuvent être passés à l’aide de la *va_list* paramètre.  
  
 En règle générale, cette fonction est appelée par `COleControlSite::InvokeHelper`.  
  
##  <a name="isdefaultbutton"></a>  COleControlSite::IsDefaultButton  
 Détermine si le contrôle est le bouton par défaut.  
  
```  
BOOL IsDefaultButton();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le contrôle est le bouton par défaut dans la fenêtre, sinon, zéro.  
  
##  <a name="iswindowenabled"></a>  COleControlSite::IsWindowEnabled  
 Détermine si le site de contrôle est activé.  
  
```  
virtual BOOL IsWindowEnabled() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le contrôle est activé, sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 La valeur est récupérée à partir de la propriété du contrôle activé stock.  
  
##  <a name="m_biswindowless"></a>  COleControlSite::m_bIsWindowless  
 Détermine si l’objet est un contrôle sans fenêtre.  
  
```  
BOOL m_bIsWindowless;  
```  
  
### <a name="remarks"></a>Notes  
 Différent de zéro si le contrôle n’a aucune fenêtre, sinon, zéro.  
  
##  <a name="m_ctlinfo"></a>  COleControlSite::m_ctlInfo  
 Informations sur la gestion des entrées au clavier par le contrôle.  
  
```  
CONTROLINFO m_ctlInfo;  
```  
  
### <a name="remarks"></a>Notes  
 Ces informations sont stockées dans un [CONTROLINFO](http://msdn.microsoft.com/library/windows/desktop/ms680734) structure.  
  
##  <a name="m_dweventsink"></a>  COleControlSite::m_dwEventSink  
 Contient le cookie du point de connexion à partir de récepteur d’événements du contrôle.  
  
```  
DWORD m_dwEventSink;  
```  
  
##  <a name="m_dwmiscstatus"></a>  COleControlSite::m_dwMiscStatus  
 Contient diverses informations à propos du contrôle.  
  
```  
DWORD m_dwMiscStatus;  
```  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)dans le Kit de développement logiciel Windows.  
  
##  <a name="m_dwpropnotifysink"></a>  COleControlSite::m_dwPropNotifySink  
 Contient le [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) cookie.  
  
```  
DWORD m_dwPropNotifySink;  
```  
  
##  <a name="m_dwstyle"></a>  COleControlSite::m_dwStyle  
 Contient les styles de fenêtre du contrôle.  
  
```  
DWORD m_dwStyle;  
```  
  
##  <a name="m_hwnd"></a>  COleControlSite::m_hWnd  
 Contient le `HWND` du contrôle, ou **NULL** si le contrôle est sans fenêtre.  
  
```  
HWND m_hWnd;  
```  
  
##  <a name="m_iidevents"></a>  COleControlSite::m_iidEvents  
 Contient l’ID de l’interface du récepteur d’événements par défaut du contrôle.  
  
```  
IID m_iidEvents;  
```  
  
##  <a name="m_nid"></a>  COleControlSite::m_nID  
 Contient l’ID d’élément boîte de dialogue. du contrôle  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_pactiveobject"></a>  COleControlSite::m_pActiveObject  
 Contient le [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) interface du contrôle.  
  
```  
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;  
```  
  
##  <a name="m_pctrlcont"></a>  COleControlSite::m_pCtrlCont  
 Contient le conteneur du contrôle (représentant le formulaire).  
  
```  
COleControlContainer* m_pCtrlCont;  
```  
  
##  <a name="m_pinplaceobject"></a>  COleControlSite::m_pInPlaceObject  
 Contient le `IOleInPlaceObject` [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) interface du contrôle.  
  
```  
LPOLEINPLACEOBJECT m_pInPlaceObject;  
```  
  
##  <a name="m_pobject"></a>  COleControlSite::m_pObject  
 Contient le **IOleObjectInterface** interface du contrôle.  
  
```  
LPOLEOBJECT m_pObject;  
```  
  
##  <a name="m_pwindowlessobject"></a>  COleControlSite::m_pWindowlessObject  
 Contient le `IOleInPlaceObjectWindowless` [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) interface du contrôle.  
  
```  
IOleInPlaceObjectWindowless* m_pWindowlessObject;  
```  
  
##  <a name="m_pwndctrl"></a>  COleControlSite::m_pWndCtrl  
 Contient un pointeur vers le `CWnd` objet qui représente le contrôle lui-même.  
  
```  
CWnd* m_pWndCtrl;  
```  
  
##  <a name="m_rect"></a>  COleControlSite::m_rect  
 Contient les limites du contrôle, par rapport à la fenêtre du conteneur.  
  
```  
CRect m_rect;  
```  
  
##  <a name="modifystyle"></a>  COleControlSite::ModifyStyle  
 Modifie les styles du contrôle.  
  
```  
virtual BOOL ModifyStyle(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwRemove*  
 Les styles à supprimer les styles de fenêtre en cours.  
  
 *dwAdd*  
 Les styles à ajouter des styles de fenêtre en cours.  
  
 *nIndicateurs*  
 Positionnement des indicateurs des fenêtres. Pour obtenir la liste des valeurs possibles, consultez la [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) fonction dans le SDK Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les styles sont modifiées, sinon zéro.  
  
### <a name="remarks"></a>Notes  
 Achat d’actions propriété Enabled du contrôle sera modifié pour correspondre au paramètre de **WS_DISABLED**. Propriété de Style de bordure du contrôle stock sera modifiée pour correspondre au paramètre demandé pour `WS_BORDER`. Tous les autres styles sont appliqués directement à un handle de fenêtre du contrôle, s’il en existe.  
  
 Modifie les styles de fenêtre du contrôle. Styles d’être ajoutés ou supprimés peuvent être combinées à l’aide de l’opération de bits OR ( &#124; ) (opérateur). Consultez le [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) fonction dans le SDK Windows pour plus d’informations sur les styles de fenêtres disponibles.  
  
 Si *nIndicateurs* est différent de zéro, `ModifyStyle` appelle la fonction Win32 `SetWindowPos`et redessine la fenêtre en combinant *nIndicateurs* avec quatre indicateurs suivants :  
  
- `SWP_NOSIZE` Conserve la taille actuelle.  
  
- `SWP_NOMOVE` Conserve la position actuelle.  
  
- `SWP_NOZORDER` Conserve l’ordre de plan actuel.  
  
- `SWP_NOACTIVATE` N’active pas la fenêtre.  
  
 Pour modifier une fenêtre de styles étendus, appelez [ModifyStyleEx](#modifystyleex).  
  
##  <a name="modifystyleex"></a>  COleControlSite::ModifyStyleEx  
 Modifie les styles étendus du contrôle.  
  
```  
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwRemove*  
 Les styles étendus à supprimer les styles de fenêtre en cours.  
  
 *dwAdd*  
 Les styles étendus à ajouter des styles de fenêtre en cours.  
  
 *nIndicateurs*  
 Positionnement des indicateurs des fenêtres. Pour obtenir la liste des valeurs possibles, consultez la [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) fonction dans le SDK Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les styles sont modifiées, sinon zéro.  
  
### <a name="remarks"></a>Notes  
 La propriété du contrôle stock apparence sera modifiée pour correspondre au paramètre de **WS_EX_CLIENTEDGE**. Tous les autres styles de fenêtre étendus sont appliqués directement à un handle de fenêtre du contrôle, s’il en existe.  
  
 Modifie la fenêtre étendus des styles de l’objet de site du contrôle. Styles d’être ajoutés ou supprimés peuvent être combinées à l’aide de l’opération de bits OR ( &#124; ) (opérateur). Consultez le [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) fonction dans le SDK Windows pour plus d’informations sur les styles de fenêtres disponibles.  
  
 Si *nIndicateurs* est différent de zéro, `ModifyStyleEx` appelle la fonction Win32 `SetWindowPos`et redessine la fenêtre en combinant *nIndicateurs* avec quatre indicateurs suivants :  
  
- `SWP_NOSIZE` Conserve la taille actuelle.  
  
- `SWP_NOMOVE` Conserve la position actuelle.  
  
- `SWP_NOZORDER` Conserve l’ordre de plan actuel.  
  
- `SWP_NOACTIVATE` N’active pas la fenêtre.  
  
 Pour modifier une fenêtre de styles étendus, appelez [ModifyStyle](#modifystyle).  
  
##  <a name="movewindow"></a>  COleControlSite::MoveWindow  
 Modifie la position du contrôle.  
  
```  
virtual void MoveWindow(
    int x,  
    int y,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Paramètres  
 *x*  
 La nouvelle position du côté gauche de la fenêtre.  
  
 *y*  
 La nouvelle position du bord supérieur de la fenêtre.  
  
 *nWidth*  
 La nouvelle largeur de la fenêtre  
  
 *nHeight*  
 La nouvelle hauteur de la fenêtre.  
  
##  <a name="quickactivate"></a>  COleControlSite::QuickActivate  
 Rapide active le contrôle de contenu.  
  
```  
virtual BOOL QuickActivate();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le site de contrôle a été activé, sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée uniquement si l’utilisateur remplace le processus de création du contrôle.  
  
 Le `IPersist*::Load` et `IPersist*::InitNew` méthodes doivent être appelées après l’activation rapide. Le contrôle doit établir ses connexions aux récepteurs du conteneur pendant l’activation rapide. Toutefois, ces connexions ne sont pas actives jusqu'à ce que `IPersist*::Load` ou `IPersist*::InitNew` a été appelée.  
  
##  <a name="safesetproperty"></a>  COleControlSite::SafeSetProperty  
 Définit la propriété du contrôle spécifiée par *dwDispID*.  
  
```  
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDispID*  
 Identifie l’ID de dispatch de la propriété ou méthode, trouvée dans le contrôle `IDispatch` interface, à définir.  
  
 *vtProp*  
 Spécifie le type de propriété à définir. Pour les valeurs possibles, consultez la section Notes pour [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Un seul paramètre de type spécifié par *vtProp*.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Contrairement aux `SetProperty` et `SetPropertyV`, si une erreur s’est produite (par exemple, la tentative de définir une propriété qui n’existe pas), aucune exception n’est levée.  
  
##  <a name="setdefaultbutton"></a>  COleControlSite::SetDefaultButton  
 Définit le contrôle comme le bouton par défaut.  
  
```  
void SetDefaultButton(BOOL bDefault);
```  
  
### <a name="parameters"></a>Paramètres  
 *bNiveau par défaut*  
 Différent de zéro si le contrôle doit être le bouton par défaut ; Sinon, zéro.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Le contrôle doit avoir la **OLEMISC_ACTSLIKEBUTTON** état bit défini.  
  
##  <a name="setdlgctrlid"></a>  COleControlSite::SetDlgCtrlID  
 Modifie la valeur de l’identificateur d’élément boîte de dialogue du contrôle.  
  
```  
virtual int SetDlgCtrlID(int nID);
```  
  
### <a name="parameters"></a>Paramètres  
 *nID*  
 La nouvelle valeur de l’identificateur.  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, la boîte de dialogue précédente élément identificateur de la fenêtre. Sinon, 0.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setfocus"></a>  COleControlSite::SetFocus  
 Définit le focus sur le contrôle.  
  
```  
virtual CWnd* SetFocus();  
virtual CWnd* SetFocus(LPMSG lpmsg);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpmsg*  
 Un pointeur vers un [MSG, structure](../../mfc/reference/msg-structure1.md). Cette structure contient le message Windows déclenchant le `SetFocus` demande pour le contrôle contenu dans le site actuel du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la fenêtre qui avait le focus.  
  
##  <a name="setproperty"></a>  COleControlSite::SetProperty  
 Définit la propriété du contrôle spécifiée par *dwDispID*.  
  
```  
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDispID*  
 Identifie l’ID de dispatch de la propriété ou méthode, trouvée dans le contrôle `IDispatch` interface, à définir.  
  
 *vtProp*  
 Spécifie le type de propriété à définir. Pour les valeurs possibles, consultez la section Notes pour [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *...*  
 Un seul paramètre de type spécifié par *vtProp*.  
  
### <a name="remarks"></a>Notes  
 Si `SetProperty` rencontre une erreur, une exception est levée.  
  
 Le type d’exception est déterminé par la valeur de retour de la tentative de définition de la propriété ou méthode. Si la valeur de retour est `DISP_E_EXCEPTION`, un `COleDispatchExcpetion` est générée ; sinon une `COleException`.  
  
##  <a name="setpropertyv"></a>  COleControlSite::SetPropertyV  
 Définit la propriété du contrôle spécifiée par *dwDispID*.  
  
```  
virtual void SetPropertyV(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    va_list argList);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDispID*  
 Identifie l’ID de dispatch de la propriété ou méthode, trouvée dans le contrôle `IDispatch` interface, à définir.  
  
 *vtProp*  
 Spécifie le type de propriété à définir. Pour les valeurs possibles, consultez la section Notes pour [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper).  
  
 *argList*  
 Pointeur désignant la liste d’arguments.  
  
### <a name="remarks"></a>Notes  
 Paramètres supplémentaires pour la méthode ou propriété appelée peuvent être passeed à l’aide de la *arg_list* paramètre. Si `SetProperty` rencontre une erreur, une exception est levée.  
  
 Le type d’exception est déterminé par la valeur de retour de la tentative de définition de la propriété ou méthode. Si la valeur de retour est `DISP_E_EXCEPTION`, un `COleDispatchExcpetion` est générée ; sinon une `COleException`.  
  
##  <a name="setwindowpos"></a>  COleControlSite::SetWindowPos  
 Définit la taille, position et ordre de plan de contrôle.  
  
```  
virtual BOOL SetWindowPos(
    const CWnd* pWndInsertAfter,  
    int x,  
    int y,  
    int cx,  
    int cy,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWndInsertAfter*  
 Pointeur vers la fenêtre.  
  
 *x*  
 La nouvelle position du côté gauche de la fenêtre.  
  
 *y*  
 La nouvelle position du bord supérieur de la fenêtre.  
  
 *CX*  
 La nouvelle largeur de la fenêtre  
  
 *CY*  
 La nouvelle hauteur de la fenêtre.  
  
 *nIndicateurs*  
 Spécifie la fenêtre de dimensionnement et de positionnement des indicateurs. Pour les valeurs possibles, consultez la section Notes pour [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) dans le Kit de développement logiciel Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite, sinon, zéro.  
  
##  <a name="setwindowtext"></a>  COleControlSite::SetWindowText  
 Définit le texte pour le site de contrôle.  
  
```  
virtual void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszString*  
 Pointeur vers une chaîne se terminant par null à utiliser en tant que le nouveau texte de titre ou le contrôle.  
  
### <a name="remarks"></a>Notes  
 Cette fonction essaie d’abord de définir la propriété stock Caption. Si la propriété stock Caption n’est pas pris en charge, il se peut que la propriété de texte est définie à la place.  
  
##  <a name="showwindow"></a>  COleControlSite::ShowWindow  
 Définit l’état d’affichage de la fenêtre.  
  
```  
virtual BOOL ShowWindow(int nCmdShow);
```  
  
### <a name="parameters"></a>Paramètres  
 *nCmdShow*  
 Spécifie comment le site de contrôle doit être affiché. Il doit être une des valeurs suivantes :  
  
- **SW_HIDE** masque cette fenêtre et passe d’activation vers une autre fenêtre.  
  
- **SW_MINIMIZE** réduit la fenêtre et Active la fenêtre de niveau supérieur dans la liste du système.  
  
- **SW_RESTORE** active et affiche la fenêtre. Si la fenêtre est réduite ou agrandie, Windows le restaure à sa taille et la position d’origine.  
  
- **SW_SHOW** Active la fenêtre et l’affiche dans sa taille actuelle et sa position.  
  
- **SW_SHOWMAXIMIZED** Active la fenêtre et l’affiche sous une fenêtre agrandie.  
  
- **SW_SHOWMINIMIZED** Active la fenêtre et l’affiche sous forme d’icône.  
  
- **SW_SHOWMINNOACTIVE** affiche la fenêtre sous forme d’icône. La fenêtre actuellement active reste active.  
  
- **SW_SHOWNA** affiche la fenêtre dans son état actuel. La fenêtre actuellement active reste active.  
  
- **SW_SHOWNOACTIVATE** affiche la fenêtre dans sa taille et la position la plus récente. La fenêtre actuellement active reste active.  
  
- **SW_SHOWNORMAL** active et affiche la fenêtre. Si la fenêtre est réduite ou agrandie, Windows le restaure à sa taille et la position d’origine.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fenêtre a été précédemment visible ; 0 si la fenêtre a été précédemment masquée.  
  
## <a name="see-also"></a>Voir aussi  
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleControlContainer, classe](../../mfc/reference/colecontrolcontainer-class.md)
