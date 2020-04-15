---
title: Classe CMFCDropDownToolbarButton
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
ms.openlocfilehash: d62d5ecb0962f74a5dac1658c207cfb08cf12588
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367608"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>Classe CMFCDropDownToolbarButton

Type de bouton de barre d'outils qui se comporte comme un bouton normal lorsque l'utilisateur clique dessus. Cependant, il ouvre une barre d’outils de débarquement [(classe CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md) si l’utilisateur appuie et maintient le bouton de la barre d’outils vers le bas.

## <a name="syntax"></a>Syntaxe

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|Construit un objet `CMFCDropDownToolbarButton`.|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CopyDe](#copyfrom)|Copie les propriétés d’un autre bouton de barre d’outils sur le bouton actuel. (Overrides [CMFCToolBarButton::CopyDe](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCDropDownToolbarButton::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Ouvre une barre d’outils de décrochage.|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Copies du texte du bouton de la barre d’outils à un menu. (Overrides [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Récupère la barre d’outils de dépôt qui est associée au bouton.|
|`CMFCDropDownToolbarButton::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Détermine si la barre d’outils d’abandon est actuellement ouverte.|
|[CMFCDropDownToolbarButton::IsExtrasize](#isextrasize)|Détermine si le bouton peut être affiché avec une bordure étendue. (Overrides [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Appelé par le cadre pour calculer la taille du bouton pour le contexte de l’appareil spécifié et l’état d’amarrage. (Overrides [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|`CMFCDropDownToolbarButton::OnCancelMode`|Appelé par le cadre pour gérer le [message WM_CANCELMODE.](/windows/win32/winmsg/wm-cancelmode) (Substitue `CMCToolBarButton::OnCancelMode`.)|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Appelé par le cadre lorsque le bouton est inséré dans une nouvelle barre d’outils. (Overrides [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Appelé par le cadre lorsque l’utilisateur clique sur le bouton de la souris. (Overrides [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Appelé par le cadre lorsque l’utilisateur libère le bouton de la souris. (Overrides [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Appelé par le cadre lorsque le barre d’outils parent gère un message WM_HELPHITTEST. (Overrides [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Modifie le menu fourni lorsque l’application affiche un menu raccourci sur la barre d’outils parent. (Overrides [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Appelé par le cadre pour dessiner le bouton en utilisant les styles spécifiés et les options. (Overrides [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Appelé par le cadre pour dessiner le bouton dans le volet **Commandes** de la boîte de dialogue **Customize.** (Overrides [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCDropDownToolbarButton::Serialize](#serialize)|Lit cet objet à partir d’une archive ou l’écrit à une archive. (Overrides [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Définit la commande par défaut que le cadre utilise lorsqu’un utilisateur clique sur le bouton.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Spécifie la durée pendant laquelle un utilisateur doit maintenir le bouton de la souris vers le bas avant que la barre d’outils de dépôt n’apparaisse.|

## <a name="remarks"></a>Notes

Un `CMFCDropDownToolBarButton` diffère d’un bouton ordinaire en ce qu’il a une petite flèche dans le coin inférieur droit du bouton. Une fois que l’utilisateur sélectionne un bouton de la barre d’outils de dépôt, le cadre affiche son icône sur le bouton de la barre d’outils de haut niveau (le bouton avec la petite flèche dans le coin inférieur droit).

Pour plus d’informations sur la façon de mettre en œuvre une barre d’outils de décrochage, voir [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md).

L’objet `CMFCDropDownToolBarButton` peut être exporté vers un objet [cmFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md) et affiché sous forme de bouton de menu avec un menu pop-up.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCDropDownToolbarButton::CopyDe

Copie les propriétés d’un autre bouton de barre d’outils sur le bouton actuel.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[dans] Une référence au bouton source à partir duquel copier.

### <a name="remarks"></a>Notes

Appelez cette méthode pour copier un autre bouton de barre d’outils sur ce bouton de barre d’outils. *src* doit être `CMFCDropDownToolbarButton`de type .

## <a name="cmfcdropdowntoolbarbuttoncmfcdropdowntoolbarbutton"></a><a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

Construit un objet `CMFCDropDownToolbarButton`.

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
[dans] Le texte par défaut du bouton.

*pToolBar*<br/>
[dans] Un pointeur `CMFCDropDownToolBar` vers l’objet qui s’affiche lorsque l’utilisateur appuie sur le bouton.

### <a name="remarks"></a>Notes

La deuxième surcharge du constructeur copie le bouton de dépôt du premier bouton de la barre d’outils que *pToolBar* spécifie.

Typiquement, un bouton de barre d’outils de dépôt utilise le texte du bouton le plus récemment utilisé dans la barre d’outils que *pToolBar* spécifie. Il utilise le texte spécifié par *lpszName* lorsque le bouton est converti en un bouton de menu ou est affiché dans **l’onglet Commandes** de la boîte de dialogue **Personnaliser.** Pour plus d’informations sur la boîte de dialogue **Customize,** voir [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCDropDownToolbarButton` un objet de la classe. Cet extrait de code fait partie de [l’échantillon Visual Studio Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

## <a name="cmfcdropdowntoolbarbuttondropdowntoolbar"></a><a name="dropdowntoolbar"></a>CMFCDropDownToolbarButton::DropDownToolbar

Ouvre une barre d’outils de décrochage.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
[dans] La fenêtre parente du cadre de dépôt, ou NULL pour utiliser la fenêtre parente du bouton de barre d’outils de dépôt.

### <a name="return-value"></a>Valeur de retour

Nonzero si la méthode est réussie; sinon 0.

### <a name="remarks"></a>Notes

La méthode [CMFCDropDownToolbarButton :::OnClick](#onclick) méthode appelle cette méthode pour ouvrir la barre d’outils de dépôt lorsque l’utilisateur appuie et maintient le bouton de la barre d’outils vers le bas.

Ces méthodes créent la barre d’outils de décrochage en utilisant le [CMFCDropDownFrame::Créer la](../../mfc/reference/cmfcdropdownframe-class.md#create) méthode. Si la barre d’outils parente est amarré verticalement, cette méthode positionne la barre d’outils de dépôt soit vers le côté gauche ou droit de la barre d’outils parent, selon l’ajustement. Sinon, cette méthode positionne la barre d’outils de dépôt sous la barre d’outils parent.

Cette méthode échoue si *pWnd* est NULL et le bouton de barre d’outils de dépôt n’a pas une fenêtre parente.

## <a name="cmfcdropdowntoolbarbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCDropDownToolbarButton::ExportToMenuButton

Copies du texte du bouton de la barre d’outils à un menu.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Paramètres

*menuButton*<br/>
[dans] Une référence au bouton du menu cible.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode appelle l’implémentation de la classe de base ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) et joint ensuite au bouton menu cible un menu pop-up qui contient chaque élément de menu de barre d’outils dans ce bouton. Cette méthode n’appende pas les sous-menus au menu pop-up.

Cette méthode échoue si la `m_pToolBar`barre d’outils parent, est NULL ou la mise en œuvre de la classe de base retourne FALSE.

## <a name="cmfcdropdowntoolbarbuttongetdropdowntoolbar"></a><a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton::GetDropDownToolBar

Récupère la barre d’outils de dépôt qui est associée au bouton.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>Valeur de retour

La barre d’outils de dépôt qui est associée au bouton.

### <a name="remarks"></a>Notes

Cette méthode `m_pToolBar` renvoie le membre des données.

## <a name="cmfcdropdowntoolbarbuttonisdropdown"></a><a name="isdropdown"></a>CMFCDropDownToolbarButton::IsDropDown

Détermine si la barre d’outils d’abandon est actuellement ouverte.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la barre d’outils de décrochage est actuellement ouverte; sinon 0.

### <a name="remarks"></a>Notes

Le cadre ouvre la barre d’outils de débarquement en utilisant la méthode [CMFCDropDownToolbarButton::DropDownToolbar.](#dropdowntoolbar) Le cadre ferme la barre d’outils de dépôt lorsque l’utilisateur appuie sur le bouton gauche-souris dans la zone non cliente de la barre d’outils de dépôt.

## <a name="cmfcdropdowntoolbarbuttonisextrasize"></a><a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtrasize

Détermine si le bouton peut être affiché avec une bordure étendue.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le bouton de la barre d’outils peut être affiché avec une bordure étendue; sinon 0.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les frontières étendues, voir [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).

## <a name="cmfcdropdowntoolbarbuttonm_uishowbardelay"></a><a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay

Spécifie la durée pendant laquelle un utilisateur doit maintenir le bouton de la souris vers le bas avant que la barre d’outils de dépôt n’apparaisse.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Notes

Le délai est mesuré en millisecondes. La valeur par défaut est 500. Vous pouvez définir un autre délai en modifiant la valeur de ce membre de données partagé.

## <a name="cmfcdropdowntoolbarbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCDropDownToolbarButton::OnCalculateSize

Appelé par le cadre pour calculer la taille du bouton pour le contexte de l’appareil spécifié et l’état d’amarrage.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Le contexte de l’appareil qui affiche le bouton.

*tailleDefault*<br/>
[dans] La taille par défaut du bouton.

*bHorz (en)*<br/>
[dans] L’état de quai de la barre d’outils parent. Ce paramètre est VRAI si la barre d’outils est amarré horizontalement ou flotte, ou FALSE si la barre d’outils est amarré verticalement.

### <a name="return-value"></a>Valeur de retour

Une `SIZE` structure qui contient les dimensions du bouton, en pixels.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) en ajoutant la largeur de la flèche de chute vers le bas à la dimension horizontale de la taille du bouton.

## <a name="cmfcdropdowntoolbarbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd

Appelé par le cadre lorsque le bouton est inséré dans une nouvelle barre d’outils.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] La nouvelle fenêtre parente.

### <a name="remarks"></a>Notes

Cette méthode remplace la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) en effaçant l’étiquette de texte ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) et en définissant le [CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) et [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) membres de données à FALSE.

