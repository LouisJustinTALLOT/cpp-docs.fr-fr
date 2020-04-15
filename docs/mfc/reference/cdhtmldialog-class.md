---
title: CDHtmlDialog, classe
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
ms.openlocfilehash: 57ea8f3a1dbbce4fcfa350bd99e4ee628e9675c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375684"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog, classe

Est utilisé pour créer des boîtes de dialogue qui utilisent HTML plutôt que de dialoguer les ressources pour implémenter leur interface utilisateur.

## <a name="syntax"></a>Syntaxe

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDHtmlDialog::CDHtmlDialog](#cdhtmldialog)|Construit un objet CDHtmlDialog.|
|[CDHtmlDialog:](#_dtorcdhtmldialog)|Détruit un objet CDHtmlDialog.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDHtmlDialog::CanAccessExternal](#canaccessexternal)|Dépassement qui est appelé comme une vérification d’accès pour voir si les objets de script sur la page chargée peuvent accéder à l’expédition externe du site de contrôle. Vérifie pour s’assurer que l’expédition est soit sûr pour le script ou la zone actuelle permet des objets qui ne sont pas sûrs pour le script.|
|[CDHtmlDialog::CreateControlSite](#createcontrolsite)|Utilisé pour créer une instance de site de contrôle pour héberger le contrôle WebBrowser sur le dialogue.|
|[CDHtmlDialog::DDX-DHtml-AxControl](#ddx_dhtml_axcontrol)|Échangez des données entre une variable de membre et la valeur de propriété d’un contrôle ActiveX sur une page HTML.|
|[CDHtmlDialog::DDX-DHtml-CheckBox](#ddx_dhtml_checkbox)|Échangez des données entre une variable de membre et une case à cocher sur une page HTML.|
|[CDHtmlDialog::DDX-DHtml-ElementText](#ddx_dhtml_elementtext)|Échangez des données entre une variable de membre et n’importe quelle propriété d’élément HTML sur une page HTML.|
|[CDHtmlDialog::DDX-DHtml-Radio](#ddx_dhtml_radio)|Échangez des données entre une variable de membre et un bouton radio sur une page HTML.|
|[CDHtmlDialog::DDX-DHtml-SelectIndex](#ddx_dhtml_selectindex)|Obtient ou définit l’index d’une boîte de liste sur une page HTML.|
|[CDHtmlDialog::DDX-DHtml-SelectString](#ddx_dhtml_selectstring)|Obtient ou définit le texte d’affichage d’une entrée de boîte de liste (basé sur l’index actuel) sur une page HTML.|
|[CDHtmlDialog::DDX-DHtml-SelectValue](#ddx_dhtml_selectvalue)|Obtient ou définit la valeur d’une entrée de boîte de liste (basée sur l’index actuel) sur une page HTML.|
|[CDHtmlDialog::DestroyModeless](#destroymodeless)|Détruit une boîte de dialogue sans mode.|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|Permet des boîtes de dialogue sans mode.|
|[CDHtmlDialog::FilterDataObject](#filterdataobject)|Permet au dialogue de filtrer les objets de données de presse-papiers créés par le navigateur hébergé.|
|[CDHtmlDialog::GetControlDispatch](#getcontroldispatch)|Récupère l’interface `IDispatch` sur un contrôle ActiveX intégré dans le document HTML.|
|[CDHtmlDialog::GetControlProperty](#getcontrolproperty)|Récupère la propriété demandée du contrôle ActiveX spécifié.|
|[CDHtmlDialog::GetCurrentUrl](#getcurrenturl)|Récupère le localisateur de ressources uniformes (URL) associé au document actuel.|
|[CDHtmlDialog::GetDHtmlDocument](#getdhtmldocument)|Récupère l’interface IHTMLDocument2 sur le document HTML actuellement chargé.|
|[CDHtmlDialog::GetDropTarget](#getdroptarget)|Appelé par le contrôle WebBrowser contenu quand il est utilisé comme une cible de chute pour permettre au dialogue de fournir une alternative [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).|
|[CDHtmlDialog::GetElement](#getelement)|Obtient une interface sur un élément HTML.|
|[CDHtmlDialog::GetElementHtml](#getelementhtml)|Récupère la `innerHTML` propriété d’un élément HTML.|
|[CDHtmlDialog::GetElementInterface](#getelementinterface)|Récupère le pointeur d’interface demandé à partir d’un élément HTML.|
|[CDHtmlDialog::GetElementProperty](#getelementproperty)|Récupère la valeur de la propriété d’un élément HTML.|
|[CDHtmlDialog::GetElementText](#getelementtext)|Récupère la `innerText` propriété d’un élément HTML.|
|[CDHtmlDialog::GetEvent](#getevent)|Obtient `IHTMLEventObj` le pointeur de l’objet événement actuel.|
|[CDHtmlDialog::GetExternal](#getexternal)|Obtient l’interface `IDispatch` de l’hôte.|
|[CDHtmlDialog::GetHostInfo](#gethostinfo)|Récupère les capacités d’interface utilisateur de l’hôte.|
|[CDHtmlDialog::GetOptionKeyPath](#getoptionkeypath)|Récupère la clé de registre en vertu de laquelle les préférences des utilisateurs sont stockées.|
|[CDHtmlDialog::HideUI](#hideui)|Cache l’interface utilisateur de l’hôte.|
|[CDHtmlDialog::IsExternalDispatchSafe](#isexternaldispatchsafe)|Indique si l’interface de `IDispatch` l’hôte est sûre pour le script.|
|[CDHtmlDialog::LoadDeResource](#loadfromresource)|Charge la ressource spécifiée dans le contrôle WebBrowser.|
|[CDHtmlDialog::Naviguer](#navigate)|Accède à l'URL spécifiée.|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|Appelé par le cadre avant qu’un événement de navigation ne soit déclenché.|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|Appelé par le cadre pour aviser une demande lorsqu’un document a atteint l’état READYSTATE_COMPLETE.|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|Appelé par le cadre lorsque la fenêtre de document est activée ou désactivée.|
|[CDHtmlDialog::OnFrameWindowActivate](#onframewindowactivate)|Appelé par le cadre lorsque la fenêtre de cadre est activée ou désactivée.|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|Appelé en réponse au message WM_INITDIALOG.|
|[CDHtmlDialog::OnNavigateComplete](#onnavigatecomplete)|Appelé par le cadre après un événement de navigation est terminée.|
|[CDHtmlDialog::ResizeBorder](#resizeborder)|Alerte l’objet dont il a besoin pour resize son espace frontalier.|
|[CDHtmlDialog::SetControlProperty](#setcontrolproperty)|Définit la propriété d’un contrôle ActiveX à une nouvelle valeur.|
|[CDHtmlDialog::SetElementHtml](#setelementhtml)|Définit `innerHTML` la propriété d’un élément HTML.|
|[CDHtmlDialog::SetElementProperty](#setelementproperty)|Définit une propriété d’un élément HTML.|
|[CDHtmlDialog::SetElementText](#setelementtext)|Définit `innerText` la propriété d’un élément HTML.|
|[CDHtmlDialog::SetExternalDispatch](#setexternaldispatch)|Définit l’interface `IDispatch` de l’hôte.|
|[CDHtmlDialog::SetHostFlags](#sethostflags)|Définit les drapeaux de l’interface utilisateur de l’hôte.|
|[CDHtmlDialog::ShowContextMenu](#showcontextmenu)|Appelé quand un menu contextuelle est sur le point d’être affiché.|
|[CDHtmlDialog::ShowUI](#showui)|Affiche l’interface utilisateur de l’hôte.|
|[CDHtmlDialog::TranslateAccelerator](#translateaccelerator)|Appelé à traiter les messages clés de l’accélérateur de menu.|
|[CDHtmlDialog::TranslateUrl](#translateurl)|Appelé à modifier l’URL à charger.|
|[CDHtmlDialog::UpdateUI](#updateui)|Appelé à aviser l’hôte que l’état de commandement a changé.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDHtmlDialog::m_bUseHtmlTitle](#m_busehtmltitle)|Indique s’il faut utiliser le titre du document HTML comme légende du dialogue.|
|[CDHtmlDialog::m_nHtmlResID](#m_nhtmlresid)|Id de ressources de la ressource HTML à afficher.|
|[CDHtmlDialog::m_pBrowserApp](#m_pbrowserapp)|Un pointeur vers une application de navigateur Web.|
|[CDHtmlDialog::m_spHtmlDoc](#m_sphtmldoc)|Un pointeur vers un document HTML.|
|[CDHtmlDialog::m_strCurrentUrl](#m_strcurrenturl)|L’URL actuelle.|
|[CDHtmlDialog::m_szHtmlResID](#m_szhtmlresid)|Version chaîne de l’ID de ressources HTML.|

## <a name="remarks"></a>Notes

`CDHtmlDialog`peut charger le HTML à afficher à partir d’une ressource HTML ou d’une URL.

`CDHtmlDialog`peut également effectuer l’échange de données avec des contrôles HTML et gérer les événements à partir de contrôles HTML, tels que les clics de boutons.

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

## <a name="requirements"></a>Spécifications

**En-tête:** afxdhtml.h

## <a name="ddx_dhtml-helper-macros"></a><a name="ddx_dhtml_helper_macros"></a>DDX_DHtml Aides Macros

Les macros d’aide DDX_DHtml permettent un accès facile aux propriétés couramment utilisées des contrôles sur une page HTML.

### <a name="data-exchange-macros"></a>Macros d’échange de données

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|Définit ou récupère la propriété Value à partir du contrôle sélectionné.|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|Définit ou récupère le texte entre les balises de démarrage et de fin de l’élément actuel.|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|Définit ou récupère le HTML entre les balises de démarrage et de fin de l’élément actuel.|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|Définit ou récupère l’URL de destination ou le point d’ancrage.|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|Définit ou récupère la fenêtre ou le cadre cible.|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|Définit ou récupère le nom d’une image ou d’un clip vidéo dans le document.|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|Définit ou récupère l’URL du cadre associé.|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|Définit ou récupère l’URL du cadre associé.|

## <a name="cdhtmldialogcanaccessexternal"></a><a name="canaccessexternal"></a>CDHtmlDialog::CanAccessExternal

Dépassement qui est appelé comme une vérification d’accès pour voir si les objets de script sur la page chargée peuvent accéder à l’expédition externe du site de contrôle. Vérifie pour s’assurer que l’expédition est soit sûr pour le script ou la zone actuelle permet des objets qui ne sont pas sûrs pour le script.

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="cdhtmldialogcdhtmldialog"></a><a name="cdhtmldialog"></a>CDHtmlDialog::CDHtmlDialog

Construit une boîte de dialogue HTML dynamique basée sur les ressources.

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
La chaîne non terminée qui est le nom d’une ressource de modèle de boîte de dialogue.

*szHtmlResID*<br/>
La chaîne non terminée qui est le nom d’une ressource HTML.

*pParentWnd*<br/>
Un pointeur vers l’objet de fenêtre du parent ou du propriétaire (du type [CWnd)](../../mfc/reference/cwnd-class.md)auquel appartient l’objet de dialogue. S’il s’agit de NULL, la fenêtre parente de l’objet de dialogue est réglée sur la fenêtre d’application principale.

*nIDTemplate (en)*<br/>
Contient le numéro d’identification d’une ressource de modèle de boîte de dialogue.

*nHtmlResID (en anglais)*<br/>
Contient le numéro d’identification d’une ressource HTML.

### <a name="remarks"></a>Notes

La deuxième forme du constructeur donne accès à la ressource de dialogue par le nom du modèle. La troisième forme du constructeur donne accès à la ressource de dialogue par l’intermédiaire de l’ID du modèle de ressources. Habituellement, l’ID commence par le **préfixe IDD_.**

## <a name="cdhtmldialogcdhtmldialog"></a><a name="_dtorcdhtmldialog"></a>CDHtmlDialog:

Détruit un objet CDHtmlDialog.

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Notes

La fonction de membre [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) doit être utilisée pour détruire les boîtes de dialogue sans mode qui sont créées par [CDialog::Créer](../../mfc/reference/cdialog-class.md#create).

## <a name="cdhtmldialogcreatecontrolsite"></a><a name="createcontrolsite"></a>CDHtmlDialog::CreateControlSite

Utilisé pour créer une instance de site de contrôle pour héberger le contrôle WebBrowser sur le dialogue.

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>Paramètres

*pContainer*<br/>
Un pointeur à l’objet [COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)

*ppSite*<br/>
Un pointeur à un pointeur à un [COleControlSite](../../mfc/reference/colecontrolsite-class.md).

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous pouvez remplacer cette fonction de membre pour retourner une instance de votre propre classe de site de contrôle.

## <a name="cdhtmldialogddx_dhtml_axcontrol"></a><a name="ddx_dhtml_axcontrol"></a>CDHtmlDialog::DDX-DHtml-AxControl

Échangez des données entre une variable de membre et la valeur de propriété d’un contrôle ActiveX sur une page HTML.

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

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
La valeur du paramètre d’identification de l’étiquette d’objet dans la source HTML pour le contrôle ActiveX.

*dispId*<br/>
L’ID de répartition de la propriété avec laquelle vous souhaitez échanger des données.

*szPropName (en)*<br/>
Nom de la propriété.

*Var*<br/>
Le membre de données, de type VARIANT, [COleVariant](../../mfc/reference/colevariant-class.md), ou [CComVariant](../../atl/reference/ccomvariant-class.md), qui détient la valeur échangée avec la propriété de contrôle ActiveX.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

## <a name="cdhtmldialogddx_dhtml_checkbox"></a><a name="ddx_dhtml_checkbox"></a>CDHtmlDialog::DDX-DHtml-CheckBox

Échangez des données entre une variable de membre et une case à cocher sur une page HTML.

```
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*value*<br/>
La valeur échangée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

## <a name="cdhtmldialogddx_dhtml_elementtext"></a><a name="ddx_dhtml_elementtext"></a>CDHtmlDialog::DDX-DHtml-ElementText

Échangez des données entre une variable de membre et n’importe quelle propriété d’élément HTML sur une page HTML.

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

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*dispId*<br/>
L’ID de répartition de l’élément HTML avec lequel vous souhaitez échanger des données.

*value*<br/>
La valeur échangée.

## <a name="cdhtmldialogddx_dhtml_radio"></a><a name="ddx_dhtml_radio"></a>CDHtmlDialog::DDX-DHtml-Radio

Échangez des données entre une variable de membre et un bouton radio sur une page HTML.

```
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*value*<br/>
La valeur échangée.

## <a name="cdhtmldialogddx_dhtml_selectindex"></a><a name="ddx_dhtml_selectindex"></a>CDHtmlDialog::DDX-DHtml-SelectIndex

Obtient ou définit l’index d’une boîte de liste sur une page HTML.

```
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
La valeur que vous avez spécifiée pour le paramètre du `id` contrôle HTML.

*value*<br/>
La valeur échangée.

## <a name="cdhtmldialogddx_dhtml_selectstring"></a><a name="ddx_dhtml_selectstring"></a>CDHtmlDialog::DDX-DHtml-SelectString

Obtient ou définit le texte d’affichage d’une entrée de boîte de liste (basé sur l’index actuel) sur une page HTML.

```
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*value*<br/>
La valeur échangée.

## <a name="cdhtmldialogddx_dhtml_selectvalue"></a><a name="ddx_dhtml_selectvalue"></a>CDHtmlDialog::DDX-DHtml-SelectValue

Obtient ou définit la valeur d’une entrée de boîte de liste (basée sur l’index actuel) sur une page HTML.

```
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*szId*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*value*<br/>
La valeur échangée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

## <a name="cdhtmldialogdestroymodeless"></a><a name="destroymodeless"></a>CDHtmlDialog::DestroyModeless

Détache une boîte de dialogue sans `CDHtmlDialog` mode de l’objet et détruit l’objet.

```
void DestroyModeless();
```

## <a name="cdhtmldialogenablemodeless"></a><a name="enablemodeless"></a>CDHtmlDialog::EnableModeless

Permet des boîtes de dialogue sans mode.

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>Paramètres

*fEnable*<br/>
Voir *fEnable* in [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) in the Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)), tel que décrit dans le SDK Windows.

## <a name="cdhtmldialogfilterdataobject"></a><a name="filterdataobject"></a>CDHtmlDialog::FilterDataObject

Permet au dialogue de filtrer les objets de données de presse-papiers créés par le navigateur hébergé.

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>Paramètres

*Aop*<br/>
Voir *pDO* dans [IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) dans le Windows SDK.

*ppDORet*<br/>
Voir *ppDORet* dans `IDocHostUIHandler::FilterDataObject` le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne S_FALSE.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)), tel que décrit dans le Windows SDK.

## <a name="cdhtmldialoggetcontroldispatch"></a><a name="getcontroldispatch"></a>CDHtmlDialog::GetControlDispatch

Récupère l’interface `IDispatch` sur un contrôle ActiveX intégré dans le document HTML retourné par [GetDHtmlDocument](#getdhtmldocument).

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>Paramètres

*szId*<br/>
L’ID HTML d’un contrôle ActiveX.

*ppdisp*<br/>
L’interface `IDispatch` du contrôle si elle est trouvée dans la page Web.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="cdhtmldialoggetcontrolproperty"></a><a name="getcontrolproperty"></a>CDHtmlDialog::GetControlProperty

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

*szPropName (en)*<br/>
Le nom d’une propriété dans le lieu par défaut de l’utilisateur actuel.

*pdispControl*<br/>
Le `IDispatch` pointeur d’un contrôle ActiveX.

*dispId*<br/>
L’identification de répartition d’une propriété.

### <a name="return-value"></a>Valeur de retour

Une variante contenant la propriété demandée ou une variante vide si le contrôle ou la propriété n’a pas pu être trouvé.

### <a name="remarks"></a>Notes

Les surcharges sont répertoriées du moins efficace en haut au plus efficace en bas.

## <a name="cdhtmldialoggetcurrenturl"></a><a name="getcurrenturl"></a>CDHtmlDialog::GetCurrentUrl

Récupère le localisateur de ressources uniformes (URL) associé au document actuel.

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>Paramètres

*szUrl*<br/>
Un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant l’URL à récupérer.

## <a name="cdhtmldialoggetdhtmldocument"></a><a name="getdhtmldocument"></a>CDHtmlDialog::GetDHtmlDocument

Récupère l’interface [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) sur le document HTML actuellement chargé.

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>Paramètres

* \* \** Un pointeur à un pointeur d’un document HTML.

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard. Retourne S_OK en cas de succès.

## <a name="cdhtmldialoggetdroptarget"></a><a name="getdroptarget"></a>CDHtmlDialog::GetDropTarget

Appelé par le contrôle WebBrowser contenu quand il est utilisé comme une cible de chute pour permettre au dialogue de fournir une alternative [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>Paramètres

*pDropTarget*<br/>
Voir *pDropTarget* dans [IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)) dans le Windows SDK.

*ppDropTarget*<br/>
Voir *ppDropTarget* dans `IDocHostUIHandler::GetDropTarget` le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\)), tel que décrit dans le Windows SDK.

## <a name="cdhtmldialoggetelement"></a><a name="getelement"></a>CDHtmlDialog::GetElement

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
Un `IDispatch` pointeur sur l’élément demandé ou la collection d’éléments.

*pbCollection*<br/>
Un BOOL indiquant si l’objet représenté par *ppdisp* est un seul élément ou une collection d’éléments.

*pphtmlElement*<br/>
Un `IHTMLElement` pointeur à l’élément demandé.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Utilisez la première surcharge si vous avez besoin de gérer les conditions dans lesquelles il peut y avoir plus d’un élément avec l’ID spécifié. Vous pouvez utiliser le dernier paramètre pour savoir si le pointeur d’interface retourné est à une collection ou un seul élément. Si le pointeur d’interface est sur `IHTMLElementCollection` une collection, vous pouvez interroger pour le et utiliser sa `item` propriété pour se référer aux éléments par position ordinaire.

La deuxième surcharge échouera s’il y a plus d’un élément avec le même ID dans la page.

## <a name="cdhtmldialoggetelementhtml"></a><a name="getelementhtml"></a>CDHtmlDialog::GetElementHtml

Récupère la `innerHTML` propriété de l’élément HTML identifié par *szElementId*.

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>Paramètres

*szElementId*<br/>
L’ID d’un élément HTML.

### <a name="return-value"></a>Valeur de retour

La `innerHTML` propriété de l’élément HTML identifié par *szElementId* ou NULL si l’élément n’a pas pu être trouvé.

## <a name="cdhtmldialoggetelementinterface"></a><a name="getelementinterface"></a>CDHtmlDialog::GetElementInterface

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
L’interface ID (IID) de l’interface demandée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

## <a name="cdhtmldialoggetelementproperty"></a><a name="getelementproperty"></a>CDHtmlDialog::GetElementProperty

Récupère la valeur de la propriété identifiée par *dispId* de l’élément HTML identifié par *szElementId*.

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>Paramètres

*szElementId*<br/>
L’ID d’un élément HTML.

*dispId*<br/>
L’identification de répartition d’une propriété.

### <a name="return-value"></a>Valeur de retour

La valeur de la propriété ou d’une variante vide si la propriété ou l’élément n’a pas pu être trouvé.

## <a name="cdhtmldialoggetelementtext"></a><a name="getelementtext"></a>CDHtmlDialog::GetElementText

Récupère la `innerText` propriété de l’élément HTML identifié par *szElementId*.

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>Paramètres

*szElementId*<br/>
L’ID d’un élément HTML.

### <a name="return-value"></a>Valeur de retour

La `innerText` propriété de l’élément HTML identifiée par *szElementId* ou NULL si la propriété ou l’élément n’a pas pu être trouvé.

## <a name="cdhtmldialoggetevent"></a><a name="getevent"></a>CDHtmlDialog::GetEvent

Retourne `IHTMLEventObj` le pointeur à l’objet événementiel actuel.

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>Paramètres

*ppEventObj*<br/>
Adresse d’un pointeur qui `IHTMLEventObj` sera rempli avec le pointeur d’interface.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction ne doit être appelée qu’à l’intérieur d’un gestionnaire d’événements DHTML.

## <a name="cdhtmldialoggetexternal"></a><a name="getexternal"></a>CDHtmlDialog::GetExternal

Obtient l’interface `IDispatch` de l’hôte.

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>Paramètres

*ppDispatch*<br/>
Voir *ppDispatch* dans [IDocHostUIHandler:GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)) dans le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès ou E_NOTIMPL sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)), tel que décrit dans le Windows SDK.

## <a name="cdhtmldialoggethostinfo"></a><a name="gethostinfo"></a>CDHtmlDialog::GetHostInfo

Récupère les capacités d’interface utilisateur de l’hôte.

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>Paramètres

*pInfo (en anglais)*<br/>
Voir *pInfo* dans [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) dans le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)), tel que décrit dans le Windows SDK.

## <a name="cdhtmldialoggetoptionkeypath"></a><a name="getoptionkeypath"></a>CDHtmlDialog::GetOptionKeyPath

Récupère la clé de registre en vertu de laquelle les préférences des utilisateurs sont stockées.

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>Paramètres

*pchKey (en)*<br/>
Voir *pchKey* dans [IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)) dans le Windows SDK.

*dw*<br/>
Voir *dw* dans `IDocHostUIHandler::GetOptionKeyPath` le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\)), tel que décrit dans le Windows SDK.

## <a name="cdhtmldialoghideui"></a><a name="hideui"></a>CDHtmlDialog::HideUI

Cache l’interface utilisateur de l’hôte.

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\)), tel que décrit dans le SDK Windows.

## <a name="cdhtmldialogisexternaldispatchsafe"></a><a name="isexternaldispatchsafe"></a>CDHtmlDialog::IsExternalDispatchSafe

Indique si l’interface de `IDispatch` l’hôte est sûre pour le script.

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>Valeur de retour

Retourne FALSE.

## <a name="cdhtmldialogloadfromresource"></a><a name="loadfromresource"></a>CDHtmlDialog::LoadDeResource

Charge la ressource spécifiée dans le contrôle WebBrowser dans le dialogue DHTML.

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>Paramètres

*lpszResource*<br/>
Un pointeur à une chaîne contenant le nom de la ressource à charger.

*nRes*<br/>
ID de la ressource à charger.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

## <a name="cdhtmldialogm_busehtmltitle"></a><a name="m_busehtmltitle"></a>CDHtmlDialog::m_bUseHtmlTitle

Indique s’il faut utiliser le titre du document HTML comme légende du dialogue.

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Notes

Si **m**' **bUseHtmlTitle** est VRAI, la légende de dialogue est définie égale au titre du document HTML; autrement, la légende dans la ressource de dialogue est utilisée.

## <a name="cdhtmldialogm_nhtmlresid"></a><a name="m_nhtmlresid"></a>CDHtmlDialog::m_nHtmlResID

Id de ressources de la ressource HTML à afficher.

```
UINT m_nHtmlResID;
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

## <a name="cdhtmldialogm_pbrowserapp"></a><a name="m_pbrowserapp"></a>CDHtmlDialog::m_pBrowserApp

Un pointeur vers une application de navigateur Web.

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

## <a name="cdhtmldialogm_sphtmldoc"></a><a name="m_sphtmldoc"></a>CDHtmlDialog::m_spHtmlDoc

Un pointeur vers un document HTML.

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

## <a name="cdhtmldialogm_strcurrenturl"></a><a name="m_strcurrenturl"></a>CDHtmlDialog::m_strCurrentUrl

L’URL actuelle.

```
CString m_strCurrentUrl;
```

## <a name="cdhtmldialogm_szhtmlresid"></a><a name="m_szhtmlresid"></a>CDHtmlDialog::m_szHtmlResID

Version chaîne de l’ID de ressources HTML.

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

## <a name="cdhtmldialognavigate"></a><a name="navigate"></a>CDHtmlDialog::Naviguer

Navigue vers la ressource identifiée par l’URL spécifiée par *lpszURL*.

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
Un pointeur à une chaîne contenant l’URL à cibler.

*dwFlags*<br/>
Les drapeaux d’une variable qui précise s’il faut ajouter la ressource à la liste d’histoire, s’il faut lire au cache ou écrire à partir du cache, et s’il faut afficher la ressource dans une nouvelle fenêtre. La variable peut être une combinaison des valeurs définies par le recensement [de BrowserNavConstants.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\))

*lpszTargetFrameName*<br/>
Un pointeur à une chaîne qui contient le nom du cadre dans lequel afficher la ressource.

*lpszHeaders (en)*<br/>
Un pointeur à une valeur qui spécifie les en-têtes HTTP à envoyer au serveur. Ces en-têtes sont ajoutés aux en-têtes Par défaut d’Internet Explorer. Les en-têtes peuvent spécifier des informations telles que l’action requise du serveur, le type de données transmises au serveur ou un code d’état. Ce paramètre est ignoré si l’URL n’est pas une URL HTTP.

*lpvPostData*<br/>
Un pointeur sur les données à envoyer avec la transaction HTTP POST. Par exemple, la transaction POST est utilisée pour envoyer des données recueillies par un formulaire HTML. Si ce paramètre ne spécifie aucune donnée postale, `Navigate` émet une transaction HTTP GET. Ce paramètre est ignoré si l’URL n’est pas une URL HTTP.

*dwPostDataLen*<br/>
Données à envoyer avec la transaction HTTP POST. Par exemple, la transaction POST est utilisée pour envoyer des données recueillies par un formulaire HTML. Si ce paramètre ne spécifie aucune donnée postale, `Navigate` émet une transaction HTTP GET. Ce paramètre est ignoré si l’URL n’est pas une URL HTTP.

## <a name="cdhtmldialogonbeforenavigate"></a><a name="onbeforenavigate"></a>CDHtmlDialog::OnBeforeNavigate

Appelé par le cadre pour provoquer un incendie d’événement avant qu’une navigation ne se produise.

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
Pointeur vers un objet `IDispatch` .

*szUrl*<br/>
Un pointeur à une chaîne contenant l’URL pour naviguer vers.

## <a name="cdhtmldialogondocumentcomplete"></a><a name="ondocumentcomplete"></a>CDHtmlDialog::OnDocumentComplete

Appelé par le cadre à aviser une demande lorsqu’un document a atteint l’état READYSTATE_COMPLETE.

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
Pointeur vers un objet `IDispatch` .

*szUrl*<br/>
Un pointeur à une chaîne contenant l’URL qui a été navigué à.

## <a name="cdhtmldialogondocwindowactivate"></a><a name="ondocwindowactivate"></a>CDHtmlDialog::OnDocWindowActivate

Appelé par le cadre lorsque la fenêtre de document est activée ou désactivée.

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Paramètres

*fActivate*<br/>
Voir *fActivate* dans [IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) in the Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)), tel que décrit dans le Windows SDK.

## <a name="cdhtmldialogonframewindowactivate"></a><a name="onframewindowactivate"></a>CDHtmlDialog::OnFrameWindowActivate

Appelé par le cadre lorsque la fenêtre de cadre est activée ou désactivée.

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>Paramètres

*fActivate*<br/>
Voir *fActivate* in [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) in the Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)), tel que décrit dans le SDK Windows.

## <a name="cdhtmldialogoninitdialog"></a><a name="oninitdialog"></a>CDHtmlDialog::OnInitDialog

Appelé en réponse au message WM_INITDIALOG.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

La implémentation par défaut renvoie TRUE.

### <a name="remarks"></a>Notes

Ce message est envoyé à la `Create` `CreateIndirect`boîte `DoModal` de dialogue pendant le , , ou les appels, qui se produisent immédiatement avant la boîte de dialogue est affiché.

Remplacer cette fonction de membre si vous avez besoin d’effectuer un traitement spécial lorsque la boîte de dialogue est paralysée. Dans la version prépondérer, `OnInitDialog` appelez d’abord la classe de base, mais ignorez sa valeur de retour. Vous retournerez normalement VRAI de votre fonction de membre prépondérer.

Windows appelle `OnInitDialog` la fonction à travers la procédure de dialogue-boîte globale standard commune à toutes les boîtes de dialogue Microsoft Foundation Class Library, plutôt que par le biais de votre carte de message, de sorte que vous n’avez pas besoin d’une entrée de carte de message pour cette fonction membre.

## <a name="cdhtmldialogonnavigatecomplete"></a><a name="onnavigatecomplete"></a>CDHtmlDialog::OnNavigateComplete

Appelé par le cadre après la navigation à l’URL spécifiée est terminée.

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>Paramètres

*pDisp*<br/>
Pointeur vers un objet `IDispatch` .

*szUrl*<br/>
Un pointeur à une chaîne contenant l’URL qui a été navigué à.

## <a name="cdhtmldialogresizeborder"></a><a name="resizeborder"></a>CDHtmlDialog::ResizeBorder

Alerte l’objet dont il a besoin pour resize son espace frontalier.

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>Paramètres

*prcBorder (prcBorder)*<br/>
Voir *prcBorder* dans [IDocHostUIHandler::ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\)) in the Windows SDK.

*pUIWindow (en)*<br/>
Voir *pUIWindow* dans `IDocHostUIHandler::ResizeBorder` le Windows SDK.

*fFrameWindow*<br/>
Voir *fFrameWindow* dans `IDocHostUIHandler::ResizeBorder` le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

## <a name="cdhtmldialogsetcontrolproperty"></a><a name="setcontrolproperty"></a>CDHtmlDialog::SetControlProperty

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
L’id de répartition de la propriété à définir.

*pVar*<br/>
Pointeur vers un VARIANT contenant la nouvelle valeur de la propriété.

*pdispControl*<br/>
Pointeur vers l’interface `IDispatch` d’un contrôle ActiveX.

*szPropName (en)*<br/>
Chaîne contenant le nom de la propriété à définir.

## <a name="cdhtmldialogsetelementhtml"></a><a name="setelementhtml"></a>CDHtmlDialog::SetElementHtml

Définit `innerHTML` la propriété d’un élément HTML.

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

*punkElem (punkElem)*<br/>
Le `IUnknown` pointeur d’un élément HTML.

## <a name="cdhtmldialogsetelementproperty"></a><a name="setelementproperty"></a>CDHtmlDialog::SetElementProperty

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
L’id de répartition de la propriété à définir.

*pVar*<br/>
Nouvelle valeur de la propriété.

## <a name="cdhtmldialogsetelementtext"></a><a name="setelementtext"></a>CDHtmlDialog::SetElementText

Définit `innerText` la propriété d’un élément HTML.

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

*punkElem (punkElem)*<br/>
Le `IUnknown` pointeur d’un élément HTML.

## <a name="cdhtmldialogsetexternaldispatch"></a><a name="setexternaldispatch"></a>CDHtmlDialog::SetExternalDispatch

Définit l’interface `IDispatch` de l’hôte.

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>Paramètres

*pdispExternal*<br/>
La `IDispatch` nouvelle interface.

## <a name="cdhtmldialogsethostflags"></a><a name="sethostflags"></a>CDHtmlDialog::SetHostFlags

Définit les drapeaux de l’interface utilisateur hôte.

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Pour les valeurs possibles, voir [DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) dans le SDK Windows.

## <a name="cdhtmldialogshowcontextmenu"></a><a name="showcontextmenu"></a>CDHtmlDialog::ShowContextMenu

Appelé quand un menu contextuelle est sur le point d’être affiché.

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>Paramètres

*dwID dwID*<br/>
Voir *dwID* dans [IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) dans le Windows SDK.

*Ppt*<br/>
Voir *ppt* dans `IDocHostUIHandler::ShowContextMenu` le Windows SDK.

*pcmdtReserved*<br/>
Voir *pcmdtReserved* in `IDocHostUIHandler::ShowContextMenu` the Windows SDK.

*pdispReserved*<br/>
Voir *pdispReserved* in `IDocHostUIHandler::ShowContextMenu` in the Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne S_FALSE.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)), tel que décrit dans le Windows SDK.

## <a name="cdhtmldialogshowui"></a><a name="showui"></a>CDHtmlDialog::ShowUI

Affiche l’interface utilisateur de l’hôte.

```
STDMETHOD(ShowUI)(
    DWORD dwID,
    IOleInPlaceActiveObject* pActiveObject,
    IOleCommandTarget* pCommandTarget,
    IOleInPlaceFrame* pFrame,
    IOleInPlaceUIWindow* pDoc);
```

### <a name="parameters"></a>Paramètres

*dwID dwID*<br/>
Voir *dwID* dans [IDocHostUIHandler:ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) dans le Windows SDK.

*pActiveObject*<br/>
Voir *d pActiveObject* dans `IDocHostUIHandler::ShowUI` le Windows SDK.

*pCommandTarget*<br/>
Voir *pCommandTarget* dans `IDocHostUIHandler::ShowUI` le Windows SDK.

*pFrame (en)*<br/>
Voir *pFrame* dans `IDocHostUIHandler::ShowUI` le Windows SDK.

*pDoc (en)*<br/>
Voir *pDoc* dans `IDocHostUIHandler::ShowUI` le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne S_FALSE.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)), tel que décrit dans le SDK Windows.

## <a name="cdhtmldialogtranslateaccelerator"></a><a name="translateaccelerator"></a>CDHtmlDialog::TranslateAccelerator

Appelé à traiter les messages clés de l’accélérateur de menu.

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>Paramètres

*lpMsg*<br/>
Voir *lpMsg* dans [IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)) in the Windows SDK.

*pguidCmdGroup*<br/>
Voir *pguidCmdGroup* dans `IDocHostUIHandler::TranslateAccelerator` le Windows SDK.

*nCmdID (en)*<br/>
Voir *nCmdID* dans `IDocHostUIHandler::TranslateAccelerator` le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne S_FALSE.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\)), tel que décrit dans le Windows SDK.

## <a name="cdhtmldialogtranslateurl"></a><a name="translateurl"></a>CDHtmlDialog::TranslateUrl

Appelé à modifier l’URL à charger.

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>Paramètres

*dwTranslate*<br/>
Voir *dwTranslate* dans [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) in the Windows SDK.

*pchURLIn pchURLIn*<br/>
Voir *pchURLIn* dans `IDocHostUIHandler::TranslateUrl` le Windows SDK.

*ppchURLOut*<br/>
Voir *ppchURLOut* dans `IDocHostUIHandler::TranslateUrl` le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Retourne S_FALSE.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)), tel que décrit dans le SDK Windows.

## <a name="cdhtmldialogupdateui"></a><a name="updateui"></a>CDHtmlDialog::UpdateUI

Appelé à aviser l’hôte que l’état de commandement a changé.

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

### <a name="remarks"></a>Notes

Cette fonction de membre est la mise en œuvre de CDHtmlDialog de [IDocHostUIHandler::UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\)), tel que décrit dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon DHtmlExplore](../../overview/visual-cpp-samples.md)<br/>
[DDX_DHtml Helper, structure](#ddx_dhtml_helper_macros)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
