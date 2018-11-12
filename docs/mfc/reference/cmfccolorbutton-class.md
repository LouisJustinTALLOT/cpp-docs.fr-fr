---
title: Cmfccolorbutton, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
ms.openlocfilehash: 97012e1d8cdc36f080245243c5f099b340225fc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533859"
---
# <a name="cmfccolorbutton-class"></a>Cmfccolorbutton, classe

Le `CMFCColorButton` et [cmfccolorbar, classe](../../mfc/reference/cmfccolorbar-class.md) classes sont utilisées ensemble pour implémenter un contrôle de sélecteur de couleurs.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Construit un nouvel `CMFCColorButton` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Active et désactive un bouton « automatique » est positionné au-dessus des boutons de couleur normale. (Le bouton automatique standard du système est intitulé **automatique**.)|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Active et désactive un bouton « autre » qui se trouve sous les boutons de couleur normale. (Le système standard « autre » bouton est intitulé **couleurs supplémentaires**.)|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Récupère la couleur automatique en cours.|
|[CMFCColorButton::GetColor](#getcolor)|Récupère la couleur d’un bouton.|
|[CMFCColorButton::SetColor](#setcolor)|Définit la couleur d’un bouton.|
|[CMFCColorButton::SetColorName](#setcolorname)|Définit un nom de couleur.|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Définit le nombre de colonnes dans la boîte de dialogue de sélecteur de couleurs.|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Spécifie une liste de couleurs de document spécifique qui sont affichés dans la boîte de dialogue de sélecteur de couleurs.|
|[CMFCColorButton::SetPalette](#setpalette)|Spécifie une palette de couleurs d’affichage standard.|
|[CMFCColorButton::SizeToContent](#sizetocontent)|Modifie la taille du contrôle button, en fonction de sa taille de texte et image.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Indique si le bouton de couleur actuel est affiché dans le style visuel de Windows XP.|
|[CMFCColorButton::OnDraw](#ondraw)|Appelé par l’infrastructure pour afficher une image du bouton.|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Appelé par l’infrastructure pour afficher la bordure du bouton.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Appelé par l’infrastructure pour afficher un rectangle de focus lorsque le bouton présente un intérêt particulier.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Appelé par le framework lorsque la boîte de dialogue de sélecteur de couleurs est sur le point d’être affiché.|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Initialise le `m_pPalette` protégé les données membres à la palette spécifiée ou de la palette du système par défaut.|
|[CMFCColorButton::UpdateColor](#updatecolor)|Appelé par le framework lorsque l’utilisateur sélectionne une couleur de la palette de la boîte de dialogue de sélecteur de couleurs.|

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|`m_bAltColorDlg`|Valeur booléenne. Si la valeur est TRUE, l’infrastructure affiche le [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) boîte de dialogue de couleur lorsque le *autres* bouton est activé, ou si la valeur est FALSE, le système de boîte de dialogue couleur. La valeur par défaut est TRUE. Pour plus d’informations, consultez [CMFCColorButton::EnableOtherButton](#enableotherbutton).|
|`m_bAutoSetFocus`|Valeur booléenne. Si la valeur est TRUE, le framework définit le focus sur le menu de couleur lorsque le menu s’affiche, ou si la valeur est FALSE, ne change pas le focus. La valeur par défaut est TRUE.|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Indique si le mode de personnalisation est activé pour le bouton de couleur.|
|`m_Color`|Un [COLORREF](/windows/desktop/gdi/colorref) valeur. Contient la couleur actuellement sélectionnée.|
|`m_ColorAutomatic`|Un [COLORREF](/windows/desktop/gdi/colorref) valeur. Contient la couleur actuellement sélectionnée par défaut.|
|`m_Colors`|Un [CArray](../../mfc/reference/carray-class.md) de [COLORREF](/windows/desktop/gdi/colorref) valeurs. Contient les couleurs disponibles.|
|`m_lstDocColors`|Un [CList](../../mfc/reference/clist-class.md) de [COLORREF](/windows/desktop/gdi/colorref) valeurs. Contient les couleurs de document en cours.|
|`m_nColumns`|Entier. Contient le nombre de colonnes à afficher dans la grille de couleurs dans un menu de sélection de couleur.|
|`m_pPalette`|Un pointeur vers un [CPalette](../../mfc/reference/cpalette-class.md). Contient les couleurs qui sont disponibles dans le menu de sélection de couleur actuelle.|
|`m_pPopup`|Un pointeur vers un [cmfccolorpopupmenu, classe](../../mfc/reference/cmfccolorpopupmenu-class.md) objet. Le menu de sélection de couleur qui s’affiche lorsque vous cliquez sur le bouton de couleur.|
|`m_strAutoColorText`|Chaîne. L’étiquette du bouton « automatique » dans un menu de sélection de couleur.|
|`m_strDocColorsText`|Chaîne. L’étiquette du bouton dans un menu de sélection de couleur qui affiche les couleurs de document.|
|`m_strOtherText`|Chaîne. L’étiquette du bouton « autre » dans un menu de sélection de couleur.|

## <a name="remarks"></a>Notes

Par défaut, le `CMFCColorButton` classe se comporte comme un bouton de commande qui ouvre une boîte de dialogue de sélecteur de couleurs. La boîte de dialogue de sélecteur de couleurs contient un tableau de boutons de petite couleur et un bouton « autre » qui affiche un sélecteur de couleurs personnalisées. (Le système standard « autre » bouton est intitulé **couleurs supplémentaires**.) Lorsqu’un utilisateur sélectionne une nouvelle couleur, le `CMFCColorButton` objet reflète la modification et affiche la couleur sélectionnée.

Créer un contrôle de bouton de couleur directement dans votre code, ou à l’aide de la **ClassWizard** outil et un modèle de boîte de dialogue. Si vous créez directement un contrôle de bouton de couleur, ajoutez un `CMFCColorButton` variable et votre application, puis appelez le constructeur et `Create` méthodes de la `CMFCColorButton` objet. Si vous utilisez le **ClassWizard**, ajoutez un `CButton` variable à votre application, puis modifiez le type de la variable de `CButton` à `CMFCColorButton`.

La boîte de dialogue de sélecteur de couleurs ( [cmfccolorbar, classe](../../mfc/reference/cmfccolorbar-class.md)) est affiché par le [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) méthode lorsque l’infrastructure appelle la `OnLButtonDown` Gestionnaire d’événements. Le [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) méthode peut être substituée pour prendre en charge la sélection de couleur personnalisée.

Le `CMFCColorButton` objet informe le parent que le passage d’une couleur en lui envoyant une WM_COMMAND | Notification de BN_CLICKED. Le parent utilise le [CMFCColorButton::GetColor](#getcolor) méthode pour récupérer la couleur actuelle.

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer un bouton de couleur à l’aide de différentes méthodes de la `CMFCColorButton` classe. Les méthodes de définir la couleur du bouton couleur et son nombre de colonnes et activer l’automatique et les autres boutons. Cet exemple fait partie de la [exemple de démonstration de barre d’état](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcolorbutton.h

##  <a name="cmfccolorbutton"></a>  CMFCColorButton::CMFCColorButton

Construit un nouvel `CMFCColorButton` objet.

```
CMFCColorButton();
```

##  <a name="enableautomaticbutton"></a>  CMFCColorButton::EnableAutomaticButton

Activer ou désactiver le bouton « automatique » d’un contrôle de sélecteur de couleurs et définir la couleur automatique (par défaut).

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[in] Spécifie le texte du bouton automatique.

*automatiqueCouleur*<br/>
[in] Une valeur RVB qui spécifie l’automatique couleur du bouton par défaut.

*bActivez*<br/>
[in] Spécifie si le bouton automatique est activé ou désactivé.

### <a name="remarks"></a>Notes

##  <a name="enableotherbutton"></a>  CMFCColorButton::EnableOtherButton

Activer ou désactiver le bouton « autre » qui apparaît sous les boutons de couleur normale.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[in] Spécifie le texte du bouton.

*bAltColorDlg*<br/>
[in] Spécifie si le [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) boîte de dialogue ou la boîte de dialogue de couleur système est ouvert lorsque l’utilisateur clique sur le bouton.

*bActivez*<br/>
[in] Spécifie si le bouton « autre » est activé ou désactivé.

### <a name="remarks"></a>Notes

Cliquez sur le bouton « autre » pour afficher une boîte de dialogue couleur. Si le *bAltColorDlg* paramètre est TRUE, le [cmfccolordialog, classe](../../mfc/reference/cmfccolordialog-class.md) est affichée ; sinon, la boîte de dialogue de couleur système est affichée.

##  <a name="getautomaticcolor"></a>  CMFCColorButton::GetAutomaticColor

Récupère la couleur automatique (par défaut) en cours.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur RVB représentant la couleur automatique en cours.

### <a name="remarks"></a>Notes

La couleur automatique actuelle est définie par le [CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton) (méthode).

##  <a name="getcolor"></a>  CMFCColorButton::GetColor

Récupère la couleur actuellement sélectionnée.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur RVB.

### <a name="remarks"></a>Notes

##  <a name="isdrawxptheme"></a>  CMFCColorButton::IsDrawXPTheme

Indique si le bouton de couleur actuel est affiché dans le style visuel de Windows XP.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si les styles visuels sont pris en charge et le bouton de couleur actuel est affiché dans le style visuel de Windows XP ; Sinon, FALSE.

##  <a name="m_benabledincustomizemode"></a>  CMFCColorButton::m_bEnabledInCustomizeMode

Définit un bouton de couleur pour le mode de personnalisation.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Notes

Si vous avez besoin ajouter un bouton de couleur à la page d’une boîte de dialogue Personnalisation (ou autorisez l’utilisateur à effectuer une autre sélection de couleur au cours de personnalisation), activer le bouton en définissant le `m_bEnabledInCustomizeMode` membre sur TRUE. Par défaut, ce membre est défini sur FALSE.

##  <a name="ondraw"></a>  CMFCColorButton::OnDraw

Appelé par l’infrastructure pour afficher une image du bouton.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointe vers le contexte de périphérique qui est utilisé pour restituer l’image du bouton.

*Rect*<br/>
[in] Un rectangle qui délimite le bouton.

*uiState*<br/>
[in] Spécifie l’état visuel du bouton.

### <a name="remarks"></a>Notes

Substituez cette méthode pour personnaliser le processus de rendu.

##  <a name="ondrawborder"></a>  CMFCColorButton::OnDrawBorder

Appelé par l’infrastructure pour afficher la bordure du bouton.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointe vers le contexte de périphérique utilisé pour dessiner la bordure.

*rectClient*<br/>
[in] Un rectangle dans le contexte de périphérique spécifié par le *pDC* paramètre qui définit les limites du bouton à dessiner.

*uiState*<br/>
[in] Spécifie l’état visuel du bouton.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour personnaliser l’apparence de bordure du bouton de couleur.

##  <a name="ondrawfocusrect"></a>  CMFCColorButton::OnDrawFocusRect

Appelé par l’infrastructure pour afficher un rectangle de focus quand le bouton a le focus.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointe vers le contexte de périphérique utilisé pour dessiner le rectangle de focus.

*rectClient*<br/>
[in] Un rectangle dans le contexte de périphérique spécifié par le *pDC* paramètre qui définit les limites du bouton.

### <a name="remarks"></a>Notes

Substituez cette méthode pour personnaliser l’apparence du rectangle de focus.

##  <a name="onshowcolorpopup"></a>  CMFCColorButton::OnShowColorPopup

Appelé avant que la barre de couleurs contextuelle s’affiche.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Notes

##  <a name="rebuildpalette"></a>  CMFCColorButton::RebuildPalette

Initialise le `m_pPalette` protégé les données membres à la palette spécifiée ou de la palette du système par défaut.

```
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pPal*|[in] Pointeur vers une palette logique, ou NULL. Si NULL, la palette du système par défaut est utilisée.|

##  <a name="setcolor"></a>  CMFCColorButton::SetColor

Spécifie la couleur du bouton.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
[in] Une valeur RVB.

### <a name="remarks"></a>Notes

##  <a name="setcolorname"></a>  CMFCColorButton::SetColorName

Spécifie le nom d’une couleur.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
[in] La valeur de couleur RVB.

*strName*<br/>
[in] Nom de la couleur.

### <a name="remarks"></a>Notes

La liste des noms de couleur est globale pour chaque application. Par conséquent, cette méthode transfère ses paramètres [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).

##  <a name="setcolumnsnumber"></a>  CMFCColorButton::SetColumnsNumber

Définit le nombre de colonnes qui sont affichées dans le tableau de couleurs est présenté à l’utilisateur pendant le processus de sélection de couleur de l’utilisateur.

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Paramètres

*nColumns*<br/>
[in] Spécifie le nombre de colonnes.

### <a name="remarks"></a>Notes

L’utilisateur peut sélectionner une couleur à partir d’une barre de couleurs contextuelle qui affiche un tableau de couleurs prédéfinies. Utilisez cette méthode pour définir le nombre de colonnes dans la table.

##  <a name="setdocumentcolors"></a>  CMFCColorButton::SetDocumentColors

Spécifie un jeu de couleurs et le nom du groupe. Le jeu de couleurs est affiché à l’aide un [cmfccolorbar, classe](../../mfc/reference/cmfccolorbar-class.md) objet.

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[in] Spécifie l’étiquette à afficher avec le jeu de couleurs de document.

*lstColors*<br/>
[in] Une référence à une liste de valeurs RVB.

### <a name="remarks"></a>Notes

Un `CMFCColorButton` objet conserve une liste de valeurs RVB qui sont transférés vers un [cmfccolorbar, classe](../../mfc/reference/cmfccolorbar-class.md) objet. Lorsque la barre de couleurs s’affiche, ces couleurs sont affichés dans une section spéciale dont le nom est spécifié par le *lpszLabel* paramètre.

##  <a name="setpalette"></a>  CMFCColorButton::SetPalette

Spécifie les couleurs standards à afficher sur la barre de couleurs contextuelle.

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Paramètres

*pPalette*<br/>
[in] Pointeur vers une palette de couleurs.

### <a name="remarks"></a>Notes

##  <a name="sizetocontent"></a>  CMFCColorButton::SizeToContent

Redimensionne le contrôle bouton pour s’ajuster à son texte et l’image.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Paramètres

*bCalcOnly*<br/>
[in] Si elle est différente de zéro, la nouvelle taille du contrôle button est calculée, mais la taille réelle n’est pas modifiée.

### <a name="return-value"></a>Valeur de retour

Un `CSize` objet qui spécifie une nouvelle taille de contrôle de bouton.

### <a name="remarks"></a>Notes

##  <a name="updatecolor"></a>  CMFCColorButton::UpdateColor

Appelé par le framework lorsque l’utilisateur sélectionne une couleur à partir de la barre de couleurs qui s’affiche lorsque l’utilisateur clique sur le bouton de couleur.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
[in] Une couleur sélectionnée par l’utilisateur.

### <a name="remarks"></a>Notes

Le `UpdateColor` fonction modifie la couleur du bouton actuellement sélectionné et informe son parent en envoyant un message WM_COMMAND avec une notification standard BN_CLICKED. Utilisez le [CMFCColorButton::GetColor](#getcolor) méthode pour récupérer la couleur sélectionnée.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton, classe](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar, classe](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/desktop/gdi/colorref)<br/>
[CPalette, classe](../../mfc/reference/cpalette-class.md)<br/>
[CArray, classe](../../mfc/reference/carray-class.md)<br/>
[CList, classe](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
