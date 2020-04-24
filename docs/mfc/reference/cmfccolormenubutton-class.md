---
title: Classe CMFCColorMenuButton
ms.date: 11/04/2016
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
helpviewer_keywords:
- CMFCColorMenuButton [MFC], CMFCColorMenuButton
- CMFCColorMenuButton [MFC], EnableAutomaticButton
- CMFCColorMenuButton [MFC], EnableDocumentColors
- CMFCColorMenuButton [MFC], EnableOtherButton
- CMFCColorMenuButton [MFC], EnableTearOff
- CMFCColorMenuButton [MFC], GetAutomaticColor
- CMFCColorMenuButton [MFC], GetColor
- CMFCColorMenuButton [MFC], GetColorByCmdID
- CMFCColorMenuButton [MFC], OnChangeParentWnd
- CMFCColorMenuButton [MFC], OpenColorDialog
- CMFCColorMenuButton [MFC], SetColor
- CMFCColorMenuButton [MFC], SetColorByCmdID
- CMFCColorMenuButton [MFC], SetColorName
- CMFCColorMenuButton [MFC], SetColumnsNumber
- CMFCColorMenuButton [MFC], CopyFrom
- CMFCColorMenuButton [MFC], CreatePopupMenu
- CMFCColorMenuButton [MFC], IsEmptyMenuAllowed
- CMFCColorMenuButton [MFC], OnDraw
- CMFCColorMenuButton [MFC], OnDrawOnCustomizeList
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
ms.openlocfilehash: 9c895573c626a890facfef689fce4b516aff5115
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752517"
---
# <a name="cmfccolormenubutton-class"></a>Classe CMFCColorMenuButton

La `CMFCColorMenuButton` classe prend en charge une commande de menu ou un bouton de barre d’outils qui démarre une boîte de dialogue de cueilleur de couleur.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|Construit un objet `CMFCColorMenuButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Permet et désactive un bouton "automatique" qui est positionné au-dessus des boutons de couleur ordinaires. (Le bouton automatique système standard est étiqueté **automatique**.)|
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Permet l’affichage de couleurs spécifiques au document au lieu des couleurs du système.|
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Permet et désactive un bouton "autre" qui est placé en dessous des boutons de couleur ordinaires. (Le système standard "autre" bouton est étiqueté **Plus de couleurs**.)|
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Permet d’arracher une vitre de couleur.|
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Récupère la couleur automatique actuelle.|
|[CMFCColorMenuButton::GetColor](#getcolor)|Récupère la couleur du bouton actuel.|
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Récupère la couleur qui correspond à une pièce d’identité de commande spécifiée.|
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Appelé par le cadre lorsque la fenêtre parente change.|
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Ouvre une boîte de dialogue de sélection de couleurs.|
|[CMFCColorMenuButton::SetColor](#setcolor)|Définit la couleur du bouton de couleur actuel.|
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Définit la couleur du bouton de menu couleur spécifié.|
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Définit un nouveau nom pour la couleur spécifiée.|
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Définit le nombre de colonnes `CMFCColorBar` qui sont affichées par un objet.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCColorMenuButton::CopyDe](#copyfrom)|Copie un autre bouton de barre d’outils sur le bouton actuel.|
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|Crée une boîte de dialogue de cueilleur de couleurs.|
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Indique si les menus vides sont pris en charge.|
|[CMFCColorMenuButton::OnDraw](#ondraw)|Appelé par le cadre pour afficher une image sur un bouton.|
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Appelé par le `CMFCColorMenuButton` cadre avant qu’un objet ne soit affiché dans la liste d’une boîte de dialogue de personnalisation de la barre d’outils.|

## <a name="remarks"></a>Notes

Pour remplacer la commande de menu `CMFCColorMenuButton` d’origine `CMFCColorMenuButton` ou le bouton de barre d’outils par `ReplaceButton` un objet, créez l’objet, définissez tous les styles de [classe CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) appropriés, puis appelez la méthode de la classe [CMFCToolBar.](../../mfc/reference/cmfctoolbar-class.md) Si vous personnalisez une barre d’outils, appelez la méthode [CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) méthode.

La boîte de dialogue de cueilleur de couleurs est créée pendant le traitement du [CMFCColorMenuButton ::CreatePopupMenu](#createpopupmenu) gestionnaire d’événement. Le gestionnaire de l’événement informe le cadre parent avec un message WM_COMMAND. L’objet `CMFCColorMenuButton` envoie l’ID de contrôle qui est affecté à la commande de menu d’origine ou bouton de barre d’outils.

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer et configurer un bouton `CMFCColorMenuButton` de menu couleur en utilisant différentes méthodes dans la classe. Dans l’exemple, un `CPalette` objet est d’abord créé `CMFCColorMenuButton` puis utilisé pour construire un objet de la classe. L’objet `CMFCColorMenuButton` est ensuite configuré en permettant ses boutons automatiques et autres, et en définissant sa couleur et le nombre de colonnes. Ce code fait partie de [l’échantillon Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxcolormenubutton.h

## <a name="cmfccolormenubuttoncmfccolormenubutton"></a><a name="cmfccolormenubutton"></a>CMFCColorMenuButton::CMFCColorMenuButton

Construit un objet `CMFCColorMenuButton`.

```
CMFCColorMenuButton();

