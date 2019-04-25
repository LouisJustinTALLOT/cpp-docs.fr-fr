---
title: CDHtmlDialog Class
ms.date: 03/27/2019
f1_keywords:
- CDHtmlDialog
- AFXDHTML/CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CanAccessExternal
- AFXDHTML/CDHtmlDialog::CreateControlSite
- AFXDHTML/CDHtmlDialog::DDX_DHtml_AxControl
- AFXDHTML/CDHtmlDialog::DDX_DHtml_CheckBox
- AFXDHTML/CDHtmlDialog::DDX_DHtml_ElementText
- AFXDHTML/CDHtmlDialog::DDX_DHtml_Radio
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectIndex
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectString
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectValue
- AFXDHTML/CDHtmlDialog::DestroyModeless
- AFXDHTML/CDHtmlDialog::EnableModeless
- AFXDHTML/CDHtmlDialog::FilterDataObject
- AFXDHTML/CDHtmlDialog::GetControlDispatch
- AFXDHTML/CDHtmlDialog::GetControlProperty
- AFXDHTML/CDHtmlDialog::GetCurrentUrl
- AFXDHTML/CDHtmlDialog::GetDHtmlDocument
- AFXDHTML/CDHtmlDialog::GetDropTarget
- AFXDHTML/CDHtmlDialog::GetElement
- AFXDHTML/CDHtmlDialog::GetElementHtml
- AFXDHTML/CDHtmlDialog::GetElementInterface
- AFXDHTML/CDHtmlDialog::GetElementProperty
- AFXDHTML/CDHtmlDialog::GetElementText
- AFXDHTML/CDHtmlDialog::GetEvent
- AFXDHTML/CDHtmlDialog::GetExternal
- AFXDHTML/CDHtmlDialog::GetHostInfo
- AFXDHTML/CDHtmlDialog::GetOptionKeyPath
- AFXDHTML/CDHtmlDialog::HideUI
- AFXDHTML/CDHtmlDialog::IsExternalDispatchSafe
- AFXDHTML/CDHtmlDialog::LoadFromResource
- AFXDHTML/CDHtmlDialog::Navigate
- AFXDHTML/CDHtmlDialog::OnBeforeNavigate
- AFXDHTML/CDHtmlDialog::OnDocumentComplete
- AFXDHTML/CDHtmlDialog::OnDocWindowActivate
- AFXDHTML/CDHtmlDialog::OnFrameWindowActivate
- AFXDHTML/CDHtmlDialog::OnInitDialog
- AFXDHTML/CDHtmlDialog::OnNavigateComplete
- AFXDHTML/CDHtmlDialog::ResizeBorder
- AFXDHTML/CDHtmlDialog::SetControlProperty
- AFXDHTML/CDHtmlDialog::SetElementHtml
- AFXDHTML/CDHtmlDialog::SetElementProperty
- AFXDHTML/CDHtmlDialog::SetElementText
- AFXDHTML/CDHtmlDialog::SetExternalDispatch
- AFXDHTML/CDHtmlDialog::SetHostFlags
- AFXDHTML/CDHtmlDialog::ShowContextMenu
- AFXDHTML/CDHtmlDialog::ShowUI
- AFXDHTML/CDHtmlDialog::TranslateAccelerator
- AFXDHTML/CDHtmlDialog::TranslateUrl
- AFXDHTML/CDHtmlDialog::UpdateUI
- AFXDHTML/CDHtmlDialog::m_bUseHtmlTitle
- AFXDHTML/CDHtmlDialog::m_nHtmlResID
- AFXDHTML/CDHtmlDialog::m_pBrowserApp
- AFXDHTML/CDHtmlDialog::m_spHtmlDoc
- AFXDHTML/CDHtmlDialog::m_strCurrentUrl
- AFXDHTML/CDHtmlDialog::m_szHtmlResID
helpviewer_keywords:
- CDHtmlDialog [MFC], CDHtmlDialog
- CDHtmlDialog [MFC], CanAccessExternal
- CDHtmlDialog [MFC], CreateControlSite
- CDHtmlDialog [MFC], DDX_DHtml_AxControl
- CDHtmlDialog [MFC], DDX_DHtml_CheckBox
- CDHtmlDialog [MFC], DDX_DHtml_ElementText
- CDHtmlDialog [MFC], DDX_DHtml_Radio
- CDHtmlDialog [MFC], DDX_DHtml_SelectIndex
- CDHtmlDialog [MFC], DDX_DHtml_SelectString
- CDHtmlDialog [MFC], DDX_DHtml_SelectValue
- CDHtmlDialog [MFC], DestroyModeless
- CDHtmlDialog [MFC], EnableModeless
- CDHtmlDialog [MFC], FilterDataObject
- CDHtmlDialog [MFC], GetControlDispatch
- CDHtmlDialog [MFC], GetControlProperty
- CDHtmlDialog [MFC], GetCurrentUrl
- CDHtmlDialog [MFC], GetDHtmlDocument
- CDHtmlDialog [MFC], GetDropTarget
- CDHtmlDialog [MFC], GetElement
- CDHtmlDialog [MFC], GetElementHtml
- CDHtmlDialog [MFC], GetElementInterface
- CDHtmlDialog [MFC], GetElementProperty
- CDHtmlDialog [MFC], GetElementText
- CDHtmlDialog [MFC], GetEvent
- CDHtmlDialog [MFC], GetExternal
- CDHtmlDialog [MFC], GetHostInfo
- CDHtmlDialog [MFC], GetOptionKeyPath
- CDHtmlDialog [MFC], HideUI
- CDHtmlDialog [MFC], IsExternalDispatchSafe
- CDHtmlDialog [MFC], LoadFromResource
- CDHtmlDialog [MFC], Navigate
- CDHtmlDialog [MFC], OnBeforeNavigate
- CDHtmlDialog [MFC], OnDocumentComplete
- CDHtmlDialog [MFC], OnDocWindowActivate
- CDHtmlDialog [MFC], OnFrameWindowActivate
- CDHtmlDialog [MFC], OnInitDialog
- CDHtmlDialog [MFC], OnNavigateComplete
- CDHtmlDialog [MFC], ResizeBorder
- CDHtmlDialog [MFC], SetControlProperty
- CDHtmlDialog [MFC], SetElementHtml
- CDHtmlDialog [MFC], SetElementProperty
- CDHtmlDialog [MFC], SetElementText
- CDHtmlDialog [MFC], SetExternalDispatch
- CDHtmlDialog [MFC], SetHostFlags
- CDHtmlDialog [MFC], ShowContextMenu
- CDHtmlDialog [MFC], ShowUI
- CDHtmlDialog [MFC], TranslateAccelerator
- CDHtmlDialog [MFC], TranslateUrl
- CDHtmlDialog [MFC], UpdateUI
- CDHtmlDialog [MFC], m_bUseHtmlTitle
- CDHtmlDialog [MFC], m_nHtmlResID
- CDHtmlDialog [MFC], m_pBrowserApp
- CDHtmlDialog [MFC], m_spHtmlDoc
- CDHtmlDialog [MFC], m_strCurrentUrl
- CDHtmlDialog [MFC], m_szHtmlResID
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
ms.openlocfilehash: d53d3afb464b9dcfa32ab3cf4ee51446f8313a92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168061"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog Class

