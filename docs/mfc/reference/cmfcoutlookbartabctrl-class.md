---
title: CMFCOutlookBarTabCtrl Class
ms.date: 10/18/2018
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
ms.openlocfilehash: 309b74126f57e76aa6399f57382d88fee4400700
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369664"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class

Contrôle onglet qui a l'apparence visuelle du **Volet de navigation** dans Microsoft Outlook.
Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|Constructeur par défaut.|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|Ajoute un contrôle Windows comme nouvel onglet dans la barre Outlook.|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Appelé par le cadre pour déterminer les dimensions de la boîte de modification qui `CMFCBaseTabCtrl::CalcRectEdit`apparaît quand un utilisateur renomme un onglet. (Overrides .)|
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|Appelé par le cadre lors des opérations de resizing pour déterminer si moins de boutons de page d’onglet à barres Outlook peuvent être affichés que sont actuellement visibles.|
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|Appelé par le cadre lors des opérations de resizing pour déterminer si plus de boutons de page d’onglet à barres Outlook peuvent être affichés que sont actuellement visibles.|
|[CMFCOutlookBarTabCtrl::Créer](#create)|Crée le contrôle de l’onglet barre Outlook.|
|`CMFCOutlookBarTabCtrl::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|Précise si l’animation qui se produit pendant le commutateur entre les onglets actifs est activée.|
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|Précise si un utilisateur peut modifier les étiquettes de texte sur les boutons d’onglet de la barre Outlook. (Overrides [CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|Appelé par le cadre pour activer les boutons qui permettent à l’utilisateur de faire défiler les boutons sur la vitre de la barre Outlook.|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|Identifie la vitre qui contient un point spécifié. (Overrides [CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|Retourne la taille de la bordure du contrôle de l’onglet Outlook.|
|`CMFCOutlookBarTabCtrl::GetTabArea`|Récupère la taille et la position de la zone de l’onglet du contrôle de l’onglet. (Overrides [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|
|`CMFCOutlookBarTabCtrl::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|Détermine si l’animation qui se produit pendant le commutateur entre les onglets actifs est activée.|
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|Détermine si le contrôle de l’onglet barre Outlook est dans un mode qui imite Microsoft Outlook 2003.|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Détermine si un point se trouve à l’intérieur de la zone de l’onglet. (Overrides [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Détermine si un onglet est amovible. (Overrides [CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable).)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Appelé par le cadre lorsqu’un onglet est inséré ou enlevé. (Substitue `CMFCBaseTabCtrl::OnChangeTabs`.)|
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|Appelé par le cadre pour diminuer le nombre de boutons de page d’onglet qui sont visibles.|
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|Appelé par le cadre pour augmenter le nombre de boutons de page d’onglet qui sont visibles.|
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|Affiche le dialogue sur les **options de panoramique de navigation.**|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Recalcule la disposition interne du contrôle de l’onglet. (Overrides [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|Définit l’onglet actif. (Overrides [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|Définit la taille de la bordure du contrôle de l’onglet Outlook.|
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|Définit l’alignement des étiquettes de texte sur les boutons d’onglet de la barre Outlook.|
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|Définit la bitmap qui contient les icônes qui sont affichées sur le bas de la barre Outlook en mode Outlook 2003 (voir [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md)).|
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>Notes

Pour créer une barre Outlook qui dispose `CMFCOutlookBar` d’un support d’amarrage, utilisez un objet pour héberger le contrôle de l’onglet Barre Outlook. Pour plus d’informations, voir [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCOutlookBarTabCtrl` initialiser un objet `CMFCOutlookBarTabCtrl` et utiliser diverses méthodes dans la classe. L’exemple montre comment activer l’édition place de l’étiquette de texte sur les boutons de la page d’onglet de la barre Outlook, activer l’animation, activer les poignées de défilement qui permettent à l’utilisateur de faire défiler les boutons sur la barre Outlook, de définir la taille de la bordure du contrôle de l’onglet Outlook et de définir l’alignement des étiquettes de texte sur les boutons d’onglet de la barre Outlook. Cet extrait de code fait partie de [l’échantillon Outlook Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxoutlookbartabctrl.h

## <a name="cmfcoutlookbartabctrladdcontrol"></a><a name="addcontrol"></a>CMFCOutlookBarTabCtrl::AddControl

Ajoute un contrôle Windows comme nouvel onglet dans la barre Outlook.

```
void AddControl(
    CWnd* pWndCtrl,
    LPCTSTR lpszName,
    int nImageID=-1,
    BOOL bDetachable=TRUE,
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```

### <a name="parameters"></a>Paramètres

*pWndCtrl*<br/>
[dans] Un pointeur à un contrôle à ajouter.

*lpszName (en)*<br/>
[dans] Spécifie le nom de l’onglet.

*bDétachable*<br/>
[dans] Si TRUE, la page sera créée comme amovible.

*nImageID (en)*<br/>
[dans] Index d’image dans la liste d’images interne pour que l’image soit affichée dans le nouvel onglet.

*dwControlBarStyle (en)*<br/>
[dans] Spécifie le style AFX_ CBRS_MD pour les vitres d’amarrage enveloppées.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour ajouter un contrôle comme une nouvelle page d’une barre de perspective.

Cette fonction appelle en interne sur [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab).

Si vous *définissez bDetachable* à TRUE, `AddControl` en interne crée un `CDockablePaneAdapter` objet et enveloppe le contrôle supplémentaire. Il définit automatiquement la classe de temps d’exécution `CMFCOutlookBar` de la fenêtre tabbed à `CMultiPaneFrameWnd`la classe de temps d’exécution et la classe de temps d’exécution du cadre flottant à .

### <a name="example"></a>Exemple

L’exemple suivant montre comment `AddControl` utiliser `CMFCOutlookBarTabCtrl` la méthode dans la classe. Cet extrait de code fait partie de [l’échantillon Outlook Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

## <a name="cmfcoutlookbartabctrlcanshowfewerpagebuttons"></a><a name="canshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::CanShowFewerPageButtons

Appelé par le cadre lors des opérations de resizing pour déterminer si moins de boutons de page d’onglet à barres Outlook peuvent être affichés que sont actuellement visibles.

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI s’il y a plus d’un bouton; autrement FALSE.

### <a name="remarks"></a>Notes

Le contrôle de l’onglet Outlook ajoute ou supprime dynamiquement les onglets de l’écran en fonction de la quantité de place disponible. Cette méthode est utilisée par le cadre pour aider à ce processus.

## <a name="cmfcoutlookbartabctrlcanshowmorepagebuttons"></a><a name="canshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::CanShowMorePageButtons

Appelé par le cadre lors des opérations de resizing pour déterminer si plus de boutons de page d’onglet à barres Outlook peuvent être affichés que sont actuellement visibles.

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI s’il y a des boutons qui ne sont pas actuellement visibles; autrement FALSE.

### <a name="remarks"></a>Notes

Le contrôle de l’onglet Outlook ajoute ou supprime dynamiquement les onglets de l’écran, selon la quantité de place disponible. Cette méthode est utilisée par le cadre pour aider à ce processus.

## <a name="cmfcoutlookbartabctrlcreate"></a><a name="create"></a>CMFCOutlookBarTabCtrl::Créer

Crée le contrôle de l’onglet barre Outlook.

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
[dans] Spécifie la taille et la position initiales, en pixels.

*pParentWnd*<br/>
[dans] Points à la fenêtre parent. Ne doit pas être NULL.

*nID*<br/>
[dans] L’ID de contrôle.

### <a name="return-value"></a>Valeur de retour

Nonzero si le contrôle a été créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Habituellement, les commandes d’onglets de barre de perspective sont créées lorsque [la classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md) contrôle le WM_CREATE message du processus.

## <a name="cmfcoutlookbartabctrlenableanimation"></a><a name="enableanimation"></a>CMFCOutlookBarTabCtrl::EnableAnimation

Précise si l’animation qui se produit pendant le commutateur entre les onglets actifs est activée.

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] Précise si l’animation doit être activée ou désactivée.

### <a name="remarks"></a>Notes

Appelez cette fonction pour activer et désactiver l’animation. Lorsque l’utilisateur ouvre une page d’onglet, la légende de la page glisse vers le haut ou vers le bas si l’animation est activée. Si l’animation est désactivée, la page devient active immédiatement.

Par défaut, l’animation est activée.

## <a name="cmfcoutlookbartabctrlenableinplaceedit"></a><a name="enableinplaceedit"></a>CMFCOutlookBarTabCtrl::EnableInPlaceEdit

Précise si un utilisateur peut modifier les étiquettes de texte sur les boutons de la page d’onglet de la barre Outlook.

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
Si VRAI, activez l’édition place de l’étiquette de texte. Si FALSE, désactiver l’édition sur place.

### <a name="remarks"></a>Notes

Appelez cette fonction pour activer ou désactiver l’édition place des étiquettes de texte sur les boutons de page onglet. Par défaut, l’édition en place est désactivée.

## <a name="cmfcoutlookbartabctrlenablescrollbuttons"></a><a name="enablescrollbuttons"></a>CMFCOutlookBarTabCtrl::EnableScrollButtons

Appelé par le cadre pour activer les poignées de défilement qui permettent à l’utilisateur de faire défiler les boutons sur le volet de barre Outlook.

```
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] Détermine si les boutons de défilement sont affichés.

*bIsUp (En)*<br/>
[dans] Détermine si la barre de défilement supérieure est affichée.

*bIsDown (en)*<br/>
[dans] Détermine si la barre de défilement inférieure est affichée.

### <a name="remarks"></a>Notes

Permet l’affichage des boutons de défilement. Cette méthode est appelée par le cadre lorsque l’onglet actif change pour restaurer les boutons de défilement.

## <a name="cmfcoutlookbartabctrlgetbordersize"></a><a name="getbordersize"></a>CMFCOutlookBarTabCtrl::GetBorderSize

Retourne la taille de la bordure du contrôle de l’onglet Outlook.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille de la bordure, en pixels.

## <a name="cmfcoutlookbartabctrlgetvisiblepagebuttons"></a><a name="getvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::GetVisiblePageButtons

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcoutlookbartabctrlisanimation"></a><a name="isanimation"></a>CMFCOutlookBarTabCtrl::IsAnimation

Précise si l’animation qui se produit pendant le commutateur entre les onglets actifs est activée.

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’animation est activée; sinon 0.

### <a name="remarks"></a>Notes

Appelez le [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation) fonction pour activer ou désactiver l’animation.

## <a name="cmfcoutlookbartabctrlismode2003"></a><a name="ismode2003"></a>CMFCOutlookBarTabCtrl::IsMode2003

Détermine si le contrôle de l’onglet barre Outlook est dans un mode qui imite Microsoft Outlook 2003.

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le contrôle de l’onglet barres Outlook est en mode Outlook 2003; autrement FALSE;

### <a name="remarks"></a>Notes

Cette valeur est définie par [CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003).

## <a name="cmfcoutlookbartabctrlonshowfewerpagebuttons"></a><a name="onshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::OnShowFewerPageButtons

Appelé par le cadre pour diminuer le nombre de boutons de page d’onglet qui sont visibles.

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>Notes

Cette méthode ajuste le nombre de boutons visibles de l’onglet de page lorsque le contrôle est resized.

## <a name="cmfcoutlookbartabctrlonshowmorepagebuttons"></a><a name="onshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::OnShowMorePageButtons

Appelé par le cadre pour augmenter le nombre de boutons de page d’onglet qui sont visibles.

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>Notes

Cette méthode ajuste le nombre de boutons de page d’onglets qui sont visibles lorsque le contrôle est resized.

## <a name="cmfcoutlookbartabctrlonshowoptions"></a><a name="onshowoptions"></a>CMFCOutlookBarTabCtrl::OnShowOptions

Affiche la boîte de dialogue **Navigation Pane Options.**

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>Notes

La boîte de dialogue **Navigation Pane Options** permet à l’utilisateur de sélectionner les boutons de la page d’onglets à afficher et l’ordre dans lequel ils sont affichés.

Cette méthode est appelée par le cadre lorsque l’utilisateur sélectionne l’élément de menu **Navigation Pane Options** à partir du menu de personnalisation du contrôle.

## <a name="cmfcoutlookbartabctrlsetactivetab"></a><a name="setactivetab"></a>CMFCOutlookBarTabCtrl::SetActiveTab

Définit l’onglet actif. L’onglet actif est celui qui est ouvert, avec son contenu visible.

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>Paramètres

*Ccfi*<br/>
[dans] L’indice zéro d’un onglet à ouvrir.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’onglet spécifié a été ouvert avec succès; sinon 0.

### <a name="remarks"></a>Notes

L’effet visuel du réglage de l’onglet actif dépend de si vous avez activé l’animation. Pour plus d’informations, voir [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation).

## <a name="cmfcoutlookbartabctrlsetbordersize"></a><a name="setbordersize"></a>CMFCOutlookBarTabCtrl::SetBorderSize

Définit la taille de la bordure du contrôle de l’onglet Outlook.

```
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>Paramètres

*nBorderSize (en)*<br/>
[dans] Spécifie la nouvelle taille de la bordure en pixels.

### <a name="remarks"></a>Notes

Définit la nouvelle taille de la bordure et récalcule la disposition de la fenêtre de perspective.

## <a name="cmfcoutlookbartabctrlsetpagebuttontextalign"></a><a name="setpagebuttontextalign"></a>CMFCOutlookBarTabCtrl::SetPageButtonTextAlign

Définit l’alignement des étiquettes de texte sur les boutons d’onglet de la barre Outlook.

```
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Paramètres

*uiAlign*<br/>
[dans] Spécifie l’alignement du texte.

*bRedraw (en)*<br/>
[dans] Si VRAI, la fenêtre de perspective sera redessiné.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour modifier l’alignement du texte pour les boutons de page.

*uiAlign* peut être l’une des valeurs suivantes :

|Constant|Signification|
|--------------|-------------|
|TA_LEFT|Alignement gauche|
|TA_CENTER|Alignement central|
|TA_RIGHT|Alignement droit|

La valeur par défaut est TA_CENTER.

## <a name="cmfcoutlookbartabctrlsettoolbarimagelist"></a><a name="settoolbarimagelist"></a>CMFCOutlookBarTabCtrl::SetToolbarImageList

Définit la bitmap qui contient les icônes qui sont affichées sur le bas de la barre Outlook en mode Outlook 2003.

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
[dans] Spécifie l’ID de ressources de l’image à charger.

*Cx*<br/>
[dans] Spécifie la largeur d’une image dans la liste d’images, en pixels.

*clrTransp*<br/>
[dans] Une valeur RGB qui spécifie la couleur transparente.

### <a name="return-value"></a>Valeur de retour

Rendements VRAI en cas de succès; autrement retourne FALSE.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour joindre une liste d’images dont les images seront affichées sur les boutons de la barre d’outils en mode Microsoft Office 2003. Les index d’image doivent correspondre aux index de page.

Cette méthode ne doit pas être appelée si ce n’est en mode Microsoft Office 2003. Pour plus d’informations, voir [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="cmfcoutlookbartabctrlsetvisiblepagebuttons"></a><a name="setvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::SetVisiblePageButtons

```
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>Paramètres

[dans] *nVisiblePageButtons*<br/>

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[Classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[Classe CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)
