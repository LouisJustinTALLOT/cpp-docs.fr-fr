---
title: Cmfctoolbareditboxbutton, classe
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
ms.openlocfilehash: ac07ff4e6bf97518e2c659a9d6df9bd721b6b806
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291611"
---
# <a name="cmfctoolbareditboxbutton-class"></a>Cmfctoolbareditboxbutton, classe

Un bouton de barre d’outils qui contient un contrôle d’édition ( [classe CEdit](../../mfc/reference/cedit-class.md)).

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
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Spécifie si un utilisateur permet d’étendre le bouton au cours de personnalisation. (Substitue [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Copie les propriétés d’un autre bouton de barre d’outils pour le bouton en cours. (Substitue [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::CreateEdit](#createedit)|Crée un nouveau contrôle d’édition dans le bouton.|
|`CMFCToolBarEditBoxButton::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Récupère le premier `CMFCToolBarEditBoxButton` objet dans l’application qui possède l’ID de commande spécifiée.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Récupère le texte du premier contrôle de barre d’outils de la zone Modifier ayant l’ID de commande spécifiée.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Récupère l’ID de ressource du menu contextuel qui est associé au bouton.|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Récupère le rectangle englobant de la partie de modifier l’édition du bouton de zone.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Retourne un pointeur vers le contrôle d’édition qui est incorporé dans le bouton.|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Récupère le handle de fenêtre qui est associé au bouton de barre d’outils. (Substitue [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Récupère la région de la zone cliente du bouton qui doit être redessiné. (Substitue [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|
|`CMFCToolBarEditBoxButton::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Détermine si une bordure du bouton est affichée lorsqu’un utilisateur clique sur le bouton. (Substitue [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Détermine si les boutons de zone d’édition ont un style à deux dimensions.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Spécifie si le bouton traite le [WM_COMMAND](/windows/desktop/menurc/wm-command) message. (Substitue [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Appelé par le framework lorsque le bouton est ajouté à un **personnaliser** boîte de dialogue. (Substitue [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Appelé par l’infrastructure pour calculer la taille du bouton pour le contexte de périphérique spécifié et l’état d’ancrage. (Substitue [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Appelé par le framework lorsque le bouton est inséré dans une nouvelle barre d’outils. (Substitue [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Appelé par le framework lorsque l’utilisateur clique sur le bouton de la souris. (Substitue [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Appelé par l’infrastructure lors de la barre d’outils parent gère un message WM_CTLCOLOR. (Substitue [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarEditBoxButton::OnDraw`|Appelé par l’infrastructure pour dessiner le bouton en utilisant les options et les styles spécifiés. (Substitue [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Appelé par l’infrastructure pour dessiner le bouton dans le **commandes** volet de la **personnaliser** boîte de dialogue. (Substitue [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Appelé par le framework lorsque la police globale a été modifiée. (Substitue [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Appelé par le framework lorsque la barre d’outils parent se déplace. (Substitue [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Appelé par le framework lorsque le bouton est visible ou invisible. (Substitue [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Appelé par l’infrastructure lors de la barre d’outils parent change sa taille ou la position et cette modification entraîne le bouton Modifier la taille. (Substitue [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Appelé par l’infrastructure lors de la barre d’outils parent met à jour son texte d’info-bulle. (Substitue [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarEditBoxButton::Serialize`|Lit de cet objet à partir d’une archive ou écrit dans une archive. (Substitue [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarEditBoxButton::SetACCData`|Remplit le fourni `CAccessibilityData` objet avec les données d’accessibilité à partir du bouton de barre d’outils. (Substitue [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContents](#setcontents)|Définit le texte dans le contrôle d’édition du bouton.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Recherche le bouton de contrôle d’édition qui possède un ID de commande spécifié et définit le texte dans le contrôle d’édition de ce bouton.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Spécifie l’ID de ressource du menu contextuel qui est associé au bouton.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Spécifie l’apparence de style à deux dimensions de boutons de zone d’édition dans l’application.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Spécifie le style du bouton. (Substitue [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|

## <a name="remarks"></a>Notes

Pour ajouter un bouton de zone de modification à une barre d’outils, procédez comme suit :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.

2. Construire un `CMFCToolBarEditBoxButton` objet.

3. Dans le Gestionnaire de messages qui traite le message AFX_WM_RESETTOOLBAR, remplacez le bouton fictif avec le nouveau bouton de zone de liste déroulante à l’aide de [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Pour plus d’informations, consultez [Procédure pas à pas : Placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCToolBarEditBoxButton` . L’exemple montre comment spécifier qu’un utilisateur peut étirer le bouton au cours de personnalisation, spécifier qu’une bordure du bouton s’affiche lorsqu’un utilisateur clique sur le bouton, définir le texte dans le contrôle de zone de texte, spécifier l’apparence de style à deux dimensions de boutons de zone d’édition dans l’appli cations et spécifiez le style d’une barre d’outils de contrôle zone d’édition.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtoolbareditboxbutton.h

##  <a name="canbestretched"></a>  CMFCToolBarEditBoxButton::CanBeStretched

Spécifie si un utilisateur permet d’étendre le bouton au cours de personnalisation.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valeur de retour

Cette méthode retourne la valeur TRUE.

### <a name="remarks"></a>Notes

Par défaut, le framework n’autorise pas l’utilisateur étirer un bouton de barre d’outils au cours de personnalisation. Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) en autorisant l’utilisateur étirer un bouton de barre d’outils de zone Modifier au cours de personnalisation.

##  <a name="cmfctoolbareditboxbutton"></a>  CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

Construit un [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) objet.

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
[in] Spécifie l’ID de contrôle.

*iImage*<br/>
[in] Spécifie l’index de base zéro d’une image de la barre d’outils. L’image se trouve dans le [cmfctoolbarimages, classe](../../mfc/reference/cmfctoolbarimages-class.md) objet [cmfctoolbar, classe](../../mfc/reference/cmfctoolbar-class.md) classe conserve.

*dwStyle*<br/>
[in] Spécifie le style de contrôle d’édition.

*iWidth*<br/>
[in] Spécifie la largeur en pixels du contrôle d’édition.

### <a name="remarks"></a>Notes

Le constructeur par défaut définit le style de contrôle d’édition à la combinaison suivante :

WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL

La largeur par défaut du contrôle est 150 pixels.

##  <a name="copyfrom"></a>  CMFCToolBarEditBoxButton::CopyFrom

Copie les propriétés d’un autre bouton de barre d’outils pour le bouton en cours.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[in] Une référence au bouton de la source à partir duquel copier.

### <a name="remarks"></a>Notes

Appelez cette méthode pour copier un autre bouton de barre d’outils sur ce bouton de barre d’outils. *src* doit être de type `CMFCToolBarEditBoxButton`.

##  <a name="createedit"></a>  CMFCToolBarEditBoxButton::CreateEdit

Crée un nouveau contrôle d’édition dans le bouton.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[in] Spécifie la fenêtre parente du contrôle d’édition. Il ne doit pas être NULL.

*rect*<br/>
[in] Spécifie la taille et la position du contrôle d’édition.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le contrôle d’édition qui vient d’être créé ; sa valeur est NULL si la création et la pièce jointe du contrôle échouent.

### <a name="remarks"></a>Notes

Vous construisez un `CMFCToolBarEditBoxButton` objet en deux étapes. Tout d’abord appeler le constructeur, puis appelez `CreateEdit`, ce qui crée le contrôle d’édition Windows et l’attache à la `CMFCToolBarEditBoxButton` objet.

##  <a name="getbycmd"></a>  CMFCToolBarEditBoxButton::GetByCmd

Récupère le premier `CMFCToolBarEditBoxButton` objet dans l’application qui possède l’ID de commande spécifiée.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
[in] ID de commande du bouton à récupérer.

### <a name="return-value"></a>Valeur de retour

Le premier `CMFCToolBarEditBoxButton` objet dans l’application qui a l’ID de commande spécifié, ou NULL si aucun objet n’existe.

### <a name="remarks"></a>Notes

Cette méthode d’utilitaire partagé est utilisée par les méthodes telles que [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall) et [CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall) pour définir ou obtenir le texte de la barre d’outils de zone première édition contrôle ayant l’ID de commande spécifiée.

##  <a name="getcontentsall"></a>  CMFCToolBarEditBoxButton::GetContentsAll

Récupère le texte du premier contrôle de barre d’outils de la zone Modifier ayant l’ID de commande spécifiée.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
[in] L’ID de commande du bouton à partir duquel récupérer le contenu.

### <a name="return-value"></a>Valeur de retour

Un `CString` objet qui contient le texte du premier contrôle de barre d’outils de la zone Modifier ayant l’ID de commande spécifiée.

### <a name="remarks"></a>Notes

Cette méthode retourne une chaîne vide si aucun `CMFCToolBarEditBoxButton` objets ont des ID de commande spécifié.

##  <a name="getcontextmenuid"></a>  CMFCToolBarEditBoxButton::GetContextMenuID

Récupère l’ID de ressource du menu contextuel qui est associé au bouton.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Valeur de retour

L’ID de ressource du menu contextuel qui est associé avec le bouton ou 0 si le bouton n’a aucun menu contextuel associé.

### <a name="remarks"></a>Notes

L’infrastructure utilise l’ID de ressource pour créer le menu contextuel lorsque l’utilisateur clique sur le bouton.

##  <a name="geteditborder"></a>  CMFCToolBarEditBoxButton::GetEditBorder

Récupère le rectangle englobant de la partie de modifier l’édition du bouton de zone.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>Paramètres

*rectBorder*<br/>
[out] Une référence à la `CRect` objet qui reçoit le rectangle englobant.

### <a name="remarks"></a>Notes

Cette méthode récupère le rectangle englobant du contrôle d’édition dans les coordonnées clientes. Il étend la taille du rectangle dans chaque direction d’un pixel.

Le [CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) méthode appelle cette méthode lorsqu’il dessine la bordure autour d’un `CMFCToolBarEditBoxButton` objet.

##  <a name="geteditbox"></a>  CMFCToolBarEditBoxButton::GetEditBox

Retourne un pointeur vers le [classe CEdit](../../mfc/reference/cedit-class.md) contrôle qui est incorporé dans le bouton.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le [classe CEdit](../../mfc/reference/cedit-class.md) contrôle qui contient le bouton. Sa valeur est NULL si le `CEdit` contrôle n’a pas encore été créé.

### <a name="remarks"></a>Notes

Vous créez le `CEdit` contrôle en appelant [CMFCToolBarEditBoxButton::CreateEdit](#createedit).

##  <a name="gethwnd"></a>  CMFCToolBarEditBoxButton::GetHwnd

Récupère le handle de fenêtre qui est associé au bouton de barre d’outils.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valeur de retour

Le handle de fenêtre qui est associé au bouton.

### <a name="remarks"></a>Notes

Cette méthode remplace la [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) méthode en retournant le handle de fenêtre de la partie de contrôle d’édition du bouton de zone de modification.

##  <a name="getinvalidaterect"></a>  CMFCToolBarEditBoxButton::GetInvalidateRect

Récupère la région de la zone cliente du bouton qui doit être redessiné.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>Valeur de retour

Un `CRect` objet qui spécifie la région qui doit être redessinée.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base, [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), en incluant dans la région de la zone de l’étiquette de texte.

##  <a name="havehotborder"></a>  CMFCToolBarEditBoxButton::HaveHotBorder

Détermine si une bordure du bouton est affichée lorsqu’un utilisateur clique sur le bouton.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si un bouton affiche sa bordure lorsque sélectionné ; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base, [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), en retournant une valeur différente de zéro si le contrôle est visible.

##  <a name="isflatmode"></a>  CMFCToolBarEditBoxButton::IsFlatMode

Détermine si les boutons de zone d’édition ont un style à deux dimensions.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les boutons ont un style à deux dimensions ; Sinon, 0.

### <a name="remarks"></a>Notes

Par défaut, les boutons de zone d’édition ont un style à deux dimensions. Utilisez le [CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode) méthode pour modifier l’apparence de style à deux dimensions pour votre application.

##  <a name="notifycommand"></a>  CMFCToolBarEditBoxButton::NotifyCommand

Spécifie si le bouton traite le [WM_COMMAND](/windows/desktop/menurc/wm-command) message.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Paramètres

*iNotifyCode*<br/>
[in] Le message de notification qui est associé à la commande.

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton traite le message WM_COMMAND, ou FALSE pour indiquer que le message doit être géré par la barre d’outils parent.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode lorsqu’il est sur le point d’envoyer un [WM_COMMAND](/windows/desktop/menurc/wm-command) message vers la fenêtre parente.

Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) en traitant le [EN_UPDATE](/windows/desktop/Controls/en-update) notification. Pour chaque zone d’édition avec le même ID de commande en tant que cet objet, il définit son étiquette de texte à l’étiquette de texte de cet objet.

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarEditBoxButton::OnAddToCustomizePage

Appelé par le framework lorsque le bouton est ajouté à un **personnaliser** boîte de dialogue.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) en copiant les propriétés à partir de ce contrôle dans la barre d’outils quelconque qui a le même ID de commande en tant que cet objet. Cette méthode ne fait rien si aucune barre d’outils n’a un contrôle de zone d’édition qui possède le même ID de commande en tant que cet objet.

Pour plus d’informations sur la **personnaliser** boîte de dialogue, consultez [cmfctoolbarscustomizedialog, classe](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

##  <a name="onchangeparentwnd"></a>  CMFCToolBarEditBoxButton::OnChangeParentWnd

Appelé par le framework lorsque le bouton est inséré dans une nouvelle barre d’outils.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[in] Pointeur vers la nouvelle fenêtre parente.

### <a name="remarks"></a>Notes

Cette méthode substitue l’implémentation de classe de base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) en recréant interne `CEdit` objet.

##  <a name="onclick"></a>  CMFCToolBarEditBoxButton::OnClick

Appelé par le framework lorsque l’utilisateur clique sur le bouton de la souris.

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

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le bouton traite le message de clic ; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode substitue l’implémentation de classe de base ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) en retournant une valeur différente de zéro si le texte interne `CEdit` objet est visible.

##  <a name="onctlcolor"></a>  CMFCToolBarEditBoxButton::OnCtlColor

Appelé par l’infrastructure lors de la barre d’outils parent gère un message WM_CTLCOLOR.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Le contexte de périphérique qui affiche le bouton.

*nCtlColor*<br/>
[in] Inutilisé.

### <a name="return-value"></a>Valeur de retour

Handle vers le pinceau de fenêtre global.

### <a name="remarks"></a>Notes

Cette méthode substitue l’implémentation de classe de base ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) en définissant les couleurs de texte et d’arrière-plan du contexte de périphérique fourni globale de texte et les couleurs d’arrière-plan, respectivement.

Pour plus d’informations sur les options globales qui sont disponibles pour votre application, consultez [afx_global_data, Structure](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onglobalfontschanged"></a>  CMFCToolBarEditBoxButton::OnGlobalFontsChanged

Appelé par le framework lorsque la police globale a été modifiée.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) en modifiant la police du contrôle à celle de la police globale.

Pour plus d’informations sur les options globales qui sont disponibles pour votre application, consultez [afx_global_data, Structure](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onmove"></a>  CMFCToolBarEditBoxButton::OnMove

Appelé par le framework lorsque la barre d’outils parent se déplace.

```
virtual void OnMove();
```

### <a name="remarks"></a>Notes

Cette méthode substitue l’implémentation de classe par défaut ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) en mettant à jour la position d’interne `CEdit` objet

##  <a name="onshow"></a>  CMFCToolBarEditBoxButton::OnShow

Appelé par le framework lorsque le bouton est visible ou invisible.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
[in] Spécifie si le bouton est visible. Si ce paramètre est TRUE, le bouton est visible. Sinon, le bouton n’est pas visible.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) en affichant le bouton si *bShow* a la valeur TRUE. Sinon, cette méthode masque le bouton.

##  <a name="onsize"></a>  CMFCToolBarEditBoxButton::OnSize

Appelé par l’infrastructure lors de la barre d’outils parent change sa taille ou la position et cette modification entraîne le bouton Modifier la taille.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Paramètres

*iSize*<br/>
[in] La nouvelle largeur du bouton, en pixels.

### <a name="remarks"></a>Notes

Cette méthode substitue l’implémentation de classe par défaut, [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), en mettant à jour la taille et la position d’interne `CEdit` objet.

##  <a name="onupdatetooltip"></a>  CMFCToolBarEditBoxButton::OnUpdateToolTip

Appelé par l’infrastructure lors de la barre d’outils parent met à jour son texte d’info-bulle.

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
[in] Le contrôle qui affiche le texte d’info-bulle.

*str*<br/>
[out] Un `CString` objet qui reçoit le texte d’info-bulle mis à jour.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode met à jour le texte d’info-bulle ; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de classe de base ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) en affichant le texte d’info-bulle associé à la partie d’édition du bouton. Si le texte interne `CEdit` objet est NULL ou un handle de fenêtre de la `CEdit` objet n’identifie pas une fenêtre existante, cette méthode ne fait rien et retourne FALSE.

##  <a name="setcontents"></a>  CMFCToolBarEditBoxButton::SetContents

Définit le texte dans le contrôle de zone de texte.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>Paramètres

*sContents*<br/>
[in] Spécifie le nouveau texte à définir.

##  <a name="setcontentsall"></a>  CMFCToolBarEditBoxButton::SetContentsAll

Recherche un [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) objet qui a un ID de commande spécifié et définit le texte spécifié dans sa zone de texte.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
[in] Spécifie l’ID de commande du contrôle pour lequel le texte sera modifié.

*strContents*<br/>
[in] Spécifie le nouveau texte à définir.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le texte a été défini ; 0 si le `CMFCToolBarEditBoxButton` contrôle avec l’ID de commande spécifié n’existe pas.

##  <a name="setcontextmenuid"></a>  CMFCToolBarEditBoxButton::SetContextMenuID

Spécifie l’ID de ressource du menu contextuel qui est associé au bouton.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
[in] L’ID de ressource du menu contextuel.

### <a name="remarks"></a>Notes

L’infrastructure utilise l’ID de ressource pour créer le menu contextuel quand l’utilisateur clique sur le bouton de barre d’outils.

##  <a name="setflatmode"></a>  CMFCToolBarEditBoxButton::SetFlatMode

Spécifie l’apparence de style à deux dimensions de boutons de zone d’édition dans l’application.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>Paramètres

*bFlat*<br/>
[in] Le style plat pour les boutons de zone d’édition. Si ce paramètre est TRUE, l’apparence de style à deux dimensions est activé ; Sinon, l’apparence de style à deux dimensions est désactivée.

### <a name="remarks"></a>Notes

Le style plat par défaut pour les boutons de zone d’édition est TRUE. Utilisez le [CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode) méthode pour récupérer l’apparence de style à deux dimensions pour votre application.

##  <a name="setstyle"></a>  CMFCToolBarEditBoxButton::SetStyle

Spécifie le style d’une barre d’outils de contrôle zone d’édition.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Paramètres

*nStyle*<br/>
[in] Un nouveau style à définir.

### <a name="remarks"></a>Notes

Cette méthode définit [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) à *nStyle* il désactive également la zone de texte lorsque l’application est en mode de personnalisation et l’active lorsque l’application n’est pas en mode personnaliser (voir [ CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) et [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Consultez [Styles de contrôle de barre d’outils](../../mfc/reference/toolbar-control-styles.md) pour obtenir la liste des indicateurs de style valide.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit, classe](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Procédure pas à pas : Placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
