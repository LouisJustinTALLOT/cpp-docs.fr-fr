---
description: 'En savoir plus sur : classe CMFCColorMenuButton'
title: CMFCColorMenuButton, classe
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
ms.openlocfilehash: 4ba0934e872adc4e4b33c2ae5700ecb0fc46e6d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327674"
---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton, classe

La `CMFCColorMenuButton` classe prend en charge une commande de menu ou un bouton de barre d’outils qui démarre une boîte de dialogue de sélection de couleurs.

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
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Active et désactive un bouton « automatique » positionné au-dessus des boutons de couleur standard. (Le bouton automatique système standard est intitulé **automatique**.)|
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Active l’affichage des couleurs spécifiques au document à la place des couleurs système.|
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Active et désactive un bouton « autre » positionné sous les boutons de couleur standard. (Le bouton « autre » du système standard est intitulé **plus de couleurs**.)|
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Permet de détacher un volet couleur.|
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Récupère la couleur automatique actuelle.|
|[CMFCColorMenuButton :: GetColor](#getcolor)|Récupère la couleur du bouton actuel.|
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Récupère la couleur qui correspond à un ID de commande spécifié.|
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Appelé par le Framework lorsque la fenêtre parente est modifiée.|
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Ouvre une boîte de dialogue de sélection de couleur.|
|[CMFCColorMenuButton :: SetColor](#setcolor)|Définit la couleur du bouton de couleur actuel.|
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Définit la couleur du bouton de menu de couleur spécifié.|
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Définit un nouveau nom pour la couleur spécifiée.|
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Définit le nombre de colonnes affichées par un `CMFCColorBar` objet.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCColorMenuButton :: CopyFrom](#copyfrom)|Copie un autre bouton de barre d’outils sur le bouton actuel.|
|[CMFCColorMenuButton :: CreatePopupMenu](#createpopupmenu)|Crée une boîte de dialogue de sélection de couleurs.|
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Indique si les menus vides sont pris en charge.|
|[CMFCColorMenuButton :: OnDraw](#ondraw)|Appelé par le Framework pour afficher une image sur un bouton.|
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Appelé par le Framework avant qu’un `CMFCColorMenuButton` objet ne soit affiché dans la liste d’une boîte de dialogue de personnalisation de barre d’outils.|

## <a name="remarks"></a>Notes

Pour remplacer la commande de menu ou le bouton de barre d’outils d’origine par un `CMFCColorMenuButton` objet, créez l' `CMFCColorMenuButton` objet, définissez les styles de [classe CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) appropriés, puis appelez la `ReplaceButton` méthode de la classe de [classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) . Si vous personnalisez une barre d’outils, appelez la méthode [CMFCToolBarsCustomizeDialog :: ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) .

La boîte de dialogue Sélecteur de couleurs est créée lors du traitement du gestionnaire d’événements [CMFCColorMenuButton :: CreatePopupMenu](#createpopupmenu) . Le gestionnaire d’événements notifie le frame parent avec un message de WM_COMMAND. L' `CMFCColorMenuButton` objet envoie l’ID de contrôle assigné à la commande de menu ou au bouton de barre d’outils d’origine.

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer et configurer un bouton de menu de couleur à l’aide de diverses méthodes de la `CMFCColorMenuButton` classe. Dans l’exemple, un `CPalette` objet est d’abord créé, puis utilisé pour construire un objet de la `CMFCColorMenuButton` classe. L' `CMFCColorMenuButton` objet est ensuite configuré en activant ses boutons automatique et autres, et en définissant sa couleur et le nombre de colonnes. Ce code fait partie de l' [exemple Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxcolormenubutton. h

## <a name="cmfccolormenubuttoncmfccolormenubutton"></a><a name="cmfccolormenubutton"></a> CMFCColorMenuButton::CMFCColorMenuButton

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
dans ID de commande de bouton.

*lpszText*<br/>
dans Texte du bouton.

*pPalette*<br/>
dans Pointeur vers la palette de couleurs du bouton.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

Le premier constructeur est le constructeur par défaut. La couleur actuelle de l’objet et la couleur automatique sont initialisées au noir (RVB (0, 0, 0)).

Le deuxième constructeur initialise le bouton à la couleur qui correspond à l’ID de commande spécifié.

## <a name="cmfccolormenubuttoncopyfrom"></a><a name="copyfrom"></a> CMFCColorMenuButton :: CopyFrom

Copie un objet dérivé de la [classe CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)vers un autre.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
dans Bouton source à copier.

### <a name="remarks"></a>Notes

Substituez cette méthode pour copier des objets dérivés de l' `CMFCColorMenuButton` objet.

## <a name="cmfccolormenubuttoncreatepopupmenu"></a><a name="createpopupmenu"></a> CMFCColorMenuButton :: CreatePopupMenu

Crée une boîte de dialogue de sélection de couleurs.

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>Valeur renvoyée

Objet qui représente une boîte de dialogue de sélecteur de couleurs.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure quand l’utilisateur appuie sur un bouton de menu couleur.

## <a name="cmfccolormenubuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a> CMFCColorMenuButton::EnableAutomaticButton

Active et désactive un bouton « automatique » positionné au-dessus des boutons de couleur standard. (Le bouton automatique système standard est intitulé **automatique**.)

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
dans Spécifie le texte du bouton qui est affiché lorsque le bouton devient automatique.

*colorAutomatic*<br/>
dans Spécifie une nouvelle couleur automatique.

*bEnable*<br/>
dans Spécifie si le bouton est automatique ou non.

### <a name="remarks"></a>Notes

Le bouton automatique applique la couleur par défaut actuelle.

## <a name="cmfccolormenubuttonenabledocumentcolors"></a><a name="enabledocumentcolors"></a> CMFCColorMenuButton::EnableDocumentColors

Active l’affichage des couleurs spécifiques au document à la place des couleurs système.

```cpp
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
dans Spécifie le texte du bouton.

*bEnable*<br/>
dans TRUE pour afficher les couleurs spécifiques au document ou FALSe pour afficher les couleurs système.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour afficher les couleurs actuelles du document ou les couleurs de la palette système lorsque l’utilisateur clique sur un bouton de menu couleur.

## <a name="cmfccolormenubuttonenableotherbutton"></a><a name="enableotherbutton"></a> CMFCColorMenuButton::EnableOtherButton

Active et désactive un bouton « autre » positionné sous les boutons de couleur standard. (Le bouton « autre » du système standard est intitulé **plus de couleurs**.)

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
dans Spécifiez TRUE pour afficher la boîte de `CMFCColorDialog` dialogue, ou false pour afficher la boîte de dialogue couleur système standard.

*bEnable*<br/>
dans Spécifiez TRUE pour afficher le bouton « Other » (autre). Sinon, FALSe. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cmfccolormenubuttonenabletearoff"></a><a name="enabletearoff"></a> CMFCColorMenuButton::EnableTearOff

Permet de détacher un volet couleur.

```cpp
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
dans Spécifie l’ID du volet détachable.

*nVertDockColumns*<br/>
dans Spécifie le nombre de colonnes dans le volet couleur ancré verticalement en état de déchirement.

*nHorzDockRows*<br/>
dans Spécifie le nombre de lignes pour le volet couleur ancré horizontalement en état de déchirement.

### <a name="remarks"></a>Notes

Appelez cette méthode pour activer la fonctionnalité de déchirage du volet couleur qui s’affiche lorsque le `CMFCColorMenuButton` bouton est enfoncé.

## <a name="cmfccolormenubuttongetautomaticcolor"></a><a name="getautomaticcolor"></a> CMFCColorMenuButton::GetAutomaticColor

Récupère la couleur automatique actuelle.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur de couleur RVB qui représente la couleur automatique actuelle.

### <a name="remarks"></a>Notes

Appelez cette méthode pour obtenir la couleur automatique définie par [CMFCColorMenuButton :: EnableAutomaticButton](#enableautomaticbutton).

## <a name="cmfccolormenubuttongetcolor"></a><a name="getcolor"></a> CMFCColorMenuButton :: GetColor

Récupère la couleur du bouton actuel.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Couleur du bouton.

### <a name="remarks"></a>Notes

## <a name="cmfccolormenubuttongetcolorbycmdid"></a><a name="getcolorbycmdid"></a> CMFCColorMenuButton::GetColorByCmdID

Récupère la couleur qui correspond à un ID de commande spécifié.

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>Paramètres

*uiCmdID*<br/>
dans ID de commande.

### <a name="return-value"></a>Valeur renvoyée

Couleur qui correspond à l’ID de commande spécifié.

### <a name="remarks"></a>Notes

Utilisez cette méthode lorsque vous avez plusieurs boutons de couleur dans une application. Quand l’utilisateur clique sur un bouton de couleur, le bouton envoie son ID de commande dans un WM_COMMAND message à son parent. La `GetColorByCmdID` méthode utilise l’ID de commande pour récupérer la couleur correspondante.

## <a name="cmfccolormenubuttonisemptymenuallowed"></a><a name="isemptymenuallowed"></a> CMFCColorMenuButton::IsEmptyMenuAllowed

Indique si les menus vides sont pris en charge.

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si les menus vides sont autorisés ; Sinon, zéro.

### <a name="remarks"></a>Notes

Les menus vides sont pris en charge par défaut. Substituez cette méthode pour modifier ce comportement dans la classe dérivée.

## <a name="cmfccolormenubuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a> CMFCColorMenuButton::OnChangeParentWnd

Appelé par le Framework lorsque la fenêtre parente est modifiée.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Pointeur vers la nouvelle fenêtre parente.

### <a name="remarks"></a>Notes

## <a name="cmfccolormenubuttonondraw"></a><a name="ondraw"></a> CMFCColorMenuButton :: OnDraw

Appelé par le Framework pour afficher une image sur un bouton.

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

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rectangulaire*<br/>
dans Rectangle qui délimite la zone à redessiner.

*pImages*<br/>
dans Pointe vers une liste d’images de barre d’outils.

*bHorz*<br/>
dans TRUE pour spécifier que la barre d’outils est dans un état d’ancrage horizontal ; Sinon, FALSe. La valeur par défaut est TRUE.

*bCustomizeMode*<br/>
dans TRUE pour spécifier que l’application est en mode de personnalisation. Sinon, FALSe. La valeur par défaut est FALSE.

*bHighlight*<br/>
dans TRUE pour spécifier que le bouton est mis en surbrillance ; Sinon, FALSe. La valeur par défaut est FALSE.

*bDrawBorder*<br/>
dans TRUE pour spécifier que la bordure du bouton est affichée ; Sinon, FALSe. La valeur par défaut est TRUE.

*bGrayDisabledButtons*<br/>
dans TRUE pour spécifier que les boutons désactivés sont grisés (grisés); Sinon, FALSe. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cmfccolormenubuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a> CMFCColorMenuButton::OnDrawOnCustomizeList

Appelé par le Framework avant qu’un `CMFCColorMenuButton` objet ne soit affiché dans la liste d’une boîte de dialogue de personnalisation de barre d’outils.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rectangulaire*<br/>
dans Rectangle qui délimite le bouton à dessiner.

*bSelected*<br/>
dans TRUE spécifie que le bouton est dans l’état sélectionné ; Sinon, FALSe.

### <a name="return-value"></a>Valeur renvoyée

Largeur du bouton.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure quand un `CMFCColorMenuButton` objet est affiché dans la zone de liste pendant le processus de personnalisation de la barre d’outils.

## <a name="cmfccolormenubuttonopencolordialog"></a><a name="opencolordialog"></a> CMFCColorMenuButton::OpenColorDialog

Ouvre une boîte de dialogue de sélection de couleur.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Paramètres

*colorDefault*<br/>
dans Couleur par défaut qui est sélectionnée dans la boîte de dialogue couleur.

*colorRes*<br/>
à Retourne la couleur sélectionnée par l’utilisateur dans la boîte de dialogue couleur.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’utilisateur sélectionne une nouvelle couleur ; Sinon, zéro.

### <a name="remarks"></a>Notes

Quand l’utilisateur clique sur le bouton de menu, appelez cette méthode pour ouvrir une boîte de dialogue de couleur. Si la valeur de retour est différente de zéro, la couleur sélectionnée par l’utilisateur est stockée dans le paramètre *colorRes* . Utilisez la méthode [CMFCColorMenuButton :: EnableOtherButton](#enableotherbutton) pour basculer entre la boîte de dialogue couleur standard et la boîte de dialogue [classe CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) .

## <a name="cmfccolormenubuttonsetcolor"></a><a name="setcolor"></a> CMFCColorMenuButton :: SetColor

Définit la couleur du bouton de couleur actuel.

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>Paramètres

*Language*<br/>
dans Valeur de couleur RVB.

*bNotify*<br/>
dans TRUE pour appliquer la couleur de paramètre *CLR* à un bouton de menu ou un bouton de barre d’outils associé. Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelez cette méthode pour modifier la couleur du bouton de couleur actuel. Si le paramètre *bNotify* est différent de zéro, la couleur du bouton correspondant dans un menu contextuel ou une barre d’outils associé est remplacée par la couleur spécifiée par le paramètre *CLR* .

## <a name="cmfccolormenubuttonsetcolorbycmdid"></a><a name="setcolorbycmdid"></a> CMFCColorMenuButton::SetColorByCmdID

Définit la couleur du bouton de menu de couleur spécifié.

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>Paramètres

*uiCmdID*<br/>
dans ID de ressource d’un bouton de menu couleur.

*color*<br/>
dans Valeur de couleur RVB.

## <a name="cmfccolormenubuttonsetcolorname"></a><a name="setcolorname"></a> CMFCColorMenuButton::SetColorName

Définit un nouveau nom pour la couleur spécifiée.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
dans Valeur RVB de la couleur dont le nom change.

*strName*<br/>
dans Nouveau nom de la couleur.

### <a name="remarks"></a>Notes

## <a name="cmfccolormenubuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a> CMFCColorMenuButton::SetColumnsNumber

Définit le nombre de colonnes à afficher dans un contrôle de sélection de couleur (objet [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) ).

```cpp
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Paramètres

*nColumns*<br/>
dans Nombre de colonnes à afficher.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar, classe](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog, classe](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[CMFCColorButton, classe](../../mfc/reference/cmfccolorbutton-class.md)
