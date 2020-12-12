---
description: 'En savoir plus sur : classe CMFCToolBarEditBoxButton'
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
ms.openlocfilehash: 1cdf401d7ef6409163334104b20d6ce92940f677
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163897"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton, classe

Bouton de barre d’outils qui contient un contrôle d’édition ( [classe CEdit](../../mfc/reference/cedit-class.md)).

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
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Spécifie si un utilisateur peut étirer le bouton pendant la personnalisation. (Substitue [CMFCToolBarButton :: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarEditBoxButton :: CopyFrom](#copyfrom)|Copie les propriétés d’un autre bouton de barre d’outils sur le bouton actuel. (Substitue [CMFCToolBarButton :: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton :: CreateEdit](#createedit)|Crée un nouveau contrôle d’édition dans le bouton.|
|`CMFCToolBarEditBoxButton::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Récupère le premier `CMFCToolBarEditBoxButton` objet de l’application qui a l’ID de commande spécifié.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Récupère le texte du premier contrôle de barre d’outils de zone d’édition qui a l’ID de commande spécifié.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Récupère l’ID de ressource du menu contextuel associé au bouton.|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Récupère le rectangle englobant de la partie modifiable du bouton modifier la zone d’édition.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton :: GetEditBox](#geteditbox)|Retourne un pointeur vers le contrôle d’édition incorporé dans le bouton.|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Récupère le handle de fenêtre associé au bouton de barre d’outils. (Substitue [CMFCToolBarButton :: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Récupère la zone de la zone cliente du bouton qui doit être redessinée. (Substitue [CMFCToolBarButton :: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|
|`CMFCToolBarEditBoxButton::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Détermine si une bordure du bouton s’affiche lorsqu’un utilisateur clique sur le bouton. (Substitue [CMFCToolBarButton :: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Détermine si les boutons de zone d’édition ont un style en deux dimensions.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Spécifie si le bouton traite le message de [WM_COMMAND](/windows/win32/menurc/wm-command) . (Substitue [CMFCToolBarButton :: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Appelée par l’infrastructure quand le bouton est ajouté à une boîte de dialogue **personnaliser** . (Substitue [CMFCToolBarButton :: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Appelé par l’infrastructure pour calculer la taille du bouton pour le contexte de périphérique et l’état d’ancrage spécifiés. (Substitue [CMFCToolBarButton :: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Appelée par l’infrastructure quand le bouton est inséré dans une nouvelle barre d’outils. (Substitue [CMFCToolBarButton :: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarEditBoxButton :: OnClick](#onclick)|Appelée par l’infrastructure quand l’utilisateur clique sur le bouton de la souris. (Substitue [CMFCToolBarButton :: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Appelé par le Framework lorsque la barre d’outils parente gère un message de WM_CTLCOLOR. (Substitue [CMFCToolBarButton :: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarEditBoxButton::OnDraw`|Appelé par l’infrastructure pour dessiner le bouton à l’aide des styles et options spécifiés. (Substitue [CMFCToolBarButton :: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Appelée par l’infrastructure pour dessiner le bouton dans le volet **commandes** de la boîte de dialogue **personnaliser** . (Substitue [CMFCToolBarButton :: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Appelé par le Framework lorsque la police globale a changé. (Substitue [CMFCToolBarButton :: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Appelé par le Framework lorsque la barre d’outils parente se déplace. (Substitue [CMFCToolBarButton :: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarEditBoxButton :: OnShow](#onshow)|Appelé par le Framework lorsque le bouton devient visible ou invisible. (Substitue [CMFCToolBarButton :: onshow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|[CMFCToolBarEditBoxButton :: OnSize](#onsize)|Appelé par l’infrastructure quand la barre d’outils parente modifie sa taille ou sa position et que cette modification entraîne la modification de la taille du bouton. (Substitue [CMFCToolBarButton :: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Appelé par le Framework lorsque la barre d’outils parente met à jour son texte d’info-bulle. (Substitue [CMFCToolBarButton :: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarEditBoxButton::Serialize`|Lit cet objet à partir d’une archive ou l’écrit dans une archive. (Substitue [CMFCToolBarButton :: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarEditBoxButton::SetACCData`|Remplit l’objet fourni `CAccessibilityData` avec les données d’accessibilité à partir du bouton de barre d’outils. (Substitue [CMFCToolBarButton :: SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton :: SetContents](#setcontents)|Définit le texte dans le contrôle d’édition du bouton.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton :: SetContentsAll](#setcontentsall)|Recherche le bouton de contrôle d’édition qui possède un ID de commande spécifié et définit le texte dans le contrôle d’édition de ce bouton.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Spécifie l’ID de ressource du menu contextuel associé au bouton.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Spécifie l’apparence à deux dimensions (Flat) des boutons de zone d’édition dans l’application.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton :: SetStyle](#setstyle)|Spécifie le style du bouton. (Substitue [CMFCToolBarButton :: SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|

## <a name="remarks"></a>Notes

Pour ajouter un bouton de zone d’édition à une barre d’outils, procédez comme suit :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.

2. Construisez un `CMFCToolBarEditBoxButton` objet.

3. Dans le gestionnaire de messages qui traite le message AFX_WM_RESETTOOLBAR, remplacez le bouton factice par le nouveau bouton de zone de liste déroulante à l’aide de [CMFCToolBar :: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Pour plus d’informations, consultez [procédure pas à pas : ajout de contrôles aux barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCToolBarEditBoxButton` . L’exemple montre comment spécifier qu’un utilisateur peut étirer le bouton pendant la personnalisation, spécifier qu’une bordure du bouton s’affiche lorsqu’un utilisateur clique sur le bouton, définir le texte dans le contrôle zone de texte, spécifier l’apparence à deux dimensions (Flat) des boutons de zone d’édition dans l’application et spécifier le style d’un contrôle zone d’édition de barre d’outils.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtoolbareditboxbutton. h

## <a name="cmfctoolbareditboxbuttoncanbestretched"></a><a name="canbestretched"></a> CMFCToolBarEditBoxButton::CanBeStretched

Spécifie si un utilisateur peut étirer le bouton pendant la personnalisation.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valeur renvoyée

Cette méthode retourne TRUE.

### <a name="remarks"></a>Notes

Par défaut, l’infrastructure ne permet pas à l’utilisateur d’étirer un bouton de barre d’outils pendant la personnalisation. Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton :: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) en permettant à l’utilisateur d’étirer un bouton de barre d’outils de zone d’édition pendant la personnalisation.

## <a name="cmfctoolbareditboxbuttoncmfctoolbareditboxbutton"></a><a name="cmfctoolbareditboxbutton"></a> CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

Construit un objet [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) .

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
dans Spécifie l’ID du contrôle.

*iImage*<br/>
dans Spécifie l’index de base zéro d’une image de barre d’outils. L’image se trouve dans l’objet de [classe CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) géré par la classe de [classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) .

*dwStyle*<br/>
dans Spécifie le style du contrôle d’édition.

*iWidth*<br/>
dans Spécifie la largeur en pixels du contrôle d’édition.

### <a name="remarks"></a>Notes

Le constructeur par défaut définit le style du contrôle de modification sur la combinaison suivante :

WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL

La largeur par défaut du contrôle est de 150 pixels.

## <a name="cmfctoolbareditboxbuttoncopyfrom"></a><a name="copyfrom"></a> CMFCToolBarEditBoxButton :: CopyFrom

Copie les propriétés d’un autre bouton de barre d’outils sur le bouton actuel.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
dans Référence au bouton source à partir duquel effectuer la copie.

### <a name="remarks"></a>Notes

Appelez cette méthode pour copier un autre bouton de barre d’outils sur ce bouton de barre d’outils. *src* doit être de type `CMFCToolBarEditBoxButton` .

## <a name="cmfctoolbareditboxbuttoncreateedit"></a><a name="createedit"></a> CMFCToolBarEditBoxButton::CreateEdit

Crée un nouveau contrôle d’édition dans le bouton.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Spécifie la fenêtre parente du contrôle d’édition. Il ne doit pas être NULL.

*rectangulaire*<br/>
dans Spécifie la taille et la position du contrôle d’édition.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le contrôle d’édition nouvellement créé ; la valeur est NULL si la création et la pièce jointe du contrôle échouent.

### <a name="remarks"></a>Notes

Vous construisez un `CMFCToolBarEditBoxButton` objet en deux étapes. Appelez d’abord le constructeur, puis appelez `CreateEdit` , qui crée le contrôle d’édition Windows et l’attache à l' `CMFCToolBarEditBoxButton` objet.

## <a name="cmfctoolbareditboxbuttongetbycmd"></a><a name="getbycmd"></a> CMFCToolBarEditBoxButton::GetByCmd

Récupère le premier `CMFCToolBarEditBoxButton` objet de l’application qui a l’ID de commande spécifié.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de commande du bouton à récupérer.

### <a name="return-value"></a>Valeur renvoyée

Premier `CMFCToolBarEditBoxButton` objet de l’application qui a l’ID de commande spécifié, ou null si aucun objet de ce type n’existe.

### <a name="remarks"></a>Notes

Cette méthode utilitaire partagée est utilisée par les méthodes telles que [CMFCToolBarEditBoxButton :: SetContentsAll](#setcontentsall) et [CMFCToolBarEditBoxButton :: GetContentsAll](#getcontentsall) pour définir ou recevoir le texte du premier contrôle de barre d’outils de zone d’édition avec l’ID de commande spécifié.

## <a name="cmfctoolbareditboxbuttongetcontentsall"></a><a name="getcontentsall"></a> CMFCToolBarEditBoxButton::GetContentsAll

Récupère le texte du premier contrôle de barre d’outils de zone d’édition qui a l’ID de commande spécifié.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de commande du bouton à partir duquel récupérer le contenu.

### <a name="return-value"></a>Valeur renvoyée

`CString`Objet qui contient le texte du premier contrôle de barre d’outils de zone d’édition avec l’ID de commande spécifié.

### <a name="remarks"></a>Notes

Cette méthode retourne la chaîne vide si aucun `CMFCToolBarEditBoxButton` objet n’a l’ID de commande spécifié.

## <a name="cmfctoolbareditboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a> CMFCToolBarEditBoxButton::GetContextMenuID

Récupère l’ID de ressource du menu contextuel associé au bouton.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Valeur renvoyée

L’ID de ressource du menu contextuel associé au bouton ou 0 si le bouton n’est pas associé à un menu contextuel.

### <a name="remarks"></a>Notes

L’infrastructure utilise l’ID de ressource pour créer le menu contextuel quand l’utilisateur clique avec le bouton droit sur le bouton.

## <a name="cmfctoolbareditboxbuttongeteditborder"></a><a name="geteditborder"></a> CMFCToolBarEditBoxButton::GetEditBorder

Récupère le rectangle englobant de la partie modifiable du bouton modifier la zone d’édition.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>Paramètres

*rectBorder*<br/>
à Référence à l' `CRect` objet qui reçoit le rectangle englobant.

### <a name="remarks"></a>Notes

Cette méthode récupère le rectangle englobant du contrôle d’édition dans les coordonnées clientes. Il étend la taille du rectangle dans chaque direction d’un pixel.

La méthode [CMFCVisualManager :: OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) appelle cette méthode lorsqu’elle dessine la bordure autour d’un `CMFCToolBarEditBoxButton` objet.

## <a name="cmfctoolbareditboxbuttongeteditbox"></a><a name="geteditbox"></a> CMFCToolBarEditBoxButton::GetEditBox

Retourne un pointeur vers le contrôle de [classe CEdit](../../mfc/reference/cedit-class.md) incorporé dans le bouton.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le contrôle de [classe CEdit](../../mfc/reference/cedit-class.md) contenu dans le bouton. La valeur est NULL si le `CEdit` contrôle n’a pas encore été créé.

### <a name="remarks"></a>Notes

Vous créez le `CEdit` contrôle en appelant [CMFCToolBarEditBoxButton :: CreateEdit](#createedit).

## <a name="cmfctoolbareditboxbuttongethwnd"></a><a name="gethwnd"></a> CMFCToolBarEditBoxButton::GetHwnd

Récupère le handle de fenêtre associé au bouton de barre d’outils.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valeur renvoyée

Handle de fenêtre associé au bouton.

### <a name="remarks"></a>Notes

Cette méthode remplace la méthode [CMFCToolBarButton :: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) en retournant le handle de fenêtre de la partie du contrôle d’édition du bouton de zone d’édition.

## <a name="cmfctoolbareditboxbuttongetinvalidaterect"></a><a name="getinvalidaterect"></a> CMFCToolBarEditBoxButton::GetInvalidateRect

Récupère la zone de la zone cliente du bouton qui doit être redessinée.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>Valeur renvoyée

`CRect`Objet qui spécifie la région qui doit être redessinée.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base, [CMFCToolBarButton :: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), en incluant dans la zone la zone de l’étiquette de texte.

## <a name="cmfctoolbareditboxbuttonhavehotborder"></a><a name="havehotborder"></a> CMFCToolBarEditBoxButton::HaveHotBorder

Détermine si une bordure du bouton s’affiche lorsqu’un utilisateur clique sur le bouton.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si un bouton affiche sa bordure lorsqu’il est sélectionné ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base, [CMFCToolBarButton :: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), en retournant une valeur différente de zéro si le contrôle est visible.

## <a name="cmfctoolbareditboxbuttonisflatmode"></a><a name="isflatmode"></a> CMFCToolBarEditBoxButton::IsFlatMode

Détermine si les boutons de zone d’édition ont un style en deux dimensions.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si les boutons ont un style à deux dimensions ; Sinon, 0.

### <a name="remarks"></a>Notes

Par défaut, les boutons de zone d’édition ont un style à deux dimensions. Utilisez la méthode [CMFCToolBarEditBoxButton :: SetFlatMode](#setflatmode) pour modifier l’apparence à deux dimensions de style pour votre application.

## <a name="cmfctoolbareditboxbuttonnotifycommand"></a><a name="notifycommand"></a> CMFCToolBarEditBoxButton::NotifyCommand

Spécifie si le bouton traite le message de [WM_COMMAND](/windows/win32/menurc/wm-command) .

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Paramètres

*iNotifyCode*<br/>
dans Message de notification associé à la commande.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le bouton traite le message WM_COMMAND, ou FALSe pour indiquer que le message doit être géré par la barre d’outils parente.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode lorsqu’il est sur le paragraphe d’envoyer un message [WM_COMMAND](/windows/win32/menurc/wm-command) à la fenêtre parente.

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton :: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) en traitant la notification [EN_UPDATE](/windows/win32/Controls/en-update) . Pour chaque zone d’édition avec le même ID de commande que cet objet, elle définit son étiquette de texte sur l’étiquette de texte de cet objet.

## <a name="cmfctoolbareditboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a> CMFCToolBarEditBoxButton::OnAddToCustomizePage

Appelée par l’infrastructure quand le bouton est ajouté à une boîte de dialogue **personnaliser** .

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton :: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) en copiant les propriétés du contrôle zone d’édition dans toutes les barres d’outils qui ont le même ID de commande que cet objet. Cette méthode ne fait rien si aucune barre d’outils n’a de contrôle de zone d’édition ayant le même ID de commande que cet objet.

Pour plus d’informations sur la boîte de dialogue **personnaliser** , consultez [CMFCToolBarsCustomizeDialog, classe](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

## <a name="cmfctoolbareditboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a> CMFCToolBarEditBoxButton::OnChangeParentWnd

Appelée par l’infrastructure quand le bouton est inséré dans une nouvelle barre d’outils.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Pointeur vers la nouvelle fenêtre parente.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de la classe de base ( [CMFCToolBarButton :: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) en recréant l' `CEdit` objet interne.

## <a name="cmfctoolbareditboxbuttononclick"></a><a name="onclick"></a> CMFCToolBarEditBoxButton :: OnClick

Appelée par l’infrastructure quand l’utilisateur clique sur le bouton de la souris.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
[in] Inutilisé.

*bDelay*<br/>
[in] Inutilisé.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le bouton traite le message Click ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de la classe de base ( [CMFCToolBarButton :: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) en retournant une valeur différente de zéro si l' `CEdit` objet interne est visible.

## <a name="cmfctoolbareditboxbuttononctlcolor"></a><a name="onctlcolor"></a> CMFCToolBarEditBoxButton::OnCtlColor

Appelé par le Framework lorsque la barre d’outils parente gère un message de WM_CTLCOLOR.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Contexte de périphérique qui affiche le bouton.

*nCtlColor*<br/>
[in] Inutilisé.

### <a name="return-value"></a>Valeur renvoyée

Handle du pinceau de fenêtre Global.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de la classe de base ( [CMFCToolBarButton :: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) en affectant respectivement aux couleurs de texte et d’arrière-plan du contexte de périphérique fourni le texte global et les couleurs d’arrière-plan.

Pour plus d’informations sur les options globales disponibles pour votre application, consultez [AFX_GLOBAL_DATA structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbareditboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a> CMFCToolBarEditBoxButton::OnGlobalFontsChanged

Appelé par le Framework lorsque la police globale a changé.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton :: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) en remplaçant la police du contrôle par celle de la police globale.

Pour plus d’informations sur les options globales disponibles pour votre application, consultez [AFX_GLOBAL_DATA structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbareditboxbuttononmove"></a><a name="onmove"></a> CMFCToolBarEditBoxButton::OnMove

Appelé par le Framework lorsque la barre d’outils parente se déplace.

```
virtual void OnMove();
```

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de classe par défaut ( [CMFCToolBarButton :: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) en mettant à jour la position de l' `CEdit` objet interne.

## <a name="cmfctoolbareditboxbuttononshow"></a><a name="onshow"></a> CMFCToolBarEditBoxButton :: OnShow

Appelé par le Framework lorsque le bouton devient visible ou invisible.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
dans Spécifie si le bouton est visible. Si ce paramètre a la valeur TRUE, le bouton est visible. Dans le cas contraire, le bouton n’est pas visible.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton :: onshow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) en affichant le bouton si *bShow* a la valeur true. Sinon, cette méthode masque le bouton.

## <a name="cmfctoolbareditboxbuttononsize"></a><a name="onsize"></a> CMFCToolBarEditBoxButton :: OnSize

Appelé par l’infrastructure quand la barre d’outils parente modifie sa taille ou sa position et que cette modification entraîne la modification de la taille du bouton.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Paramètres

*iSize*<br/>
dans Nouvelle largeur du bouton, en pixels.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de classe par défaut, [CMFCToolBarButton :: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), en mettant à jour la taille et la position de l' `CEdit` objet interne.

## <a name="cmfctoolbareditboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a> CMFCToolBarEditBoxButton::OnUpdateToolTip

Appelé par le Framework lorsque la barre d’outils parente met à jour son texte d’info-bulle.

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
dans Contrôle qui affiche le texte d’info-bulle.

*str*<br/>
à `CString` Objet qui reçoit le texte info-bulle mis à jour.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la méthode met à jour le texte de l’info-bulle ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton :: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) en affichant le texte d’info-bulle associé à la partie modifiable du bouton. Si l' `CEdit` objet interne est null ou si le handle de fenêtre de l' `CEdit` objet n’identifie pas une fenêtre existante, cette méthode ne fait rien et retourne false.

## <a name="cmfctoolbareditboxbuttonsetcontents"></a><a name="setcontents"></a> CMFCToolBarEditBoxButton::SetContents

Définit le texte dans le contrôle zone de texte.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>Paramètres

*sContents*<br/>
dans Spécifie le nouveau texte à définir.

## <a name="cmfctoolbareditboxbuttonsetcontentsall"></a><a name="setcontentsall"></a> CMFCToolBarEditBoxButton::SetContentsAll

Recherche un objet [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) qui a un ID de commande spécifié et définit le texte spécifié dans sa zone de texte.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans Spécifie l’ID de commande du contrôle pour lequel le texte sera modifié.

*strContents*<br/>
dans Spécifie le nouveau texte à définir.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le texte a été défini ; 0 si le `CMFCToolBarEditBoxButton` contrôle avec l’ID de commande spécifié n’existe pas.

## <a name="cmfctoolbareditboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a> CMFCToolBarEditBoxButton::SetContextMenuID

Spécifie l’ID de ressource du menu contextuel associé au bouton.

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de ressource du menu contextuel.

### <a name="remarks"></a>Notes

L’infrastructure utilise l’ID de ressource pour créer le menu contextuel quand l’utilisateur clique avec le bouton droit sur le bouton de barre d’outils.

## <a name="cmfctoolbareditboxbuttonsetflatmode"></a><a name="setflatmode"></a> CMFCToolBarEditBoxButton::SetFlatMode

Spécifie l’apparence à deux dimensions (Flat) des boutons de zone d’édition dans l’application.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>Paramètres

*bFlat*<br/>
dans Style à deux dimensions pour les boutons de zone d’édition. Si ce paramètre a la valeur TRUE, l’apparence du style plat est activée ; Sinon, l’apparence du style plat est désactivée.

### <a name="remarks"></a>Notes

Le style à deux dimensions par défaut des boutons de zone d’édition est TRUE. Utilisez la méthode [CMFCToolBarEditBoxButton :: IsFlatMode](#isflatmode) pour récupérer l’apparence à deux dimensions de style pour votre application.

## <a name="cmfctoolbareditboxbuttonsetstyle"></a><a name="setstyle"></a> CMFCToolBarEditBoxButton :: SetStyle

Spécifie le style d’un contrôle zone d’édition de barre d’outils.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
dans Nouveau style à définir.

### <a name="remarks"></a>Notes

Cette méthode définit [CMFCToolBarButton :: m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) sur *nStyle* elle désactive également la zone de texte lorsque l’application est en mode de personnalisation et l’active quand l’application n’est pas en mode de personnalisation (consultez [CMFCToolBar :: SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) et [CMFCToolBar :: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Pour obtenir la liste des indicateurs de style valides, consultez [styles de contrôle de barre d’outils](../../mfc/reference/toolbar-control-styles.md) .

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit, classe](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar :: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Procédure pas à pas : ajout de contrôles aux barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
