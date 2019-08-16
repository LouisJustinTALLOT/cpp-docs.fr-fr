---
title: CMFCDropDownToolbarButton, classe
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
ms.openlocfilehash: fcfb521e309463da81d0064451297b3b73610d2f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505330"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton, classe

Type de bouton de barre d'outils qui se comporte comme un bouton normal lorsque l'utilisateur clique dessus. Toutefois, il ouvre une barre d’outils déroulante ( [classe CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md) si l’utilisateur appuie sur le bouton de barre d’outils et le maintient enfoncé.

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
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Copie les propriétés d’un autre bouton de barre d’outils sur le bouton actuel. (Substitue [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCDropDownToolbarButton::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Ouvre une barre d’outils déroulante.|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Copie le texte du bouton de barre d’outils dans un menu. (Substitue [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Récupère la barre d’outils déroulante associée au bouton.|
|`CMFCDropDownToolbarButton::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Détermine si la barre d’outils déroulante est actuellement ouverte.|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Détermine si le bouton peut être affiché avec une bordure étendue. (Substitue [CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Appelé par l’infrastructure pour calculer la taille du bouton pour le contexte de périphérique et l’état d’ancrage spécifiés. (Substitue [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|`CMFCDropDownToolbarButton::OnCancelMode`|Appelé par l’infrastructure pour gérer le message [WM_CANCELMODE](/windows/win32/winmsg/wm-cancelmode) . (Substitue `CMCToolBarButton::OnCancelMode`.)|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Appelée par l’infrastructure quand le bouton est inséré dans une nouvelle barre d’outils. (Substitue [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Appelée par l’infrastructure quand l’utilisateur clique sur le bouton de la souris. (Substitue [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Appelée par l’infrastructure quand l’utilisateur relâche le bouton de la souris. (Substitue [CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Appelée par l’infrastructure lorsque la barre d’outils parente gère un message WM_HELPHITTEST. (Substitue [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Modifie le menu fourni lorsque l’application affiche un menu contextuel dans la barre d’outils parente. (Substitue [CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Appelé par l’infrastructure pour dessiner le bouton à l’aide des styles et options spécifiés. (Substitue [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Appelée par l’infrastructure pour dessiner le bouton dans le volet **commandes** de la boîte de dialogue **personnaliser** . (Substitue [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCDropDownToolbarButton::Serialize](#serialize)|Lit cet objet à partir d’une archive ou l’écrit dans une archive. (Substitue [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Définit la commande par défaut utilisée par l’infrastructure lorsqu’un utilisateur clique sur le bouton.|

### <a name="data-members"></a>Membres de données

|Nom|Description|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Spécifie la durée pendant laquelle un utilisateur doit maintenir le bouton de la souris enfoncé avant que la barre d’outils déroulante ne s’affiche.|

## <a name="remarks"></a>Notes

Un `CMFCDropDownToolBarButton` est différent d’un bouton ordinaire, car il comporte une petite flèche dans le coin inférieur droit du bouton. Une fois que l’utilisateur a sélectionné un bouton dans la barre d’outils déroulante, l’infrastructure affiche son icône sur le bouton de barre d’outils de niveau supérieur (le bouton avec la petite flèche dans le coin inférieur droit).

Pour plus d’informations sur la façon d’implémenter une barre d’outils déroulante, consultez [CMFCDropDownToolBar, classe](../../mfc/reference/cmfcdropdowntoolbar-class.md).

L' `CMFCDropDownToolBarButton` objet peut être exporté vers un objet de [classe CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) et affiché sous la forme d’un bouton de menu avec un menu contextuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdropdowntoolbar.h

##  <a name="copyfrom"></a>  CMFCDropDownToolbarButton::CopyFrom

Copie les propriétés d’un autre bouton de barre d’outils sur le bouton actuel.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
dans Référence au bouton source à partir duquel effectuer la copie.

### <a name="remarks"></a>Notes

Appelez cette méthode pour copier un autre bouton de barre d’outils sur ce bouton de barre d’outils. *src* doit être de type `CMFCDropDownToolbarButton`.

##  <a name="cmfcdropdowntoolbarbutton"></a>  CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

Construit un objet `CMFCDropDownToolbarButton`.

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
dans Texte par défaut du bouton.

*pToolBar*<br/>
dans Pointeur vers l' `CMFCDropDownToolBar` objet qui est affiché lorsque l’utilisateur appuie sur le bouton.

### <a name="remarks"></a>Notes

La deuxième surcharge du constructeur copie sur le bouton de liste déroulante, le premier bouton de la barre d’outils que *pToolBar* spécifie.

En règle générale, un bouton déroulant de barre d’outils utilise le texte du bouton utilisé le plus récemment dans la barre d’outils que *pToolBar* spécifie. Elle utilise le texte spécifié par *lpszName* lorsque le bouton est converti en bouton de menu ou s’affiche sous l’onglet **commandes** de la boîte de dialogue **personnaliser** . Pour plus d’informations sur la boîte de dialogue **personnaliser** , consultez [CMFCToolBarsCustomizeDialog, classe](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCDropDownToolbarButton` classe. Cet extrait de code fait partie de l' [exemple de démonstration Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

##  <a name="dropdowntoolbar"></a>  CMFCDropDownToolbarButton::DropDownToolbar

Ouvre une barre d’outils déroulante.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
dans Fenêtre parente du frame déroulant, ou NULL pour utiliser la fenêtre parente du bouton déroulant de la barre d’outils.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode réussit; Sinon, 0.

### <a name="remarks"></a>Notes

La méthode [CMFCDropDownToolbarButton:: OnClick](#onclick) appelle cette méthode pour ouvrir la barre d’outils déroulante lorsque l’utilisateur appuie sur le bouton de barre d’outils et le maintient enfoncé.

Cette méthode crée la barre d’outils déroulante à l’aide de la méthode [CMFCDropDownFrame:: Create](../../mfc/reference/cmfcdropdownframe-class.md#create) . Si la barre d’outils parente est ancrée verticalement, cette méthode positionne la barre d’outils déroulante sur le côté gauche ou à droite de la barre d’outils parent, en fonction de l’adéquation. Sinon, cette méthode positionne la barre d’outils déroulante sous la barre d’outils parente.

Cette méthode échoue si *pwnd* a la valeur null et que le bouton déroulant de la barre d’outils n’a pas de fenêtre parente.

##  <a name="exporttomenubutton"></a>  CMFCDropDownToolbarButton::ExportToMenuButton

Copie le texte du bouton de barre d’outils dans un menu.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Paramètres

*menuButton*<br/>
dans Référence au bouton de menu cible.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode appelle l’implémentation de la classe de base ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)), puis ajoute au bouton de menu cible un menu contextuel qui contient chaque élément de menu de la barre d’outils dans ce bouton. Cette méthode n’ajoute pas de sous-menus au menu contextuel.

Cette méthode échoue si la barre d’outils `m_pToolBar`parente,, a la valeur null ou si l’implémentation de la classe de base retourne false.

##  <a name="getdropdowntoolbar"></a>  CMFCDropDownToolbarButton::GetDropDownToolBar

Récupère la barre d’outils déroulante associée au bouton.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>Valeur de retour

Barre d’outils déroulante associée au bouton.

### <a name="remarks"></a>Notes

Cette méthode retourne le `m_pToolBar` membre de données.

##  <a name="isdropdown"></a>  CMFCDropDownToolbarButton::IsDropDown

Détermine si la barre d’outils déroulante est actuellement ouverte.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la barre d’outils déroulante est actuellement ouverte; Sinon, 0.

### <a name="remarks"></a>Notes

Le Framework ouvre la barre d’outils déroulante à l’aide de la méthode [CMFCDropDownToolbarButton::D ropdowntoolbar](#dropdowntoolbar) . L’infrastructure ferme la barre d’outils déroulante quand l’utilisateur appuie sur le bouton gauche de la souris dans la zone non cliente de la barre d’outils déroulante.

##  <a name="isextrasize"></a>  CMFCDropDownToolbarButton::IsExtraSize

Détermine si le bouton peut être affiché avec une bordure étendue.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le bouton de barre d’outils peut être affiché avec une bordure étendue; Sinon, 0.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les bordures étendues, consultez [CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).

##  <a name="m_uishowbardelay"></a>  CMFCDropDownToolbarButton::m_uiShowBarDelay

Spécifie la durée pendant laquelle un utilisateur doit maintenir le bouton de la souris enfoncé avant que la barre d’outils déroulante ne s’affiche.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Notes

Le délai est mesuré en millisecondes. La valeur par défaut est de 500 ms. Vous pouvez définir un autre délai en modifiant la valeur de ce membre de données partagées.

##  <a name="oncalculatesize"></a>  CMFCDropDownToolbarButton::OnCalculateSize

Appelé par l’infrastructure pour calculer la taille du bouton pour le contexte de périphérique et l’état d’ancrage spécifiés.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Contexte de périphérique qui affiche le bouton.

*sizeDefault*<br/>
dans Taille par défaut du bouton.

*bHorz*<br/>
dans État d’ancrage de la barre d’outils parente. Ce paramètre a la valeur TRUE si la barre d’outils est ancrée horizontalement ou est flottante, ou FALSe si la barre d’outils est ancrée verticalement.

### <a name="return-value"></a>Valeur de retour

`SIZE` Structure qui contient les dimensions du bouton, en pixels.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) en ajoutant la largeur de la flèche déroulante à la dimension horizontale de la taille du bouton.

##  <a name="onchangeparentwnd"></a>  CMFCDropDownToolbarButton::OnChangeParentWnd

Appelée par l’infrastructure quand le bouton est inséré dans une nouvelle barre d’outils.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Nouvelle fenêtre parente.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de la classe de base ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) en effaçant l’étiquette de texte ( [CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) et en définissant les [CMFCToolBarButton:: m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) et [CMFCToolBarButton :: m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) données membres de la valeur false.

##  <a name="onclick"></a>  CMFCDropDownToolbarButton::OnClick

Appelée par l’infrastructure quand l’utilisateur clique sur le bouton de la souris.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
dans Fenêtre parente du bouton de barre d’outils.

*bDelay*<br/>
dans TRUE si le message doit être traité avec un délai.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le bouton traite le message Click; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base, [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), en mettant à jour l’état de la barre d’outils déroulante.

Quand un utilisateur clique sur le bouton de barre d’outils, cette méthode crée une minuterie qui attend la durée spécifiée par le membre de données [CMFCDropDownToolbarButton:: m_uiShowBarDelay](#m_uishowbardelay) , puis ouvre la barre d’outils déroulante à l’aide de [CMFCDropDownToolbarButton ::D méthode ropDownToolbar](#dropdowntoolbar) . Cette méthode ferme la barre d’outils déroulante la deuxième fois que l’utilisateur clique sur le bouton de barre d’outils.

##  <a name="onclickup"></a>  CMFCDropDownToolbarButton::OnClickUp

Appelée par l’infrastructure quand l’utilisateur relâche le bouton de la souris.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le bouton traite le message Click; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base, [CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), en mettant à jour l’état de la barre d’outils déroulante.

Cette méthode arrête le minuteur de barre d’outils déroulante s’il est actif. Elle ferme la barre d’outils déroulante si elle est ouverte.

Pour plus d’informations sur la barre d’outils déroulante et le minuteur de barre d’outils déroulante, consultez [CMFCDropDownToolbarButton:: OnClick](#onclick).

##  <a name="oncontexthelp"></a>  CMFCDropDownToolbarButton::OnContextHelp

Appelée par l’infrastructure lorsque la barre d’outils parente gère un message WM_HELPHITTEST.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
dans Fenêtre parente du bouton de barre d’outils.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le bouton traite le message d’aide; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) en appelant la méthode [CMFCDropDownToolbarButton:: OnClick](#onclick) avec *bDelay* défini sur false. Cette méthode retourne la valeur retournée par [CMFCDropDownToolbarButton:: OnClick](#onclick).

Pour plus d’informations sur le message WM_HELPHITTEST, [consultez TN028: Prise en charge](../../mfc/tn028-context-sensitive-help-support.md)de l’aide contextuelle.

##  <a name="oncustomizemenu"></a>  CMFCDropDownToolbarButton::OnCustomizeMenu

Modifie le menu fourni lorsque l’application affiche un menu contextuel dans la barre d’outils parente.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Paramètres

*pMenu*<br/>
dans Menu à personnaliser.

### <a name="return-value"></a>Valeur de retour

Cette méthode retourne TRUE.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) en désactivant les éléments de menu suivants:

- **Copier l’image du bouton**

- **Apparence du bouton**

- **Image**

- **Text**

- **Image et texte**

Substituez cette méthode pour modifier le menu contextuel que l’infrastructure affiche en mode de personnalisation.

##  <a name="ondraw"></a>  CMFCDropDownToolbarButton::OnDraw

Appelé par l’infrastructure pour dessiner le bouton à l’aide des styles et options spécifiés.

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
dans Contexte de périphérique qui affiche le bouton.

*rect*<br/>
dans Rectangle englobant du bouton.

*pImages*<br/>
dans Collection d’images de barre d’outils qui est associée au bouton.

*bHorz*<br/>
dans État d’ancrage de la barre d’outils parente. Ce paramètre a la valeur TRUE lorsque le bouton est ancré horizontalement et FALSe lorsque le bouton est ancré verticalement.

*bCustomizeMode*<br/>
dans Spécifie si la barre d’outils est en mode de personnalisation. Ce paramètre a la valeur TRUE lorsque la barre d’outils est en mode de personnalisation et FALSe lorsque la barre d’outils n’est pas en mode de personnalisation.

*bHighlight*<br/>
dans Spécifie si le bouton est mis en surbrillance. Ce paramètre a la valeur TRUE lorsque le bouton est mis en surbrillance et FALSe lorsque le bouton n’est pas mis en surbrillance.

*bDrawBorder*<br/>
dans Spécifie si le bouton doit afficher sa bordure. Ce paramètre a la valeur TRUE lorsque le bouton doit afficher sa bordure et FALSe lorsque le bouton ne doit pas afficher sa bordure.

*bGrayDisabledButtons*<br/>
dans Spécifie s’il faut ombrer les boutons désactivés ou utiliser la collection d’images désactivées. Ce paramètre a la valeur TRUE lorsque les boutons désactivés doivent être grisés et FALSe lorsque cette méthode doit utiliser la collection d’images désactivées.

### <a name="remarks"></a>Notes

Substituez cette méthode pour personnaliser le dessin du bouton de barre d’outils.

##  <a name="ondrawoncustomizelist"></a>  CMFCDropDownToolbarButton::OnDrawOnCustomizeList

Appelée par l’infrastructure pour dessiner le bouton dans le volet **commandes** de la boîte de dialogue **personnaliser** .

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Contexte de périphérique qui affiche le bouton.

*rect*<br/>
dans Rectangle englobant du bouton.

*bSelected*<br/>
dans Indique si le bouton est sélectionné. Si ce paramètre a la valeur TRUE, le bouton est sélectionné. Si ce paramètre a la valeur FALSe, le bouton n’est pas sélectionné.

### <a name="return-value"></a>Valeur de retour

Largeur, en pixels, du bouton sur le contexte de périphérique spécifié.

### <a name="remarks"></a>Notes

Cette méthode est appelée par la boîte de dialogue de personnalisation (onglet **commandes** ) lorsque le bouton doit s’afficher dans la zone de liste owner-draw.

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) en remplaçant l’étiquette de texte du bouton par le nom du bouton (autrement dit, par la valeur du paramètre *lpszName* que vous avez passé au constructeur ).

##  <a name="serialize"></a>  CMFCDropDownToolbarButton::Serialize

Lit cet objet à partir d’une archive ou l’écrit dans une archive.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*ar*<br/>
dans `CArchive` Objet à partir duquel ou à sérialiser.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) en SÉRIALISANT l’ID de ressource de la barre d’outils parente. Lors du chargement de l’archive ( [CArchive:: IsLoading](../../mfc/reference/carchive-class.md#isloading) retourne une valeur différente de zéro), cette méthode `m_pToolBar` définit le membre de données sur la barre d’outils qui contient l’ID de ressource sérialisée.

##  <a name="setdefaultcommand"></a>  CMFCDropDownToolbarButton::SetDefaultCommand

Définit la commande par défaut utilisée par l’infrastructure lorsqu’un utilisateur clique sur le bouton.

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de la commande par défaut.

### <a name="remarks"></a>Notes

Appelez cette méthode pour spécifier une commande par défaut qui est exécutée par l’infrastructure quand l’utilisateur clique sur le bouton. Un élément avec l’ID de commande spécifié par *uiCmd* doit se trouver dans la barre d’outils déroulante parent.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar, classe](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton, classe](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Procédure pas à pas : Placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
