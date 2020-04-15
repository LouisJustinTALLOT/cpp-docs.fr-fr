---
title: CMFCColorBar, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCColorBar
- AFXCOLORBAR/CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::ContextToSize
- AFXCOLORBAR/CMFCColorBar::CreateControl
- AFXCOLORBAR/CMFCColorBar::Create
- AFXCOLORBAR/CMFCColorBar::EnableAutomaticButton
- AFXCOLORBAR/CMFCColorBar::EnableOtherButton
- AFXCOLORBAR/CMFCColorBar::GetColor
- AFXCOLORBAR/CMFCColorBar::GetCommandID
- AFXCOLORBAR/CMFCColorBar::GetHighlightedColor
- AFXCOLORBAR/CMFCColorBar::GetHorzMargin
- AFXCOLORBAR/CMFCColorBar::GetVertMargin
- AFXCOLORBAR/CMFCColorBar::IsTearOff
- AFXCOLORBAR/CMFCColorBar::SetColor
- AFXCOLORBAR/CMFCColorBar::SetColorName
- AFXCOLORBAR/CMFCColorBar::SetCommandID
- AFXCOLORBAR/CMFCColorBar::SetDocumentColors
- AFXCOLORBAR/CMFCColorBar::SetHorzMargin
- AFXCOLORBAR/CMFCColorBar::SetVertMargin
- AFXCOLORBAR/CMFCColorBar::AdjustLocations
- AFXCOLORBAR/CMFCColorBar::AllowChangeTextLabels
- AFXCOLORBAR/CMFCColorBar::AllowShowOnList
- AFXCOLORBAR/CMFCColorBar::CalcSize
- AFXCOLORBAR/CMFCColorBar::CreatePalette
- AFXCOLORBAR/CMFCColorBar::GetColorGridSize
- AFXCOLORBAR/CMFCColorBar::GetExtraHeight
- AFXCOLORBAR/CMFCColorBar::InitColors
- AFXCOLORBAR/CMFCColorBar::OnKey
- AFXCOLORBAR/CMFCColorBar::OnSendCommand
- AFXCOLORBAR/CMFCColorBar::OnUpdateCmdUI
- AFXCOLORBAR/CMFCColorBar::OpenColorDialog
- AFXCOLORBAR/CMFCColorBar::Rebuild
- AFXCOLORBAR/CMFCColorBar::SelectPalette
- AFXCOLORBAR/CMFCColorBar::SetPropList
- AFXCOLORBAR/CMFCColorBar::ShowCommandMessageString
helpviewer_keywords:
- CMFCColorBar [MFC], CMFCColorBar
- CMFCColorBar [MFC], ContextToSize
- CMFCColorBar [MFC], CreateControl
- CMFCColorBar [MFC], Create
- CMFCColorBar [MFC], EnableAutomaticButton
- CMFCColorBar [MFC], EnableOtherButton
- CMFCColorBar [MFC], GetColor
- CMFCColorBar [MFC], GetCommandID
- CMFCColorBar [MFC], GetHighlightedColor
- CMFCColorBar [MFC], GetHorzMargin
- CMFCColorBar [MFC], GetVertMargin
- CMFCColorBar [MFC], IsTearOff
- CMFCColorBar [MFC], SetColor
- CMFCColorBar [MFC], SetColorName
- CMFCColorBar [MFC], SetCommandID
- CMFCColorBar [MFC], SetDocumentColors
- CMFCColorBar [MFC], SetHorzMargin
- CMFCColorBar [MFC], SetVertMargin
- CMFCColorBar [MFC], AdjustLocations
- CMFCColorBar [MFC], AllowChangeTextLabels
- CMFCColorBar [MFC], AllowShowOnList
- CMFCColorBar [MFC], CalcSize
- CMFCColorBar [MFC], CreatePalette
- CMFCColorBar [MFC], GetColorGridSize
- CMFCColorBar [MFC], GetExtraHeight
- CMFCColorBar [MFC], InitColors
- CMFCColorBar [MFC], OnKey
- CMFCColorBar [MFC], OnSendCommand
- CMFCColorBar [MFC], OnUpdateCmdUI
- CMFCColorBar [MFC], OpenColorDialog
- CMFCColorBar [MFC], Rebuild
- CMFCColorBar [MFC], SelectPalette
- CMFCColorBar [MFC], SetPropList
- CMFCColorBar [MFC], ShowCommandMessageString
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
ms.openlocfilehash: 7b63fb66b800bd758c7f4c89c553e857ad9bbfbc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367772"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar, classe

