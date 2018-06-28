---
title: Classe de CMFCColorBar | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8786a35653dbf3d4de14b81563011b3a031c9c4b
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038996"
---
# <a name="cmfccolorbar-class"></a>Classe de CMFCColorBar
La `CMFCColorBar` classe représente une barre de contrôle d’ancrage que vous pouvez sélectionner des couleurs dans un document ou une application.  
  
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
|[CMFCColorBar::ContextToSize](#contexttosize)|Calcule les marges horizontales et verticales qui doivent contenir les boutons sur le contrôle de barre de couleur, puis ajuste l’emplacement de ces boutons.|  
|[CMFCColorBar::CreateControl](#createcontrol)|Crée une fenêtre de contrôle de barre de couleur, attache à le `CMFCColorBar` de l’objet et redimensionne le contrôle pour qu’il contienne la palette de couleurs de spécifié.|  
|[CMFCColorBar::Create](#create)|Crée une fenêtre de contrôle de barre de couleur et l’attache à le `CMFCColorBar` objet.|  
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Affiche ou masque le bouton automatique.|  
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Active ou désactive l’affichage de la boîte de dialogue qui permet à l’utilisateur de sélectionner des couleurs supplémentaires.|  
|[CMFCColorBar::GetColor](#getcolor)|Récupère la couleur actuellement sélectionnée.|  
|[CMFCColorBar::GetCommandID](#getcommandid)|Récupère l’ID de commande du contrôle de barre de couleur actuelle.|  
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Récupère la couleur qui signifie qu’un bouton de couleur a le focus ; Autrement dit, le bouton est *à chaud*.|  
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Récupère la marge horizontale, qui est l’espace entre la gauche ou cellule de la couleur de droite et la limite de la zone cliente.|  
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Récupère la marge verticale, qui est l’espace entre le haut ou cellule de couleur inférieure et la limite de la zone cliente.|  
|[CMFCColorBar::IsTearOff](#istearoff)|Indique si la barre de couleur actuelle est ancrable.|  
|[CMFCColorBar::SetColor](#setcolor)|Définit la couleur actuellement sélectionnée.|  
|[CMFCColorBar::SetColorName](#setcolorname)|Définit un nouveau nom d’une couleur spécifiée.|  
|[CMFCColorBar::SetCommandID](#setcommandid)|Définit un nouvel ID de commande pour un contrôle de barre de couleur.|  
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Définit la liste des couleurs utilisées dans le document actif.|  
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Définit la marge horizontale, qui est l’espace entre la gauche ou cellule de la couleur de droite et la limite de la zone cliente.|  
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Définit la marge verticale, qui est l’espace entre la cellule de couleur en haut ou en bas et de la limite de la zone cliente.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Ajuste les positions des boutons de couleur sur le contrôle de barre de couleur.|  
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Indique si l’étiquette de texte des boutons de couleur peut modifier.|  
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Indique si l’objet de contrôle de barre de couleur permettre apparaître dans une liste de la barre d’outils pendant le processus de personnalisation.|  
|[CMFCColorBar::CalcSize](#calcsize)|Appelé par l’infrastructure dans le cadre du processus de calcul de disposition.|  
|[CMFCColorBar::CreatePalette](#createpalette)|Initialise une palette de couleurs dans un tableau de couleurs spécifié.|  
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Calcule le nombre de lignes et colonnes dans la grille d’un contrôle de barre de couleur.|  
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Calcule la hauteur supplémentaire nécessitant la barre de couleurs en cours pour afficher les éléments d’interface utilisateur divers tels que les **autres** bouton, couleurs du document et ainsi de suite.|  
|[CMFCColorBar::InitColors](#initcolors)|Initialise un tableau de couleurs avec les couleurs dans une palette spécifiée ou de la palette par défaut du système.|  
|[CMFCColorBar::OnKey](#onkey)|Appelé par l’infrastructure quand un utilisateur appuie sur un bouton de clavier.|  
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Appelé par l’infrastructure pour fermer une hiérarchie des contrôles de fenêtre contextuelle.|  
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Appelé par l’infrastructure pour activer ou désactiver un élément d’interface utilisateur d’un contrôle de barre de couleur avant que l’élément est affiché.|  
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Ouvre une boîte de dialogue couleur.|  
|[CMFCColorBar::Rebuild](#rebuild)|Complètement redessine le contrôle de barre de couleur.|  
|[CMFCColorBar::SelectPalette](#selectpalette)|Définit la palette logique du contexte de périphérique spécifié à la palette du bouton parent du contrôle de barre de couleur actuelle.|  
|[CMFCColorBar::SetPropList](#setproplist)|Définit le `m_pWndPropList` protégé par membre de données du pointeur spécifié vers un contrôle de grille de propriétés.|  
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|La fenêtre frame qui possède le contrôle de barre de couleur pour mettre à jour la ligne du message dans la barre d’état des demandes.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|`m_bInternal`|Un champ booléen qui détermine si les événements de souris sont traités. En règle générale, les événements de souris sont traitées lorsque ce champ est `TRUE` et le mode de personnalisation est `FALSE`.|  
|`m_bIsEnabled`|Valeur booléenne qui indique si un contrôle est activé.|  
|`m_bIsTearOff`|Valeur booléenne qui indique si le contrôle de barre de couleur prend en charge l’ancrage.|  
|`m_BoxSize`|A [CSize](../../atl-mfc-shared/reference/csize-class.md) objet qui spécifie la taille d’une cellule dans une grille de la barre de couleurs.|  
|`m_bShowDocColorsWhenDocked`|Valeur booléenne qui indique s’il faut afficher les couleurs de document lors de la barre de couleurs est ancrée. Pour plus d’informations, consultez [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|  
|`m_bStdColorDlg`|Valeur booléenne qui indique s’il faut afficher la boîte de dialogue couleur système standard ou [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) boîte de dialogue. Pour plus d’informations, consultez [CMFCColorBar::EnableOtherButton](#enableotherbutton).|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) qui stocke la couleur automatique. Pour plus d’informations, consultez [CMFCColorBar::EnableOtherButton](#enableotherbutton).|  
|`m_ColorNames`|Un [CMap](../../mfc/reference/cmap-class.md) objet qui associe un jeu de RVB des couleurs avec leurs noms.|  
|`m_colors`|A [CArray](../../mfc/reference/carray-class.md) de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeurs contenant les couleurs affichées dans le contrôle de barre de couleur.|  
|`m_ColorSelected`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur qui est la couleur actuellement sélectionnée par l’utilisateur à partir du contrôle de barre de couleur.|  
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md) de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeurs contenant les couleurs qui sont actuellement utilisés dans un document.|  
|`m_nCommandID`|Entier non signé qui est l’ID de commande d’un bouton de couleur.|  
|`m_nHorzMargin`|Entier qui est la marge horizontale entre les boutons de couleur dans une grille de couleurs.|  
|`m_nHorzOffset`|Entier qui est le décalage horizontal au centre du bouton de couleur. Cette valeur est importante si le bouton affiche du texte ou une image en plus d’une couleur.|  
|`m_nNumColumns`|Entier qui indique le nombre de colonnes dans une grille de contrôle de barre de couleurs de couleurs.|  
|`m_nNumColumnsVert`|Entier qui indique le nombre de colonnes dans une grille orientée verticalement de couleurs.|  
|`m_nNumRowsHorz`|Entier qui indique le nombre de colonnes dans une grille orientée horizontalement de couleurs.|  
|`m_nRowHeight`|Entier qui correspond à la hauteur d’une ligne de boutons de couleur dans une grille de couleurs.|  
|`m_nVertMargin`|Entier qui est la marge verticale entre les boutons de couleur dans une grille de couleurs.|  
|`m_nVertOffset`|Entier qui est le décalage vertical au centre du bouton de couleur. Cette valeur est importante si le bouton affiche du texte ou une image en plus d’une couleur.|  
|`m_Palette`|A [CPalette](../../mfc/reference/cpalette-class.md) des couleurs utilisées dans le contrôle de barre de couleur.|  
|`m_pParentBtn`|Un pointeur vers un [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) objet qui est le parent du bouton actuel. Cette valeur est significative si le bouton de couleur est dans une hiérarchie des contrôles de barre d’outils ou dans un contrôle de grille de propriétés de couleur.|  
|`m_pParentRibbonBtn`|Un pointeur vers un [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) objet qui se trouve sur le ruban et est le parent de bouton du bouton actuel. Cette valeur est significative si le bouton de couleur est dans une hiérarchie des contrôles de barre d’outils ou dans un contrôle de grille de propriétés de couleur.|  
|`m_pWndPropList`|Un pointeur vers un [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) objet.|  
|`m_strAutoColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui est le texte qui est affiché sur le **automatique** bouton. Pour plus d’informations, consultez [CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton).|  
|`m_strDocColors`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui est le texte qui est affiché sur le bouton de couleurs du document. Pour plus d’informations, consultez [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|  
|`m_strOtherColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui est le texte qui est affiché sur le *autres* bouton. Pour plus d’informations, consultez [CMFCColorBar::EnableOtherButton](#enableotherbutton).|  
  
## <a name="remarks"></a>Notes  
 En règle générale, vous ne créez pas un `CMFCColorBar` directement l’objet. Au lieu de cela, le [CMFCColorMenuButton classe](../../mfc/reference/cmfccolormenubutton-class.md) (utilisé dans les menus et barres d’outils) ou le [CMFCColorButton classe](../../mfc/reference/cmfccolorbutton-class.md) crée le `CMFCColorBar` objet.  
  
 La `CMFCColorBar` classe fournit les fonctionnalités suivantes :  
  
-   Ajuste automatiquement la liste des couleurs du document.  
  
-   Enregistre et restaure son état, ainsi que l’état du document.  
  
-   Gère le bouton « automatique ».  
  
-   Utilise le [CMFCColorPickerCtrl classe](../../mfc/reference/cmfccolorpickerctrl-class.md) contrôle pour sélectionner une couleur personnalisée.  
  
-   Prend en charge un état « détacher » (s’il est créé à l’aide de la [CMFCColorMenuButton classe](../../mfc/reference/cmfccolormenubutton-class.md)).  
  
 Pour incorporer le `CMFCColorBar` fonctionnalité dans votre application :  
  
1.  Créer un bouton de menu standard et attribuez-le à un ID, par exemple ID_CHAR_COLOR.  
  
2.  Dans votre classe de fenêtre frame, substituez le [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) (méthode) et remplacer le menu régulière bouton avec un [CMFCColorMenuButton classe](../../mfc/reference/cmfccolormenubutton-class.md) objet (en appelant [CMFCToolBar : : ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).  
  
3.  Définir tous les styles et activer ou désactiver les fonctionnalités de la `CMFCColorBar` au cours de l’objet [CMFCColorMenuButton classe](../../mfc/reference/cmfccolormenubutton-class.md) création. Le `CMFCColorMenuButton` objet crée dynamiquement le `CMFCColorBar` objet après le framework appelle la `CreatePopupMenu` (méthode).  
  
 Lorsque l’utilisateur clique sur un bouton de contrôle de barre de couleur, le framework utilise le `ON_COMMAND` macro pour notifier le parent du contrôle de barre de couleur. Dans la macro, le paramètre d’ID de commande est la valeur que vous avez affecté au bouton du contrôle de barre de couleurs à l’étape 1 (ID_CHAR_COLOR dans cet exemple). Pour plus d’informations, consultez la [CMFCColorMenuButton classe](../../mfc/reference/cmfccolormenubutton-class.md), [CMFCColorButton classe](../../mfc/reference/cmfccolorbutton-class.md), [CMFCColorPickerCtrl classe](../../mfc/reference/cmfccolorpickerctrl-class.md), [CFrameWndEx classe](../../mfc/reference/cframewndex-class.md), et [CMFCToolBar classe](../../mfc/reference/cmfctoolbar-class.md) classes.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer une barre de couleur à l’aide de différentes méthodes de la `CMFCColorBar` classe. Les méthodes de définir les marges horizontales et verticales, activer le bouton autre, créent une fenêtre de contrôle de barre de couleur et définit la couleur actuellement sélectionnée. Cet exemple fait partie de la [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
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
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcolorbar.h  
  
##  <a name="adjustlocations"></a>  CMFCColorBar::AdjustLocations  
 Ajuste les positions des boutons de couleur sur le contrôle de barre de couleur.  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par l’infrastructure lors du traitement du message WM_SIZE.  
  
##  <a name="allowchangetextlabels"></a>  CMFCColorBar::AllowChangeTextLabels  
 Indique si l’étiquette de texte des boutons de couleur peut modifier.  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Toujours `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Par défaut, cette méthode retourne toujours `FALSE`, ce qui signifie que les étiquettes de texte ne peut pas être modifié. Substituez cette méthode pour permettre la modification des étiquettes de texte.  
  
##  <a name="allowshowonlist"></a>  CMFCColorBar::AllowShowOnList  
 Indique si l’objet de contrôle de barre de couleur permettre apparaître dans une liste de la barre d’outils pendant le processus de personnalisation.  
  
```  
virtual BOOL AllowShowOnList() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Toujours `TRUE`.  
  
### <a name="remarks"></a>Notes  
 Par défaut, cette méthode retourne toujours `TRUE`, ce qui signifie que l’infrastructure peut afficher le contrôle de barre de couleur au cours du processus de personnalisation. Substituez cette méthode pour implémenter un comportement différent.  
  
##  <a name="calcsize"></a>  CMFCColorBar::CalcSize  
 Appelé par l’infrastructure dans le cadre du processus de calcul de disposition.  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bVertDock*  
 `TRUE` Pour spécifier que le contrôle de barre de couleur est ancré verticalement ; `FALSE` pour spécifier que le contrôle de barre de couleur est ancré horizontalement.  
  
### <a name="return-value"></a>Valeur de retour  
 La taille du tableau de boutons de couleur dans un contrôle de barre de couleur.  
  
##  <a name="cmfccolorbar"></a>  CMFCColorBar::CMFCColorBar  
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
 [in] *couleurs*  
 Un tableau de couleurs affichée par l’infrastructure sur le contrôle de barre de couleur.  
  
 [in] *couleur*  
 La couleur initialement sélectionnée.  
  
 [in] *lpszAutoColor*  
 L’étiquette de texte de la *automatique* bouton de couleur (par défaut), ou `NULL`.  
  
 L’étiquette standard pour le bouton automatique est **automatique**.  
  
 [in] *lpszOtherColor*  
 L’étiquette de texte de la *autres* bouton qui affiche d’autres options de couleur, ou `NULL`.  
  
 L’étiquette standard pour l’autre bouton est **autres couleurs...** .  
  
 [in] *lpszDocColors*  
 L’étiquette de texte du bouton de couleurs de document. La palette de couleurs du document répertorie toutes les couleurs que le document utilise actuellement.  
  
 [in] *lstDocColors*  
 Une liste de couleurs que le document utilise actuellement.  
  
 [in] *nColumns*  
 Le nombre de colonnes qui a le groupe de couleurs.  
  
 [in] *nRowsDockHorz*  
 Le nombre de lignes de la barre de couleur lorsqu’il est ancré horizontalement.  
  
 [in] *nColDockVert*  
 Le nombre de colonnes de la barre de couleur lorsqu’il est ancré verticalement.  
  
 [in] *automatiqueCouleur*  
 La couleur par défaut que le framework s’applique lorsque vous cliquez sur le bouton automatique.  
  
 [in] *nCommandID*  
 ID de la commande de contrôle de barre de couleur.  
  
 [in] *pParentBtn*  
 Pointeur vers un bouton parent.  
  
 [in] *src*  
 Existant `CMFCColorBar` à copier dans le nouvel objet `CMFCColorBar` objet.  
  
 [in] *uiCommandID*  
 ID de la commande.  
  
##  <a name="contexttosize"></a>  CMFCColorBar::ContextToSize  
 Calcule les marges horizontales et verticales qui sont nécessaires pour contenir les boutons sur le contrôle de barre de couleur et ajuste l’emplacement de ces boutons.  
  
```  
void ContextToSize(
    BOOL bSquareButtons = TRUE,   
    BOOL bCenterButtons = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *bSquareButtons*|`TRUE` Pour spécifier que la forme des boutons sur un contrôle de barre de couleur sont carrées ; dans le cas contraire, `FALSE`. La valeur par défaut est `TRUE`.|  
|[in] *bCenterButtons*|`TRUE` Pour spécifier que le contenu sur un bouton de contrôle de barre de couleur est centré ; dans le cas contraire, `FALSE`. La valeur par défaut est `TRUE`.|  
  
### <a name="remarks"></a>Notes  
  
##  <a name="create"></a>  CMFCColorBar::Create  
 Crée une fenêtre de contrôle de barre de couleur et l’attache à le `CMFCColorBar` objet.  
  
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
 [in] *pParentWnd*  
 Pointeur vers la fenêtre parente.  
  
 [in] *dwStyle*  
 Combinaison de bits de (OR) [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] *nID*  
 ID de la commande.  
  
 [in] *pPalette*  
 Pointeur vers une palette de couleurs. La valeur par défaut est `NULL`.  
  
 [in] *nColumns*  
 Le nombre de colonnes dans le contrôle de barre de couleur. La valeur par défaut est 0.  
  
 [in] *nRowsDockHorz*  
 Le nombre de lignes dans le contrôle de barre de couleur lorsqu’il est ancré horizontalement. La valeur par défaut est 0.  
  
 [in] *nColDockVert*  
 Le nombre de colonnes dans le contrôle de barre de couleur lorsqu’il est ancré verticalement. La valeur par défaut est 0.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si cette méthode a réussi ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Pour construire un `CMFCColorBar` d’objet, appelez le constructeur de classe, cette méthode. Le `Create` méthode crée le contrôle Windows et initialise une liste de couleurs.  
  
##  <a name="createcontrol"></a>  CMFCColorBar::CreateControl  
 Crée une fenêtre de contrôle de barre de couleur, attache à le `CMFCColorBar` de l’objet et redimensionne la fenêtre de contrôle pour qu’il contienne la palette de couleurs de spécifié.  
  
```  
virtual BOOL CreateControl(
    CWnd* pParentWnd,  
    const CRect& rect,  
    UINT nID,  
    int nColumns=-1,  
    CPalette* pPalette=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pParentWnd*  
 Pointeur vers la fenêtre parente. Ne peut pas être `NULL`.  
  
 [in] *rect*  
 Un rectangle englobant qui indique où dessiner le contrôle de barre de couleur.  
  
 [in] *nID*  
 L’ID du contrôle.  
  
 [in] *nColumns*  
 Le nombre idéal de colonnes dans le contrôle de barre de couleur. Cette méthode modifie ce nombre pour s’ajuster à la palette de couleurs de spécifié. La valeur par défaut est -1, ce qui signifie que ce paramètre n’est pas spécifié.  
  
 [in] *pPalette*  
 Pointeur vers une palette de couleurs, ou `NULL`. Si ce paramètre est `NULL`, cette méthode calcule la taille du contrôle de barre de couleur comme si 20 couleurs ont été spécifiées. La valeur par défaut est `NULL`.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si cette méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode utilise le *rect*, *nColumns*, et *pPalette* paramètres pour calculer le nombre approprié ou de lignes et de colonnes dans le contrôle de barre de couleur, puis appelle la [CMFCColorBar::Create](#create) (méthode).  
  
##  <a name="createpalette"></a>  CMFCColorBar::CreatePalette  
 Initialise une palette de couleurs dans un tableau de couleurs spécifié.  
  
```  
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,   
    CPalette& palette);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *arColors*|Un tableau de couleurs.|  
|[in] *palette*|Une palette de couleurs.|  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si cette méthode a réussi ; dans le cas contraire, `FALSE`.  
  
##  <a name="enableautomaticbutton"></a>  CMFCColorBar::EnableAutomaticButton  
 Affiche ou masque le bouton automatique.  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszLabel*  
 L’étiquette de texte de la *automatique* bouton de couleur (par défaut), ou `NULL`.  
  
 L’étiquette standard pour le bouton automatique est **automatique**.  
  
 [in] *automatiqueCouleur*  
 La couleur par défaut que le framework s’applique lorsque vous cliquez sur le bouton automatique.  
  
 [in] *bActivez*  
 `TRUE` Pour activer le bouton automatique ; `FALSE` pour désactiver le bouton automatique. La valeur par défaut est `TRUE`.  
  
### <a name="remarks"></a>Notes  
 L’étiquette de texte du bouton automatique est supprimée si la *lpszLabel* paramètre est `NULL` ou *bActivez* paramètre est `FALSE`.  
  
##  <a name="enableotherbutton"></a>  CMFCColorBar::EnableOtherButton  
 Active ou désactive l’affichage de la boîte de dialogue qui permet à l’utilisateur de sélectionner des couleurs supplémentaires.  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszLabel*  
 L’étiquette de texte de la *autres* bouton qui affiche d’autres options de couleur, ou `NULL`.  
  
 L’étiquette standard pour ce bouton est **autres couleurs...** .  
  
 [in] *bAltColorDlg*  
 `TRUE` Pour afficher le [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) boîte de dialogue. `FALSE` pour afficher la norme [CColorDialog](../../mfc/reference/ccolordialog-class.md) boîte de dialogue. La valeur par défaut est `TRUE`.  
  
 [in] `bEnable`  
 `TRUE` Pour activer le bouton ; `FALSE` pour désactiver le bouton. La valeur par défaut est `TRUE`.  
  
##  <a name="getcolor"></a>  CMFCColorBar::GetColor  
 Récupère la couleur actuellement sélectionnée.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La couleur actuellement sélectionnée.  
  
##  <a name="getcolorgridsize"></a>  CMFCColorBar::GetColorGridSize  
 Calcule le nombre de lignes et colonnes dans la grille d’un contrôle de barre de couleur.  
  
```  
CSize GetColorGridSize(BOOL bVertDock) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *bVertDock*|`TRUE` Pour effectuer le calcul pour un contrôle de barre de couleur ancré verticalement ; dans le cas contraire, effectuer le calcul pour un contrôle ancré horizontalement.|  
  
### <a name="return-value"></a>Valeur de retour  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) dont l’objet `cx` composant contient le nombre de colonnes et dont `cy` composant contient le nombre de lignes.  
  
##  <a name="getcommandid"></a>  CMFCColorBar::GetCommandID  
 Récupère l’ID de commande du contrôle de barre de couleur actuelle.  
  
```  
UINT GetCommandID() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un ID de commande.  
  
### <a name="remarks"></a>Notes  
 Lorsque l’utilisateur sélectionne une nouvelle couleur, le framework envoie l’ID de commande dans un message WM_COMMAND pour notifier le parent de la `CMFCColorBar` objet.  
  
##  <a name="getextraheight"></a>  CMFCColorBar::GetExtraHeight  
 Calcule la hauteur supplémentaire nécessitant la barre de couleurs en cours pour afficher les éléments d’interface utilisateur divers, tels que les **autres** couleurs de bouton ou un document.  
  
```  
int GetExtraHeight(int nNumColumns) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *nNumColumns*|Si le contrôle de barre de couleurs contient des couleurs du document, le nombre de colonnes à afficher dans la grille de couleurs du document. Sinon, cette valeur n’est pas utilisée.|  
  
### <a name="return-value"></a>Valeur de retour  
 La hauteur supplémentaire calculée qui est requise.  
  
##  <a name="gethighlightedcolor"></a>  CMFCColorBar::GetHighlightedColor  
 Récupère la couleur qui signifie qu’un bouton de couleur a le focus ; Autrement dit, le bouton est *à chaud*.  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur RVB.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="gethorzmargin"></a>  CMFCColorBar::GetHorzMargin  
 Récupère la marge horizontale, qui est l’espace entre la gauche ou cellule de la couleur de droite et la limite de la zone cliente.  
  
```  
int GetHorzMargin();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La marge horizontale.  
  
##  <a name="getvertmargin"></a>  CMFCColorBar::GetVertMargin  
 Récupère la marge verticale, qui est l’espace entre le haut ou cellule de couleur inférieure et la limite de la zone cliente.  
  
```  
int GetVertMargin() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La marge verticale.  
  
##  <a name="initcolors"></a>  CMFCColorBar::InitColors  
 Initialise un tableau de couleurs avec les couleurs dans une palette spécifiée, ou avec la palette par défaut du système.  
  
```  
static int InitColors(
    CPalette* pPalette,   
    CArray<COLORREF, COLORREF>& arColors);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *pPalette*|Un pointeur vers un objet de la palette, ou `NULL`. Si ce paramètre est `NULL`, cette méthode utilise la palette par défaut du système d’exploitation.|  
|[in] *arColors*|Un tableau de couleurs.|  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans le tableau de couleurs.  
  
##  <a name="istearoff"></a>  CMFCColorBar::IsTearOff  
 Indique si la barre de couleur actuelle est ancrable.  
  
```  
BOOL IsTearOff() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le contrôle de barre de couleur actuelle est ancrable ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Si le contrôle de barre de couleur est ancrable, peut être détaché une barre de contrôle et ancré à un autre emplacement.  
  
##  <a name="onkey"></a>  CMFCColorBar::OnKey  
 Appelé par l’infrastructure quand un utilisateur appuie sur un bouton de clavier.  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nChar*  
 Le code de touche virtuelle pour un utilisateur a appuyé sur la clé.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si cette méthode traite la clé spécifiée ; dans le cas contraire, `FALSE`.  
  
##  <a name="onsendcommand"></a>  CMFCColorBar::OnSendCommand  
 Appelé par l’infrastructure pour fermer une hiérarchie de menus contextuels.  
  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *pButton*|Pointeur vers un contrôle qui réside sur une barre d’outils.|  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si cette méthode a réussi ; dans le cas contraire, `FALSE`.  
  
##  <a name="onupdatecmdui"></a>  CMFCColorBar::OnUpdateCmdUI  
 Appelé par l’infrastructure pour activer ou désactiver un élément d’interface utilisateur d’un contrôle de barre de couleur avant que l’élément est affiché.  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pTarget*  
 Pointeur vers une fenêtre qui contient un élément d’interface utilisateur pour mettre à jour.  
  
 [in] *bDisableIfNoHndler*  
 `TRUE` Pour désactiver l’élément d’interface utilisateur si aucun gestionnaire n’est défini dans une table des messages ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’un utilisateur de votre application clique sur un élément d’interface utilisateur, l’élément doit savoir si elle doit être affiché comme activé ou désactivé. La cible du message de commande fournit ces informations en implémentant un `ON_UPDATE_COMMAND_UI` Gestionnaire de commandes. Utilisez cette méthode pour aider à traiter la commande. Pour plus d’informations, consultez [CCmdUI (classe)](../../mfc/reference/ccmdui-class.md).  
  
##  <a name="opencolordialog"></a>  CMFCColorBar::OpenColorDialog  
 Ouvre une boîte de dialogue couleur.  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *colorDefault*  
 La couleur sélectionnée par défaut lorsque la boîte de dialogue couleur s’ouvre.  
  
 [out] *colorRes*  
 La couleur sélectionné par un utilisateur.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si l’utilisateur a sélectionné une couleur ; `FALSE` si l’utilisateur a annulé la boîte de dialogue couleur.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="rebuild"></a>  CMFCColorBar::Rebuild  
 Complètement redessine le contrôle de barre de couleur.  
  
```  
virtual void Rebuild();
```  
  
##  <a name="selectpalette"></a>  CMFCColorBar::SelectPalette  
 Définit la palette logique du contexte de périphérique spécifié à la palette du bouton parent du contrôle de barre de couleur actuelle.  
  
```  
CPalette* SelectPalette(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *contrôleur de domaine principal*|Pointeur vers le contexte de périphérique du bouton parent du contrôle de barre de couleur actuelle.|  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la palette est remplacée par la palette du bouton parent du contrôle de barre de couleur actuelle.  
  
##  <a name="setcolor"></a>  CMFCColorBar::SetColor  
 Définit la couleur actuellement sélectionnée.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *couleur*  
 Une valeur de couleur RVB.  
  
##  <a name="setcolorname"></a>  CMFCColorBar::SetColorName  
 Définit un nouveau nom d’une couleur spécifiée.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *couleur*  
 La valeur RVB d’une couleur.  
  
 [in] *strName*  
 Le nouveau nom de la couleur spécifiée.  
  
### <a name="remarks"></a>Notes  
 Cette méthode modifie le nom de la couleur spécifiée dans toutes les `CMFCColorBar` objets dans votre application.  
  
##  <a name="setcommandid"></a>  CMFCColorBar::SetCommandID  
 Définit un nouvel ID de commande pour un contrôle de barre de couleur.  
  
```  
void SetCommandID(UINT nCommandID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nCommandID*  
 Un ID de commande.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour modifier l’ID de commande d’un contrôle de barre de couleur et de notification de la fenêtre parente du contrôle que l’ID a changé.  
  
##  <a name="setdocumentcolors"></a>  CMFCColorBar::SetDocumentColors  
 Définit la liste des couleurs utilisées dans le document actif.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszCaption,  
    CList<COLORREF,COLORREF>& lstDocColors,  
    BOOL bShowWhenDocked=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszCaption*  
 Une légende qui s’affiche lorsque le contrôle de barre de couleur n’est pas ancré.  
  
 [in] *lstDocColors*  
 Une liste de couleurs qui remplace les couleurs du document actif.  
  
 [in] *bShowWhenDocked*  
 `TRUE` Pour afficher les couleurs du document lorsque le contrôle de barre de couleur est ancré ; dans le cas contraire, `FALSE`. La valeur par défaut est `FALSE`.  
  
### <a name="remarks"></a>Notes  
 *Couleurs de document* sont les couleurs qui sont actuellement utilisés dans un document. Le framework gère automatiquement une liste de couleurs du document, mais vous pouvez utiliser cette méthode pour modifier la liste.  
  
##  <a name="sethorzmargin"></a>  CMFCColorBar::SetHorzMargin  
 Définit la marge horizontale, qui est l’espace entre la gauche ou cellule de la couleur de droite et la limite de la zone cliente.  
  
```  
void SetHorzMargin(int nHorzMargin);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nHorzMargin*  
 La marge horizontale, en pixels.  
  
### <a name="remarks"></a>Notes  
 Par défaut, le [CMFCColorBar::CMFCColorBar](#cmfccolorbar) constructeur définit la marge horizontale de 4 pixels.  
  
##  <a name="setproplist"></a>  CMFCColorBar::SetPropList  
 Définit le `m_pWndPropList` protégé par membre de données du pointeur spécifié vers un contrôle de grille de propriétés.  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *pWndList*|Pointeur vers l’objet de contrôle de grille de propriété.|  
  
##  <a name="setvertmargin"></a>  CMFCColorBar::SetVertMargin  
 Définit la marge verticale, qui est l’espace entre la cellule de couleur en haut ou en bas et de la limite de la zone cliente.  
  
```  
void SetVertMargin(int nVertMargin);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nVertMargin*  
 La marge verticale, en pixels.  
  
### <a name="remarks"></a>Notes  
 Par défaut, le [CMFCColorBar::CMFCColorBar](#cmfccolorbar) constructeur définit la marge verticale de 4 pixels.  
  
##  <a name="showcommandmessagestring"></a>  CMFCColorBar::ShowCommandMessageString  
 La fenêtre frame qui possède le contrôle de barre de couleur pour mettre à jour la ligne du message dans la barre d’état des demandes.  
  
```  
virtual void ShowCommandMessageString(UINT uiCmdId);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiCmdId*  
 Un ID de commande. (Ce paramètre est ignoré.)  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le message WM_SETMESSAGESTRING au propriétaire du contrôle de barre de couleur.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
