---
title: Classe CMFCColorButton
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
ms.openlocfilehash: 21d05fd8e805467f1a7a77d20c81d5ba0401455e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367733"
---
# <a name="cmfccolorbutton-class"></a>Classe CMFCColorButton

Les `CMFCColorButton` classes et [cmFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md) sont utilisées ensemble pour mettre en œuvre un contrôle de cueilleur de couleurs.

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
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Permet et désactive un bouton "automatique" qui est positionné au-dessus des boutons de couleur ordinaires. (Le bouton automatique système standard est étiqueté **automatique**.)|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Permet et désactive un bouton "autre" qui est placé en dessous des boutons de couleur ordinaires. (Le système standard "autre" bouton est étiqueté **Plus de couleurs**.)|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Récupère la couleur automatique actuelle.|
|[CMFCColorButton::GetColor](#getcolor)|Récupère la couleur d’un bouton.|
|[CMFCColorButton::SetColor](#setcolor)|Définit la couleur d’un bouton.|
|[CMFCColorButton::SetColorName](#setcolorname)|Définit un nom de couleur.|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Définit le nombre de colonnes sur la boîte de dialogue de cueilleur de couleurs.|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Spécifie une liste de couleurs spécifiques au document qui sont affichées sur la boîte de dialogue de cueilleur de couleurs.|
|[CMFCColorButton::SetPalette](#setpalette)|Spécifie une palette de couleurs d’affichage standard.|
|[CMFCColorButton::SizeToContent](#sizetocontent)|Modifie la taille du contrôle du bouton, en fonction de son texte et de la taille de son image.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Indique si le bouton de couleur actuel est affiché dans le style visuel de Windows XP.|
|[CMFCColorButton::OnDraw](#ondraw)|Appelé par le cadre pour afficher une image du bouton.|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Appelé par le cadre pour afficher la bordure du bouton.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Appelé par le cadre pour afficher un rectangle de mise au point lorsque le bouton a une mise au point.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Appelé par le cadre lorsque la boîte de dialogue cueilleur de couleur est sur le point d’être affiché.|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Initialise le `m_pPalette` membre des données protégées à la palette spécifiée ou à la palette de système par défaut.|
|[CMFCColorButton::UpdateColor](#updatecolor)|Appelé par le cadre lorsque l’utilisateur sélectionne une couleur de la palette de la boîte de dialogue cueilleur de couleurs.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|`m_bAltColorDlg`|Valeur booléenne. Si VRAI, le cadre affiche la boîte de dialogue couleur [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) lorsque *l’autre* bouton est cliqué, ou si FALSE, la boîte de dialogue couleur du système. La valeur par défaut est TRUE. Pour plus d’informations, voir [CMFCColorButton::EnableOtherButton](#enableotherbutton).|
|`m_bAutoSetFocus`|Valeur booléenne. Si VRAI, le cadre met l’accent sur le menu couleur lorsque le menu est affiché, ou si FALSE, ne change pas la mise au point. La valeur par défaut est TRUE.|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Indique si le mode de personnalisation est activé pour le bouton de couleur.|
|`m_Color`|Une valeur [COLORREF.](/windows/win32/gdi/colorref) Contient la couleur actuellement sélectionnée.|
|`m_ColorAutomatic`|Une valeur [COLORREF.](/windows/win32/gdi/colorref) Contient la couleur par défaut actuellement sélectionnée.|
|`m_Colors`|Un [CArray](../../mfc/reference/carray-class.md) des valeurs [COLORREF.](/windows/win32/gdi/colorref) Contient les couleurs actuellement disponibles.|
|`m_lstDocColors`|Une [liste](../../mfc/reference/clist-class.md) de valeurs [COLORREF.](/windows/win32/gdi/colorref) Contient les couleurs actuelles du document.|
|`m_nColumns`|Entier. Contient le nombre de colonnes à afficher dans la grille de couleurs dans un menu de sélection de couleurs.|
|`m_pPalette`|Un pointeur à un [CPalette](../../mfc/reference/cpalette-class.md). Contient les couleurs qui sont disponibles dans le menu actuel de sélection des couleurs.|
|`m_pPopup`|Un pointeur vers un objet [cmFCColorPopupMenu Class.](../../mfc/reference/cmfccolorpopupmenu-class.md) Le menu de sélection des couleurs qui s’affiche lorsque vous cliquez sur le bouton couleur.|
|`m_strAutoColorText`|Une chaîne. L’étiquette du bouton "automatique" dans un menu de sélection de couleurs.|
|`m_strDocColorsText`|Une chaîne. L’étiquette du bouton dans un menu de sélection de couleurs qui affiche les couleurs du document.|
|`m_strOtherText`|Une chaîne. L’étiquette du bouton "autre" dans un menu de sélection de couleurs.|

## <a name="remarks"></a>Notes

Par défaut, `CMFCColorButton` la classe se comporte comme un bouton poussoir qui ouvre une boîte de dialogue de cueilleur de couleurs. La boîte de dialogue de cueilleur de couleurs contient une gamme de petits boutons de couleur et un bouton « autre » qui affiche un cueilleur de couleur personnalisé. (Le système standard "autre" bouton est étiqueté **Plus de couleurs**.) Lorsqu’un utilisateur sélectionne une `CMFCColorButton` nouvelle couleur, l’objet reflète le changement et affiche la couleur sélectionnée.

Créez un contrôle de bouton de couleur directement dans votre code, soit en utilisant l’outil **ClassWizard** et un modèle de boîte de dialogue. Si vous créez un contrôle de `CMFCColorButton` bouton de couleur directement, ajoutez `Create` une variable `CMFCColorButton` à votre application, puis appelez le constructeur et les méthodes de l’objet. Si vous utilisez le **ClassWizard**, ajoutez une `CButton` variable à votre `CButton` application, puis modifiez le type de la variable à `CMFCColorButton`partir de .

La boîte de dialogue de cueilleur de couleurs ( [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)) est affichée par la `OnLButtonDown` méthode [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) méthode lorsque le cadre appelle le gestionnaire d’événements. La méthode [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) méthode peut être remplacé pour soutenir la sélection de couleurs personnalisées.

L’objet `CMFCColorButton` informe son parent qu’une couleur change en lui envoyant un WM_COMMAND BN_CLICKED notification. Le parent utilise la méthode [CMFCColorButton::GetColor](#getcolor) pour récupérer la couleur actuelle.

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer un bouton `CMFCColorButton` de couleur en utilisant différentes méthodes dans la classe. Les méthodes fixent la couleur du bouton de couleur et son nombre de colonnes, et activent l’automatique et les autres boutons. Cet exemple fait partie de [l’échantillon de démonstration de barre d’état](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête:** afxcolorbutton.h

## <a name="cmfccolorbuttoncmfccolorbutton"></a><a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton

Construit un nouvel objet `CMFCColorButton`.

```
CMFCColorButton();
```

## <a name="cmfccolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorButton::EnableAutomaticButton

Activez ou désactivez le bouton "automatique" d’un contrôle de cueilleur de couleurs et définissez la couleur automatique (par défaut).

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[dans] Spécifie le texte du bouton automatique.

*couleurAutomatique*<br/>
[dans] Une valeur RGB qui spécifie la couleur par défaut du bouton automatique.

*bEnable*<br/>
[dans] Précise si le bouton automatique est activé ou désactivé.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton

Activez ou désactivez le bouton « autre », qui apparaît sous les boutons de couleur ordinaires.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[dans] Spécifie le texte du bouton.

*bAltColorDlg*<br/>
[dans] Précise si la boîte de dialogue [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ou la boîte de dialogue couleur du système est ouverte lorsque l’utilisateur clique sur le bouton.

*bEnable*<br/>
[dans] Précise si le bouton "autre" est activé ou désactivé.

### <a name="remarks"></a>Notes

Cliquez sur le bouton "autre" pour afficher une boîte de dialogue couleur. Si le paramètre *bAltColorDlg* est VRAI, la [classe CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) est affichée; autrement, la boîte de dialogue couleur système est affichée.

## <a name="cmfccolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor

Récupère la couleur automatique (par défaut) actuelle.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur RGB représentant la couleur automatique actuelle.

### <a name="remarks"></a>Notes

La couleur automatique actuelle est définie par la méthode [CMFCColorButton::EnableAutomaticButton.](#enableautomaticbutton)

## <a name="cmfccolorbuttongetcolor"></a><a name="getcolor"></a>CMFCColorButton::GetColor

Récupère la couleur actuellement sélectionnée.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur RGB.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbuttonisdrawxptheme"></a><a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme

Indique si le bouton de couleur actuel est affiché dans le style visuel de Windows XP.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si les styles visuels sont pris en charge et le bouton de couleur actuel est affiché dans le style visuel de Windows XP; autrement, FALSE.

## <a name="cmfccolorbuttonm_benabledincustomizemode"></a><a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode

Définit un bouton de couleur en mode personnalisation.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Notes

Si vous avez besoin d’ajouter un bouton de couleur à la page d’un dialogue de personnalisation `m_bEnabledInCustomizeMode` (ou permettre à l’utilisateur de faire une autre sélection de couleurs lors de la personnalisation), activez le bouton en définissant le membre à TRUE. Par défaut, ce membre est configuré à FALSE.

## <a name="cmfccolorbuttonondraw"></a><a name="ondraw"></a>CMFCColorButton::OnDraw

Appelé par le cadre pour rendre une image du bouton.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Indique le contexte de l’appareil qui est utilisé pour rendre l’image du bouton.

*Rect*<br/>
[dans] Un rectangle qui limite le bouton.

*uiState (uiState)*<br/>
[dans] Spécifie l’état visuel du bouton.

### <a name="remarks"></a>Notes

Remplacer cette méthode pour personnaliser le processus de rendu.

## <a name="cmfccolorbuttonondrawborder"></a><a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder

Appelé par le cadre pour afficher la bordure du bouton.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Points au contexte de l’appareil utilisé pour dessiner la frontière.

*rectClient*<br/>
[dans] Un rectangle dans le contexte de l’appareil qui est spécifié par le paramètre *pDC* qui définit les limites du bouton à dessiner.

*uiState (uiState)*<br/>
[dans] Spécifie l’état visuel du bouton.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour personnaliser l’apparence de la bordure du bouton de couleur.

## <a name="cmfccolorbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCColorButton::OnDrawFocusRect

Appelé par le cadre pour afficher un rectangle de mise au point lorsque le bouton est focalisant.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Points au contexte de l’appareil utilisé pour dessiner le rectangle de mise au point.

*rectClient*<br/>
[dans] Un rectangle dans le contexte de l’appareil spécifié par le paramètre *pDC* qui définit les limites du bouton.

### <a name="remarks"></a>Notes

Remplacer cette méthode pour personnaliser l’apparence du rectangle de mise au point.

## <a name="cmfccolorbuttononshowcolorpopup"></a><a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup

Appelé avant la barre de couleur popup est affiché.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Notes

## <a name="cmfccolorbuttonrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColorButton::RebuildPalette

Initialise le `m_pPalette` membre des données protégées à la palette spécifiée ou à la palette de système par défaut.

```
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*pPal (en)*|[dans] Un pointeur vers une palette logique ou NULL. Si NULL, la palette de système par défaut est utilisée.|

## <a name="cmfccolorbuttonsetcolor"></a><a name="setcolor"></a>CMFCColorButton::SetColor

Spécifie la couleur du bouton.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
[dans] Une valeur RGB.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFCColorButton::SetColorName

Spécifie le nom d’une couleur.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
[dans] La valeur RGB de la couleur.

*strName*<br/>
[dans] Le nom de la couleur.

### <a name="remarks"></a>Notes

La liste des noms de couleurs est globale par application. Par conséquent, cette méthode transfère ses paramètres à [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).

## <a name="cmfccolorbuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber

Définit le nombre de colonnes qui sont affichées dans le tableau des couleurs qui est présenté à l’utilisateur pendant le processus de sélection des couleurs de l’utilisateur.

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Paramètres

*nColumns*<br/>
[dans] Spécifie le nombre de colonnes.

### <a name="remarks"></a>Notes

L’utilisateur peut sélectionner une couleur à partir d’une barre de couleur popup qui affiche une table de couleurs prédéfinies. Utilisez cette méthode pour définir le nombre de colonnes dans le tableau.

## <a name="cmfccolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors

Spécifie un ensemble de couleurs et le nom de l’ensemble. L’ensemble de couleurs est affiché à l’aide d’un objet [cmFCColorBar Class.](../../mfc/reference/cmfccolorbar-class.md)

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[dans] Spécifie l’étiquette à afficher avec l’ensemble des couleurs du document.

*lstColors*<br/>
[dans] Une référence à une liste de valeurs RGB.

### <a name="remarks"></a>Notes

Un `CMFCColorButton` objet conserve une liste de valeurs RGB qui sont transférées à un objet [de classe CMFCColorBar.](../../mfc/reference/cmfccolorbar-class.md) Lorsque la barre de couleur est affichée, ces couleurs sont affichées dans une section spéciale dont l’étiquette est spécifiée par le paramètre *lpszLabel.*

## <a name="cmfccolorbuttonsetpalette"></a><a name="setpalette"></a>CMFCColorButton::SetPalette

Spécifie les couleurs standard à afficher sur la barre de couleur popup.

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Paramètres

*pPalette (pPalette)*<br/>
[dans] Un pointeur à une palette de couleurs.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCColorButton::SizeToContent

Resizes le contrôle du bouton pour s’adapter à son texte et son image.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Paramètres

*bCalcOnly*<br/>
[dans] Si non zéro, la nouvelle taille du contrôle du bouton est calculée, mais la taille réelle n’est pas modifiée.

### <a name="return-value"></a>Valeur de retour

Un `CSize` objet qui spécifie une nouvelle taille de commande de bouton.

### <a name="remarks"></a>Notes

## <a name="cmfccolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFCColorButton::Mise à jourColor

Appelé par le cadre lorsque l’utilisateur sélectionne une couleur de la barre de couleur qui s’affiche lorsque l’utilisateur clique sur le bouton de couleur.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
[dans] Une couleur sélectionnée par l’utilisateur.

### <a name="remarks"></a>Notes

La `UpdateColor` fonction modifie la couleur du bouton actuellement sélectionné et informe son parent en envoyant un message WM_COMMAND avec une notification standard BN_CLICKED. Utilisez la méthode [CMFCColorButton::GetColor](#getcolor) pour récupérer la couleur sélectionnée.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCButton](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar, classe](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[Classe CPalette](../../mfc/reference/cpalette-class.md)<br/>
[Classe CArray](../../mfc/reference/carray-class.md)<br/>
[CList, classe](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