La `CMFCColorBar` classe représente une barre de contrôle d’amarrage qui peut sélectionner des couleurs dans un document ou une application.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|Construit un objet `CMFCColorBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCColorBar::ContextTosize](#contexttosize)|Calcule les marges verticales et horizontales qui sont nécessaires pour contenir les boutons sur le contrôle de la barre de couleur, puis ajuste l’emplacement de ces boutons.|
|[CMFCColorBar::CreateControl](#createcontrol)|Crée une fenêtre de contrôle de `CMFCColorBar` barre de couleur, l’attache à l’objet, et resizes le contrôle pour contenir la palette spécifiée de couleurs.|
|[CMFCColorBar::Créer](#create)|Crée une fenêtre de contrôle de `CMFCColorBar` barre de couleur et la fixe à l’objet.|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Affiche ou cache le bouton automatique.|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Permet ou désactive l’affichage d’une boîte de dialogue qui permet à l’utilisateur de sélectionner plus de couleurs.|
|[CMFCColorBar::GetColor](#getcolor)|Récupère la couleur actuellement sélectionnée.|
|[CMFCColorBar::GetCommandID](#getcommandid)|Récupère l’ID de commande du contrôle actuel de la barre de couleur.|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Récupère la couleur qui signifie qu’un bouton de couleur a la mise au point; c’est-à-dire, le bouton est *chaud*.|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Récupère la marge horizontale, qui est l’espace entre la cellule de couleur gauche ou droite et la limite de la zone client.|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Récupère la marge verticale, qui est l’espace entre la cellule de couleur supérieure ou inférieure et la limite de la zone client.|
|[CMFCColorBar::IsTearOff](#istearoff)|Indique si la barre de couleur actuelle est amarable.|
|[CMFCColorBar::SetColor](#setcolor)|Définit la couleur qui est actuellement sélectionnée.|
|[CMFCColorBar::SetColorName](#setcolorname)|Définit un nouveau nom pour une couleur spécifiée.|
|[CMFCColorBar::SetCommandID](#setcommandid)|Définit une nouvelle pièce d’identité de commande pour un contrôle de barre de couleur.|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Définit la liste des couleurs qui sont utilisées dans le document actuel.|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Définit la marge horizontale, qui est l’espace entre la cellule de couleur gauche ou droite et la limite de zone client.|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Définit la marge verticale, qui est l’espace entre la cellule de couleur supérieure ou inférieure et la limite de zone client.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Ajuste les positions des boutons de couleur sur le contrôle de la barre de couleur.|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Indique si l’étiquette de texte des boutons de couleur peut changer.|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Indique si l’objet de contrôle de barre de couleur peut apparaître dans une liste de barre d’outils pendant le processus de personnalisation.|
|[CMFCColorBar::CalcSize](#calcsize)|Appelé par le cadre dans le cadre du processus de calcul de la mise en page.|
|[CMFCColorBar::CreatePalette](#createpalette)|Initialise une palette avec les couleurs dans un tableau spécifié de couleurs.|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Calcule le nombre de lignes et de colonnes dans la grille d’un contrôle de barre de couleur.|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Calcule la hauteur supplémentaire que la barre de couleur actuelle nécessite pour afficher divers éléments d’interface utilisateur tels que **l’autre** bouton, couleurs de document, et ainsi de suite.|
|[CMFCColorBar::InitColors](#initcolors)|Initialise un tableau de couleurs avec les couleurs dans une palette spécifiée ou la palette par défaut du système.|
|[CMFCColorBar::OnKey](#onkey)|Appelé par le cadre quand un utilisateur appuie sur un bouton clavier.|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Appelé par le cadre à fermer une hiérarchie des contrôles popup.|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Appelé par le cadre pour activer ou désactiver un élément utilisateur-interface d’un contrôle de barre de couleur avant que l’élément est affiché.|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Ouvre une boîte de dialogue couleur.|
|[CMFCColorBar::Reconstruire](#rebuild)|Redessine complètement le contrôle de la barre de couleur.|
|[CMFCColorBar::SelectPalette](#selectpalette)|Définit la palette logique du contexte de l’appareil spécifié à la palette du bouton parent du contrôle actuel de la barre de couleur.|
|[CMFCColorBar::SetPropList](#setproplist)|Définit `m_pWndPropList` le membre des données protégées au pointeur spécifié à un contrôle du réseau de propriété.|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Demande la fenêtre de cadre qui possède le contrôle de la barre de couleur pour mettre à jour la ligne de message dans la barre d’état.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|`m_bInternal`|Un champ Boolean qui détermine si les événements de souris sont traités. Typiquement, les événements de souris sont traités lorsque ce champ est VRAI et le mode de personnalisation est FALSE.|
|`m_bIsEnabled`|Un Boolean qui indique si un contrôle est activé.|
|`m_bIsTearOff`|Un Boolean qui indique si le contrôle de la barre de couleur prend en charge l’amarrage.|
|`m_BoxSize`|Un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) qui spécifie la taille d’une cellule dans une grille de barre de couleur.|
|`m_bShowDocColorsWhenDocked`|Un Boolean qui indique s’il faut afficher les couleurs du document lorsque la barre de couleur est amarré. Pour plus d’informations, voir [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_bStdColorDlg`|Un Boolean qui indique s’il faut montrer la boîte de dialogue couleur système standard ou la boîte de dialogue [CMFCColorDialog.](../../mfc/reference/cmfccolordialog-class.md) Pour plus d’informations, voir [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorAutomatic`|Un [COLORREF](/windows/win32/gdi/colorref) qui stocke la couleur automatique actuelle. Pour plus d’informations, voir [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorNames`|Un objet [CMap](../../mfc/reference/cmap-class.md) qui associe un ensemble de couleurs RGB avec leurs noms.|
|`m_colors`|Un [CArray](../../mfc/reference/carray-class.md) des valeurs [COLORREF](/windows/win32/gdi/colorref) qui contient les couleurs qui sont affichées dans le contrôle de la barre de couleur.|
|`m_ColorSelected`|Une valeur [COLORREF](/windows/win32/gdi/colorref) qui est la couleur que l’utilisateur a actuellement sélectionnée à partir du contrôle de la barre de couleur.|
|`m_lstDocColors`|Une [liste](../../mfc/reference/clist-class.md) de valeurs [COLORREF](/windows/win32/gdi/colorref) qui contient les couleurs qui sont actuellement utilisées dans un document.|
|`m_nCommandID`|Un insigned integer qui est l’ID de commande d’un bouton de couleur.|
|`m_nHorzMargin`|Un intégrant qui est la marge horizontale entre les boutons de couleur dans une grille de couleurs.|
|`m_nHorzOffset`|Un intégrier qui est le décalage horizontal au centre du bouton de couleur. Cette valeur est significative si le bouton affiche du texte ou une image en plus d’une couleur.|
|`m_nNumColumns`|Un intégrant qui est le nombre de colonnes dans une grille de contrôle de barre de couleur des couleurs.|
|`m_nNumColumnsVert`|Un integer qui est le nombre de colonnes dans une grille verticalement orientée de couleurs.|
|`m_nNumRowsHorz`|Un integer qui est le nombre de colonnes dans une grille horizontalement orientée de couleurs.|
|`m_nRowHeight`|Un intégrant qui est la hauteur d’une rangée de boutons de couleur dans une grille de couleurs.|
|`m_nVertMargin`|Un intégrant qui est la marge verticale entre les boutons de couleur dans une grille de couleurs.|
|`m_nVertOffset`|Un intégrier qui est le décalage vertical au centre du bouton de couleur. Cette valeur est significative si le bouton affiche du texte ou une image en plus d’une couleur.|
|`m_Palette`|Une [CPalette](../../mfc/reference/cpalette-class.md) des couleurs qui sont utilisées dans le contrôle de la barre de couleur.|
|`m_pParentBtn`|Un pointeur vers un objet [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) qui est le parent du bouton actuel. Cette valeur est significative si le bouton de couleur est dans une hiérarchie de contrôles de barre d’outils ou est dans un contrôle de grille de propriété de couleur.|
|`m_pParentRibbonBtn`|Un pointeur à un objet [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) qui est sur le ruban et est le bouton parent du bouton actuel. Cette valeur est significative si le bouton de couleur est dans une hiérarchie de contrôles de barre d’outils ou est dans un contrôle de grille de propriété de couleur.|
|`m_pWndPropList`|Un pointeur à un objet [CMFCPropertyGridCtrl.](../../mfc/reference/cmfcpropertygridctrl-class.md)|
|`m_strAutoColor`|Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui est le texte qui s’affiche sur le bouton **automatique.** Pour plus d’informations, voir [CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton).|
|`m_strDocColors`|Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui est le texte qui est affiché sur le bouton de couleurs de document. Pour plus d’informations, voir [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_strOtherColor`|Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui est le texte qui s’affiche sur *l’autre* bouton. Pour plus d’informations, voir [CMFCColorBar::EnableOtherButton](#enableotherbutton).|

## <a name="remarks"></a>Notes

Habituellement, vous ne `CMFCColorBar` créez pas un objet directement. Au lieu de cela, la [classe CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (utilisée dans les menus `CMFCColorBar` et les barres d’outils) ou la classe [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) crée l’objet.

La `CMFCColorBar` classe fournit la fonctionnalité suivante :

- Ajuste automatiquement la liste des couleurs du document.

- Sauve et restaure son état, ainsi que l’état du document.

- Gère le bouton "automatique".

- Utilise le contrôle [cmFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md) pour sélectionner une couleur personnalisée.

- Prend en charge un état de « déchirure » (s’il est créé en utilisant la [classe CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)).

Pour intégrer `CMFCColorBar` la fonctionnalité dans votre application :

1. Créez un bouton de menu régulier et attribuez-lui une pièce d’identité, par exemple ID_CHAR_COLOR.

1. Dans votre classe de fenêtre de cadre, remplacez le [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) méthode et remplacer le bouton de menu régulier par un objet [cmFCColorMenuButton Classe](../../mfc/reference/cmfccolormenubutton-class.md) (en appelant [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Définissez tous les styles et activez `CMFCColorBar` ou désactivez les caractéristiques de l’objet lors de la création [de la classe CMFCColorMenuButton.](../../mfc/reference/cmfccolormenubutton-class.md) L’objet `CMFCColorMenuButton` crée `CMFCColorBar` dynamiquement l’objet `CreatePopupMenu` après que le cadre appelle la méthode.

Lorsque l’utilisateur clique sur un bouton de `ON_COMMAND` contrôle de la barre de couleur, le cadre utilise la macro pour aviser le parent du contrôle de la barre de couleur. Dans la macro, le paramètre d’identification de commande est la valeur que vous avez assignée au bouton de contrôle de la barre de couleur à l’étape 1 (ID_CHAR_COLOR dans cet exemple). Pour plus d’informations, consultez la [classe CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md), [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md), [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md), [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md), et [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md) classes.

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer une barre `CMFCColorBar` de couleur en utilisant différentes méthodes dans la classe. Les méthodes fixent les marges horizontales et verticales, activent l’autre bouton, créent une fenêtre de commande de barre de couleur et définit la couleur actuellement sélectionnée. Cet exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxcolorbar.h

## <a name="cmfccolorbaradjustlocations"></a><a name="adjustlocations"></a>CMFCColorBar::AdjustLocations

Ajuste les positions des boutons de couleur sur le contrôle de la barre de couleur.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre pendant WM_SIZE traitement des messages.

## <a name="cmfccolorbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCColorBar::AllowChangeTextLabels

Indique si l’étiquette de texte des boutons de couleur peut changer.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Valeur de retour

Toujours FALSE.

### <a name="remarks"></a>Notes

Par défaut, cette méthode renvoie toujours FALSE, ce qui signifie que les étiquettes de texte ne peuvent pas être modifiées. Remplacer cette méthode pour permettre de modifier les étiquettes de texte.

## <a name="cmfccolorbarallowshowonlist"></a><a name="allowshowonlist"></a>CMFCColorBar::AllowShowOnList

Indique si l’objet de contrôle de barre de couleur peut apparaître dans une liste de barre d’outils pendant le processus de personnalisation.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>Valeur de retour

Toujours TRUE.

### <a name="remarks"></a>Notes

Par défaut, cette méthode renvoie toujours TRUE, ce qui signifie que le cadre peut afficher le contrôle de la barre de couleur pendant le processus de personnalisation. Remplacer cette méthode pour mettre en œuvre un comportement différent.

## <a name="cmfccolorbarcalcsize"></a><a name="calcsize"></a>CMFCColorBar::CalcSize

Appelé par le cadre dans le cadre du processus de calcul de la mise en page.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Paramètres

*bVertDock (en)*<br/>
[dans] VRAI pour spécifier que le contrôle de la barre de couleur est amarré verticalement; FALSE pour spécifier que le contrôle de la barre de couleur est amarré horizontalement.

### <a name="return-value"></a>Valeur de retour

La taille de la gamme de boutons de couleur dans un contrôle de barre de couleur.

## <a name="cmfccolorbarcmfccolorbar"></a><a name="cmfccolorbar"></a>CMFCColorBar::CMFCColorBar

Construit un objet `CMFCColorBar`.

```
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    int nRowsDockHorz,
    int nColDockVert,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCColorButton* pParentBtn);

CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCRibbonColorButton* pParentRibbonBtn);

