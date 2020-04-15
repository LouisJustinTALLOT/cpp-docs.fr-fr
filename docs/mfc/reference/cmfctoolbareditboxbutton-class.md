---
title: CMFCToolBarEditBoxButton, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CanBeStretched
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CopyFrom
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetByCmd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContentsAll
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetEditBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetHwnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetInvalidateRect
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::HaveHotBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::IsFlatMode
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::NotifyCommand
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnAddToCustomizePage
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnChangeParentWnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnClick
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnCtlColor
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnGlobalFontsChanged
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnMove
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnShow
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnSize
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnUpdateToolTip
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarEditBoxButton [MFC], CMFCToolBarEditBoxButton
- CMFCToolBarEditBoxButton [MFC], CanBeStretched
- CMFCToolBarEditBoxButton [MFC], CopyFrom
- CMFCToolBarEditBoxButton [MFC], GetByCmd
- CMFCToolBarEditBoxButton [MFC], GetContentsAll
- CMFCToolBarEditBoxButton [MFC], GetContextMenuID
- CMFCToolBarEditBoxButton [MFC], GetEditBorder
- CMFCToolBarEditBoxButton [MFC], GetHwnd
- CMFCToolBarEditBoxButton [MFC], GetInvalidateRect
- CMFCToolBarEditBoxButton [MFC], HaveHotBorder
- CMFCToolBarEditBoxButton [MFC], IsFlatMode
- CMFCToolBarEditBoxButton [MFC], NotifyCommand
- CMFCToolBarEditBoxButton [MFC], OnAddToCustomizePage
- CMFCToolBarEditBoxButton [MFC], OnChangeParentWnd
- CMFCToolBarEditBoxButton [MFC], OnClick
- CMFCToolBarEditBoxButton [MFC], OnCtlColor
- CMFCToolBarEditBoxButton [MFC], OnGlobalFontsChanged
- CMFCToolBarEditBoxButton [MFC], OnMove
- CMFCToolBarEditBoxButton [MFC], OnShow
- CMFCToolBarEditBoxButton [MFC], OnSize
- CMFCToolBarEditBoxButton [MFC], OnUpdateToolTip
- CMFCToolBarEditBoxButton [MFC], SetContextMenuID
- CMFCToolBarEditBoxButton [MFC], SetFlatMode
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
ms.openlocfilehash: 52989f7b523bf0ba9a00da350242a968ca0db153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360470"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton, classe