Permet de créer des boîtes de dialogue qui utilisent HTML plutôt que des ressources de boîte de dialogue pour implémenter leur interface utilisateur.

## <a name="syntax"></a>Syntaxe

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDHtmlDialog::CDHtmlDialog](#cdhtmldialog)|Construit un objet CDHtmlDialog.|
|[CDHtmlDialog::~CDHtmlDialog](#_dtorcdhtmldialog)|Détruit un objet CDHtmlDialog.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|Substituables qui est appelé une vérification pour voir si les objets de script sur la page chargée peuvent accéder à la distribution externe du site de contrôle d’accès. Vérifie que la distribution est soit sécurisé pour le script ou le fuseau actuel permet pour les objets qui ne sont pas sécurisés pour les scripts.|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|Overridable utilisé pour créer une instance de site de contrôle pour héberger le contrôle WebBrowser sur la boîte de dialogue.|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|Échange des données entre une variable de membre et la valeur de propriété d’un contrôle ActiveX sur une page HTML.|
|[CDHtmlDialog::DDX_DHtml_CheckBox](#ddx_dhtml_checkbox)|Échange des données entre une variable de membre et une case à cocher sur une page HTML.|
|[CDHtmlDialog::DDX_DHtml_ElementText](#ddx_dhtml_elementtext)|Échange des données entre une variable de membre et de n’importe quelle propriété d’élément HTML sur une page HTML.|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|Échange des données entre une variable de membre et un bouton radio sur une page HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|Obtient ou définit l’index d’une zone de liste sur une page HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectString](#ddx_dhtml_selectstring)|Obtient ou définit le texte d’affichage d’une entrée de zone de liste (selon l’index actuel) sur une page HTML.|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|Obtient ou définit la valeur d’une entrée de zone de liste (selon l’index actuel) sur une page HTML.|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|Détruit une boîte de dialogue non modale.|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|Permet de boîtes de dialogue non modale.|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|Permet à la boîte de dialogue Filtrer les objets de données du Presse-papiers créés par le navigateur hébergé.|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|Récupère le `IDispatch` interface sur un contrôle ActiveX incorporé dans le document HTML.|
|[CDHtmlDialog::GetControlProperty](#getcontrolproperty)|Récupère la propriété demandée du contrôle ActiveX spécifié.|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|Récupère l’URL Uniform Resource Locator () associés avec le document actif.|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|Récupère l’interface IHTMLDocument2 sur le document HTML actuellement chargé.|
|[CDHtmlDialog::GetDropTarget](#getdroptarget)|Appelé par le contrôle WebBrowser relation contenant-contenu quand il est utilisé comme cible de déplacement pour permettre la boîte de dialogue de fournir un autre [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).|
|[CDHtmlDialog::GetElement](#getelement)|Obtient une interface sur un élément HTML.|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|Récupère le `innerHTML` propriété d’un élément HTML.|
|[CDHtmlDialog::GetElementInterface](#getelementinterface)|Récupère le pointeur d’interface demandé à partir d’un élément HTML.|
|[CDHtmlDialog::GetElementProperty](#getelementproperty)|Récupère la valeur de propriété d’un élément HTML.|
|[CDHtmlDialog::GetElementText](#getelementtext)|Récupère le `innerText` propriété d’un élément HTML.|
|[CDHtmlDialog::GetEvent](#getevent)|Obtient le `IHTMLEventObj` pointeur vers l’objet d’événement en cours.|
|[CDHtmlDialog::GetExternal](#getexternal)|Obtient l’hôte `IDispatch` interface.|
|[CDHtmlDialog::GetHostInfo](#gethostinfo)|Récupère les fonctionnalités d’interface utilisateur de l’hôte.|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|Récupère la clé de Registre sous laquelle les préférences de l’utilisateur sont stockés.|
|[CDHtmlDialog::HideUI](#hideui)|Masque l’interface utilisateur de l’ordinateur hôte.|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|Indique si l’hôte `IDispatch` interface est sécurisé pour le script.|
|[CDHtmlDialog::LoadFromResource](#loadfromresource)|Charge la ressource spécifiée dans le contrôle WebBrowser.|
|[CDHtmlDialog::Navigate](#navigate)|Navigue vers l’URL spécifiée.|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|Appelé par l’infrastructure avant un événement de navigation est déclenché.|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|Appelé par l’infrastructure pour avertir une application lorsqu’un document atteint l’état READYSTATE_COMPLETE.|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|Appelé par l’infrastructure lors de la fenêtre de document est activée ou désactivée.|
|[CDHtmlDialog::OnFrameWindowActivate](#onframewindowactivate)|Appelé par l’infrastructure lors de la fenêtre frame est activée ou désactivée.|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|Appelée en réponse au message WM_INITDIALOG.|
|[CDHtmlDialog::OnNavigateComplete](#onnavigatecomplete)|Appelé par le framework après qu’un événement de navigation est terminé.|
|[CDHtmlDialog::ResizeBorder](#resizeborder)|Alerte de l’objet qu’il doit redimensionner son espace de bordure.|
|[CDHtmlDialog::SetControlProperty](#setcontrolproperty)|Définit la propriété d’un contrôle ActiveX à une nouvelle valeur.|
|[CDHtmlDialog::SetElementHtml](#setelementhtml)|Définit le `innerHTML` propriété d’un élément HTML.|
|[CDHtmlDialog::SetElementProperty](#setelementproperty)|Définit une propriété d’un élément HTML.|
|[CDHtmlDialog::SetElementText](#setelementtext)|Définit le `innerText` propriété d’un élément HTML.|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|Définit l’hôte `IDispatch` interface.|
|[CDHtmlDialog::SetHostFlags](#sethostflags)|Définit les indicateurs de l’interface utilisateur de l’ordinateur hôte.|
|[CDHtmlDialog::ShowContextMenu](#showcontextmenu)|Appelée lorsqu’un menu contextuel est sur le point d’être affiché.|
|[CDHtmlDialog::ShowUI](#showui)|Affiche l’interface utilisateur de l’ordinateur hôte.|
|[CDHtmlDialog::TranslateAccelerator](#translateaccelerator)|Appelé pour traiter les messages de touche d’accès rapide de menu.|
|[CDHtmlDialog::TranslateUrl](#translateurl)|Appelé pour modifier l’URL à charger.|
|[CDHtmlDialog::UpdateUI](#updateui)|Appelé pour avertir l’hôte que l’état de la commande a changé.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|Indique s’il faut utiliser le HTML titre du document en tant que légende de la boîte de dialogue.|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|Ressource ID de la ressource HTML à afficher.|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|Pointeur vers une application de navigateur Web.|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|Pointeur vers un document HTML.|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|L’URL actuelle.|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|Version de chaîne de l’ID de ressource HTML.|

## <a name="remarks"></a>Notes

`CDHtmlDialog` peut charger le code HTML à afficher à partir d’une ressource HTML ou une URL.

`CDHtmlDialog` peuvent également données échanger avec des contrôles HTML et gérer les événements de contrôles HTML, tels que les clics de bouton.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdhtml.h

##  <a name="ddx_dhtml_helper_macros"></a>  DDX_DHtml Helper Macros

Les macros d’assistance de DDX_DHtml permettent un accès facile aux propriétés des contrôles sur une page HTML couramment utilisés.

### <a name="data-exchange-macros"></a>Macros d’échange de données

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|Définit ou récupère la valeur de propriété à partir du contrôle sélectionné.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|Définit ou récupère le texte entre les balises de début et de fin de l’élément actuel.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|Définit ou récupère le code HTML entre les balises de début et de fin de l’élément actuel.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|Définit ou récupère la destination URL ou point d’ancrage.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|Définit ou récupère la fenêtre ou frame cible.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|Définit ou récupère le nom d’une image ou un clip vidéo dans le document.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|Définit ou récupère l’URL de l’image associée.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|Définit ou récupère l’URL de l’image associée.|

##  <a name="canaccessexternal"></a>  CDHtmlDialog::CanAccessExternal

Substituables qui est appelé une vérification pour voir si les objets de script sur la page chargée peuvent accéder à la distribution externe du site de contrôle d’accès. Vérifie que la distribution est soit sécurisé pour le script ou le fuseau actuel permet pour les objets qui ne sont pas sécurisés pour les scripts.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

##  <a name="cdhtmldialog"></a>  CDHtmlDialog::CDHtmlDialog

Construit une boîte de dialogue dynamique HTML ressource.

```
CDHtmlDialog();

CDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID,
    CWnd *pParentWnd = NULL);

CDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd *pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszTemplateName*<br/>
La chaîne se terminant par null qui est le nom d’une ressource de modèle de boîte de dialogue.

*szHtmlResID*<br/>
La chaîne se terminant par null qui est le nom d’une ressource HTML.

*pParentWnd*<br/>
Un pointeur vers l’objet de fenêtre parente ou propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la boîte de dialogue fenêtre l’objet parent est définie dans la fenêtre principale de l’application.

*nIDTemplate*<br/>
Contient le numéro d’ID d’une ressource de modèle de boîte de dialogue.

*nHtmlResID*<br/>
Contient le numéro d’ID d’une ressource HTML.

### <a name="remarks"></a>Notes

La deuxième forme du constructeur fournit l’accès à la ressource de boîte de dialogue via le nom du modèle. La troisième forme du constructeur fournit l’accès à la ressource de boîte de dialogue via l’ID du modèle de ressource. En règle générale, l’ID commence par la **IDD_** préfixe.

##  <a name="_dtorcdhtmldialog"></a>  CDHtmlDialog::~CDHtmlDialog

Détruit un objet CDHtmlDialog.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Notes

Le [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) fonction membre doit être utilisée pour détruire les boîtes de dialogue non modale qui sont créés par [CDialog::Create](../../mfc/reference/cdialog-class.md#create).

##  <a name="createcontrolsite"></a>  CDHtmlDialog::CreateControlSite

Overridable utilisé pour créer une instance de site de contrôle pour héberger le contrôle WebBrowser sur la boîte de dialogue.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>Paramètres

*pContainer*<br/>
Un pointeur vers le [COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md) objet

*ppSite*<br/>
Un pointeur vers un pointeur vers un [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous pouvez remplacer cette fonction membre pour retourner une instance de votre propre classe de site du contrôle.

##  <a name="ddx_dhtml_axcontrol"></a>  CDHtmlDialog::DDX_DHtml_AxControl

Échange des données entre une variable de membre et la valeur de propriété d’un contrôle ActiveX sur une page HTML.

```
void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    VARIANT& var);

void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    LPCTSTR szPropName,
    VARIANT& var);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*szId*<br/>
La valeur du paramètre d’ID de la balise object dans la source HTML pour le contrôle ActiveX.

*dispId*<br/>
L’ID de dispatch de la propriété avec laquelle vous souhaitez échanger des données.

*szPropName*<br/>
Nom de la propriété.

*var*<br/>
Le membre de données de type VARIANT, [COleVariant](../../mfc/reference/colevariant-class.md), ou [CComVariant](../../atl/reference/ccomvariant-class.md), qui contient la valeur échangée avec la propriété du contrôle ActiveX.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

##  <a name="ddx_dhtml_checkbox"></a>  CDHtmlDialog::DDX_DHtml_CheckBox

Échange des données entre une variable de membre et une case à cocher sur une page HTML.

```
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*szId*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*value*<br/>
La valeur qui est échangée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

##  <a name="ddx_dhtml_elementtext"></a>  CDHtmlDialog::DDX_DHtml_ElementText

Échange des données entre une variable de membre et de n’importe quelle propriété d’élément HTML sur une page HTML.

```
void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    CString& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    short& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    int& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    long& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    DWORD& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    float& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    double& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*szId*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*dispId*<br/>
L’ID de dispatch de l’élément HTML avec laquelle vous souhaitez échanger des données.

*value*<br/>
La valeur qui est échangée.

##  <a name="ddx_dhtml_radio"></a>  CDHtmlDialog::DDX_DHtml_Radio

Échange des données entre une variable de membre et un bouton radio sur une page HTML.

```
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*szId*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*value*<br/>
La valeur qui est échangée.

##  <a name="ddx_dhtml_selectindex"></a>  CDHtmlDialog::DDX_DHtml_SelectIndex

Obtient ou définit l’index d’une zone de liste sur une page HTML.

```
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*szId*<br/>
La valeur que vous avez spécifié pour le contrôle HTML `id` paramètre.

*value*<br/>
La valeur qui est échangée.

##  <a name="ddx_dhtml_selectstring"></a>  CDHtmlDialog::DDX_DHtml_SelectString

Obtient ou définit le texte d’affichage d’une entrée de zone de liste (selon l’index actuel) sur une page HTML.

```
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*szId*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*value*<br/>
La valeur qui est échangée.

##  <a name="ddx_dhtml_selectvalue"></a>  CDHtmlDialog::DDX_DHtml_SelectValue

Obtient ou définit la valeur d’une entrée de zone de liste (selon l’index actuel) sur une page HTML.

```
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*szId*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*value*<br/>
La valeur qui est échangée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

##  <a name="destroymodeless"></a>  CDHtmlDialog::DestroyModeless

Détache une boîte de dialogue non modale à partir de la `CDHtmlDialog` de l’objet et détruit l’objet.

```
void DestroyModeless();
```

##  <a name="enablemodeless"></a>  CDHtmlDialog::EnableModeless

Permet de boîtes de dialogue non modale.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>Paramètres

*fEnable*<br/>
Consultez *fEnable* dans [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="filterdataobject"></a>  CDHtmlDialog::FilterDataObject

Permet à la boîte de dialogue Filtrer les objets de données du Presse-papiers créés par le navigateur hébergé.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>Paramètres

*pDO*<br/>
Consultez *pDO* dans [IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) dans le SDK Windows.

*ppDORet*<br/>
Consultez *ppDORet* dans `IDocHostUIHandler::FilterDataObject` dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Returns S_FALSE.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="getcontroldispatch"></a>  CDHtmlDialog::GetControlDispatch

Récupère le `IDispatch` interface sur un contrôle ActiveX incorporé dans le document HTML retourné par [GetDHtmlDocument](#getdhtmldocument).

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>Paramètres

*szId*<br/>
L’ID HTML d’un contrôle ActiveX.

*ppdisp*<br/>
Le `IDispatch` interface du contrôle si trouvé dans la page Web.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="getcontrolproperty"></a>  CDHtmlDialog::GetControlProperty

Récupère la propriété demandée du contrôle ActiveX spécifié.

```
VARIANT GetControlProperty(
    LPCTSTR szId,
    LPCTSTR szPropName);

VARIANT GetControlProperty(
    LPCTSTR szId,
    DISPID dispId);

VARIANT GetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId);
```

### <a name="parameters"></a>Paramètres

*szId*<br/>
L’ID HTML d’un contrôle ActiveX.

*szPropName*<br/>
Le nom d’une propriété dans les paramètres régionaux par défaut de l’utilisateur actuel.

*pdispControl*<br/>
Le `IDispatch` pointeur d’un contrôle ActiveX.

*dispId*<br/>
L’ID de dispatch d’une propriété.

### <a name="return-value"></a>Valeur de retour

Une variante contenant la propriété demandée ou une variante vide si le contrôle ou la propriété est introuvable.

### <a name="remarks"></a>Notes

Les surcharges sont classés dans moins efficace dans la partie supérieure la plus efficace en bas.

##  <a name="getcurrenturl"></a>  CDHtmlDialog::GetCurrentUrl

Récupère l’URL Uniform Resource Locator () associés avec le document actif.

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>Paramètres

*szUrl*<br/>
Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet contenant l’URL à récupérer.

##  <a name="getdhtmldocument"></a>  CDHtmlDialog::GetDHtmlDocument

Récupère le [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) interface sur le document HTML actuellement chargé.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>Paramètres

*\*\*pphtmlDoc* un pointeur vers un pointeur vers un document HTML.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard. Retourne S_OK en cas de réussite.

##  <a name="getdroptarget"></a>  CDHtmlDialog::GetDropTarget

Appelé par le contrôle WebBrowser relation contenant-contenu quand il est utilisé comme cible de déplacement pour permettre la boîte de dialogue de fournir un autre [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>Paramètres

*pDropTarget*<br/>
Consultez *pDropTarget* dans [IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) dans le SDK Windows.

*ppDropTarget*<br/>
Consultez *ppDropTarget* dans `IDocHostUIHandler::GetDropTarget` dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="getelement"></a>  CDHtmlDialog::GetElement

Retourne une interface sur l’élément HTML spécifié par *szElementId*.

```
HRESULT GetElement(
    LPCTSTR szElementId,
    IDispatch** ppdisp,
    BOOL* pbCollection = NULL);

HRESULT GetElement(
    LPCTSTR szElementId,
    IHTMLElement** pphtmlElement);
```

### <a name="parameters"></a>Paramètres

*szElementId*<br/>
L’ID d’un élément HTML.

*ppdisp*<br/>
Un `IDispatch` pointeur vers l’élément demandé ou une collection d’éléments.

*pbCollection*<br/>
Une valeur Booléenne indiquant si l’objet représenté par *ppdisp* est un élément unique ou une collection d’éléments.

*pphtmlElement*<br/>
Un `IHTMLElement` pointeur vers l’élément demandé.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Utiliser la première surcharge si vous avez besoin gérer les conditions dans lesquelles il peut y avoir plus d’un élément avec l’ID spécifié. Vous pouvez utiliser le dernier paramètre pour déterminer si le pointeur d’interface retourné à une collection ou un seul élément. Si le pointeur d’interface se trouve sur une collection, vous pouvez interroger pour les `IHTMLElementCollection` et utiliser ses `item` propriété pour faire référence aux éléments par position ordinale.

La deuxième surcharge échoue s’il existe plusieurs éléments avec le même ID dans la page.

##  <a name="getelementhtml"></a>  CDHtmlDialog::GetElementHtml

Récupère le `innerHTML` propriété de l’élément HTML identifié par *szElementId*.

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>Paramètres

*szElementId*<br/>
L’ID d’un élément HTML.

### <a name="return-value"></a>Valeur de retour

Le `innerHTML` propriété de l’élément HTML identifié par *szElementId* ou NULL si l’élément n’a pas pu être trouvé.

##  <a name="getelementinterface"></a>  CDHtmlDialog::GetElementInterface

Récupère le pointeur d’interface demandé à partir de l’élément HTML identifié par *szElementId*.

```
template <class Q> HRESULT GetElementInterface(
    LPCTSTR szElementId,
    Q** ppvObj);

HRESULT GetElementInterface(
    LPCTSTR szElementId,
    REFIID refiid,
    void** ppvObj);
```

### <a name="parameters"></a>Paramètres

*szElementId*<br/>
L’ID d’un élément HTML.

*ppvObj*<br/>
Adresse d’un pointeur qui sera rempli avec le pointeur d’interface demandé si l’élément est trouvé et la requête réussit.

*refiid*<br/>
L’ID d’interface (IID) de l’interface demandée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

##  <a name="getelementproperty"></a>  CDHtmlDialog::GetElementProperty

Récupère la valeur de la propriété identifiée par *dispId* à partir de l’élément HTML identifié par *szElementId*.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>Paramètres

*szElementId*<br/>
L’ID d’un élément HTML.

*dispId*<br/>
L’ID de dispatch d’une propriété.

### <a name="return-value"></a>Valeur de retour

La valeur de la propriété ou une variante vide si la propriété ou l’élément est introuvable.

##  <a name="getelementtext"></a>  CDHtmlDialog::GetElementText

Récupère le `innerText` propriété de l’élément HTML identifié par *szElementId*.

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>Paramètres

*szElementId*<br/>
L’ID d’un élément HTML.

### <a name="return-value"></a>Valeur de retour

Le `innerText` propriété de l’élément HTML identifié par *szElementId* ou NULL si la propriété ou l’élément est introuvable.

##  <a name="getevent"></a>  CDHtmlDialog::GetEvent

Retourne le `IHTMLEventObj` pointeur vers l’objet d’événement en cours.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>Paramètres

*ppEventObj*<br/>
Adresse d’un pointeur qui sera rempli avec la `IHTMLEventObj` pointeur d’interface.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction doit uniquement être appelée à partir de dans un gestionnaire d’événements DHTML.

##  <a name="getexternal"></a>  CDHtmlDialog::GetExternal

Obtient l’hôte `IDispatch` interface.

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>Paramètres

*ppDispatch*<br/>
Consultez *ppDispatch* dans [IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite ou E_NOTIMPL en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="gethostinfo"></a>  CDHtmlDialog::GetHostInfo

Récupère les fonctionnalités d’interface utilisateur de l’hôte.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>Paramètres

*pInfo*<br/>
Consultez *pInfo* dans [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="getoptionkeypath"></a>  CDHtmlDialog::GetOptionKeyPath

Récupère la clé de Registre sous laquelle les préférences de l’utilisateur sont stockés.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>Paramètres

*pchKey*<br/>
Consultez *pchKey* dans [IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) dans le SDK Windows.

*dw*<br/>
Consultez *dw* dans `IDocHostUIHandler::GetOptionKeyPath` dans le Kit de développement logiciel Windows.

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="hideui"></a>  CDHtmlDialog::HideUI

Masque l’interface utilisateur de l’ordinateur hôte.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="isexternaldispatchsafe"></a>  CDHtmlDialog::IsExternalDispatchSafe

Indique si l’hôte `IDispatch` interface est sécurisé pour le script.

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur FALSE.

##  <a name="loadfromresource"></a>  CDHtmlDialog::LoadFromResource

Charge la ressource spécifiée dans le contrôle WebBrowser dans la boîte de dialogue DHTML.

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>Paramètres

*lpszResource*<br/>
Un pointeur vers une chaîne contenant le nom de la ressource à charger.

*nRes*<br/>
ID de la ressource à charger.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

##  <a name="m_busehtmltitle"></a>  CDHtmlDialog::m_bUseHtmlTitle

Indique s’il faut utiliser le HTML titre du document en tant que légende de la boîte de dialogue.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Notes

Si **m**_ **bUseHtmlTitle** a la valeur TRUE, la légende de la boîte de dialogue est définie comme égale au titre du document HTML ; sinon, la légende dans la ressource de boîte de dialogue est utilisée.

##  <a name="m_nhtmlresid"></a>  CDHtmlDialog::m_nHtmlResID

Ressource ID de la ressource HTML à afficher.

```
UINT m_nHtmlResID;
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

##  <a name="m_pbrowserapp"></a>  CDHtmlDialog::m_pBrowserApp

Pointeur vers une application de navigateur Web.

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

##  <a name="m_sphtmldoc"></a>  CDHtmlDialog::m_spHtmlDoc

Pointeur vers un document HTML.

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

##  <a name="m_strcurrenturl"></a>  CDHtmlDialog::m_strCurrentUrl

L’URL actuelle.

```
CString m_strCurrentUrl;
```

##  <a name="m_szhtmlresid"></a>  CDHtmlDialog::m_szHtmlResID

Version de chaîne de l’ID de ressource HTML.

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

##  <a name="navigate"></a>  CDHtmlDialog::Navigate

Accède à la ressource identifiée par l’URL spécifiée par *lpszURL*.

```
void Navigate(
    LPCTSTR lpszURL,
    DWORD dwFlags = 0,
    LPCTSTR lpszTargetFrameName = NULL,
    LPCTSTR lpszHeaders = NULL,
    LPVOID lpvPostData = NULL,
    DWORD dwPostDataLen = 0);
```

### <a name="parameters"></a>Paramètres

*lpszURL*<br/>
Un pointeur vers une chaîne contenant l’URL à cibler.

*dwFlags*<br/>
Les indicateurs d’une variable qui spécifie s’il faut ajouter la ressource à la liste d’historique lire dans le cache ou écrire à partir du cache et s’il faut afficher la ressource dans une nouvelle fenêtre. La variable peut être une combinaison des valeurs définies par le [BrowserNavConstants](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\)) énumération.

*lpszTargetFrameName*<br/>
Un pointeur vers une chaîne qui contient le nom du frame dans lequel afficher la ressource.

*lpszHeaders*<br/>
Pointeur vers une valeur qui spécifie les en-têtes HTTP à envoyer au serveur. Ces en-têtes sont ajoutés aux en-têtes Internet Explorer par défaut. Les en-têtes peuvent spécifier ces informations comme l’action requise du serveur, le type des données transmises sur le serveur, ou un code d’état. Ce paramètre est ignoré si l’URL n’est pas une URL HTTP.

*lpvPostData*<br/>
Pointeur vers les données à envoyer avec la transaction de la requête HTTP POST. Par exemple, la transaction de POST est utilisée pour envoyer des données collectées par un formulaire HTML. Si ce paramètre ne spécifie pas de toutes les données post, `Navigate` émet une transaction HTTP GET. Ce paramètre est ignoré si l’URL n’est pas une URL HTTP.

*dwPostDataLen*<br/>
Données à envoyer avec la transaction de la requête HTTP POST. Par exemple, la transaction de POST est utilisée pour envoyer des données collectées par un formulaire HTML. Si ce paramètre ne spécifie pas de toutes les données post, `Navigate` émet une transaction HTTP GET. Ce paramètre est ignoré si l’URL n’est pas une URL HTTP.

##  <a name="onbeforenavigate"></a>  CDHtmlDialog::OnBeforeNavigate

Appelé par l’infrastructure pour provoquer un événement se déclenche avant une navigation.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
Pointeur vers un objet `IDispatch` .

*szUrl*<br/>
Un pointeur vers une chaîne contenant l’URL à atteindre.

##  <a name="ondocumentcomplete"></a>  CDHtmlDialog::OnDocumentComplete

Appelé par l’infrastructure pour avertir une application lorsqu’un document a atteint l’état READYSTATE_COMPLETE.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
Pointeur vers un objet `IDispatch` .

*szUrl*<br/>
Un pointeur vers une chaîne contenant l’URL qui a été atteinte.

##  <a name="ondocwindowactivate"></a>  CDHtmlDialog::OnDocWindowActivate

Appelé par l’infrastructure lors de la fenêtre de document est activée ou désactivée.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Paramètres

*fActivate*<br/>
Consultez *fActivate* dans [IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="onframewindowactivate"></a>  CDHtmlDialog::OnFrameWindowActivate

Appelé par l’infrastructure lors de la fenêtre frame est activée ou désactivée.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Paramètres

*fActivate*<br/>
Consultez *fActivate* dans [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="oninitdialog"></a>  CDHtmlDialog::OnInitDialog

Appelée en réponse au message WM_INITDIALOG.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

L’implémentation par défaut retourne la valeur TRUE.

### <a name="remarks"></a>Notes

Ce message est envoyé à la boîte de dialogue pendant les `Create`, `CreateIndirect`, ou `DoModal` appels, qui se produisent immédiatement avant l’affichage de la boîte de dialogue.

Remplacez cette fonction membre, si vous avez besoin effectuer un traitement spécial lors de l’initialisation de la boîte de dialogue. Dans la version substituée, tout d’abord appeler la classe de base `OnInitDialog` mais ne pas tenir compte de sa valeur de retour. Vous renvoie normalement la valeur TRUE à partir de votre fonction membre substitué.

Appels de Windows le `OnInitDialog` fonctionner à travers de la procédure standard global-boîte de dialogue commune à toutes les boîtes de dialogue Bibliothèque Microsoft Foundation Class, plutôt que via votre table des messages, par conséquent, il est inutile une entrée de table des messages pour cette fonction membre.

##  <a name="onnavigatecomplete"></a>  CDHtmlDialog::OnNavigateComplete

Appelé par l’infrastructure après que la navigation vers l’URL spécifiée est terminée.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
Pointeur vers un objet `IDispatch` .

*szUrl*<br/>
Un pointeur vers une chaîne contenant l’URL qui a été atteinte.

##  <a name="resizeborder"></a>  CDHtmlDialog::ResizeBorder

Alerte de l’objet qu’il doit redimensionner son espace de bordure.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>Paramètres

*prcBorder*<br/>
Consultez *prcBorder* dans [IDocHostUIHandler::ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) dans le SDK Windows.

*pUIWindow*<br/>
Consultez *pUIWindow* dans `IDocHostUIHandler::ResizeBorder` dans le SDK Windows.

*fFrameWindow*<br/>
Consultez *fFrameWindow* dans `IDocHostUIHandler::ResizeBorder` dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

##  <a name="setcontrolproperty"></a>  CDHtmlDialog::SetControlProperty

Définit la propriété d’un contrôle ActiveX à une nouvelle valeur.

```
void SetControlProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    LPCTSTR szElementId,
    LPCTSTR szPropName,
    VARIANT* pVar);
```

### <a name="parameters"></a>Paramètres

*szElementId*<br/>
L’ID HTML d’un contrôle ActiveX.

*dispId*<br/>
L’ID de dispatch de la propriété à définir.

*pVar*<br/>
Pointeur vers un VARIANT contenant la nouvelle valeur de propriété.

*pdispControl*<br/>
Pointeur vers un contrôle ActiveX `IDispatch` interface.

*szPropName*<br/>
Chaîne contenant le nom de la propriété à définir.

##  <a name="setelementhtml"></a>  CDHtmlDialog::SetElementHtml

Définit le `innerHTML` propriété d’un élément HTML.

```
void SetElementHtml(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementHtml(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Paramètres

*szElementId*<br/>
L’ID d’un élément HTML.

*bstrText*<br/>
Nouvelle valeur de la propriété `innerHTML`.

*punkElem*<br/>
Le `IUnknown` pointeur d’un élément HTML.

##  <a name="setelementproperty"></a>  CDHtmlDialog::SetElementProperty

Définit une propriété d’un élément HTML.

```
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>Paramètres

*szElementId*<br/>
L’ID d’un élément HTML.

*dispId*<br/>
L’ID de dispatch de la propriété à définir.

*pVar*<br/>
Nouvelle valeur de la propriété.

##  <a name="setelementtext"></a>  CDHtmlDialog::SetElementText

Définit le `innerText` propriété d’un élément HTML.

```
void SetElementText(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementText(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>Paramètres

*szElementId*<br/>
L’ID d’un élément HTML.

*bstrText*<br/>
Nouvelle valeur de la propriété `innerText`.

*punkElem*<br/>
Le `IUnknown` pointeur d’un élément HTML.

##  <a name="setexternaldispatch"></a>  CDHtmlDialog::SetExternalDispatch

Définit l’hôte `IDispatch` interface.

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>Paramètres

*pdispExternal*<br/>
La nouvelle `IDispatch` interface.

##  <a name="sethostflags"></a>  CDHtmlDialog::SetHostFlags

Définit l’hôte des indicateurs de l’interface utilisateur.

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Pour connaître les valeurs possibles, consultez [DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) dans le SDK Windows.

##  <a name="showcontextmenu"></a>  CDHtmlDialog::ShowContextMenu

Appelée lorsqu’un menu contextuel est sur le point d’être affiché.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>Paramètres

*dwID*<br/>
Consultez *dwID* dans [IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) dans le SDK Windows.

*ppt*<br/>
Consultez *ppt* dans `IDocHostUIHandler::ShowContextMenu` dans le Kit de développement logiciel Windows.

*pcmdtReserved*<br/>
Consultez *pcmdtReserved* dans `IDocHostUIHandler::ShowContextMenu` dans le SDK Windows.

*pdispReserved*<br/>
Consultez *pdispReserved* dans `IDocHostUIHandler::ShowContextMenu` dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Returns S_FALSE.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="showui"></a>  CDHtmlDialog::ShowUI

Affiche l’interface utilisateur de l’ordinateur hôte.

```
STDMETHOD(ShowUI)(
    DWORD dwID,
    IOleInPlaceActiveObject* pActiveObject,
    IOleCommandTarget* pCommandTarget,
    IOleInPlaceFrame* pFrame,
    IOleInPlaceUIWindow* pDoc);
```

### <a name="parameters"></a>Paramètres

*dwID*<br/>
Consultez *dwID* dans [IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) dans le SDK Windows.

*pActiveObject*<br/>
Consultez *pActiveObject d* dans `IDocHostUIHandler::ShowUI` dans le SDK Windows.

*pCommandTarget*<br/>
Consultez *pCommandTarget* dans `IDocHostUIHandler::ShowUI` dans le SDK Windows.

*pFrame*<br/>
Consultez *pFrame* dans `IDocHostUIHandler::ShowUI` dans le SDK Windows.

*pDoc*<br/>
Consultez *pDoc* dans `IDocHostUIHandler::ShowUI` dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Returns S_FALSE.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="translateaccelerator"></a>  CDHtmlDialog::TranslateAccelerator

Appelé pour traiter les messages de touche d’accès rapide de menu.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>Paramètres

*lpMsg*<br/>
Consultez *lpMsg* dans [IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) dans le SDK Windows.

*pguidCmdGroup*<br/>
Consultez *pguidCmdGroup* dans `IDocHostUIHandler::TranslateAccelerator` dans le SDK Windows.

*nCmdID*<br/>
Consultez *nCmdID* dans `IDocHostUIHandler::TranslateAccelerator` dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Returns S_FALSE.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="translateurl"></a>  CDHtmlDialog::TranslateUrl

Appelé pour modifier l’URL à charger.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>Paramètres

*dwTranslate*<br/>
Consultez *dwTranslate* dans [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) dans le SDK Windows.

*pchURLIn*<br/>
Consultez *pchURLIn* dans `IDocHostUIHandler::TranslateUrl` dans le SDK Windows.

*ppchURLOut*<br/>
Consultez *ppchURLOut* dans `IDocHostUIHandler::TranslateUrl` dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Returns S_FALSE.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)), comme décrit dans le SDK Windows.

##  <a name="updateui"></a>  CDHtmlDialog::UpdateUI

Appelé pour avertir l’hôte que l’état de la commande a changé.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction membre est l’implémentation de CDHtmlDialog de [IDocHostUIHandler::UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\)), comme décrit dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[MFC exemple DHtmlExplore](../../overview/visual-cpp-samples.md)<br/>
[DDX_DHtml Helper, structure](#ddx_dhtml_helper_macros)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