CMFCColorBar(
    CMFCColorBar& src,
    UINT uiCommandID);
```

### <a name="parameters"></a>Paramètres

*Couleurs*<br/>
[dans] Un tableau de couleurs que le cadre affiche sur le contrôle de la barre de couleur.

*Couleur*<br/>
[dans] La couleur initialement sélectionnée.

*lpszAutoColor*<br/>
[dans] L’étiquette de texte du bouton *couleur automatique* (par défaut) ou NULL.

L’étiquette standard pour le bouton automatique est **automatique**.

*lpszOtherColor*<br/>
[dans] L’étiquette de texte de *l’autre* bouton, qui affiche plus de choix de couleurs, ou NULL.

L’étiquette standard pour l’autre bouton est **Plus de couleurs...**.

*lpszDocColors*<br/>
[dans] L’étiquette de texte du bouton de couleur de document. La palette de couleurs de document répertorie toutes les couleurs que le document utilise actuellement.

*lstDocColors (en)*<br/>
[dans] Une liste de couleurs que le document utilise actuellement.

*nColumns*<br/>
[dans] Le nombre de colonnes que la gamme de couleurs a.

*nRowsDockHorz*<br/>
[dans] Le nombre de lignes que la barre de couleur a quand il est amarré horizontalement.

*nColDockVert*<br/>
[dans] Le nombre de colonnes que la barre de couleur a quand il est amarré verticalement.

*couleurAutomatique*<br/>
[dans] La couleur par défaut que le cadre s’applique lorsque vous cliquez sur le bouton automatique.

*nCommandID (en)*<br/>
[dans] L’ID de commande de barre de couleur.

*pParentBtn*<br/>
[dans] Un pointeur sur un bouton parent.

*src*<br/>
[dans] Un `CMFCColorBar` objet existant à copier `CMFCColorBar` dans le nouvel objet.

*uiCommandID*<br/>
[dans] L’id de commande.

## <a name="cmfccolorbarcontexttosize"></a><a name="contexttosize"></a>CMFCColorBar::ContextTosize

Calcule les marges verticales et horizontales qui sont nécessaires pour contenir les boutons sur le contrôle de la barre de couleur, et ajuste l’emplacement de ces boutons.

```
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*bSquareButtons (en)*|[dans] VRAI pour spécifier que la forme des boutons sur un contrôle de barre de couleur sont carrés; autrement, FALSE. La valeur par défaut est TRUE.|
|*bCenterButtons (en)*|[dans] VRAI pour spécifier que le contenu sur le visage d’un bouton de commande de barre de couleur est centré ; autrement, FALSE. La valeur par défaut est TRUE.|

