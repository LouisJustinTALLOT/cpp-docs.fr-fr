---
title: Classe CMFCRibbonColorButton | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::AddColorsGroup
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableAutomaticButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableOtherButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetAutomaticColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetHighlightedColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::RemoveAllColorGroups
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorName
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetDocumentColors
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetPalette
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::UpdateColor
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonColorButton [MFC], CMFCRibbonColorButton
- CMFCRibbonColorButton [MFC], AddColorsGroup
- CMFCRibbonColorButton [MFC], EnableAutomaticButton
- CMFCRibbonColorButton [MFC], EnableOtherButton
- CMFCRibbonColorButton [MFC], GetAutomaticColor
- CMFCRibbonColorButton [MFC], GetColor
- CMFCRibbonColorButton [MFC], GetColorBoxSize
- CMFCRibbonColorButton [MFC], GetColumns
- CMFCRibbonColorButton [MFC], GetHighlightedColor
- CMFCRibbonColorButton [MFC], RemoveAllColorGroups
- CMFCRibbonColorButton [MFC], SetColor
- CMFCRibbonColorButton [MFC], SetColorBoxSize
- CMFCRibbonColorButton [MFC], SetColorName
- CMFCRibbonColorButton [MFC], SetColumns
- CMFCRibbonColorButton [MFC], SetDocumentColors
- CMFCRibbonColorButton [MFC], SetPalette
- CMFCRibbonColorButton [MFC], UpdateColor
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa188930f6fe80d26282252ef3aae875aa19922f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372558"
---
# <a name="cmfcribboncolorbutton-class"></a>CMFCRibbonColorButton (classe)
La classe `CMFCRibbonColorButton` implémente un bouton de couleur que vous pouvez ajouter à une barre de ruban. Le bouton de couleur du ruban affiche un menu déroulant qui contient une ou plusieurs palettes de couleurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonColorButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|Ajoute un groupe de couleurs dans la zone de couleur normale.|  
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|Spécifie si le bouton **Automatique** est activé.|  
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|Active le bouton **Autres** .|  
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||  
|[CMFCRibbonColorButton::GetColor](#getcolor)|Retourne la couleur actuellement sélectionnée.|  
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|Retourne la taille des éléments de couleur qui apparaissent dans la barre de couleurs.|  
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||  
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|Retourne la couleur de l’élément actuellement sélectionné dans la palette de couleurs contextuelle.|  
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|Supprime tous les groupes de couleurs de la zone de couleur normale.|  
|[CMFCRibbonColorButton::SetColor](#setcolor)|Sélectionne une couleur dans la zone de couleur normale.|  
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|Définit la taille de tous les éléments de couleur qui apparaissent dans la barre de couleurs.|  
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||  
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||  
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|Spécifie une liste de valeurs RVB à afficher dans la zone de couleur du document.|  
|[CMFCRibbonColorButton::SetPalette](#setpalette)||  
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||  
  
## <a name="remarks"></a>Notes  
 Le bouton de couleur du ruban affiche une barre de couleurs quand un utilisateur clique dessus. Par défaut, cette barre de couleurs contient une palette de sélection de couleurs appelée zone de couleur normale. Si vous le souhaitez, la barre de couleurs peut afficher un bouton **Automatique** , qui permet à l’utilisateur de sélectionner une couleur par défaut, et un bouton **Autres** qui affiche une palette de couleurs contextuelle qui contient des couleurs supplémentaires.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCRibbonColorButton` . L’exemple montre comment construire un objet `CMFCRibbonColorButton` , définir l’image de grande taille, activez le bouton **Automatique** , activer le bouton **Autres** , définir le nombre de colonnes, définir la taille de tous les éléments de couleur qui apparaissent sur la barre de couleurs, ajouter un groupe de couleurs à la zone de couleur normale et spécifier une liste de valeurs RVB à afficher dans la zone de couleur du document. Cet extrait de code fait partie de l’ [exemple Draw Client](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxribboncolorbutton.h  
  
##  <a name="addcolorsgroup"></a>  CMFCRibbonColorButton::AddColorsGroup  
 Ajoute un groupe de couleurs dans la zone de couleur normale.  
  
```  
void AddColorsGroup(
    LPCTSTR lpszName,  
    const CList<COLORREF,COLORREF>& lstColors,  
    BOOL bContiguousColumns=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszName`  
 Le nom du groupe.  
  
 [in] `lstColors`  
 La liste des couleurs.  
  
 [in] `bContiguousColumns`  
 Contrôle la façon dont les éléments de couleur sont affichés dans le groupe. Si `TRUE`, les éléments de couleur sont dessinées sans un espacement vertical. Si `FALSE`, les éléments de couleur sont dessinés avec un espacement vertical.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette fonction pour rendre la couleur contextuel Afficher plusieurs groupes de couleurs. Vous pouvez contrôler la façon dont les couleurs sont affichées dans le groupe.  
  
##  <a name="cmfcribboncolorbutton"></a>  CMFCRibbonColorButton::CMFCRibbonColorButton  
 Construit un objet `CMFCRibbonColorButton`.  
  
```  
CMFCRibbonColorButton();

 
CMFCRibbonColorButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    COLORREF color = RGB(0, 0, 0));

 
CMFCRibbonColorButton(
    UINT nID,  
    LPCTSTR lpszText,  
    BOOL bSimpleButtonLook,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    COLORREF color = RGB(0, 0, 0));
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nID`  
 Spécifie l’ID de commande de la commande à exécuter quand un utilisateur clique sur le bouton.  
  
 [in] `lpszText`  
 Spécifie le texte à afficher sur le bouton.  
  
 [in] `nSmallImageIndex`  
 Index de base zéro de la petite image à afficher sur le bouton.  
  
 [in] `color`  
 La couleur du bouton (noir par défaut).  
  
 [in] `bSimpleButtonLook`  
 Si `TRUE`, le bouton est dessiné comme un rectangle simple.  
  
 [in] `nLargeImageIndex`  
 Index de base zéro d’une grande image à afficher sur le bouton.  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="enableautomaticbutton"></a>  CMFCRibbonColorButton::EnableAutomaticButton  
 Spécifie si le bouton **Automatique** est activé.  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE,  
    LPCTSTR lpszToolTip=NULL,  
    BOOL bOnTop=TRUE,  
    BOOL bDrawBorder=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszLabel`  
 L’étiquette pour le **automatique** bouton.  
  
 [in] `colorAutomatic`  
 Une valeur RVB qui spécifie le **automatique** couleur de valeur par défaut du bouton.  
  
 [in] `bEnable`  
 `TRUE` Si le **automatique** bouton est activé ; `FALSE` si elle est désactivée.  
  
 [in] `lpszToolTip`  
 L’info-bulle de la **automatique** bouton.  
  
 [in] `bOnTop`  
 Spécifie si le **automatique** bouton s’affiche en haut, avant la palette de couleurs.  
  
 [in] `bDrawBorder`  
 `TRUE` Si l’application dessine une bordure autour de la barre de couleurs sur le bouton de couleur du ruban. Barre de couleurs affiche la couleur actuellement sélectionnée. `FALSE` Si l’application ne consomme pas une bordure  
  
##  <a name="enableotherbutton"></a>  CMFCRibbonColorButton::EnableOtherButton  
 Active le bouton **Autres** .  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    LPCTSTR lpszToolTip=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszLabel`  
 L’étiquette du bouton.  
  
 `lpszToolTip`  
 Le texte d’info-bulle pour le **autres** bouton.  
  
### <a name="remarks"></a>Notes  
 Le **autres** bouton est le bouton qui s’affiche sous le groupe de couleurs. Lorsque l’utilisateur clique sur le **autres** bouton, il affiche une boîte de dialogue couleur.  
  
##  <a name="getautomaticcolor"></a>  CMFCRibbonColorButton::GetAutomaticColor  
 Récupère la couleur actuelle du bouton automatique.  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur de couleur RVB qui représente la couleur actuelle du bouton automatique.  
  
### <a name="remarks"></a>Notes  
 La couleur du bouton automatique est définie par le `colorAutomatic` paramètre passé à la `CMFCRibbonColorButton::EnableAutomaticButton` (méthode).  
  
##  <a name="getcolor"></a>  CMFCRibbonColorButton::GetColor  
 Retourne la couleur actuellement sélectionnée.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La couleur sélectionnée en cliquant sur le bouton.  
  
##  <a name="getcolorboxsize"></a>  CMFCRibbonColorButton::GetColorBoxSize  
 Retourne la taille des éléments de couleur qui apparaissent dans la barre de couleurs.  
  
```  
CSize GetColorBoxSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La taille des boutons de couleur dans la palette de couleurs de la liste déroulante.  
  
##  <a name="getcolumns"></a>  CMFCRibbonColorButton::GetColumns  
 Obtient le nombre d’éléments dans une ligne de l’affichage de la galerie du bouton de couleur du ruban.  
  
```  
int GetColumns() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre d’icônes dans chaque ligne.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="gethighlightedcolor"></a>  CMFCRibbonColorButton::GetHighlightedColor  
 Retourne la couleur de l’élément actuellement sélectionné dans la palette de couleurs contextuelle.  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La couleur de l’élément actuellement sélectionné dans la palette de couleurs contextuelle.  
  
##  <a name="removeallcolorgroups"></a>  CMFCRibbonColorButton::RemoveAllColorGroups  
 Supprime tous les groupes de couleurs de la zone de couleur normale.  
  
```  
void RemoveAllColorGroups();
```  
  
##  <a name="setcolor"></a>  CMFCRibbonColorButton::SetColor  
 Sélectionne une couleur dans la zone de couleur normale.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `color`  
 Une couleur à définir.  
  
##  <a name="setcolorboxsize"></a>  CMFCRibbonColorButton::SetColorBoxSize  
 Définit la taille de tous les éléments de couleur qui apparaissent dans la barre de couleurs.  
  
```  
void SetColorBoxSize(CSize sizeBox);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `sizeBox`  
 La nouvelle taille des boutons de couleur dans la palette de couleurs.  
  
##  <a name="setcolorname"></a>  CMFCRibbonColorButton::SetColorName  
 Définit un nouveau nom d’une couleur spécifiée.  
  
```  
static void __stdcall SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `color`  
 La valeur RVB d’une couleur.  
  
 [in] `strName`  
 Le nouveau nom de la couleur spécifiée.  
  
### <a name="remarks"></a>Notes  
 Étant donné qu’il appelle `CMFCColorBar::SetColorName`, cette méthode modifie le nom de la couleur spécifiée dans toutes les `CMFCColorBar` objets dans votre application.  
  
##  <a name="setcolumns"></a>  CMFCRibbonColorButton::SetColumns  
 Définit le nombre de colonnes affichées dans le tableau de couleurs qui est présenté à l’utilisateur pendant le processus de sélection de couleur de l’utilisateur.  
  
```  
void SetColumns(int nColumns);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nColumns`  
 Le nombre d’icônes de couleur à afficher dans chaque ligne.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setdocumentcolors"></a>  CMFCRibbonColorButton::SetDocumentColors  
 Spécifie une liste de valeurs RVB à afficher dans la zone de couleur du document.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszLabel`  
 Le texte à afficher avec les couleurs du document.  
  
 [in] `lstColors`  
 Une référence à une liste de valeurs RVB.  
  
##  <a name="setpalette"></a>  CMFCRibbonColorButton::SetPalette  
 Spécifie les couleurs standards à afficher dans la table des couleurs affichant le bouton de couleur.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pPalette`  
 Pointeur vers une palette de couleurs.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="updatecolor"></a>  CMFCRibbonColorButton::UpdateColor  
 Appelé par le framework lorsque l’utilisateur sélectionne une couleur de la table de la couleur affichée lorsque l’utilisateur clique sur le bouton de couleur.  
  
```  
void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `color`  
 Une couleur sélectionnée par l’utilisateur.  
  
### <a name="remarks"></a>Notes  
 Le `CMFCRibbonColorButton::UpdateColor` méthode modifie les couleurs du bouton sélectionné et informe son parent en envoyant un `WM_COMMAND` des messages avec un `BN_CLICKED` standard de notification. Utilisez le [CMFCRibbonColorButton::GetColor](#getcolor) pour récupérer la couleur sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery, classe](../../mfc/reference/cmfcribbongallery-class.md)
