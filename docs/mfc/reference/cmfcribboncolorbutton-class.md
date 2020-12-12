---
description: 'En savoir plus sur : classe CMFCRibbonColorButton'
title: CMFCRibbonColorButton (classe)
ms.date: 11/04/2016
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
ms.openlocfilehash: a350339559febdc9346dcf8b342d274d00bab391
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293714"
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
|[CMFCRibbonColorButton :: AddColorsGroup](#addcolorsgroup)|Ajoute un groupe de couleurs dans la zone de couleur normale.|
|[CMFCRibbonColorButton :: EnableAutomaticButton](#enableautomaticbutton)|Spécifie si le bouton **Automatique** est activé.|
|[CMFCRibbonColorButton :: EnableOtherButton](#enableotherbutton)|Active le bouton **Autres** .|
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||
|[CMFCRibbonColorButton :: GetColor](#getcolor)|Retourne la couleur actuellement sélectionnée.|
|[CMFCRibbonColorButton :: GetColorBoxSize](#getcolorboxsize)|Retourne la taille des éléments de couleur qui apparaissent dans la barre de couleurs.|
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||
|[CMFCRibbonColorButton :: GetHighlightedColor](#gethighlightedcolor)|Retourne la couleur de l’élément actuellement sélectionné dans la palette de couleurs contextuelle.|
|[CMFCRibbonColorButton :: RemoveAllColorGroups](#removeallcolorgroups)|Supprime tous les groupes de couleurs de la zone de couleur normale.|
|[CMFCRibbonColorButton :: SetColor](#setcolor)|Sélectionne une couleur dans la zone de couleur normale.|
|[CMFCRibbonColorButton :: SetColorBoxSize](#setcolorboxsize)|Définit la taille de tous les éléments de couleur qui apparaissent dans la barre de couleurs.|
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||
|[CMFCRibbonColorButton :: SetDocumentColors](#setdocumentcolors)|Spécifie une liste de valeurs RVB à afficher dans la zone de couleur du document.|
|[CMFCRibbonColorButton::SetPalette](#setpalette)||
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||

## <a name="remarks"></a>Notes

Le bouton de couleur du ruban affiche une barre de couleurs quand un utilisateur clique dessus. Par défaut, cette barre de couleurs contient une palette de sélection de couleurs appelée zone de couleur normale. Si vous le souhaitez, la barre de couleurs peut afficher un bouton **Automatique** , qui permet à l’utilisateur de sélectionner une couleur par défaut, et un bouton **Autres** qui affiche une palette de couleurs contextuelle qui contient des couleurs supplémentaires.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCRibbonColorButton` . L’exemple montre comment construire un objet `CMFCRibbonColorButton` , définir l’image de grande taille, activez le bouton **Automatique** , activer le bouton **Autres** , définir le nombre de colonnes, définir la taille de tous les éléments de couleur qui apparaissent sur la barre de couleurs, ajouter un groupe de couleurs à la zone de couleur normale et spécifier une liste de valeurs RVB à afficher dans la zone de couleur du document. Cet extrait de code fait partie de l’ [exemple Draw Client](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxribboncolorbutton.h

## <a name="cmfcribboncolorbuttonaddcolorsgroup"></a><a name="addcolorsgroup"></a> CMFCRibbonColorButton :: AddColorsGroup

Ajoute un groupe de couleurs dans la zone de couleur normale.

```cpp
void AddColorsGroup(
    LPCTSTR lpszName,
    const CList<COLORREF,COLORREF>& lstColors,
    BOOL bContiguousColumns=FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
dans Nom du groupe.

*lstColors*<br/>
dans Liste de couleurs.

*bContiguousColumns*<br/>
dans Contrôle la façon dont les éléments de couleur sont affichés dans le groupe. Si la valeur est TRUE, les éléments de couleur sont dessinés sans espacement vertical. Si la valeur est FALSe, les éléments de couleur sont dessinés avec un espacement vertical.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour que la fenêtre contextuelle de couleur affiche plusieurs groupes de couleurs. Vous pouvez contrôler l’affichage des couleurs dans le groupe.

## <a name="cmfcribboncolorbuttoncmfcribboncolorbutton"></a><a name="cmfcribboncolorbutton"></a> CMFCRibbonColorButton :: CMFCRibbonColorButton

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

*nID*<br/>
dans Spécifie l’ID de commande de la commande à exécuter lorsqu’un utilisateur clique sur le bouton.

*lpszText*<br/>
dans Spécifie le texte à afficher sur le bouton.

*nSmallImageIndex*<br/>
dans Index de base zéro de la petite image à afficher sur le bouton.

*color*<br/>
dans Couleur du bouton (noir par défaut).

*bSimpleButtonLook*<br/>
dans Si la valeur est TRUE, le bouton est dessiné comme un rectangle simple.

*nLargeImageIndex*<br/>
dans Index de base zéro de la grande image à afficher sur le bouton.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribboncolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a> CMFCRibbonColorButton :: EnableAutomaticButton

Spécifie si le bouton **Automatique** est activé.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE,
    LPCTSTR lpszToolTip=NULL,
    BOOL bOnTop=TRUE,
    BOOL bDrawBorder=FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
dans Étiquette du bouton **automatique** .

*colorAutomatic*<br/>
dans Valeur RVB qui spécifie la couleur par défaut du bouton **automatique** .

*bEnable*<br/>
dans TRUE si le bouton **automatique** est activé ; FALSe si elle est désactivée.

*lpszToolTip*<br/>
dans Info-bulle du bouton **automatique** .

*bOnTop*<br/>
dans Spécifie si le bouton **automatique** est en haut, avant la palette de couleurs.

*bDrawBorder*<br/>
dans TRUE si l’application dessine une bordure autour de la barre de couleurs sur le bouton de couleur du ruban. Barre de couleurs affiche la couleur actuellement sélectionnée. FALSe si l’application ne dessine pas de bordure

## <a name="cmfcribboncolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a> CMFCRibbonColorButton :: EnableOtherButton

Active le bouton **Autres** .

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    LPCTSTR lpszToolTip=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
Étiquette du bouton.

*lpszToolTip*<br/>
Texte d’info-bulle pour l' **autre** bouton.

### <a name="remarks"></a>Notes

Le bouton **autre** est le bouton qui s’affiche sous le groupe de couleurs. Quand l’utilisateur clique sur l' **autre** bouton, il affiche une boîte de dialogue de couleur.

## <a name="cmfcribboncolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a> CMFCRibbonColorButton :: GetAutomaticColor

Récupère la couleur actuelle du bouton automatique.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur de couleur RVB qui représente la couleur de bouton automatique actuelle.

### <a name="remarks"></a>Notes

La couleur de bouton automatique est définie par le `colorAutomatic` paramètre passé à la `CMFCRibbonColorButton::EnableAutomaticButton` méthode.

## <a name="cmfcribboncolorbuttongetcolor"></a><a name="getcolor"></a> CMFCRibbonColorButton :: GetColor

Retourne la couleur actuellement sélectionnée.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Couleur sélectionnée en cliquant sur le bouton.

## <a name="cmfcribboncolorbuttongetcolorboxsize"></a><a name="getcolorboxsize"></a> CMFCRibbonColorButton :: GetColorBoxSize

Retourne la taille des éléments de couleur qui apparaissent dans la barre de couleurs.

```
CSize GetColorBoxSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Taille des boutons de couleur dans la palette de couleurs déroulante.

## <a name="cmfcribboncolorbuttongetcolumns"></a><a name="getcolumns"></a> CMFCRibbonColorButton :: GetColumns

Obtient le nombre d’éléments d’une ligne dans l’affichage de la Galerie du bouton de couleur du ruban.

```
int GetColumns() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’icônes dans chaque ligne.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncolorbuttongethighlightedcolor"></a><a name="gethighlightedcolor"></a> CMFCRibbonColorButton :: GetHighlightedColor

Retourne la couleur de l’élément actuellement sélectionné dans la palette de couleurs contextuelle.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Couleur de l’élément actuellement sélectionné dans la palette de couleurs contextuelle.

## <a name="cmfcribboncolorbuttonremoveallcolorgroups"></a><a name="removeallcolorgroups"></a> CMFCRibbonColorButton :: RemoveAllColorGroups

Supprime tous les groupes de couleurs de la zone de couleur normale.

```cpp
void RemoveAllColorGroups();
```

## <a name="cmfcribboncolorbuttonsetcolor"></a><a name="setcolor"></a> CMFCRibbonColorButton :: SetColor

Sélectionne une couleur dans la zone de couleur normale.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
dans Couleur à définir.

## <a name="cmfcribboncolorbuttonsetcolorboxsize"></a><a name="setcolorboxsize"></a> CMFCRibbonColorButton :: SetColorBoxSize

Définit la taille de tous les éléments de couleur qui apparaissent dans la barre de couleurs.

```cpp
void SetColorBoxSize(CSize sizeBox);
```

### <a name="parameters"></a>Paramètres

*sizeBox*<br/>
dans Nouvelle taille des boutons de couleur de la palette de couleurs.

## <a name="cmfcribboncolorbuttonsetcolorname"></a><a name="setcolorname"></a> CMFCRibbonColorButton :: SetColorName

Définit un nouveau nom pour une couleur spécifiée.

```
static void __stdcall SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
dans Valeur RVB d’une couleur.

*strName*<br/>
dans Nouveau nom pour la couleur spécifiée.

### <a name="remarks"></a>Notes

Comme il appelle `CMFCColorBar::SetColorName` , cette méthode modifie le nom de la couleur spécifiée dans tous les `CMFCColorBar` objets de votre application.

## <a name="cmfcribboncolorbuttonsetcolumns"></a><a name="setcolumns"></a> CMFCRibbonColorButton :: SetColumns

Définit le nombre de colonnes affichées dans le tableau de couleurs présenté à l’utilisateur lors du processus de sélection des couleurs de l’utilisateur.

```cpp
void SetColumns(int nColumns);
```

### <a name="parameters"></a>Paramètres

*nColumns*<br/>
dans Nombre d’icônes de couleur à afficher dans chaque ligne.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a> CMFCRibbonColorButton :: SetDocumentColors

Spécifie une liste de valeurs RVB à afficher dans la zone de couleur du document.

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
dans Texte à afficher avec les couleurs du document.

*lstColors*<br/>
dans Référence à une liste de valeurs RVB.

## <a name="cmfcribboncolorbuttonsetpalette"></a><a name="setpalette"></a> CMFCRibbonColorButton :: SetPalette

Spécifie les couleurs standard à afficher dans la table des couleurs affichée par le bouton couleur.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Paramètres

*pPalette*<br/>
dans Pointeur vers une palette de couleurs.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncolorbuttonupdatecolor"></a><a name="updatecolor"></a> CMFCRibbonColorButton :: UpdateColor

Appelé par le Framework lorsque l’utilisateur sélectionne une couleur dans la table de couleurs affichée lorsque l’utilisateur clique sur le bouton de couleur.

```cpp
void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
dans Couleur sélectionnée par l’utilisateur.

### <a name="remarks"></a>Notes

La `CMFCRibbonColorButton::UpdateColor` méthode modifie la couleur du bouton actuellement sélectionné et notifie son parent en envoyant un message d’WM_COMMAND avec une notification BN_CLICKED standard. Utilisez la méthode [CMFCRibbonColorButton :: GetColor](#getcolor) pour récupérer la couleur sélectionnée.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Cmfcribbongallery,, classe](../../mfc/reference/cmfcribbongallery-class.md)