### <a name="remarks"></a>Notes

## <a name="cmfccolorbarcreate"></a><a name="create"></a>CMFCColorBar::Créer

Crée une fenêtre de contrôle de `CMFCColorBar` barre de couleur et la fixe à l’objet.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID,
    CPalette* pPalette=NULL,
    int nColumns=0,
    int nRowsDockHorz=0,
    int nColDockVert=0);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
[dans] Pointeur vers la fenêtre parente.

*dwStyle (en)*<br/>
[dans] Une combinaison bitwise (OU) de styles de [fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
[dans] L’id de commande.

*pPalette (pPalette)*<br/>
[dans] Pointeur vers une palette de couleurs. La valeur par défaut est NULL.

*nColumns*<br/>
[dans] Le nombre de colonnes dans le contrôle de la barre de couleur. La valeur par défaut est 0.

*nRowsDockHorz*<br/>
[dans] Le nombre de lignes dans le contrôle de la barre de couleur quand il est amarré horizontalement. La valeur par défaut est 0.

*nColDockVert*<br/>
[dans] Le nombre de colonnes dans le contrôle de la barre de couleur quand il est amarré verticalement. La valeur par défaut est 0.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Pour construire `CMFCColorBar` un objet, appelez le constructeur de classe puis cette méthode. La `Create` méthode crée le contrôle Windows et initialise une liste de couleurs.

## <a name="cmfccolorbarcreatecontrol"></a><a name="createcontrol"></a>CMFCColorBar::CreateControl

Crée une fenêtre de contrôle de `CMFCColorBar` barre de couleur, l’attache à l’objet, et resizes la fenêtre de commande pour contenir la palette spécifiée de couleurs.

```
virtual BOOL CreateControl(
    CWnd* pParentWnd,
    const CRect& rect,
    UINT nID,
    int nColumns=-1,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
[dans] Pointeur vers la fenêtre parente. Ne peut pas avoir la valeur NULL.

*Rect*<br/>
[dans] Un rectangle de délimitation qui spécifie où dessiner le contrôle de la barre de couleur.

*nID*<br/>
[dans] L’ID de contrôle.

*nColumns*<br/>
[dans] Le nombre idéal de colonnes dans le contrôle de la barre de couleur. Cette méthode modifie ce nombre pour s’adapter à la palette spécifiée de couleurs. La valeur par défaut est de -1, ce qui signifie que ce paramètre n’est pas spécifié.

*pPalette (pPalette)*<br/>
[dans] Pointeur vers une palette de couleurs, ou NULL. Si ce paramètre est NULL, cette méthode calcule la taille du contrôle de la barre de couleur comme si 20 couleurs ont été spécifiées. La valeur par défaut est NULL.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode réussit; autrement FALSE.

### <a name="remarks"></a>Notes

Cette méthode utilise les paramètres *rect*, *nColumns*, et *pPalette* pour calculer le nombre approprié ou des lignes et des colonnes dans le contrôle de la barre de couleur, puis appelle le [CMFCColorBar::Créer](#create) la méthode.

## <a name="cmfccolorbarcreatepalette"></a><a name="createpalette"></a>CMFCColorBar::CreatePalette

Initialise une palette avec les couleurs dans un tableau spécifié de couleurs.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*arColors (arColors)*|[dans] Un tableau de couleurs.|
|*palette*|[dans] Une palette de couleurs.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

## <a name="cmfccolorbarenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorBar::EnableAutomaticButton

Affiche ou cache le bouton automatique.

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[dans] L’étiquette de texte du bouton *couleur automatique* (par défaut) ou NULL.

L’étiquette standard pour le bouton automatique est **automatique**.

*couleurAutomatique*<br/>
[dans] La couleur par défaut que le cadre s’applique lorsque vous cliquez sur le bouton automatique.

*bEnable*<br/>
[dans] VRAI pour activer le bouton automatique; FALSE pour désactiver le bouton automatique. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

L’étiquette de texte du bouton automatique est supprimée si le paramètre *lpszLabel* est NULL ou si le paramètre *bEnable* est FALSE.

## <a name="cmfccolorbarenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorBar::EnableOtherButton

Permet ou désactive l’affichage d’une boîte de dialogue qui permet à l’utilisateur de sélectionner plus de couleurs.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[dans] L’étiquette de texte de *l’autre* bouton, qui affiche plus de choix de couleurs, ou NULL.

L’étiquette standard pour ce bouton est **plus de couleurs...**.

*bAltColorDlg*<br/>
[dans] VRAI pour afficher la boîte de dialogue [CMFCColorDialog;](../../mfc/reference/cmfccolordialog-class.md) FALSE pour afficher la boîte de dialogue [CColorDialog](../../mfc/reference/ccolordialog-class.md) standard. La valeur par défaut est TRUE.

*bEnable*<br/>
[dans] VRAI pour activer le bouton; FALSE pour désactiver le bouton. La valeur par défaut est TRUE.

## <a name="cmfccolorbargetcolor"></a><a name="getcolor"></a>CMFCColorBar::GetColor

Récupère la couleur actuellement sélectionnée.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

La couleur actuellement sélectionnée.

## <a name="cmfccolorbargetcolorgridsize"></a><a name="getcolorgridsize"></a>CMFCColorBar::GetColorGridSize

Calcule le nombre de lignes et de colonnes dans la grille d’un contrôle de barre de couleur.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*bVertDock (en)*|[dans] VRAI pour effectuer le calcul pour un contrôle vertical de barre de couleur amarré ; autrement, effectuez le calcul d’un contrôle horizontalement amarré.|

### <a name="return-value"></a>Valeur de retour

Objet [CSize](../../atl-mfc-shared/reference/csize-class.md) `cx` dont le composant contient `cy` le nombre de colonnes et dont le composant contient le nombre de lignes.

## <a name="cmfccolorbargetcommandid"></a><a name="getcommandid"></a>CMFCColorBar::GetCommandID

Récupère l’ID de commande du contrôle actuel de la barre de couleur.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Valeur de retour

Une pièce d’identité de commande.

### <a name="remarks"></a>Notes

Lorsque l’utilisateur sélectionne une nouvelle couleur, le cadre envoie l’ID de commande `CMFCColorBar` dans un message WM_COMMAND pour aviser le parent de l’objet.

## <a name="cmfccolorbargetextraheight"></a><a name="getextraheight"></a>CMFCColorBar::GetExtraHeight

Calcule la hauteur supplémentaire dont la barre de couleur actuelle a besoin pour afficher divers éléments d’interface utilisateur, tels que **l’autre** bouton ou les couleurs de document.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*nNumColumns (en)*|[dans] Si le contrôle de la barre de couleur contient des couleurs de document, le nombre de colonnes à afficher dans la grille des couleurs de document. Sinon, cette valeur n’est pas utilisée.|

### <a name="return-value"></a>Valeur de retour

La hauteur supplémentaire calculée qui est nécessaire.

## <a name="cmfccolorbargethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCColorBar::GetHighlightedColor

Récupère la couleur qui signifie qu’un bouton de couleur a la mise au point; c’est-à-dire, le bouton est *chaud*.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur RGB.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbargethorzmargin"></a><a name="gethorzmargin"></a>CMFCColorBar::GetHorzMargin

Récupère la marge horizontale, qui est l’espace entre la cellule de couleur gauche ou droite et la limite de la zone client.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Valeur de retour

La marge horizontale.

## <a name="cmfccolorbargetvertmargin"></a><a name="getvertmargin"></a>CMFCColorBar::GetVertMargin

Récupère la marge verticale, qui est l’espace entre la cellule de couleur supérieure ou inférieure et la limite de la zone client.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Valeur de retour

La marge verticale.

## <a name="cmfccolorbarinitcolors"></a><a name="initcolors"></a>CMFCColorBar::InitColors

Initialise un tableau de couleurs avec les couleurs dans une palette spécifiée, ou avec la palette par défaut du système.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pPalette (pPalette)*|[dans] Pointeur d’un objet de palette, ou NULL. Si ce paramètre est NULL, cette méthode utilise la palette par défaut du système d’exploitation.|
|*arColors (arColors)*|[dans] Un tableau de couleurs.|

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans la gamme de couleurs.

## <a name="cmfccolorbaristearoff"></a><a name="istearoff"></a>CMFCColorBar::IsTearOff

Indique si la barre de couleur actuelle est amarable.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le contrôle actuel de barre de couleur est amarré ; autrement, FALSE.

### <a name="remarks"></a>Notes

Si le contrôle de la barre de couleur est amarré, il peut être arraché d’une barre de contrôle et amarré à un autre endroit.

## <a name="cmfccolorbaronkey"></a><a name="onkey"></a>CMFCColorBar::OnKey

Appelé par le cadre quand un utilisateur appuie sur un bouton clavier.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Paramètres

*Nchar*<br/>
[dans] Le code à clé virtuelle pour la clé qu’un utilisateur a pressé.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode traite la clé spécifiée; autrement, FALSE.

## <a name="cmfccolorbaronsendcommand"></a><a name="onsendcommand"></a>CMFCColorBar::OnSendCommand

Appelé par le cadre à fermer une hiérarchie de contrôles pop-up.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pButton*|[dans] Pointeur à un contrôle qui réside sur une barre d’outils.|

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

## <a name="cmfccolorbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCColorBar::OnUpdateCmdUI

Appelé par le cadre pour activer ou désactiver un élément utilisateur-interface d’un contrôle de barre de couleur avant que l’élément est affiché.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
[dans] Pointeur vers une fenêtre qui contient un élément d’interface utilisateur à mettre à jour.

*bDisableIfNoHndler*<br/>
[dans] VRAI pour désactiver l’élément utilisateur-interface si aucun gestionnaire n’est défini dans une carte de message ; autrement, FALSE.

### <a name="remarks"></a>Notes

Lorsqu’un utilisateur de votre application clique sur un élément d’interface utilisateur, l’élément doit savoir s’il doit être affiché comme activé ou désactivé. La cible du message de commande fournit cette information en mettant en œuvre un gestionnaire de commande ON_UPDATE_COMMAND_UI. Utilisez cette méthode pour aider à traiter la commande. Pour plus d’informations, voir [CCmdUI Class](../../mfc/reference/ccmdui-class.md).

## <a name="cmfccolorbaropencolordialog"></a><a name="opencolordialog"></a>CMFCColorBar::OpenColorDialog

Ouvre une boîte de dialogue couleur.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Paramètres

*colorDefault*<br/>
[dans] La couleur qui est sélectionnée par défaut lorsque la boîte de dialogue couleur s’ouvre.

*colorRes colorRes*<br/>
[out] La couleur qu’un utilisateur a choisie.

### <a name="return-value"></a>Valeur de retour

VRAI si l’utilisateur a choisi une couleur; FALSE si l’utilisateur a annulé la boîte de dialogue couleur.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbarrebuild"></a><a name="rebuild"></a>CMFCColorBar::Reconstruire

Redessine complètement le contrôle de la barre de couleur.

```
virtual void Rebuild();
```

## <a name="cmfccolorbarselectpalette"></a><a name="selectpalette"></a>CMFCColorBar::SelectPalette

Définit la palette logique du contexte de l’appareil spécifié à la palette du bouton parent du contrôle actuel de la barre de couleur.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pDC*|[dans] Pointeur sur le contexte de l’appareil du bouton parent du contrôle actuel de la barre de couleur.|

### <a name="return-value"></a>Valeur de retour

Pointeur vers la palette qui est remplacée par la palette du bouton parent du contrôle actuel de la barre de couleur.

## <a name="cmfccolorbarsetcolor"></a><a name="setcolor"></a>CMFCColorBar::SetColor

Définit la couleur qui est actuellement sélectionnée.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
[dans] Une valeur de couleur RGB.

## <a name="cmfccolorbarsetcolorname"></a><a name="setcolorname"></a>CMFCColorBar::SetColorName

Définit un nouveau nom pour une couleur spécifiée.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
[dans] La valeur RGB d’une couleur.

*strName*<br/>
[dans] Le nouveau nom pour la couleur spécifiée.

### <a name="remarks"></a>Notes

Cette méthode modifie le nom de `CMFCColorBar` la couleur spécifiée dans tous les objets de votre application.

## <a name="cmfccolorbarsetcommandid"></a><a name="setcommandid"></a>CMFCColorBar::SetCommandID

Définit une nouvelle pièce d’identité de commande pour un contrôle de barre de couleur.

```
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Paramètres

*nCommandID (en)*<br/>
[dans] Une pièce d’identité de commande.

### <a name="remarks"></a>Notes

Appelez cette méthode pour modifier l’ID de commande d’un contrôle de barre de couleur et pour aviser la fenêtre parente du contrôle que l’ID a changé.

## <a name="cmfccolorbarsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColorBar::SetDocumentColors

Définit la liste des couleurs qui sont utilisées dans le document actuel.

```
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszCaption*<br/>
[dans] Une légende qui s’affiche lorsque le contrôle de la barre de couleur n’est pas amarré.

*lstDocColors (en)*<br/>
[dans] Une liste de couleurs qui remplace les couleurs actuelles du document.

*bShowWhenDocked*<br/>
[dans] VRAI pour afficher les couleurs de document lorsque le contrôle de barre de couleur est amarré ; autrement, FALSE. La valeur par défaut est FALSE.

### <a name="remarks"></a>Notes

*Les couleurs de document* sont les couleurs qui sont actuellement utilisées dans un document. Le cadre maintient automatiquement une liste de couleurs de documents, mais vous pouvez utiliser cette méthode pour modifier la liste.

## <a name="cmfccolorbarsethorzmargin"></a><a name="sethorzmargin"></a>CMFCColorBar::SetHorzMargin

Définit la marge horizontale, qui est l’espace entre la cellule de couleur gauche ou droite et la limite de la zone client.

```
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Paramètres

*nHorzMargin (en)*<br/>
[dans] La marge horizontale, en pixels.

### <a name="remarks"></a>Notes

Par défaut, le [constructeur CMFCColorBar : CMFCColorBar](#cmfccolorbar) fixe la marge horizontale à 4 pixels.

## <a name="cmfccolorbarsetproplist"></a><a name="setproplist"></a>CMFCColorBar::SetPropList

Définit `m_pWndPropList` le membre des données protégées au pointeur spécifié à un contrôle du réseau de propriété.

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pWndList (en)*|[dans] Pointeur à l’objet de contrôle de grille de propriété.|

## <a name="cmfccolorbarsetvertmargin"></a><a name="setvertmargin"></a>CMFCColorBar::SetVertMargin

Définit la marge verticale, qui est l’espace entre la cellule de couleur supérieure ou inférieure et la limite de zone client.

```
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Paramètres

*nVertMargin (en)*<br/>
[dans] La marge verticale, en pixels.

### <a name="remarks"></a>Notes

Par défaut, le [constructeur CMFCColorBar : CMFCColorBar](#cmfccolorbar) fixe la marge verticale à 4 pixels.

## <a name="cmfccolorbarshowcommandmessagestring"></a><a name="showcommandmessagestring"></a>CMFCColorBar::ShowCommandMessageString

Demande la fenêtre de cadre qui possède le contrôle de la barre de couleur pour mettre à jour la ligne de message dans la barre d’état.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Paramètres

*uiCmdId*<br/>
[dans] Une pièce d’identité de commande. (Ce paramètre est ignoré.)

### <a name="remarks"></a>Notes

Cette méthode envoie le message WM_SETMESSAGESTRING au propriétaire du contrôle de la barre de couleur.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