## <a name="cmfcdropdowntoolbarbuttononclick"></a><a name="onclick"></a>CMFCDropDownToolbarButton::OnClick

Appelé par le cadre lorsque l’utilisateur clique sur le bouton de la souris.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
[dans] La fenêtre parente du bouton de la barre d’outils.

*bDelay (en)*<br/>
[dans] VRAI si le message doit être manipulé avec un retard.

### <a name="return-value"></a>Valeur de retour

Nonzero si le bouton traite le message de clic; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base, [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), en mettant à jour l’état de la barre d’outils de décrochage.

Lorsqu’un utilisateur clique sur le bouton de la barre d’outils, cette méthode crée une minuterie qui attend la durée spécifiée par le [CMFCDropDownToolbarButton : m_uiShowBarDelay](#m_uishowbardelay) membre des données, puis ouvre la barre d’outils de débarquement en utilisant la méthode [CMFCDropDownToolbarButton: :DLa méthode De l’escalade.](#dropdowntoolbar) Cette méthode ferme la barre d’outils de dépôt la deuxième fois que l’utilisateur clique sur le bouton de la barre d’outils.

## <a name="cmfcdropdowntoolbarbuttononclickup"></a><a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp

Appelé par le cadre lorsque l’utilisateur libère le bouton de la souris.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le bouton traite le message de clic; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base, [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), en mettant à jour l’état de la barre d’outils de décrochage.

Cette méthode arrête la minuterie de barre d’outils d’abandon si elle est active. Il ferme la barre d’outils de décrochage si elle est ouverte.

Pour plus d’informations sur la barre d’outils de décrochage et la minuterie de barre d’outils de décrochage, voir [CMFCDropDownToolbarButton::OnClick](#onclick).

## <a name="cmfcdropdowntoolbarbuttononcontexthelp"></a><a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnContextHelp

Appelé par le cadre lorsque le barre d’outils parent gère un message WM_HELPHITTEST.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
[dans] La fenêtre parente du bouton de la barre d’outils.

### <a name="return-value"></a>Valeur de retour

Nonzero si le bouton traite le message d’aide; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) en appelant le [CMFCDropDownToolbarButton::OnClick](#onclick) méthode avec *bDelay* mis à FALSE. Cette méthode renvoie la valeur qui est retournée par [CMFCDropDownToolbarButton::OnClick](#onclick).

Pour plus d’informations sur le message WM_HELPHITTEST, voir [TN028: Context-Sensitive Help Support](../../mfc/tn028-context-sensitive-help-support.md).

## <a name="cmfcdropdowntoolbarbuttononcustomizemenu"></a><a name="oncustomizemenu"></a>CMFCDropDownToolbarButton::OnCustomizeMenu

Modifie le menu fourni lorsque l’application affiche un menu raccourci sur la barre d’outils parent.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Paramètres

*pMenu*<br/>
[dans] Le menu à personnaliser.

### <a name="return-value"></a>Valeur de retour

Cette méthode renvoie TRUE.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) en désactivant les éléments de menu suivants :

- **Image de bouton de copie**

- **Aspect de bouton**

- **Image**

- **Text**

- **Image et texte**

Remplacez cette méthode pour modifier le menu raccourci que le cadre affiche en mode personnalisation.

## <a name="cmfcdropdowntoolbarbuttonondraw"></a><a name="ondraw"></a>CMFCDropDownToolbarButton::OnDraw

Appelé par le cadre pour dessiner le bouton en utilisant les styles spécifiés et les options.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Le contexte de l’appareil qui affiche le bouton.

*Rect*<br/>
[dans] Le rectangle de délimitation du bouton.

*pImages (en)*<br/>
[dans] La collection d’images de barres d’outils qui est associée au bouton.

*bHorz (en)*<br/>
[dans] L’état de quai de la barre d’outils parent. Ce paramètre est VRAI lorsque le bouton est amarré horizontalement et FALSE lorsque le bouton est amarré verticalement.

*bCustomizeMode*<br/>
[dans] Précise si la barre d’outils est en mode personnalisation. Ce paramètre est VRAI lorsque la barre d’outils est en mode personnalisation et FALSE lorsque la barre d’outils n’est pas en mode personnalisation.

*bHighlight (en)*<br/>
[dans] Précise si le bouton est surligné. Ce paramètre est VRAI lorsque le bouton est mis en surbrillance et FALSE lorsque le bouton n’est pas surligné.

*bDrawBorder (en anglais seulement)*<br/>
[dans] Précise si le bouton doit afficher sa bordure. Ce paramètre est VRAI lorsque le bouton doit afficher sa bordure et FALSE lorsque le bouton ne doit pas afficher sa bordure.

*bGrayDisabledButtons*<br/>
[dans] Précise s’il faut ombrager les boutons désactivés ou utiliser la collection d’images désactivées. Ce paramètre est VRAI lorsque les boutons désactivés doivent être ombragés et FALSE lorsque cette méthode doit utiliser la collection d’images désactivées.

### <a name="remarks"></a>Notes

Remplacez cette méthode pour personnaliser le dessin de bouton de barre d’outils.

## <a name="cmfcdropdowntoolbarbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList

Appelé par le cadre pour dessiner le bouton dans le volet **Commandes** de la boîte de dialogue **Customize.**

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Le contexte de l’appareil qui affiche le bouton.

*Rect*<br/>
[dans] Le rectangle de délimitation du bouton.

*bSélectré*<br/>
[dans] Si le bouton est sélectionné. Si ce paramètre est VRAI, le bouton est sélectionné. Si ce paramètre est FALSE, le bouton n’est pas sélectionné.

### <a name="return-value"></a>Valeur de retour

La largeur, en pixels, du bouton sur le contexte de l’appareil spécifié.

### <a name="remarks"></a>Notes

Cette méthode est appelée par la boîte de dialogue de personnalisation (onglet **commandes)** lorsque le bouton est nécessaire pour s’afficher sur la boîte de liste propriétaire-tirage.

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) en changeant l’étiquette de texte du bouton au nom du bouton (c’est-à-dire, à la valeur du paramètre *lpszName* que vous avez passé au constructeur).

