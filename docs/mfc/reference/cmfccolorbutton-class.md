---
description: 'En savoir plus sur : classe CMFCColorButton'
title: CMFCColorButton, classe
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
ms.openlocfilehash: b3f3e40f1e52c1a387563fde2aa1027046d557f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327692"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton, classe

Les `CMFCColorButton` classes de [classe et CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) sont utilisées ensemble pour implémenter un contrôle de sélecteur de couleurs.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Construit un nouvel objet `CMFCColorButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Active et désactive un bouton « automatique » positionné au-dessus des boutons de couleur standard. (Le bouton automatique système standard est intitulé **automatique**.)|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Active et désactive un bouton « autre » positionné sous les boutons de couleur standard. (Le bouton « autre » du système standard est intitulé **plus de couleurs**.)|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Récupère la couleur automatique actuelle.|
|[CMFCColorButton :: GetColor](#getcolor)|Récupère la couleur d’un bouton.|
|[CMFCColorButton :: SetColor](#setcolor)|Définit la couleur d’un bouton.|
|[CMFCColorButton::SetColorName](#setcolorname)|Définit un nom de couleur.|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Définit le nombre de colonnes dans la boîte de dialogue Sélecteur de couleurs.|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Spécifie la liste des couleurs spécifiques au document qui sont affichées dans la boîte de dialogue Sélecteur de couleurs.|
|[CMFCColorButton::SetPalette](#setpalette)|Spécifie une palette de couleurs d’affichage standard.|
|[CMFCColorButton :: SizeToContent](#sizetocontent)|Modifie la taille du contrôle bouton, en fonction de la taille du texte et de l’image.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Indique si le bouton de couleur actuel est affiché dans le style visuel de Windows XP.|
|[CMFCColorButton :: OnDraw](#ondraw)|Appelé par le Framework pour afficher une image du bouton.|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Appelé par le Framework pour afficher la bordure du bouton.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Appelé par l’infrastructure pour afficher un rectangle de focus lorsque le bouton a le focus.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Appelé par le Framework lorsque la boîte de dialogue Sélecteur de couleurs est sur le présent affichée.|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Initialise les `m_pPalette` données membres protégées à la palette spécifiée ou à la palette système par défaut.|
|[CMFCColorButton::UpdateColor](#updatecolor)|Appelé par le Framework lorsque l’utilisateur sélectionne une couleur dans la palette de la boîte de dialogue Sélecteur de couleurs.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|`m_bAltColorDlg`|Valeur booléenne. Si la valeur est TRUE, l’infrastructure affiche la boîte de dialogue couleur [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) lorsque l’utilisateur clique sur l' *autre* bouton, ou si la valeur est false, la boîte de dialogue couleur système. La valeur par défaut est TRUE. Pour plus d’informations, consultez [CMFCColorButton :: EnableOtherButton](#enableotherbutton).|
|`m_bAutoSetFocus`|Valeur booléenne. Si la valeur est TRUE, l’infrastructure définit le focus dans le menu couleur lorsque le menu est affiché, ou si la valeur est FALSe, ne change pas le focus. La valeur par défaut est TRUE.|
|[CMFCColorButton :: m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Indique si le mode de personnalisation est activé pour le bouton de couleur.|
|`m_Color`|Valeur [COLORREF](/windows/win32/gdi/colorref) . Contient la couleur actuellement sélectionnée.|
|`m_ColorAutomatic`|Valeur [COLORREF](/windows/win32/gdi/colorref) . Contient la couleur par défaut actuellement sélectionnée.|
|`m_Colors`|[CArray](../../mfc/reference/carray-class.md) de valeurs [COLORREF](/windows/win32/gdi/colorref) . Contient les couleurs actuellement disponibles.|
|`m_lstDocColors`|[CList](../../mfc/reference/clist-class.md) de valeurs [COLORREF](/windows/win32/gdi/colorref) . Contient les couleurs du document actif.|
|`m_nColumns`|Entier. Contient le nombre de colonnes à afficher dans la grille de couleurs dans un menu de sélection de couleurs.|
|`m_pPalette`|Pointeur vers un [cpalette](../../mfc/reference/cpalette-class.md). Contient les couleurs qui sont disponibles dans le menu de sélection de la couleur actuelle.|
|`m_pPopup`|Pointeur vers un objet de [classe CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md) . Menu de sélection de couleur qui s’affiche lorsque vous cliquez sur le bouton couleur.|
|`m_strAutoColorText`|Une chaîne. Étiquette du bouton « automatique » dans un menu de sélection de couleurs.|
|`m_strDocColorsText`|Une chaîne. Étiquette du bouton dans un menu de sélection de couleur qui affiche les couleurs du document.|
|`m_strOtherText`|Une chaîne. Étiquette du bouton « autre » dans un menu de sélection de couleurs.|

## <a name="remarks"></a>Notes

Par défaut, la `CMFCColorButton` classe se comporte comme un bouton de commande qui ouvre une boîte de dialogue de sélection de couleurs. La boîte de dialogue Sélecteur de couleurs contient un tableau de petits boutons de couleur et un bouton « autre » qui affiche un sélecteur de couleurs personnalisées. (Le bouton « autre » du système standard est intitulé **plus de couleurs**.) Lorsqu’un utilisateur sélectionne une nouvelle couleur, l' `CMFCColorButton` objet reflète la modification et affiche la couleur sélectionnée.

Créez un contrôle de bouton de couleur directement dans votre code, ou à l’aide de l’outil **ClassWizard** et d’un modèle de boîte de dialogue. Si vous créez un contrôle de bouton de couleur directement, ajoutez une `CMFCColorButton` variable à votre application, puis appelez le constructeur et les `Create` méthodes de l' `CMFCColorButton` objet. Si vous utilisez l' **Assistant ClassWizard**, ajoutez une `CButton` variable à votre application, puis remplacez le type de la variable par `CButton` `CMFCColorButton` .

La boîte de dialogue Sélecteur de couleurs ( [classe CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)) est affichée par la méthode [CMFCColorButton :: OnShowColorPopup](#onshowcolorpopup) lorsque le Framework appelle le `OnLButtonDown` Gestionnaire d’événements. La méthode [CMFCColorButton :: OnShowColorPopup](#onshowcolorpopup) peut être substituée pour prendre en charge la sélection de couleurs personnalisée.

L' `CMFCColorButton` objet informe son parent qu’une couleur est modifiée en l’envoyant un WM_COMMAND | Notification de BN_CLICKED. Le parent utilise la méthode [CMFCColorButton :: GetColor](#getcolor) pour récupérer la couleur actuelle.

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer un bouton de couleur à l’aide de différentes méthodes dans la `CMFCColorButton` classe. Les méthodes définissent la couleur du bouton de couleur et de son nombre de colonnes, et activent les boutons automatique et autres. Cet exemple fait partie de l' [exemple de démonstration](../../overview/visual-cpp-samples.md)de la barre d’État.

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête :** afxcolorbutton. h

## <a name="cmfccolorbuttoncmfccolorbutton"></a><a name="cmfccolorbutton"></a> CMFCColorButton::CMFCColorButton

Construit un nouvel objet `CMFCColorButton`.

```
CMFCColorButton();
```

## <a name="cmfccolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a> CMFCColorButton::EnableAutomaticButton

Active ou désactive le bouton « automatique » d’un contrôle de sélecteur de couleurs et définit la couleur automatique (par défaut).

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
dans Spécifie le texte du bouton automatique.

*colorAutomatic*<br/>
dans Valeur RVB qui spécifie la couleur par défaut du bouton automatique.

*bEnable*<br/>
dans Spécifie si le bouton automatique est activé ou désactivé.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a> CMFCColorButton::EnableOtherButton

Activez ou désactivez le bouton « autre », qui apparaît sous les boutons de couleur standard.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
dans Spécifie le texte du bouton.

*bAltColorDlg*<br/>
dans Spécifie si la boîte de dialogue [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ou la boîte de dialogue couleur système est ouverte lorsque l’utilisateur clique sur le bouton.

*bEnable*<br/>
dans Spécifie si le bouton « autre » est activé ou désactivé.

### <a name="remarks"></a>Notes

Cliquez sur le bouton « autre » pour afficher une boîte de dialogue de couleur. Si le paramètre *bAltColorDlg* a la valeur true, la [classe CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) est affichée ; dans le cas contraire, la boîte de dialogue couleur système s’affiche.

## <a name="cmfccolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a> CMFCColorButton::GetAutomaticColor

Récupère la couleur automatique (par défaut) actuelle.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur RVB représentant la couleur automatique actuelle.

### <a name="remarks"></a>Notes

La couleur automatique actuelle est définie par la méthode [CMFCColorButton :: EnableAutomaticButton](#enableautomaticbutton) .

## <a name="cmfccolorbuttongetcolor"></a><a name="getcolor"></a> CMFCColorButton :: GetColor

Récupère la couleur actuellement sélectionnée.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur RVB.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbuttonisdrawxptheme"></a><a name="isdrawxptheme"></a> CMFCColorButton::IsDrawXPTheme

Indique si le bouton de couleur actuel est affiché dans le style visuel de Windows XP.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si les styles visuels sont pris en charge et que le bouton de couleur actuel est affiché dans le style visuel de Windows XP ; Sinon, FALSe.

## <a name="cmfccolorbuttonm_benabledincustomizemode"></a><a name="m_benabledincustomizemode"></a> CMFCColorButton :: m_bEnabledInCustomizeMode

Définit un bouton de couleur en mode de personnalisation.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Notes

Si vous devez ajouter un bouton de couleur à la page de la boîte de dialogue de personnalisation (ou autoriser l’utilisateur à effectuer une autre sélection de couleur pendant la personnalisation), activez le bouton en affectant la `m_bEnabledInCustomizeMode` valeur true au membre. Par défaut, ce membre est défini sur FALSe.

## <a name="cmfccolorbuttonondraw"></a><a name="ondraw"></a> CMFCColorButton :: OnDraw

Appelé par l’infrastructure pour restituer une image du bouton.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointe vers le contexte de périphérique qui est utilisé pour restituer l’image du bouton.

*rectangulaire*<br/>
dans Rectangle qui délimite le bouton.

*uiState*<br/>
dans Spécifie l’état visuel du bouton.

### <a name="remarks"></a>Notes

Substituez cette méthode pour personnaliser le processus de rendu.

## <a name="cmfccolorbuttonondrawborder"></a><a name="ondrawborder"></a> CMFCColorButton::OnDrawBorder

Appelé par le Framework pour afficher la bordure du bouton.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointe vers le contexte de périphérique utilisé pour dessiner la bordure.

*rectClient*<br/>
dans Rectangle dans le contexte de périphérique spécifié par le paramètre *PDC* qui définit les limites du bouton à dessiner.

*uiState*<br/>
dans Spécifie l’état visuel du bouton.

### <a name="remarks"></a>Notes

Substituez cette fonction pour personnaliser l’apparence de la bordure du bouton de couleur.

## <a name="cmfccolorbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a> CMFCColorButton::OnDrawFocusRect

Appelé par le Framework pour afficher un rectangle de focus lorsque le bouton a le focus.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointe vers le contexte de périphérique utilisé pour dessiner le rectangle de focus.

*rectClient*<br/>
dans Rectangle dans le contexte de périphérique spécifié par le paramètre *PDC* qui définit les limites du bouton.

### <a name="remarks"></a>Notes

Substituez cette méthode pour personnaliser l’apparence du rectangle de focus.

## <a name="cmfccolorbuttononshowcolorpopup"></a><a name="onshowcolorpopup"></a> CMFCColorButton::OnShowColorPopup

Appelé avant l’affichage de la barre de couleurs contextuelle.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Notes

## <a name="cmfccolorbuttonrebuildpalette"></a><a name="rebuildpalette"></a> CMFCColorButton::RebuildPalette

Initialise les `m_pPalette` données membres protégées à la palette spécifiée ou à la palette système par défaut.

```cpp
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>Paramètres