CMFCColorMenuButton(
    UINT uiCmdID,
    LPCTSTR lpszText,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>Paramètres

*uiCmdID*<br/>
[dans] Une carte d’identité de commande de bouton.

*lpszText*<br/>
[dans] Le texte du bouton.

*pPalette (pPalette)*<br/>
[dans] Un pointeur sur la palette de couleurs du bouton.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Le premier constructeur est le constructeur par défaut. La couleur actuelle de l’objet et la couleur automatique sont parasésées au noir (RGB(0, 0, 0)).

Le deuxième constructeur initialise le bouton à la couleur qui correspond à l’ID de commande spécifié.

## <a name="cmfccolormenubuttoncopyfrom"></a><a name="copyfrom"></a>CMFCColorMenuButton::CopyDe

Copies d’un objet [de classe CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)à un autre.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[dans] Bouton source à copier.

### <a name="remarks"></a>Notes

Remplacer cette méthode pour copier les `CMFCColorMenuButton` objets dérivés de l’objet.

## <a name="cmfccolormenubuttoncreatepopupmenu"></a><a name="createpopupmenu"></a>CMFCColorMenuButton::CreatePopupMenu

Crée une boîte de dialogue de cueilleur de couleurs.

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>Valeur de retour

Un objet qui représente une boîte de dialogue de cueilleur de couleur.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre lorsque l’utilisateur appuie sur un bouton de menu couleur.

## <a name="cmfccolormenubuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorMenuButton::EnableAutomaticButton

Permet et désactive un bouton "automatique" qui est positionné au-dessus des boutons de couleur ordinaires. (Le bouton automatique système standard est étiqueté **automatique**.)

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[dans] Spécifie le texte du bouton qui s’affiche lorsque le bouton devient automatique.

*couleurAutomatique*<br/>
[dans] Specifie une nouvelle couleur automatique.

*bEnable*<br/>
[dans] Précise si le bouton est automatique ou non.

### <a name="remarks"></a>Notes

Le bouton automatique applique la couleur par défaut actuelle.

## <a name="cmfccolormenubuttonenabledocumentcolors"></a><a name="enabledocumentcolors"></a>CMFCColorMenuButton::EnableDocumentColors

Permet l’affichage de couleurs spécifiques au document au lieu des couleurs du système.

```cpp
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[dans] Spécifie le texte du bouton.

*bEnable*<br/>
[dans] VRAI pour afficher des couleurs spécifiques aux documents ou FALSE pour afficher les couleurs du système.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour afficher les couleurs actuelles du document ou les couleurs de palette du système lorsque l’utilisateur clique sur un bouton de menu couleur.

## <a name="cmfccolormenubuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorMenuButton::EnableOtherButton

Permet et désactive un bouton "autre" qui est placé en dessous des boutons de couleur ordinaires. (Le système standard "autre" bouton est étiqueté **Plus de couleurs**.)

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[dans] Spécifie le texte du bouton.

*bAltColorDlg*<br/>
[dans] Spécifiez `CMFCColorDialog` TRUE pour afficher la boîte de dialogue, ou FALSE pour afficher la boîte de dialogue couleur standard du système.

*bEnable*<br/>
[dans] Spécifiez TRUE pour afficher le bouton "autre"; autrement, FALSE. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cmfccolormenubuttonenabletearoff"></a><a name="enabletearoff"></a>CMFCColorMenuButton::EnableTearOff

Permet d’arracher une vitre de couleur.

```cpp
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
[dans] Spécifie l’ID pour la vitre larme.

*nVertDockColumns (en)*<br/>
[dans] Spécifie le nombre de colonnes dans la vitre de couleur à quai verticalement pendant qu’il est en état de déchirure.

*nHorzDockRows*<br/>
[dans] Spécifie le nombre de rangées pour la vitre de couleur horizontalement amarré pendant qu’il est en état de déchirure.

### <a name="remarks"></a>Notes

Appelez cette méthode pour activer la fonction "tear-off" pour `CMFCColorMenuButton` le volet couleur qui apparaît lorsque le bouton est appuyé.

## <a name="cmfccolormenubuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColorMenuButton::GetAutomaticColor

Récupère la couleur automatique actuelle.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur de couleur RGB qui représente la couleur automatique actuelle.

### <a name="remarks"></a>Notes

Appelez cette méthode pour obtenir la couleur automatique qui est définie par [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton).

## <a name="cmfccolormenubuttongetcolor"></a><a name="getcolor"></a>CMFCColorMenuButton::GetColor

Récupère la couleur du bouton actuel.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

La couleur du bouton.

### <a name="remarks"></a>Notes

## <a name="cmfccolormenubuttongetcolorbycmdid"></a><a name="getcolorbycmdid"></a>CMFCColorMenuButton::GetColorByCmdID

Récupère la couleur qui correspond à une pièce d’identité de commande spécifiée.

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>Paramètres

*uiCmdID*<br/>
[dans] Une pièce d’identité de commande.

### <a name="return-value"></a>Valeur de retour

La couleur qui correspond à l’ID de commande spécifié.

### <a name="remarks"></a>Notes

Utilisez cette méthode lorsque vous avez plusieurs boutons de couleur dans une application. Lorsque l’utilisateur clique sur un bouton couleur, le bouton envoie son identifiant de commande dans un message WM_COMMAND à son parent. La `GetColorByCmdID` méthode utilise l’ID de commande pour récupérer la couleur correspondante.

## <a name="cmfccolormenubuttonisemptymenuallowed"></a><a name="isemptymenuallowed"></a>CMFCColorMenuButton::IsEmptyMenuAllowed

Indique si les menus vides sont pris en charge.

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si les menus vides sont autorisés; autrement, zéro.

### <a name="remarks"></a>Notes

Les menus vides sont pris en charge par défaut. Remplacer cette méthode pour changer ce comportement en classe dérivée.

## <a name="cmfccolormenubuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCColorMenuButton::OnChangeParentWnd

Appelé par le cadre lorsque la fenêtre parente change.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] Un pointeur vers la nouvelle fenêtre parente.

