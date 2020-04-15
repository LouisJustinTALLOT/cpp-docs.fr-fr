---
title: Classe CPaneDialog
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
ms.openlocfilehash: ad1225034cc5eca8ca53b042ebe3b55db4a2cf09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364126"
---
# <a name="cpanedialog-class"></a>Classe CPaneDialog

La `CPaneDialog` classe prend en charge une boîte de dialogue sans mode et amarré.

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
|[CPaneDialog::Créer](#create)|Crée une boîte de dialogue amarrée `CPaneDialog` et la fixe à un objet.|
|`CPaneDialog::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CPaneDialog::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Gère le [message WM_INITDIALOG.](/windows/win32/dlgbox/wm-initdialog) (Redéfinit `CBasePane::HandleInitDialog`.)|
|`CPaneDialog::OnEraseBkgnd`|Gère le [message WM_ERASEBKGND.](/windows/win32/winmsg/wm-erasebkgnd) (Redéfinit [CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|
|`CPaneDialog::OnLButtonDblClk`|Gère le [message WM_LBUTTONDBLCLK.](/windows/win32/inputdev/wm-lbuttondblclk) (Redéfinit [CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|
|`CPaneDialog::OnLButtonDown`|Gère le [message WM_LBUTTONDOWN.](/windows/win32/inputdev/wm-lbuttondown) (Redéfinit [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|
|`CPaneDialog::OnUpdateCmdUI`|Appelé par le cadre pour mettre à jour la fenêtre de la boîte de dialogue. (Overrides [CDockablePane::OnUpdateCmdUI](cdockablepane-class.md).)|
|`CPaneDialog::OnWindowPosChanging`|Gère le [message WM_WINDOWPOSCHANGING.](/windows/win32/winmsg/wm-windowposchanging) (Redéfinit [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Spécifie le modèle d’une boîte de dialogue qui est un conteneur de contrôle OLE.|

## <a name="remarks"></a>Notes

Construire `CPaneDialog` un objet en deux étapes. Tout d’abord, construisez l’objet dans votre code. Deuxièmement, appelez [CPaneDialog::Créer](#create). Vous devez spécifier un nom de modèle de ressource valide ou une pièce d’identité de modèle et passer un pointeur à la fenêtre parente. Sinon, le processus de création échoue. La boîte de dialogue doit spécifier le style WS_CHILD et WS_VISIBLE. Nous vous recommandons également de spécifier les styles WS_CLIPCHILDREN et WS_CLIPSIBLINGS. Pour plus d’informations, voir [Windows Styles](styles-used-by-mfc.md#window-styles).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxpanedialog.h

## <a name="cpanedialogcreate"></a><a name="create"></a>CPaneDialog::Créer

Crée une boîte de dialogue d’amarrage et la fixe à un `CPaneDialog` objet.

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

*lpszWindowName (en)*<br/>
[dans] Le nom de la boîte de dialogue d’amarrage.

*pParentWnd*<br/>
[dans] Points à la fenêtre parent.

*bHasGripper (En anglais)*<br/>
[dans] VRAI pour créer la boîte de dialogue d’amarrage avec une légende (gripper); autrement, FALSE.

*lpszTemplateName*<br/>
[dans] Le nom du modèle de dialogue de ressource.

*nStyle*<br/>
[dans] Le style Windows.

*nID*<br/>
[dans] L’ID de contrôle.

*nIDTemplate (en)*<br/>
[dans] L’ID de ressource du modèle de dialogue.

*dwTabbedStyle (en)*<br/>
[dans] Le style de la fenêtre tabbed qui résulte lorsque l’utilisateur traîne une autre vitre de contrôle sur la légende de cette vitre de contrôle. La valeur par défaut est AFX_CBRS_REGULAR_TABS. Pour plus d’informations, consultez la section Remarques de la méthode [CBasePane:CreateEx.](../../mfc/reference/cbasepane-class.md#createex)

*dwControlBarStyle (en)*<br/>
[dans] Attributs de style supplémentaires. La valeur par défaut est AFX_DEFAULT_DOCKING_PANE_STYLE. Pour plus d’informations, consultez la section Remarques de la méthode [CBasePane:CreateEx.](../../mfc/reference/cbasepane-class.md#createex)

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode réussit; autrement, FALSE.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L’exemple suivant montre comment `Create` utiliser `CPaneDialog` la méthode dans la classe. Cet exemple fait partie de [l’échantillon Set Pane Size](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

## <a name="cpanedialoghandleinitdialog"></a><a name="handleinitdialog"></a>CPaneDialog::HandleInitDialog

Gère le [message WM_INITDIALOG.](/windows/win32/dlgbox/wm-initdialog)

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*wParam*<br/>
[dans] Gérer le contrôle qui est de recevoir la mise au point du clavier par défaut.

*lParam*<br/>
[dans] Spécifie d’autres données d’initialisation.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE. En outre, TRUE définit la mise au point du clavier sur le contrôle spécifié par le paramètre *wParam;* FALSE empêche de définir la mise au point du clavier par défaut.

### <a name="remarks"></a>Notes

Le cadre utilise cette méthode pour initialiser les contrôles et l’apparition d’une boîte de dialogue. Le cadre appelle cette méthode avant qu’elle n’affiche la boîte de dialogue.

## <a name="cpanedialogsetoccdialoginfo"></a><a name="setoccdialoginfo"></a>CPaneDialog::SetOccDialogInfo

Spécifie le modèle d’une boîte de dialogue qui est un conteneur de contrôle OLE.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Paramètres

*pOccDialogInfo*<br/>
[dans] Pointeur vers un modèle de boîte de dialogue qui est utilisé pour créer l’objet de boîte de dialogue. La valeur de ce paramètre est ensuite passée dans la méthode [COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) méthode.

### <a name="return-value"></a>Valeur de retour

Toujours TRUE.

### <a name="remarks"></a>Notes

Cette méthode prend en charge la classe [COccManager,](../../mfc/reference/coccmanager-class.md) qui gère les sites de contrôle OLE et les contrôles ActiveX. La structure _AFX_OCC_DIALOG_INFO est définie dans le fichier d’en-tête afxocc.h.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane, classe](../../mfc/reference/cdockablepane-class.md)<br/>
[Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles)