*pPal*\
dans Pointeur vers une palette logique ou NULL. Si la valeur est NULL, la palette système par défaut est utilisée.

## <a name="cmfccolorbuttonsetcolor"></a><a name="setcolor"></a> CMFCColorButton :: SetColor

Spécifie la couleur du bouton.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
dans Valeur RVB.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbuttonsetcolorname"></a><a name="setcolorname"></a> CMFCColorButton::SetColorName

Spécifie le nom d’une couleur.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
dans Valeur RVB de la couleur.

*strName*<br/>
dans Nom de la couleur.

### <a name="remarks"></a>Notes

La liste des noms de couleurs est globale par application. Par conséquent, cette méthode transfère ses paramètres à [CMFCColorBar :: SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).

## <a name="cmfccolorbuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a> CMFCColorButton::SetColumnsNumber

Définit le nombre de colonnes affichées dans le tableau de couleurs présenté à l’utilisateur lors du processus de sélection des couleurs de l’utilisateur.

```cpp
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Paramètres

*nColumns*<br/>
dans Spécifie le nombre de colonnes.

### <a name="remarks"></a>Notes

L’utilisateur peut sélectionner une couleur dans une barre de couleur contextuelle qui affiche une table de couleurs prédéfinies. Utilisez cette méthode pour définir le nombre de colonnes dans la table.

## <a name="cmfccolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a> CMFCColorButton::SetDocumentColors

Spécifie un jeu de couleurs et le nom de l’ensemble. L’ensemble de couleurs s’affiche à l’aide d’un objet de [classe CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) .

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
dans Spécifie l’étiquette à afficher avec l’ensemble de couleurs du document.

*lstColors*<br/>
dans Référence à une liste de valeurs RVB.

### <a name="remarks"></a>Notes

Un `CMFCColorButton` objet gère une liste de valeurs RVB qui sont transférées à un objet de [classe CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) . Lorsque la barre de couleurs est affichée, ces couleurs sont affichées dans une section spéciale dont l’étiquette est spécifiée par le paramètre *lpszLabel* .

## <a name="cmfccolorbuttonsetpalette"></a><a name="setpalette"></a> CMFCColorButton::SetPalette

Spécifie les couleurs standard à afficher dans la barre de couleurs contextuelle.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Paramètres

*pPalette*<br/>
dans Pointeur vers une palette de couleurs.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbuttonsizetocontent"></a><a name="sizetocontent"></a> CMFCColorButton :: SizeToContent

Redimensionne le contrôle bouton en fonction de son texte et de son image.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Paramètres

*bCalcOnly*<br/>
dans Si la valeur est différente de zéro, la nouvelle taille du contrôle bouton est calculée, mais la taille réelle n’est pas modifiée.

### <a name="return-value"></a>Valeur renvoyée

`CSize`Objet qui spécifie une nouvelle taille de contrôle bouton.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbuttonupdatecolor"></a><a name="updatecolor"></a> CMFCColorButton::UpdateColor

Appelé par le Framework lorsque l’utilisateur sélectionne une couleur dans la barre de couleurs qui s’affiche lorsque l’utilisateur clique sur le bouton de couleur.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
dans Couleur sélectionnée par l’utilisateur.

### <a name="remarks"></a>Notes

La `UpdateColor` fonction modifie la couleur du bouton actuellement sélectionné et notifie son parent en envoyant un message d’WM_COMMAND avec une notification BN_CLICKED standard. Utilisez la méthode [CMFCColorButton :: GetColor](#getcolor) pour récupérer la couleur sélectionnée.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton, classe](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar, classe](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[CPalette, classe](../../mfc/reference/cpalette-class.md)<br/>
[CArray (classe)](../../mfc/reference/carray-class.md)<br/>
[CList (classe)](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