Un bouton de barre d’outils qui contient un contrôle de modification ( [Classe CEdit](../../mfc/reference/cedit-class.md)).

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|Construit un objet `CMFCToolBarEditBoxButton`.|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Précise si un utilisateur peut étirer le bouton pendant la personnalisation. (Overrides [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarEditBoxButton::CopyDe](#copyfrom)|Copie les propriétés d’un autre bouton de barre d’outils sur le bouton actuel. (Overrides [CMFCToolBarButton::CopyDe](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::CreateEdit](#createedit)|Crée un nouveau contrôle de modification dans le bouton.|
|`CMFCToolBarEditBoxButton::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Récupère le `CMFCToolBarEditBoxButton` premier objet de l’application qui a l’ID de commande spécifié.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Récupère le texte du premier contrôle de la barre d’outils de la boîte de modification qui a l’ID de commande spécifié.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Récupère l’ID de ressources du menu raccourci associé au bouton.|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Récupère le rectangle de délimitation de la partie d’édition du bouton de la boîte de modification.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Retourne un pointeur au contrôle de modification qui est intégré dans le bouton.|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Récupère la poignée de fenêtre qui est associée au bouton de la barre d’outils. (Overrides [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Récupère la région de la zone cliente du bouton qui doit être redessiné. (Overrides [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|
|`CMFCToolBarEditBoxButton::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Détermine si une bordure du bouton est affichée lorsqu’un utilisateur clique sur le bouton. (Overrides [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Détermine si les boutons de boîte d’édition ont un style plat.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Précise si le bouton traite le [WM_COMMAND](/windows/win32/menurc/wm-command) message. (Overrides [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Appelé par le cadre lorsque le bouton est ajouté à une boîte de dialogue **Personnaliser.** (Overrides [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Appelé par le cadre pour calculer la taille du bouton pour le contexte de l’appareil spécifié et l’état d’amarrage. (Overrides [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Appelé par le cadre lorsque le bouton est inséré dans une nouvelle barre d’outils. (Overrides [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Appelé par le cadre lorsque l’utilisateur clique sur le bouton de la souris. (Overrides [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Appelé par le cadre lorsque le barre d’outils parent gère un message WM_CTLCOLOR. (Overrides [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarEditBoxButton::OnDraw`|Appelé par le cadre pour dessiner le bouton en utilisant les styles spécifiés et les options. (Overrides [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Appelé par le cadre pour dessiner le bouton dans le volet **Commandes** de la boîte de dialogue **Customize.** (Overrides [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Appelé par le cadre lorsque la police mondiale a changé. (Overrides [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Appelé par le cadre lorsque la barre d’outils parent se déplace. (Overrides [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Appelé par le cadre lorsque le bouton devient visible ou invisible. (Overrides [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Appelé par le cadre lorsque la barre d’outils parente change de taille ou de position, ce changement provoque le bouton de changer de taille. (Overrides [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Appelé par le cadre lorsque la barre d’outils parent met à jour son texte tooltip. (Overrides [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarEditBoxButton::Serialize`|Lit cet objet à partir d’une archive ou l’écrit à une archive. (Overrides [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarEditBoxButton::SetACCData`|Remplit l’objet fourni `CAccessibilityData` avec des données d’accessibilité à partir du bouton de la barre d’outils. (Overrides [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContents](#setcontents)|Définit le texte dans le contrôle de modification du bouton.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Trouve le bouton de commande de modification qui a un ID de commande spécifié, et définit le texte dans le contrôle de modification de ce bouton.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Spécifie l’ID de ressources du menu raccourci qui est associé au bouton.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Spécifie l’apparence de style plat des boutons de boîte d’édition dans l’application.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Spécifie le style du bouton. (Overrides [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|

## <a name="remarks"></a>Notes

Pour ajouter un bouton de boîte de modification à une barre d’outils, suivez ces étapes :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.

2. Construire `CMFCToolBarEditBoxButton` un objet.

3. Dans le gestionnaire de message qui traite le message AFX_WM_RESETTOOLBAR, remplacez le bouton factice par le nouveau bouton de boîte combo en utilisant [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Pour plus d’informations, voir [Procédure pas à pas: Mettre des contrôles sur les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCToolBarEditBoxButton` . L’exemple montre comment spécifier qu’un utilisateur peut étirer le bouton pendant la personnalisation, spécifier qu’une bordure du bouton est affichée lorsqu’un utilisateur clique sur le bouton, régle le texte dans le contrôle de la boîte de texte, spécifier l’apparence de style plat des boutons de boîte de modification dans l’application, et spécifier le style d’un contrôle de boîte de modification de la barre d’outils.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>Spécifications

**En-tête:** afxtoolbareditboxbutton.h

## <a name="cmfctoolbareditboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBeStretched

Précise si un utilisateur peut étirer le bouton pendant la personnalisation.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valeur de retour

Cette méthode renvoie TRUE.

### <a name="remarks"></a>Notes

Par défaut, le cadre ne permet pas à l’utilisateur d’étirer un bouton de barre d’outils lors de la personnalisation. Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) en permettant à l’utilisateur d’étirer un bouton de barre d’outils de boîte d’édition pendant la personnalisation.

## <a name="cmfctoolbareditboxbuttoncmfctoolbareditboxbutton"></a><a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

Construit un objet [CMFCToolBarEditBoxButton.](../../mfc/reference/cmfctoolbareditboxbutton-class.md)

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
[dans] Spécifie l’ID de contrôle.

*iImage (en)*<br/>
[dans] Spécifie l’index zéro d’une image de barre d’outils. L’image est située dans l’objet [cmFCToolBarImages Classe](../../mfc/reference/cmfctoolbarimages-class.md) que [cmFCToolBar Classe](../../mfc/reference/cmfctoolbar-class.md) Classe maintient.

*dwStyle (en)*<br/>
[dans] Spécifie le style de contrôle de modification.

*iWidth (en)*<br/>
[dans] Spécifie la largeur des pixels du contrôle de modification.

### <a name="remarks"></a>Notes

Le constructeur par défaut définit le style de commande d’édition à la combinaison suivante :

WS_CHILD WS_VISIBLE ES_AUTOHSCROLL

La largeur par défaut du contrôle est de 150 pixels.

## <a name="cmfctoolbareditboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarEditBoxButton::CopyDe

Copie les propriétés d’un autre bouton de barre d’outils sur le bouton actuel.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[dans] Une référence au bouton source à partir duquel copier.

### <a name="remarks"></a>Notes

Appelez cette méthode pour copier un autre bouton de barre d’outils sur ce bouton de barre d’outils. *src* doit être `CMFCToolBarEditBoxButton`de type .

## <a name="cmfctoolbareditboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarEditBoxButton::CreateEdit

Crée un nouveau contrôle de modification dans le bouton.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] Spécifie la fenêtre parente du contrôle de modification. Ce ne doit pas être NULL.

*Rect*<br/>
[dans] Spécifie la taille et la position du contrôle de modification.

### <a name="return-value"></a>Valeur de retour

Un pointeur pour le contrôle d’édition nouvellement créé; c’est NULL si la création et l’attachement du contrôle échouent.

### <a name="remarks"></a>Notes

Vous construisez un `CMFCToolBarEditBoxButton` objet en deux étapes. Appelez d’abord le constructeur, puis appelez, `CreateEdit`ce qui crée `CMFCToolBarEditBoxButton` le contrôle de modification Windows et le fixe à l’objet.

## <a name="cmfctoolbareditboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd

Récupère le `CMFCToolBarEditBoxButton` premier objet de l’application qui a l’ID de commande spécifié.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’ID de commande du bouton à récupérer.

### <a name="return-value"></a>Valeur de retour

Le `CMFCToolBarEditBoxButton` premier objet de l’application qui a l’ID de commande spécifié, ou NULL si aucun objet de ce genre n’existe.

### <a name="remarks"></a>Notes

Cette méthode d’utilité partagée est utilisée par des méthodes telles que [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall) et [CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall) pour définir ou obtenir le texte de la première boîte de contrôle de la barre d’outils de modification qui a l’ID de commande spécifié.

## <a name="cmfctoolbareditboxbuttongetcontentsall"></a><a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll

Récupère le texte du premier contrôle de la barre d’outils de la boîte de modification qui a l’ID de commande spécifié.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’ID de commande du bouton à partir duquel récupérer le contenu.

### <a name="return-value"></a>Valeur de retour

Un `CString` objet qui contient le texte du premier contrôle de la barre d’outils de la boîte de modification qui a l’ID de commande spécifié.

### <a name="remarks"></a>Notes

Cette méthode renvoie la `CMFCToolBarEditBoxButton` chaîne vide si aucun objet n’a l’ID de commande spécifié.

## <a name="cmfctoolbareditboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetContextMenuID

Récupère l’ID de ressources du menu raccourci associé au bouton.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Valeur de retour

L’ID de ressource du menu raccourci qui est associé au bouton ou 0 si le bouton n’a pas de menu raccourci associé.

### <a name="remarks"></a>Notes

Le cadre utilise l’ID de ressource pour créer le menu raccourci lorsque l’utilisateur clic à droite sur le bouton.

## <a name="cmfctoolbareditboxbuttongeteditborder"></a><a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder

Récupère le rectangle de délimitation de la partie d’édition du bouton de la boîte de modification.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>Paramètres

*rectBorder (rectBorder)*<br/>
[out] Une référence `CRect` à l’objet qui reçoit le rectangle de délimitation.

### <a name="remarks"></a>Notes

Cette méthode récupère le rectangle de délimitation du contrôle d’édition dans les coordonnées des clients. Il augmente la taille du rectangle dans chaque direction d’un pixel.

La [méthode CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) méthode appelle cette méthode `CMFCToolBarEditBoxButton` quand il tire la frontière autour d’un objet.

## <a name="cmfctoolbareditboxbuttongeteditbox"></a><a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox

Retourne un pointeur au contrôle [de la classe CEdit](../../mfc/reference/cedit-class.md) qui est intégré dans le bouton.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur pour le contrôle [de classe CEdit](../../mfc/reference/cedit-class.md) que le bouton contient. C’est NULL `CEdit` si le contrôle n’a pas encore été créé.

### <a name="remarks"></a>Notes

Vous créez `CEdit` le contrôle en appelant [CMFCToolBarEditBoxButton::CreateEdit](#createedit).

## <a name="cmfctoolbareditboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarEditBoxButton::GetHwnd

Récupère la poignée de fenêtre qui est associée au bouton de la barre d’outils.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valeur de retour

La poignée de fenêtre qui est associée au bouton.

### <a name="remarks"></a>Notes

Cette méthode remplace la [méthode CMFCToolBarButton : : Méthode GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) en retournant la poignée de fenêtre de la partie de contrôle de modification du bouton de la boîte d’édition.

## <a name="cmfctoolbareditboxbuttongetinvalidaterect"></a><a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect

Récupère la région de la zone cliente du bouton qui doit être redessiné.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>Valeur de retour

Un `CRect` objet qui spécifie la région qui doit être redessiné.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base, [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), en incluant dans la région la zone de l’étiquette de texte.

## <a name="cmfctoolbareditboxbuttonhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder

Détermine si une bordure du bouton est affichée lorsqu’un utilisateur clique sur le bouton.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si un bouton affiche sa bordure lorsqu’il est sélectionné; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base, [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), en retournant une valeur non zéro si le contrôle est visible.

## <a name="cmfctoolbareditboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarEditBoxButton::IsFlatMode

Détermine si les boutons de boîte d’édition ont un style plat.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si les boutons ont un style plat; autrement, 0.

### <a name="remarks"></a>Notes

Par défaut, les boutons de boîte de modification ont un style plat. Utilisez la méthode [CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode) pour modifier l’apparence de style plat pour votre application.

## <a name="cmfctoolbareditboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand

Précise si le bouton traite le [WM_COMMAND](/windows/win32/menurc/wm-command) message.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Paramètres

*iNotifyCode (en)*<br/>
[dans] Le message de notification associé à la commande.

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton traite le WM_COMMAND message, ou FALSE pour indiquer que le message doit être manipulé par la barre d’outils parent.

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode lorsqu’elle est sur le point d’envoyer un [message WM_COMMAND](/windows/win32/menurc/wm-command) à la fenêtre parente.

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) en traitant la notification [EN_UPDATE.](/windows/win32/Controls/en-update) Pour chaque boîte d’édition avec le même IDENTIFIANT de commande que cet objet, il fixe son étiquette de texte à l’étiquette de texte de cet objet.

## <a name="cmfctoolbareditboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton::OnAddToCustomizePage

Appelé par le cadre lorsque le bouton est ajouté à une boîte de dialogue **Personnaliser.**

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) en copiant les propriétés du contrôle de la boîte d’édition dans n’importe quelle barre d’outils qui a le même ID de commande que cet objet. Cette méthode ne fait rien si aucune barre d’outils n’a un contrôle de boîte de modification qui a le même ID de commande que cet objet.

Pour plus d’informations sur la boîte de dialogue **Customize,** voir [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

## <a name="cmfctoolbareditboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd

Appelé par le cadre lorsque le bouton est inséré dans une nouvelle barre d’outils.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] Un pointeur vers la nouvelle fenêtre parente.

### <a name="remarks"></a>Notes

Cette méthode remplace la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) en recréant l’objet interne. `CEdit`

## <a name="cmfctoolbareditboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarEditBoxButton::OnClick

Appelé par le cadre lorsque l’utilisateur clique sur le bouton de la souris.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
[in] Inutilisé.

*bDelay (en)*<br/>
[in] Inutilisé.

### <a name="return-value"></a>Valeur de retour

Nonzero si le bouton traite le message de clic; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de la classe de base ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) en retournant une valeur non zéro si l’objet interne `CEdit` est visible.

## <a name="cmfctoolbareditboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarEditBoxButton::OnCtlColor

Appelé par le cadre lorsque le barre d’outils parent gère un message WM_CTLCOLOR.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Le contexte de l’appareil qui affiche le bouton.

*nCtlColor (en anglais)*<br/>
[in] Inutilisé.

### <a name="return-value"></a>Valeur de retour

Une poignée à la brosse de fenêtre globale.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de la classe de base ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) en définissant les couleurs de texte et de fond du contexte fourni de l’appareil aux couleurs globales de texte et de fond, respectivement.

Pour plus d’informations sur les options globales qui sont disponibles à votre application, voir [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbareditboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton::OnGlobalFontsChanged

Appelé par le cadre lorsque la police mondiale a changé.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) en changeant la police du contrôle à celle de la police globale.

Pour plus d’informations sur les options globales qui sont disponibles à votre application, voir [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbareditboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarEditBoxButton::OnMove

Appelé par le cadre lorsque la barre d’outils parent se déplace.

```
virtual void OnMove();
```

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de la classe par défaut ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) en mettant à jour la position de l’objet interne `CEdit`

## <a name="cmfctoolbareditboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarEditBoxButton::OnShow

Appelé par le cadre lorsque le bouton devient visible ou invisible.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow (en)*<br/>
[dans] Précise si le bouton est visible. Si ce paramètre est VRAI, le bouton est visible. Sinon, le bouton n’est pas visible.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) en affichant le bouton si *bShow* est VRAI. Sinon, cette méthode cache le bouton.

## <a name="cmfctoolbareditboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarEditBoxButton::OnSize

Appelé par le cadre lorsque la barre d’outils parente change de taille ou de position, ce changement provoque le bouton de changer de taille.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Paramètres

*iSize (en)*<br/>
[dans] La nouvelle largeur du bouton, en pixels.

### <a name="remarks"></a>Notes

Cette méthode remplace la mise en œuvre par défaut de la classe, [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), en mettant à jour la taille et la position de l’objet interne. `CEdit`

## <a name="cmfctoolbareditboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarEditBoxButton::OnUpdateToolTip

Appelé par le cadre lorsque la barre d’outils parent met à jour son texte tooltip.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[in] Inutilisé.

*iButtonIndex*<br/>
[in] Inutilisé.

*wndToolTip*<br/>
[dans] Le contrôle qui affiche le texte de l’outiltip.

*Str*<br/>
[out] Un `CString` objet qui reçoit le texte de pointe d’outil mis à jour.

### <a name="return-value"></a>Valeur de retour

Nonzero si la méthode met à jour le texte tooltip; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) en affichant le texte de pointe d’outil qui est associé à la partie d’édition du bouton. Si l’objet interne `CEdit` est NULL `CEdit` ou si la poignée de fenêtre de l’objet n’identifie pas une fenêtre existante, cette méthode ne fait rien et renvoie FALSE.

## <a name="cmfctoolbareditboxbuttonsetcontents"></a><a name="setcontents"></a>CMFCToolBarEditBoxButton::SetContents

Définit le texte dans le contrôle de la boîte de texte.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>Paramètres

*sContents*<br/>
[dans] Spécifie le nouveau texte à définir.

## <a name="cmfctoolbareditboxbuttonsetcontentsall"></a><a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll

Trouve un objet [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) qui a un ID de commande spécifié et définit le texte spécifié dans sa boîte de texte.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] Spécifie l’ID de commande du contrôle pour lequel le texte sera modifié.

*strContents (en)*<br/>
[dans] Spécifie le nouveau texte à définir.

### <a name="return-value"></a>Valeur de retour

Nonzero si le texte a été défini; 0 si `CMFCToolBarEditBoxButton` le contrôle avec l’ID de commande spécifié n’existe pas.

## <a name="cmfctoolbareditboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetContextMenuID

Spécifie l’ID de ressources du menu raccourci qui est associé au bouton.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’ID de ressource du menu raccourci.

### <a name="remarks"></a>Notes

Le cadre utilise l’ID de ressource pour créer le menu raccourci lorsque l’utilisateur clique à droite sur le bouton de la barre d’outils.

## <a name="cmfctoolbareditboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode

Spécifie l’apparence de style plat des boutons de boîte d’édition dans l’application.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>Paramètres

*bFlat (en)*<br/>
[dans] Le style plat pour modifier les boutons de boîte. Si ce paramètre est VRAI, l’apparence de style plat est activée; sinon l’aspect plat de modèle est désactivé.

### <a name="remarks"></a>Notes

Le style plat par défaut pour modifier les boutons de boîte est VRAI. Utilisez la méthode [CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode) méthode pour récupérer l’apparence de style plat pour votre application.

## <a name="cmfctoolbareditboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarEditBoxButton::SetStyle

Spécifie le style d’une barre d’outils modifier le contrôle de la boîte.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
[dans] Un nouveau style à définir.

### <a name="remarks"></a>Notes

Cette méthode définit [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) à *nStyle* Il désactive également la boîte de texte lorsque l’application est en mode Personnaliser, et le permet lorsque l’application n’est pas en mode Customize (voir [CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) et [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Consultez [ToolBar Control Styles](../../mfc/reference/toolbar-control-styles.md) pour une liste de drapeaux de style valides.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::RemplacerButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Procédure pas à pas : placement de contrôles dans les barres d'outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