### <a name="remarks"></a>Notes

## <a name="cmfccolormenubuttonondraw"></a><a name="ondraw"></a>CMFCColorMenuButton::OnDraw

Appelé par le cadre pour afficher une image sur un bouton.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz=TRUE,
    BOOL bCustomizeMode=FALSE,
    BOOL bHighlight=FALSE,
    BOOL bDrawBorder=TRUE,
    BOOL bGrayDisabledButtons=TRUE);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*Rect*<br/>
[dans] Un rectangle qui limite la zone à redessiner.

*pImages (en)*<br/>
[dans] Indique une liste d’images de barres d’outils.

*bHorz (en)*<br/>
[dans] VRAI pour spécifier que la barre d’outils est dans un état horizontal à quai; autrement, FALSE. La valeur par défaut est TRUE.

*bCustomizeMode*<br/>
[dans] VRAI pour spécifier que l’application est en mode personnalisation; autrement, FALSE. La valeur par défaut est FALSE.

*bHighlight (en)*<br/>
[dans] VRAI pour spécifier que le bouton est mis en surbrillance; autrement, FALSE. La valeur par défaut est FALSE.

*bDrawBorder (en anglais seulement)*<br/>
[dans] VRAI pour spécifier que la bordure du bouton est affichée; autrement, FALSE. La valeur par défaut est TRUE.

