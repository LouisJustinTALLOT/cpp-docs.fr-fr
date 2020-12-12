---
description: 'En savoir plus sur : classe CMFCColorBar'
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
ms.openlocfilehash: 5a2935c71a5579dddb2133f2ac6589a6bd447ef6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327708"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar, classe

La `CMFCColorBar` classe représente une barre de contrôle d’ancrage qui peut sélectionner des couleurs dans un document ou une application.

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
|[CMFCColorBar::ContextToSize](#contexttosize)|Calcule les marges verticales et horizontales qui sont requises pour contenir les boutons du contrôle de barre de couleurs, puis ajuste l’emplacement de ces boutons.|
|[CMFCColorBar :: CreateControl](#createcontrol)|Crée une fenêtre de contrôle de la barre de couleurs, l’attache à l' `CMFCColorBar` objet et redimensionne le contrôle pour qu’il contienne la palette de couleurs spécifiée.|
|[CMFCColorBar :: Create](#create)|Crée une fenêtre de contrôle de la barre de couleurs et l’attache à l' `CMFCColorBar` objet.|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Affiche ou masque le bouton automatique.|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Active ou désactive l’affichage d’une boîte de dialogue qui permet à l’utilisateur de sélectionner d’autres couleurs.|
|[CMFCColorBar :: GetColor](#getcolor)|Récupère la couleur actuellement sélectionnée.|
|[CMFCColorBar::GetCommandID](#getcommandid)|Récupère l’ID de commande du contrôle de barre de couleurs actuel.|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Récupère la couleur qui signifie qu’un bouton de couleur a le focus ; autrement dit, le bouton est *actif*.|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Récupère la marge horizontale, qui est l’espace entre la cellule de couleur gauche ou droite et la limite de la zone cliente.|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Récupère la marge verticale, qui est l’espace entre la cellule de couleur supérieure ou inférieure et la limite de la zone cliente.|
|[CMFCColorBar::IsTearOff](#istearoff)|Indique si la barre de couleurs actuelle est Ancrable.|
|[CMFCColorBar :: SetColor](#setcolor)|Définit la couleur actuellement sélectionnée.|
|[CMFCColorBar::SetColorName](#setcolorname)|Définit un nouveau nom pour une couleur spécifiée.|
|[CMFCColorBar::SetCommandID](#setcommandid)|Définit un nouvel ID de commande pour un contrôle de barre de couleurs.|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Définit la liste des couleurs utilisées dans le document actif.|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Définit la marge horizontale, qui est l’espace entre la cellule de couleur gauche ou droite et la limite de la zone cliente.|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Définit la marge verticale, qui est l’espace entre la cellule de couleur supérieure ou inférieure et la limite de la zone cliente.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Ajuste les positions des boutons de couleur sur le contrôle de la barre de couleurs.|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Indique si l’étiquette de texte des boutons de couleur peut changer.|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Indique si l’objet de contrôle de la barre de couleurs peut apparaître dans une liste de barres d’outils pendant le processus de personnalisation.|
|[CMFCColorBar::CalcSize](#calcsize)|Appelée par l’infrastructure dans le cadre du processus de calcul de la disposition.|
|[CMFCColorBar::CreatePalette](#createpalette)|Initialise une palette avec les couleurs dans un tableau de couleurs spécifié.|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Calcule le nombre de lignes et de colonnes dans la grille d’un contrôle de barre de couleurs.|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Calcule la hauteur supplémentaire requise par la barre de couleurs actuelle pour afficher divers éléments d’interface utilisateur tels que l' **autre** bouton, les couleurs du document, etc.|
|[CMFCColorBar::InitColors](#initcolors)|Initialise un tableau de couleurs avec les couleurs d’une palette spécifiée ou la palette par défaut du système.|
|[CMFCColorBar :: OnKey](#onkey)|Appelé par le Framework quand un utilisateur appuie sur un bouton du clavier.|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Appelé par l’infrastructure pour fermer une hiérarchie de contrôles Popup.|
|[CMFCColorBar :: OnUpdateCmdUI](#onupdatecmdui)|Appelé par l’infrastructure pour activer ou désactiver un élément de l’interface utilisateur d’un contrôle de barre de couleurs avant l’affichage de l’élément.|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Ouvre une boîte de dialogue de couleur.|
|[CMFCColorBar :: Rebuild](#rebuild)|Redessine complètement le contrôle de la barre de couleurs.|
|[CMFCColorBar::SelectPalette](#selectpalette)|Définit la palette logique du contexte de périphérique spécifié sur la palette du bouton parent du contrôle de barre de couleurs actuel.|
|[CMFCColorBar::SetPropList](#setproplist)|Définit le `m_pWndPropList` membre de données protégées sur le pointeur spécifié vers un contrôle de grille de propriétés.|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Demande la fenêtre frame propriétaire du contrôle de barre de couleurs pour mettre à jour la ligne de message dans la barre d’État.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|`m_bInternal`|Champ booléen qui détermine si les événements de souris sont traités. En règle générale, les événements de souris sont traités lorsque ce champ a la valeur TRUE et que le mode de personnalisation a la valeur FALSe.|
|`m_bIsEnabled`|Valeur booléenne qui indique si un contrôle est activé.|
|`m_bIsTearOff`|Valeur booléenne qui indique si le contrôle de barre de couleurs prend en charge l’ancrage.|
|`m_BoxSize`|Objet [CSize](../../atl-mfc-shared/reference/csize-class.md) qui spécifie la taille d’une cellule dans une grille de la barre de couleurs.|
|`m_bShowDocColorsWhenDocked`|Valeur booléenne qui indique s’il faut afficher les couleurs du document lorsque la barre de couleurs est ancrée. Pour plus d’informations, consultez [CMFCColorBar :: SetDocumentColors](#setdocumentcolors).|
|`m_bStdColorDlg`|Valeur booléenne qui indique s’il faut afficher la boîte de dialogue couleur système standard ou la boîte de dialogue [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) . Pour plus d’informations, consultez [CMFCColorBar :: EnableOtherButton](#enableotherbutton).|
|`m_ColorAutomatic`|[COLORREF](/windows/win32/gdi/colorref) qui stocke la couleur automatique actuelle. Pour plus d’informations, consultez [CMFCColorBar :: EnableOtherButton](#enableotherbutton).|
|`m_ColorNames`|Objet [CMAP](../../mfc/reference/cmap-class.md) qui associe un jeu de couleurs RVB à leurs noms.|
|`m_colors`|[CArray](../../mfc/reference/carray-class.md) de valeurs [COLORREF](/windows/win32/gdi/colorref) qui contient les couleurs affichées dans le contrôle de la barre de couleurs.|
|`m_ColorSelected`|Valeur [COLORREF](/windows/win32/gdi/colorref) qui correspond à la couleur actuellement sélectionnée par l’utilisateur dans le contrôle de la barre de couleurs.|
|`m_lstDocColors`|[CList](../../mfc/reference/clist-class.md) de valeurs [COLORREF](/windows/win32/gdi/colorref) qui contient les couleurs actuellement utilisées dans un document.|
|`m_nCommandID`|Entier non signé qui est l’ID de commande d’un bouton de couleur.|
|`m_nHorzMargin`|Entier qui est la marge horizontale entre les boutons de couleur dans une grille de couleurs.|
|`m_nHorzOffset`|Entier qui est le décalage horizontal au centre du bouton de couleur. Cette valeur est significative si le bouton affiche du texte ou une image en plus d’une couleur.|
|`m_nNumColumns`|Entier qui est le nombre de colonnes dans une grille de contrôle de barre de couleurs de couleurs.|
|`m_nNumColumnsVert`|Entier qui est le nombre de colonnes dans une grille verticale de couleurs.|
|`m_nNumRowsHorz`|Entier qui est le nombre de colonnes dans une grille de couleurs orientée horizontalement.|
|`m_nRowHeight`|Entier qui correspond à la hauteur d’une ligne de boutons de couleur dans une grille de couleurs.|
|`m_nVertMargin`|Entier qui est la marge verticale entre les boutons de couleur dans une grille de couleurs.|
|`m_nVertOffset`|Entier qui est le décalage vertical par rapport au centre du bouton de couleur. Cette valeur est significative si le bouton affiche du texte ou une image en plus d’une couleur.|
|`m_Palette`|[Cpalette](../../mfc/reference/cpalette-class.md) des couleurs utilisées dans le contrôle de la barre de couleurs.|
|`m_pParentBtn`|Pointeur vers un objet [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) qui est le parent du bouton actuel. Cette valeur est significative si le bouton de couleur se trouve dans une hiérarchie de contrôles ToolBar ou s’il se trouve dans un contrôle de grille de propriétés de couleur.|
|`m_pParentRibbonBtn`|Pointeur vers un objet [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) qui est sur le ruban et est le bouton parent du bouton actuel. Cette valeur est significative si le bouton de couleur se trouve dans une hiérarchie de contrôles ToolBar ou s’il se trouve dans un contrôle de grille de propriétés de couleur.|
|`m_pWndPropList`|Pointeur vers un objet [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) .|
|`m_strAutoColor`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) qui est le texte affiché sur le bouton **automatique** . Pour plus d’informations, consultez [CMFCColorBar :: EnableAutomaticButton](#enableautomaticbutton).|
|`m_strDocColors`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) qui est le texte affiché sur le bouton de couleurs du document. Pour plus d’informations, consultez [CMFCColorBar :: SetDocumentColors](#setdocumentcolors).|
|`m_strOtherColor`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) qui est le texte affiché sur l' *autre* bouton. Pour plus d’informations, consultez [CMFCColorBar :: EnableOtherButton](#enableotherbutton).|

## <a name="remarks"></a>Notes

En règle générale, vous ne créez pas `CMFCColorBar` directement un objet. Au lieu de cela, la [classe CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (utilisée dans les menus et les barres d’outils) ou la [classe CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) crée l' `CMFCColorBar` objet.

La `CMFCColorBar` classe fournit les fonctionnalités suivantes :

- Ajuste automatiquement la liste des couleurs du document.

- Enregistre et restaure son état, ainsi que l’état du document.

- Gère le bouton « automatique ».

- Utilise le contrôle de [classe CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) pour sélectionner une couleur personnalisée.

- Prend en charge l’État « Tear » (s’il est créé à l’aide de la [classe CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)).

Pour incorporer les `CMFCColorBar` fonctionnalités dans votre application :

1. Créez un bouton de menu normal et attribuez-lui un ID, par exemple ID_CHAR_COLOR.

1. Dans votre classe de fenêtre frame, substituez la méthode [CFrameWndEx :: OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) et remplacez le bouton de menu normal par un objet de [classe CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (en appelant [CMFCToolBar :: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Définissez tous les styles et activez ou désactivez les fonctionnalités de l’objet lors de la création de la `CMFCColorBar` [classe CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) . L' `CMFCColorMenuButton` objet crée dynamiquement l' `CMFCColorBar` objet une fois que le Framework a appelé la `CreatePopupMenu` méthode.

Quand l’utilisateur clique sur un bouton de contrôle de la barre de couleurs, le Framework utilise la `ON_COMMAND` macro pour notifier le parent du contrôle de barre de couleurs. Dans la macro, le paramètre ID de commande correspond à la valeur que vous avez assignée au bouton de contrôle de la barre de couleurs à l’étape 1 (ID_CHAR_COLOR dans cet exemple). Pour plus d’informations, consultez la classe [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md), [classe CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md), classe [CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md), [classe CFrameWndEx](../../mfc/reference/cframewndex-class.md)et classes de [classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) .

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer une barre de couleurs à l’aide de diverses méthodes de la `CMFCColorBar` classe. Les méthodes définissent les marges horizontale et verticale, activent l’autre bouton, créent une fenêtre de contrôle de la barre de couleurs et définit la couleur actuellement sélectionnée. Cet exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

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

**En-tête :** afxcolorbar. h

## <a name="cmfccolorbaradjustlocations"></a><a name="adjustlocations"></a> CMFCColorBar::AdjustLocations

Ajuste les positions des boutons de couleur sur le contrôle de la barre de couleurs.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure pendant WM_SIZE le traitement du message.

## <a name="cmfccolorbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a> CMFCColorBar::AllowChangeTextLabels

Indique si l’étiquette de texte des boutons de couleur peut changer.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Valeur renvoyée

Toujours FALSE.

### <a name="remarks"></a>Remarques

Par défaut, cette méthode retourne toujours FALSe, ce qui signifie que les étiquettes de texte ne peuvent pas être modifiées. Substituez cette méthode pour permettre la modification des étiquettes de texte.

## <a name="cmfccolorbarallowshowonlist"></a><a name="allowshowonlist"></a> CMFCColorBar::AllowShowOnList

Indique si l’objet de contrôle de la barre de couleurs peut apparaître dans une liste de barres d’outils pendant le processus de personnalisation.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>Valeur renvoyée

Toujours TRUE.

### <a name="remarks"></a>Remarques

Par défaut, cette méthode retourne toujours la valeur TRUE, ce qui signifie que l’infrastructure peut afficher le contrôle de la barre de couleurs pendant le processus de personnalisation. Substituez cette méthode pour implémenter un comportement différent.

## <a name="cmfccolorbarcalcsize"></a><a name="calcsize"></a> CMFCColorBar::CalcSize

Appelée par l’infrastructure dans le cadre du processus de calcul de la disposition.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Paramètres

*bVertDock*<br/>
dans TRUE pour spécifier que le contrôle de la barre de couleurs est ancré verticalement ; FALSe pour spécifier que le contrôle de la barre de couleurs est ancré horizontalement.

### <a name="return-value"></a>Valeur renvoyée

Taille du tableau de boutons de couleur dans un contrôle de barre de couleurs.

## <a name="cmfccolorbarcmfccolorbar"></a><a name="cmfccolorbar"></a> CMFCColorBar::CMFCColorBar

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

*couleurs*<br/>
dans Tableau de couleurs que l’infrastructure affiche sur le contrôle de barre de couleurs.

*color*<br/>
dans Couleur initialement sélectionnée.

*lpszAutoColor*<br/>
dans Étiquette de texte du bouton de couleur *automatique* (par défaut) ou null.

L’étiquette standard du bouton automatique est **automatique**.

*lpszOtherColor*<br/>
dans Étiquette de texte de l' *autre* bouton, qui affiche plus de choix de couleurs, ou null.

L’étiquette standard de l’autre bouton est **plus de couleurs.**...

*lpszDocColors*<br/>
dans Étiquette de texte du bouton de couleurs du document. La palette de couleurs du document répertorie toutes les couleurs actuellement utilisées par le document.

*lstDocColors*<br/>
dans Liste des couleurs actuellement utilisées par le document.

*nColumns*<br/>
dans Nombre de colonnes que contient le tableau de couleurs.

*nRowsDockHorz*<br/>
dans Nombre de lignes que la barre de couleurs a lorsqu’elle est ancrée horizontalement.

*nColDockVert*<br/>
dans Nombre de colonnes de la barre de couleurs lorsqu’elle est ancrée verticalement.

*colorAutomatic*<br/>
dans Couleur par défaut appliquée par l’infrastructure lorsque vous cliquez sur le bouton automatique.

*nCommandID*<br/>
dans ID de commande du contrôle de la barre de couleurs.

*pParentBtn*<br/>
dans Pointeur vers un bouton parent.

*src*<br/>
dans Objet existant `CMFCColorBar` à copier dans le nouvel `CMFCColorBar` objet.

*uiCommandID*<br/>
dans ID de la commande.

## <a name="cmfccolorbarcontexttosize"></a><a name="contexttosize"></a> CMFCColorBar::ContextToSize

Calcule les marges verticales et horizontales qui sont requises pour contenir les boutons du contrôle de barre de couleurs, et ajuste l’emplacement de ces boutons.

```cpp
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Paramètres

*bSquareButtons*\
dans TRUE pour spécifier que la forme des boutons sur un contrôle de barre de couleurs est carrée ; Sinon, FALSe. La valeur par défaut est TRUE.

*bCenterButtons*\
dans TRUE pour spécifier que le contenu sur la face d’un bouton de contrôle de la barre de couleurs est centré ; Sinon, FALSe. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbarcreate"></a><a name="create"></a> CMFCColorBar :: Create

Crée une fenêtre de contrôle de la barre de couleurs et l’attache à l' `CMFCColorBar` objet.

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
dans Pointeur vers la fenêtre parente.

*dwStyle*<br/>
dans Combinaison de bits (OR) de [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
dans ID de la commande.

*pPalette*<br/>
dans Pointeur désignant une palette de couleurs. La valeur par défaut est NULL.

*nColumns*<br/>
dans Nombre de colonnes dans le contrôle de la barre de couleurs. La valeur par défaut est 0.

*nRowsDockHorz*<br/>
dans Nombre de lignes dans le contrôle de la barre de couleurs lorsqu’il est ancré horizontalement. La valeur par défaut est 0.

*nColDockVert*<br/>
dans Nombre de colonnes dans le contrôle de la barre de couleurs lorsqu’il est ancré verticalement. La valeur par défaut est 0.

### <a name="return-value"></a>Valeur renvoyée

TRUE si cette méthode réussit ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Pour construire un `CMFCColorBar` objet, appelez le constructeur de classe, puis cette méthode. La `Create` méthode crée le contrôle Windows et Initialise une liste de couleurs.

## <a name="cmfccolorbarcreatecontrol"></a><a name="createcontrol"></a> CMFCColorBar :: CreateControl

Crée une fenêtre de contrôle de la barre de couleurs, l’attache à l' `CMFCColorBar` objet et redimensionne la fenêtre du contrôle pour qu’elle contienne la palette de couleurs spécifiée.

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
dans Pointeur vers la fenêtre parente. Ne peut pas avoir la valeur NULL.

*rectangulaire*<br/>
dans Rectangle englobant qui spécifie l’emplacement du contrôle de la barre de couleurs.

*nID*<br/>
dans ID du contrôle.

*nColumns*<br/>
dans Nombre idéal de colonnes dans le contrôle de la barre de couleurs. Cette méthode modifie ce nombre pour qu’il corresponde à la palette de couleurs spécifiée. La valeur par défaut est-1, ce qui signifie que ce paramètre n’est pas spécifié.

*pPalette*<br/>
dans Pointeur vers une palette de couleurs, ou NULL. Si ce paramètre a la valeur NULL, cette méthode calcule la taille du contrôle de barre de couleurs comme si 20 couleurs étaient spécifiées. La valeur par défaut est NULL.

### <a name="return-value"></a>Valeur renvoyée

TRUE si cette méthode est réussie ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode utilise les paramètres *Rect*, *nColumns* et *pPalette* pour calculer le nombre approprié de lignes et de colonnes dans le contrôle de la barre de couleurs, puis appelle la méthode [CMFCColorBar :: Create](#create) .

## <a name="cmfccolorbarcreatepalette"></a><a name="createpalette"></a> CMFCColorBar::CreatePalette

Initialise une palette avec les couleurs dans un tableau de couleurs spécifié.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Paramètres

*arColors*\
dans Tableau de couleurs.

*palette*\
dans Palette de couleurs.

### <a name="return-value"></a>Valeur renvoyée

TRUE si cette méthode réussit ; Sinon, FALSe.

## <a name="cmfccolorbarenableautomaticbutton"></a><a name="enableautomaticbutton"></a> CMFCColorBar::EnableAutomaticButton

Affiche ou masque le bouton automatique.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
dans Étiquette de texte du bouton de couleur *automatique* (par défaut) ou null.

L’étiquette standard du bouton automatique est **automatique**.

*colorAutomatic*<br/>
dans Couleur par défaut appliquée par l’infrastructure lorsque vous cliquez sur le bouton automatique.

*bEnable*<br/>
dans TRUE pour activer le bouton automatique ; FALSe pour désactiver le bouton automatique. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

L’étiquette de texte du bouton automatique est supprimée si le paramètre *lpszLabel* a la valeur null ou si le paramètre *bEnable* a la valeur false.

## <a name="cmfccolorbarenableotherbutton"></a><a name="enableotherbutton"></a> CMFCColorBar::EnableOtherButton

Active ou désactive l’affichage d’une boîte de dialogue qui permet à l’utilisateur de sélectionner d’autres couleurs.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
dans Étiquette de texte de l' *autre* bouton, qui affiche plus de choix de couleurs, ou null.

L’étiquette standard de ce bouton est **plus de couleurs.**...

*bAltColorDlg*<br/>
dans TRUE pour afficher la boîte de dialogue [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ; FALSe pour afficher la boîte de dialogue [CColorDialog](../../mfc/reference/ccolordialog-class.md) standard. La valeur par défaut est TRUE.

*bEnable*<br/>
dans TRUE pour activer le bouton. FALSe pour désactiver le bouton. La valeur par défaut est TRUE.

## <a name="cmfccolorbargetcolor"></a><a name="getcolor"></a> CMFCColorBar :: GetColor

Récupère la couleur actuellement sélectionnée.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Couleur actuellement sélectionnée.

## <a name="cmfccolorbargetcolorgridsize"></a><a name="getcolorgridsize"></a> CMFCColorBar::GetColorGridSize

Calcule le nombre de lignes et de colonnes dans la grille d’un contrôle de barre de couleurs.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>Paramètres

*bVertDock*\
dans TRUE pour effectuer le calcul pour un contrôle de barre de couleurs ancré verticalement ; Sinon, effectuez le calcul pour un contrôle ancré horizontalement.

### <a name="return-value"></a>Valeur renvoyée

Objet [CSize](../../atl-mfc-shared/reference/csize-class.md) dont `cx` le composant contient le nombre de colonnes et dont `cy` le composant contient le nombre de lignes.

## <a name="cmfccolorbargetcommandid"></a><a name="getcommandid"></a> CMFCColorBar::GetCommandID

Récupère l’ID de commande du contrôle de barre de couleurs actuel.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Valeur renvoyée

ID de commande.

### <a name="remarks"></a>Notes

Lorsque l’utilisateur sélectionne une nouvelle couleur, l’infrastructure envoie l’ID de commande dans un message WM_COMMAND pour notifier le parent de l' `CMFCColorBar` objet.

## <a name="cmfccolorbargetextraheight"></a><a name="getextraheight"></a> CMFCColorBar::GetExtraHeight

Calcule la hauteur supplémentaire requise par la barre de couleurs actuelle pour afficher divers éléments d’interface utilisateur, tels que les **autres** couleurs de document ou de bouton.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Paramètres

*nNumColumns*\
dans Si le contrôle de barre de couleurs contient des couleurs de document, le nombre de colonnes à afficher dans la grille des couleurs de document. Dans le cas contraire, cette valeur n’est pas utilisée.

### <a name="return-value"></a>Valeur renvoyée

Hauteur supplémentaire calculée requise.

## <a name="cmfccolorbargethighlightedcolor"></a><a name="gethighlightedcolor"></a> CMFCColorBar::GetHighlightedColor

Récupère la couleur qui signifie qu’un bouton de couleur a le focus ; autrement dit, le bouton est *actif*.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur RVB.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbargethorzmargin"></a><a name="gethorzmargin"></a> CMFCColorBar::GetHorzMargin

Récupère la marge horizontale, qui est l’espace entre la cellule de couleur gauche ou droite et la limite de la zone cliente.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Valeur renvoyée

Marge horizontale.

## <a name="cmfccolorbargetvertmargin"></a><a name="getvertmargin"></a> CMFCColorBar::GetVertMargin

Récupère la marge verticale, qui est l’espace entre la cellule de couleur supérieure ou inférieure et la limite de la zone cliente.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Valeur renvoyée

Marge verticale.

## <a name="cmfccolorbarinitcolors"></a><a name="initcolors"></a> CMFCColorBar::InitColors

Initialise un tableau de couleurs avec les couleurs d’une palette spécifiée, ou avec la palette par défaut du système.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Paramètres

*pPalette*\
dans Pointeur vers un objet palette, ou NULL. Si ce paramètre a la valeur NULL, cette méthode utilise la palette par défaut du système d’exploitation.

*arColors*\
dans Tableau de couleurs.

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments dans le tableau de couleurs.

## <a name="cmfccolorbaristearoff"></a><a name="istearoff"></a> CMFCColorBar::IsTearOff

Indique si la barre de couleurs actuelle est Ancrable.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si le contrôle de barre de couleurs actuel est Ancrable ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si le contrôle de la barre de couleurs est Ancrable, il peut être déchiré dans une barre de contrôle et ancré à un autre emplacement.

## <a name="cmfccolorbaronkey"></a><a name="onkey"></a> CMFCColorBar :: OnKey

Appelé par le Framework quand un utilisateur appuie sur un bouton du clavier.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Paramètres

*nChar*<br/>
dans Code de la touche virtuelle pour la touche sur laquelle un utilisateur a appuyé.

### <a name="return-value"></a>Valeur renvoyée

TRUE si cette méthode traite la clé spécifiée ; Sinon, FALSe.

## <a name="cmfccolorbaronsendcommand"></a><a name="onsendcommand"></a> CMFCColorBar::OnSendCommand

Appelé par l’infrastructure pour fermer une hiérarchie de contrôles publicitaires.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Paramètres

*pButton*\
dans Pointeur vers un contrôle qui se trouve dans une barre d’outils.

### <a name="return-value"></a>Valeur renvoyée

TRUE si cette méthode réussit ; Sinon, FALSe.

## <a name="cmfccolorbaronupdatecmdui"></a><a name="onupdatecmdui"></a> CMFCColorBar :: OnUpdateCmdUI

Appelé par l’infrastructure pour activer ou désactiver un élément de l’interface utilisateur d’un contrôle de barre de couleurs avant l’affichage de l’élément.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Paramètres

*pTarget*<br/>
dans Pointeur vers une fenêtre qui contient un élément d’interface utilisateur à mettre à jour.

*bDisableIfNoHndler*<br/>
dans TRUE pour désactiver l’élément d’interface utilisateur si aucun gestionnaire n’est défini dans une table des messages ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Lorsqu’un utilisateur de votre application clique sur un élément de l’interface utilisateur, l’élément doit savoir s’il doit être affiché comme activé ou désactivé. La cible du message de commande fournit ces informations en implémentant un gestionnaire de commandes ON_UPDATE_COMMAND_UI. Utilisez cette méthode pour aider à traiter la commande. Pour plus d’informations, consultez [CCmdUI, classe](../../mfc/reference/ccmdui-class.md).

## <a name="cmfccolorbaropencolordialog"></a><a name="opencolordialog"></a> CMFCColorBar::OpenColorDialog

Ouvre une boîte de dialogue de couleur.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Paramètres

*colorDefault*<br/>
dans Couleur sélectionnée par défaut lorsque la boîte de dialogue couleur s’ouvre.

*colorRes*<br/>
à Couleur sélectionnée par un utilisateur.

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’utilisateur a sélectionné une couleur ; FALSe si l’utilisateur a annulé la boîte de dialogue couleur.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbarrebuild"></a><a name="rebuild"></a> CMFCColorBar :: Rebuild

Redessine complètement le contrôle de la barre de couleurs.

```
virtual void Rebuild();
```

## <a name="cmfccolorbarselectpalette"></a><a name="selectpalette"></a> CMFCColorBar::SelectPalette

Définit la palette logique du contexte de périphérique spécifié sur la palette du bouton parent du contrôle de barre de couleurs actuel.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*Maîtres*\
dans Pointeur vers le contexte de périphérique du bouton parent du contrôle de barre de couleurs actuel.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la palette qui est remplacée par la palette du bouton parent du contrôle de barre de couleurs actuel.

## <a name="cmfccolorbarsetcolor"></a><a name="setcolor"></a> CMFCColorBar :: SetColor

Définit la couleur actuellement sélectionnée.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
dans Valeur de couleur RVB.

## <a name="cmfccolorbarsetcolorname"></a><a name="setcolorname"></a> CMFCColorBar::SetColorName

Définit un nouveau nom pour une couleur spécifiée.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
dans Valeur RVB d’une couleur.

*strName*<br/>
dans Nouveau nom pour la couleur spécifiée.

### <a name="remarks"></a>Notes

Cette méthode modifie le nom de la couleur spécifiée dans tous les `CMFCColorBar` objets de votre application.

## <a name="cmfccolorbarsetcommandid"></a><a name="setcommandid"></a> CMFCColorBar::SetCommandID

Définit un nouvel ID de commande pour un contrôle de barre de couleurs.

```cpp
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Paramètres

*nCommandID*<br/>
dans ID de commande.

### <a name="remarks"></a>Notes

Appelez cette méthode pour modifier l’ID de commande d’un contrôle de barre de couleurs et notifier la fenêtre parente du contrôle que l’ID a changé.

## <a name="cmfccolorbarsetdocumentcolors"></a><a name="setdocumentcolors"></a> CMFCColorBar::SetDocumentColors

Définit la liste des couleurs utilisées dans le document actif.

```cpp
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszCaption*<br/>
dans Légende qui s’affiche lorsque le contrôle de la barre de couleurs n’est pas ancré.

*lstDocColors*<br/>
dans Liste de couleurs qui remplace les couleurs du document actif.

*bShowWhenDocked*<br/>
dans TRUE pour afficher les couleurs du document lorsque le contrôle de la barre de couleurs est ancré ; Sinon, FALSe. La valeur par défaut est FALSE.

### <a name="remarks"></a>Notes

Les *couleurs de document* sont les couleurs actuellement utilisées dans un document. L’infrastructure gère automatiquement une liste de couleurs de document, mais vous pouvez utiliser cette méthode pour modifier la liste.

## <a name="cmfccolorbarsethorzmargin"></a><a name="sethorzmargin"></a> CMFCColorBar::SetHorzMargin

Définit la marge horizontale, qui est l’espace entre la cellule de couleur gauche ou droite et la limite de la zone cliente.

```cpp
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Paramètres

*nHorzMargin*<br/>
dans Marge horizontale, en pixels.

### <a name="remarks"></a>Notes

Par défaut, le constructeur [CMFCColorBar :: CMFCColorBar](#cmfccolorbar) définit la marge horizontale sur 4 pixels.

## <a name="cmfccolorbarsetproplist"></a><a name="setproplist"></a> CMFCColorBar::SetPropList

Définit le `m_pWndPropList` membre de données protégées sur le pointeur spécifié vers un contrôle de grille de propriétés.

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Paramètres

*pWndList*\
dans Pointeur vers l’objet de contrôle de grille de propriétés.

## <a name="cmfccolorbarsetvertmargin"></a><a name="setvertmargin"></a> CMFCColorBar::SetVertMargin

Définit la marge verticale, qui est l’espace entre la cellule de couleur supérieure ou inférieure et la limite de la zone cliente.

```cpp
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Paramètres

*nVertMargin*<br/>
dans Marge verticale, en pixels.

### <a name="remarks"></a>Notes

Par défaut, le constructeur [CMFCColorBar :: CMFCColorBar](#cmfccolorbar) définit la marge verticale sur 4 pixels.

## <a name="cmfccolorbarshowcommandmessagestring"></a><a name="showcommandmessagestring"></a> CMFCColorBar::ShowCommandMessageString

Demande la fenêtre frame propriétaire du contrôle de barre de couleurs pour mettre à jour la ligne de message dans la barre d’État.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Paramètres

*uiCmdId*<br/>
dans ID de commande. (Ce paramètre est ignoré.)

### <a name="remarks"></a>Notes

Cette méthode envoie le message WM_SETMESSAGESTRING au propriétaire du contrôle de barre de couleurs.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
