---
description: 'En savoir plus sur : classe CPaneDialog'
title: CPaneDialog, classe
ms.date: 11/04/2016
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
ms.openlocfilehash: 6efbbf710f09cf6507853b983a68578a24111a34
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345171"
---
# <a name="cpanedialog-class"></a>CPaneDialog, classe

La `CPaneDialog` classe prend en charge une boîte de dialogue non modale et Ancrable.

## <a name="syntax"></a>Syntaxe

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|Constructeur par défaut.|
|`CPaneDialog::~CPaneDialog`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPaneDialog :: Create](#create)|Crée une boîte de dialogue Ancrable et l’attache à un `CPaneDialog` objet.|
|`CPaneDialog::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CPaneDialog::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Gère le message de [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) . (Redéfinit `CBasePane::HandleInitDialog` .)|
|`CPaneDialog::OnEraseBkgnd`|Gère le message de [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) . (Redéfinit [CWnd :: OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|
|`CPaneDialog::OnLButtonDblClk`|Gère le message de [WM_LBUTTONDBLCLK](/windows/win32/inputdev/wm-lbuttondblclk) . (Redéfinit [CWnd :: OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|
|`CPaneDialog::OnLButtonDown`|Gère le message de [WM_LBUTTONDOWN](/windows/win32/inputdev/wm-lbuttondown) . (Redéfinit [CWnd :: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|
|`CPaneDialog::OnUpdateCmdUI`|Appelé par l’infrastructure pour mettre à jour la fenêtre de la boîte de dialogue. (Substitue [CDockablePane :: OnUpdateCmdUI](cdockablepane-class.md).)|
|`CPaneDialog::OnWindowPosChanging`|Gère le message de [WM_WINDOWPOSCHANGING](/windows/win32/winmsg/wm-windowposchanging) . (Redéfinit [CWnd :: OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Spécifie le modèle pour une boîte de dialogue qui est un conteneur de contrôle OLE.|

## <a name="remarks"></a>Notes

Construisez un `CPaneDialog` objet en deux étapes. Tout d’abord, construisez l’objet dans votre code. Ensuite, appelez [CPaneDialog :: Create](#create). Vous devez spécifier un nom de modèle de ressource ou un ID de modèle valide et passer un pointeur vers la fenêtre parente. Dans le cas contraire, le processus de création échoue. La boîte de dialogue doit spécifier les WS_CHILD et le style de WS_VISIBLE. Nous vous recommandons de spécifier également les styles WS_CLIPCHILDREN et WS_CLIPSIBLINGS. Pour plus d’informations, consultez [styles de fenêtre](styles-used-by-mfc.md#window-styles).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxpanedialog. h

## <a name="cpanedialogcreate"></a><a name="create"></a> CPaneDialog :: Create

Crée une boîte de dialogue d’ancrage et l’attache à un `CPaneDialog` objet.

```
BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID,
    DWORD dwTabbedStyle= AFX_CBRS_REGULAR_TABS,
    DWORD dwControlBarStyle=AFX_DEFAULT_DOCKING_PANE_STYLE);

BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*lpszWindowName*<br/>
dans Nom de la boîte de dialogue d’ancrage.

*pParentWnd*<br/>
dans Pointe vers la fenêtre parente.

*bHasGripper*<br/>
dans TRUE pour créer la boîte de dialogue d’ancrage avec une légende (pince); Sinon, FALSe.

*lpszTemplateName*<br/>
dans Nom du modèle de boîte de dialogue de ressource.

*nStyle*<br/>
dans Style Windows.

*nID*<br/>
dans ID du contrôle.

*nIDTemplate*<br/>
dans ID de ressource du modèle de boîte de dialogue.

*dwTabbedStyle*<br/>
dans Style de la fenêtre à onglets qui résulte lorsque l’utilisateur fait glisser un autre volet de contrôle sur la légende de ce volet de contrôle. La valeur par défaut est AFX_CBRS_REGULAR_TABS. Pour plus d’informations, consultez la section Notes de la méthode [CBasePane :: CreateEx](../../mfc/reference/cbasepane-class.md#createex) .

*dwControlBarStyle*<br/>
dans Attributs de style supplémentaires. La valeur par défaut est AFX_DEFAULT_DOCKING_PANE_STYLE. Pour plus d’informations, consultez la section Notes de la méthode [CBasePane :: CreateEx](../../mfc/reference/cbasepane-class.md#createex) .

### <a name="return-value"></a>Valeur renvoyée

TRUE si cette méthode est réussie ; Sinon, FALSe.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `Create` méthode dans la `CPaneDialog` classe. Cet exemple fait partie de l' [exemple Set Pane Size](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

## <a name="cpanedialoghandleinitdialog"></a><a name="handleinitdialog"></a> CPaneDialog::HandleInitDialog

Gère le message de [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) .

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*wParam*<br/>
dans Handle du contrôle qui doit recevoir le focus clavier par défaut.

*lParam*<br/>
dans Spécifie des données d’initialisation supplémentaires.

### <a name="return-value"></a>Valeur renvoyée

TRUE si cette méthode réussit ; Sinon, FALSe. En outre, TRUE définit le focus clavier sur le contrôle spécifié par le paramètre *wParam* ; FALSe empêche de définir le focus clavier par défaut.

### <a name="remarks"></a>Notes

L’infrastructure utilise cette méthode pour initialiser des contrôles et l’apparence d’une boîte de dialogue. L’infrastructure appelle cette méthode avant d’afficher la boîte de dialogue.

## <a name="cpanedialogsetoccdialoginfo"></a><a name="setoccdialoginfo"></a> CPaneDialog::SetOccDialogInfo

Spécifie le modèle pour une boîte de dialogue qui est un conteneur de contrôle OLE.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Paramètres

*pOccDialogInfo*<br/>
dans Pointeur vers un modèle de boîte de dialogue utilisé pour créer l’objet de boîte de dialogue. La valeur de ce paramètre est ensuite transmise à la méthode [COccManager :: CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) .

### <a name="return-value"></a>Valeur renvoyée

Toujours TRUE.

### <a name="remarks"></a>Remarques

Cette méthode prend en charge la classe [COccManager](../../mfc/reference/coccmanager-class.md) , qui gère les sites de contrôle OLE et les contrôles ActiveX. La structure _AFX_OCC_DIALOG_INFO est définie dans le fichier d’en-tête afxocc. h.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane, classe](../../mfc/reference/cdockablepane-class.md)<br/>
[Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles)
