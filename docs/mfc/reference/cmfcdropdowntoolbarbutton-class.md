---
title: Cmfcdropdowntoolbarbutton, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 157bcb8b1b8341e16d7dcb6c3a9d9fc9dc1a4d4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431737"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>Cmfcdropdowntoolbarbutton, classe

Type de bouton de barre d'outils qui se comporte comme un bouton normal lorsque l'utilisateur clique dessus. Toutefois, il ouvre une barre d’outils déroulante ( [CMFCDropDownToolbar, classe](../../mfc/reference/cmfcdropdowntoolbar-class.md) si l’utilisateur appuie sur et maintient le bouton de barre d’outils.

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
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Copie les propriétés d’un autre bouton de barre d’outils pour le bouton en cours. (Substitue [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCDropDownToolbarButton::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Ouvre une barre d’outils de la liste déroulante.|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Copie le texte à partir du bouton de barre d’outils dans un menu. (Substitue [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Récupère la barre d’outils de liste déroulante qui est associée au bouton.|
|`CMFCDropDownToolbarButton::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Détermine si la barre d’outils de la liste déroulante est actuellement ouverte.|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Détermine si le bouton peut être affiché avec une bordure étendue. (Substitue [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Appelé par l’infrastructure pour calculer la taille du bouton pour le contexte de périphérique spécifié et l’état d’ancrage. (Substitue [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|`CMFCDropDownToolbarButton::OnCancelMode`|Appelé par l’infrastructure pour gérer la [WM_CANCELMODE](/windows/desktop/winmsg/wm-cancelmode) message. (Substitue `CMCToolBarButton::OnCancelMode`.)|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Appelé par le framework lorsque le bouton est inséré dans une nouvelle barre d’outils. (Substitue [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Appelé par le framework lorsque l’utilisateur clique sur le bouton de la souris. (Substitue [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Appelé par l’infrastructure lorsque l’utilisateur relâche le bouton de la souris. (Substitue [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Appelé par l’infrastructure lors de la barre d’outils parent gère un message WM_HELPHITTEST. (Substitue [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Modifie le menu fourni lorsque l’application affiche un menu contextuel dans la barre d’outils parent. (Substitue [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Appelé par l’infrastructure pour dessiner le bouton en utilisant les options et les styles spécifiés. (Substitue [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Appelé par l’infrastructure pour dessiner le bouton dans le **commandes** volet de la **personnaliser** boîte de dialogue. (Substitue [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCDropDownToolbarButton::Serialize](#serialize)|Lit de cet objet à partir d’une archive ou écrit dans une archive. (Substitue [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Définit la commande par défaut par le framework lorsqu’un utilisateur clique sur le bouton.|

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Spécifie la durée pendant laquelle un utilisateur doit maintenez le bouton de la souris avant que la barre d’outils de la liste déroulante s’affiche.|

## <a name="remarks"></a>Notes

Un `CMFCDropDownToolBarButton` diffère d’un bouton ordinaire doté d’une petite flèche située dans le coin inférieur droit du bouton. Une fois que l’utilisateur sélectionne un bouton à partir de la barre d’outils de la liste déroulante, l’infrastructure affiche son icône sur le bouton de barre d’outils de niveau supérieur (le bouton avec la flèche située dans le coin inférieur droit).

Pour plus d’informations sur la façon d’implémenter une barre d’outils de la liste déroulante, consultez [CMFCDropDownToolbar, classe](../../mfc/reference/cmfcdropdowntoolbar-class.md).

Le `CMFCDropDownToolBarButton` objet peut être exporté vers un [cmfctoolbarmenubutton, classe](../../mfc/reference/cmfctoolbarmenubutton-class.md) de l’objet et affiché sous la forme d’un bouton de menu avec un menu contextuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdropdowntoolbar.h

##  <a name="copyfrom"></a>  CMFCDropDownToolbarButton::CopyFrom

Copie les propriétés d’un autre bouton de barre d’outils pour le bouton en cours.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[in] Une référence au bouton de la source à partir duquel copier.

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

*Caractère*<br/>
[in] Le texte par défaut du bouton.

*pToolBar*<br/>
[in] Un pointeur vers le `CMFCDropDownToolBar` objet s’affiche lorsque l’utilisateur appuie sur le bouton.

### <a name="remarks"></a>Notes

La deuxième surcharge du constructeur de copie sur le bouton de liste déroulante le premier bouton à partir de la barre d’outils qui *pToolBar* spécifie.

En règle générale, un bouton de barre d’outils déroulante utilise le texte à partir du bouton des derniers fichiers utilisé dans la barre d’outils qui *pToolBar* spécifie. Elle utilise le texte spécifié par *le caractère* lorsque le bouton est converti en un bouton de menu ou s’affiche dans le **commandes** onglet de la **personnaliser** boîte de dialogue. Pour plus d’informations sur la **personnaliser** boîte de dialogue, consultez [cmfctoolbarscustomizedialog, classe](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCDropDownToolbarButton` classe. Cet extrait de code fait partie de la [exemple de démonstration Visual Studio](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

##  <a name="dropdowntoolbar"></a>  CMFCDropDownToolbarButton::DropDownToolbar

Ouvre une barre d’outils de la liste déroulante.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
[in] La fenêtre parente du cadre de la liste déroulante, ou NULL pour utiliser la fenêtre parent du bouton de barre d’outils de la liste déroulante.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode réussit ; sinon 0.

### <a name="remarks"></a>Notes

Le [CMFCDropDownToolbarButton::OnClick](#onclick) méthode appelle cette méthode pour ouvrir la barre d’outils de la liste déroulante lorsque l’utilisateur appuie sur et maintient le bouton de barre d’outils.

Cette méthode crée la barre d’outils de la liste déroulante à l’aide de la [CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create) (méthode). Si la barre d’outils parent est ancré verticalement, cette méthode positionne la barre d’outils déroulante soit sur le côté gauche ou droit de la barre d’outils parent, en fonction de l’ajuster. Sinon, cette méthode positionne la barre d’outils de liste déroulante en dessous de la barre d’outils parent.

Cette méthode échoue si *pWnd* a la valeur NULL et le bouton de barre d’outils de la liste déroulante n’a pas d’une fenêtre parente.

##  <a name="exporttomenubutton"></a>  CMFCDropDownToolbarButton::ExportToMenuButton

Copie le texte à partir du bouton de barre d’outils dans un menu.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Paramètres

*Bouton de menu*<br/>
[in] Une référence au bouton de menu cible.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode appelle l’implémentation de classe de base ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)), puis les ajoute au bouton de menu cible un menu contextuel qui contient chaque élément de menu de barre d’outils de ce bouton. Cette méthode n’ajoute pas les sous-menus au menu contextuel.

Cette méthode échoue si la barre d’outils parent, `m_pToolBar`, a la valeur NULL ou que l’implémentation de classe de base retourne FALSE.

##  <a name="getdropdowntoolbar"></a>  CMFCDropDownToolbarButton::GetDropDownToolBar

Récupère la barre d’outils de liste déroulante qui est associée au bouton.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>Valeur de retour

La barre d’outils de liste déroulante qui est associée au bouton.

### <a name="remarks"></a>Notes

Cette méthode retourne le `m_pToolBar` membre de données.

##  <a name="isdropdown"></a>  CMFCDropDownToolbarButton::IsDropDown

Détermine si la barre d’outils de la liste déroulante est actuellement ouverte.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la barre d’outils de la liste déroulante est actuellement ouvert ; sinon 0.

### <a name="remarks"></a>Notes

L’infrastructure ouvre la barre d’outils de la liste déroulante à l’aide de la [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) (méthode). Le framework ferme la barre d’outils de la liste déroulante lorsque l’utilisateur appuie sur le bouton gauche de la souris dans la zone non cliente de la barre d’outils de la liste déroulante.

##  <a name="isextrasize"></a>  CMFCDropDownToolbarButton::IsExtraSize

Détermine si le bouton peut être affiché avec une bordure étendue.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le bouton de barre d’outils peut être affiché avec une bordure étendue ; sinon 0.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les bordures étendus, consultez [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).

##  <a name="m_uishowbardelay"></a>  CMFCDropDownToolbarButton::m_uiShowBarDelay

Spécifie la durée pendant laquelle un utilisateur doit maintenez le bouton de la souris avant que la barre d’outils de la liste déroulante s’affiche.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Notes

Le délai est mesuré en millisecondes. La valeur par défaut est de 500 ms. Vous pouvez définir un autre délai en modifiant la valeur de ce membre de données partagée.

##  <a name="oncalculatesize"></a>  CMFCDropDownToolbarButton::OnCalculateSize

Appelé par l’infrastructure pour calculer la taille du bouton pour le contexte de périphérique spécifié et l’état d’ancrage.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
[in] Le contexte de périphérique qui affiche le bouton.

*sizeDefault*<br/>
[in] La taille par défaut du bouton.

*bHorz*<br/>
[in] L’état d’ancrage de la barre d’outils parent. Ce paramètre est TRUE si la barre d’outils est ancrée horizontalement ou est flottant, ou FALSE si la barre d’outils est ancrée verticalement.

### <a name="return-value"></a>Valeur de retour

Un `SIZE` structure qui contient les dimensions du bouton, en pixels.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) en ajoutant la largeur de la flèche déroulante à la dimension horizontale de la taille du bouton.

##  <a name="onchangeparentwnd"></a>  CMFCDropDownToolbarButton::OnChangeParentWnd

Appelé par le framework lorsque le bouton est inséré dans une nouvelle barre d’outils.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[in] La nouvelle fenêtre parente.

### <a name="remarks"></a>Notes

Cette méthode substitue l’implémentation de classe de base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) en désactivant l’étiquette de texte ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) et en définissant le [ CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) et [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) sur FALSE, les membres de données.

##  <a name="onclick"></a>  CMFCDropDownToolbarButton::OnClick

Appelé par le framework lorsque l’utilisateur clique sur le bouton de la souris.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
[in] La fenêtre parent du bouton de barre d’outils.

*bDelay*<br/>
[in] TRUE si le message doit être géré avec un délai.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le bouton traite le message de clic ; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base, [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), en mettant à jour l’état de la barre d’outils de la liste déroulante.

Lorsqu’un utilisateur clique sur le bouton de barre d’outils, cette méthode crée un minuteur qui attend le délai spécifié par le [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay) membre de données, puis de barre d’outils s’ouvre la liste déroulante à l’aide de la [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) (méthode). Cette méthode ferme la barre d’outils de la liste déroulante de la deuxième fois que l’utilisateur clique sur le bouton de barre d’outils.

##  <a name="onclickup"></a>  CMFCDropDownToolbarButton::OnClickUp

Appelé par l’infrastructure lorsque l’utilisateur relâche le bouton de la souris.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le bouton traite le message de clic ; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base, [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), en mettant à jour l’état de la barre d’outils de la liste déroulante.

Cette méthode arrête le minuteur de la barre d’outils de la liste déroulante si elle est active. Il ferme la barre d’outils de la liste déroulante si elle est ouverte.

Pour plus d’informations sur la barre d’outils de la liste déroulante et le minuteur de la barre d’outils de la liste déroulante, consultez [CMFCDropDownToolbarButton::OnClick](#onclick).

##  <a name="oncontexthelp"></a>  CMFCDropDownToolbarButton::OnContextHelp

Appelé par l’infrastructure lors de la barre d’outils parent gère un message WM_HELPHITTEST.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
[in] La fenêtre parent du bouton de barre d’outils.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le bouton traite le message d’aide ; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) en appelant le [CMFCDropDownToolbarButton::OnClick](#onclick) méthode avec *bDelay*défini sur FALSE. Cette méthode retourne la valeur retournée par [CMFCDropDownToolbarButton::OnClick](#onclick).

Pour plus d’informations sur le message WM_HELPHITTEST, consultez [TN028 : prise en charge d’aide contextuelle](../../mfc/tn028-context-sensitive-help-support.md).

##  <a name="oncustomizemenu"></a>  CMFCDropDownToolbarButton::OnCustomizeMenu

Modifie le menu fourni lorsque l’application affiche un menu contextuel dans la barre d’outils parent.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Paramètres

*pMenu*<br/>
[in] Menu Personnaliser.

### <a name="return-value"></a>Valeur de retour

Cette méthode retourne la valeur TRUE.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) en désactivant les éléments suivants :

- **Copier l’Image du bouton**

- **Apparence du bouton**

- **Image**

- **Text**

- **Image et texte**

Substituez cette méthode pour modifier le menu contextuel affichée par l’infrastructure dans le mode de personnalisation.

##  <a name="ondraw"></a>  CMFCDropDownToolbarButton::OnDraw

Appelé par l’infrastructure pour dessiner le bouton en utilisant les options et les styles spécifiés.

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

*contrôleur de domaine principal*<br/>
[in] Le contexte de périphérique qui affiche le bouton.

*Rect*<br/>
[in] Le rectangle englobant du bouton.

*pImages*<br/>
[in] La collection d’images de barre d’outils qui est associée au bouton.

*bHorz*<br/>
[in] L’état d’ancrage de la barre d’outils parent. Ce paramètre a la valeur TRUE lorsque le bouton est ancré horizontalement et FALSE lorsque le bouton est ancré verticalement.

*bCustomizeMode*<br/>
[in] Spécifie si la barre d’outils est en mode de personnalisation. Ce paramètre a la valeur TRUE lorsque la barre d’outils est en mode de personnalisation et FALSE lorsque la barre d’outils n’est pas en mode de personnalisation.

*bHighlight*<br/>
[in] Spécifie si le bouton est mis en surbrillance. Ce paramètre est la valeur TRUE lorsque le bouton est mis en surbrillance et FALSE lorsque le bouton n’est pas mis en surbrillance.

*bDrawBorder*<br/>
[in] Spécifie si le bouton doit afficher sa bordure. Ce paramètre a la valeur TRUE lorsque le bouton doit afficher sa bordure et la valeur FALSE lorsque le bouton ne doit pas afficher sa bordure.

*bGrayDisabledButtons*<br/>
[in] Spécifie s’il faut ombrer les boutons désactivés ou utiliser la collection d’images désactivé. Ce paramètre a la valeur TRUE lorsque les boutons désactivés doivent être grisée et FALSE lorsque cette méthode doit utiliser la collection d’images désactivé.

### <a name="remarks"></a>Notes

Substituez cette méthode pour personnaliser le dessin de bouton de barre d’outils.

##  <a name="ondrawoncustomizelist"></a>  CMFCDropDownToolbarButton::OnDrawOnCustomizeList

Appelé par l’infrastructure pour dessiner le bouton dans le **commandes** volet de la **personnaliser** boîte de dialogue.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
[in] Le contexte de périphérique qui affiche le bouton.

*Rect*<br/>
[in] Le rectangle englobant du bouton.

*bSelected*<br/>
[in] Indique si le bouton est sélectionné. Si ce paramètre est TRUE, le bouton est sélectionné. Si ce paramètre est FALSE, le bouton n’est pas sélectionné.

### <a name="return-value"></a>Valeur de retour

La largeur, en pixels, du bouton sur le contexte de périphérique spécifié.

### <a name="remarks"></a>Notes

Cette méthode est appelée par la boîte de dialogue de personnalisation ( **commandes** onglet) lorsque le bouton doit s’afficher sur la zone de liste owner-draw.

Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) en modifiant l’étiquette de texte du bouton sur le nom du bouton (autrement dit, la valeur de la *le caractère* paramètre que vous avez passé au constructeur).

##  <a name="serialize"></a>  CMFCDropDownToolbarButton::Serialize

Lit de cet objet à partir d’une archive ou écrit dans une archive.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*ar*<br/>
[in] Le `CArchive` objet à partir duquel ou de sérialisation.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) en sérialisant l’ID de ressource de la barre d’outils parent. Lorsque l’archive est cours de chargement ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) retourne une valeur différente de zéro), cette méthode définit le `m_pToolBar` données membres à la barre d’outils qui contient l’ID de ressource sérialisée.

##  <a name="setdefaultcommand"></a>  CMFCDropDownToolbarButton::SetDefaultCommand

Définit la commande par défaut par le framework lorsqu’un utilisateur clique sur le bouton.

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
[in] ID de la commande par défaut.

### <a name="remarks"></a>Notes

Appelez cette méthode pour spécifier une commande par défaut exécutée par l’infrastructure lorsque l’utilisateur clique sur le bouton. Un élément avec l’ID de commande spécifié par *uiCmd* doit se trouver dans la barre d’outils de la liste déroulante parent.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar, classe](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton, classe](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Procédure pas à pas : placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)