*bGrayDisabledButtons*<br/>
[dans] VRAI pour spécifier que les boutons désactivés sont grisés (dimmed) dehors ; autrement, FALSE. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cmfccolormenubuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCColorMenuButton::OnDrawOnCustomizeList

Appelé par le `CMFCColorMenuButton` cadre avant qu’un objet ne soit affiché dans la liste d’une boîte de dialogue de personnalisation de la barre d’outils.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*Rect*<br/>
[dans] Un rectangle qui limite le bouton à dessiner.

*bSélectré*<br/>
[dans] TRUE précise que le bouton est dans un état choisi; autrement, FALSE.

### <a name="return-value"></a>Valeur de retour

Largeur du bouton.

### <a name="remarks"></a>Notes

Cette méthode est appelée par `CMFCColorMenuButton` le cadre lorsqu’un objet est affiché dans la boîte de liste pendant le processus de personnalisation de la barre d’outils.

## <a name="cmfccolormenubuttonopencolordialog"></a><a name="opencolordialog"></a>CMFCColorMenuButton::OpenColorDialog

Ouvre une boîte de dialogue de sélection de couleurs.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Paramètres

*colorDefault*<br/>
[dans] La couleur par défaut qui est sélectionnée dans la boîte de dialogue couleur.

*colorRes colorRes*<br/>
[out] Retourne la couleur que l’utilisateur sélectionne à partir de la boîte de dialogue couleur.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur sélectionne une nouvelle couleur; autrement, zéro.

### <a name="remarks"></a>Notes

Lorsque le bouton du menu est cliqué, appelez cette méthode pour ouvrir une boîte de dialogue couleur. Si la valeur de retour est non zéro, la couleur que l’utilisateur sélectionne est stockée dans le *paramètre colorRes.* Utilisez la méthode [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton) méthode pour passer de la boîte de dialogue couleur standard et la boîte de dialogue [CMFCColorDialog Classe.](../../mfc/reference/cmfccolordialog-class.md)

## <a name="cmfccolormenubuttonsetcolor"></a><a name="setcolor"></a>CMFCColorMenuButton::SetColor

Définit la couleur du bouton de couleur actuel.

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>Paramètres

*Clr*<br/>
[dans] Une valeur de couleur RGB.

*bNotifier*<br/>
[dans] VRAI pour appliquer la couleur du paramètre *clr* à n’importe quel bouton de menu associé ou bouton de barre d’outils; autrement, FALSE.

### <a name="remarks"></a>Notes

Appelez cette méthode pour changer la couleur du bouton de couleur actuel. Si le *paramètre bNotify* n’est paszero, la couleur du bouton correspondant sur n’importe quel menu ou barre d’outils de popup associé est changée en couleur spécifiée par le paramètre *clr.*

## <a name="cmfccolormenubuttonsetcolorbycmdid"></a><a name="setcolorbycmdid"></a>CMFCColorMenuButton::SetColorByCmdID

Définit la couleur du bouton de menu couleur spécifié.

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>Paramètres

*uiCmdID*<br/>
[dans] L’ID de ressource d’un bouton de menu couleur.

*Couleur*<br/>
[dans] Une valeur de couleur RGB.

## <a name="cmfccolormenubuttonsetcolorname"></a><a name="setcolorname"></a>CMFCColorMenuButton::SetColorName

Définit un nouveau nom pour la couleur spécifiée.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
[dans] La valeur RGB de la couleur dont le nom change.

*strName*<br/>
[dans] Le nouveau nom de la couleur.

### <a name="remarks"></a>Notes

## <a name="cmfccolormenubuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColorMenuButton::SetColumnsNumber

Définit le nombre de colonnes à afficher dans un contrôle de sélection des couleurs (objet [CMFCColorBar).](../../mfc/reference/cmfccolorbar-class.md)

```cpp
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Paramètres

*nColumns*<br/>
[dans] Le nombre de colonnes à afficher.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar, classe](../../mfc/reference/cmfccolorbar-class.md)<br/>
[Classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog Classe](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[Classe CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)