## <a name="cmfcdropdowntoolbarbuttonserialize"></a><a name="serialize"></a>CMFCDropDownToolbarButton::Serialize

Lit cet objet à partir d’une archive ou l’écrit à une archive.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*Ar*<br/>
[dans] L’objet `CArchive` à partir duquel ou à laquelle sérialiser.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) en sérialisant l’ID de ressource de la barre d’outils parent. Lorsque l’archive est chargée ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) retourne une `m_pToolBar` valeur non zéro), cette méthode définit le membre des données à la barre d’outils qui contient l’ID de ressources sérialisées.

## <a name="cmfcdropdowntoolbarbuttonsetdefaultcommand"></a><a name="setdefaultcommand"></a>CMFCDropDownToolbarButton::SetDefaultCommand

Définit la commande par défaut que le cadre utilise lorsqu’un utilisateur clique sur le bouton.

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’ID de la commande par défaut.

### <a name="remarks"></a>Notes

Appelez cette méthode pour spécifier une commande par défaut que le cadre exécute lorsque l’utilisateur clique sur le bouton. Un élément avec l’ID de commande spécifié par *uiCmd* doit être situé dans la barre d’outils d’abandon parent.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[Classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton, classe](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Procédure pas à pas : placement de contrôles dans les barres d'outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
