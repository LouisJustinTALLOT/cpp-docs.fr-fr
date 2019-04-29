---
title: Cmfcoutlookbarpane, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
ms.openlocfilehash: b23aa9e30c130cea8c84290b62cc19794376d4c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374101"
---
# <a name="cmfcoutlookbarpane-class"></a>Cmfcoutlookbarpane, classe

Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

Un contrôle dérivé [cmfctoolbar, classe](../../mfc/reference/cmfctoolbar-class.md) qui peut être inséré dans une barre Outlook ( [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md)). Le volet de barre Outlook contient une colonne de grands boutons. L'utilisateur peut faire défiler vers le haut ou vers le bas la liste des boutons si elle est plus grande que le volet. Lorsque l'utilisateur détache un volet de barre Outlook de la barre Outlook, il peut flotter ou s'ancrer à la fenêtre frame principale.

## <a name="syntax"></a>Syntaxe

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Constructeur par défaut.|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCOutlookBarPane::AddButton](#addbutton)|Ajoute un bouton dans le volet de barre Outlook.|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Détermine si le volet peut être ancré à un autre volet ou une fenêtre frame. (Substitue [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|
|`CMFCOutlookBarPane::CanBeRestored`|Détermine si le système peut être restauré une barre d’outils à son état d’origine après la personnalisation. (Substitue [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCOutlookBarPane::ClearAll](#clearall)|Libère les ressources utilisées par les images dans le volet de barre Outlook.|
|[CMFCOutlookBarPane::Create](#create)|Crée le volet de barre Outlook.|
|`CMFCOutlookBarPane::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCOutlookBarPane::Dock`|Appelé par l’infrastructure pour ancrer le volet de barre Outlook. (Substitue `CPane::Dock`.)|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Spécifie si les flèches de défilement dans le volet de barre Outlook passer la liste des boutons de page, ou bouton.|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Retourne la couleur de texte (non sélectionné) standard du volet de barre Outlook.|
|`CMFCOutlookBarPane::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Détermine s’il existe une image d’arrière-plan chargée pour le volet de barre Outlook.|
|`CMFCOutlookBarPane::IsChangeState`|Détermine si un volet flottant peut être ancré. (Substitue `CPane::IsChangeState`.)|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Détermine si la bordure du bouton est grisée lorsqu’un bouton est mis en surbrillance et une image d’arrière-plan est affichée.|
|`CMFCOutlookBarPane::OnBeforeFloat`|Appelé par le framework lorsqu’un volet est sur le type float. (Substitue [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Supprime le bouton qui a un ID de commande spécifié.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|Restaure l'état initial d'une barre d'outils. (Substitue [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Définit la couleur d’arrière-plan.|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Définit l’image d’arrière-plan.|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Réinitialise le volet de barre Outlook pour le jeu initial de boutons.|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Définit le nombre de pixels de remplissage utilisé autour des boutons dans le volet de barre Outlook.|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Définit les couleurs de texte standard et en surbrillance dans le volet de barre Outlook.|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Définit la couleur transparente pour le volet de barre Outlook.|
|`CMFCOutlookBarPane::SmartUpdate`|Utilisé en interne pour mettre à jour de la barre Outlook. (Substitue `CMFCToolBar::SmartUpdate`.)|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Spécifie les éléments de menu de raccourci sont affichées dans le mode de personnalisation.|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Supprime tous les boutons dans le volet de barre Outlook. (Substitue [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|

## <a name="remarks"></a>Notes

Pour plus d’informations sur la façon d’implémenter une barre Outlook, consultez [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md).

Pour obtenir un exemple d’une barre Outlook, consultez l’exemple de projet OutlookDemo.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCOutlookBarPane` classe. L’exemple montre comment créer un volet de barre Outlook, activer le mode de défilement, activez l’ancrage et définir la couleur d’arrière-plan de la barre Outlook. Cet extrait de code fait partie de la [Outlook plusieurs vues, exemple](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxoutlookbarpane.h

##  <a name="addbutton"></a>  CMFCOutlookBarPane::AddButton

Ajoute un bouton dans le volet de barre Outlook.

```
BOOL AddButton(
    UINT uiImage,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    UINT uiImage,
    UINT uiLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    LPCTSTR szBmpFileName,
    LPCTSTR szLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HBITMAP hBmp,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HICON hIcon,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1,
    BOOL bAlphaBlend=FALSE);
```

### <a name="parameters"></a>Paramètres

*uiImage*<br/>
[in] Spécifie l’identificateur de ressource d’une image bitmap.

*lpszLabel*<br/>
[in] Spécifie le texte du bouton.

*iIdCommand*<br/>
[in] Spécifie l’ID. du contrôle de bouton

*iInsertAt*<br/>
[in] Spécifie l’index de base zéro sur la page de la barre outlook au niveau duquel insérer le bouton.

*uiLabel*<br/>
[in] Un ID de ressource de chaîne.

*szBmpFileName*<br/>
[in] Spécifie le nom du fichier d’image disque à charger.

*szLabel*<br/>
[in] Spécifie le texte du bouton.

*hBmp*<br/>
[in] Handle vers une image bitmap d’un bouton.

*hIcon*<br/>
[in] Handle vers l’icône d’un bouton.

### <a name="return-value"></a>Valeur de retour

TRUE si un bouton a été ajouté avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour insérer un nouveau bouton de la page d’une barre Outlook. L’image du bouton peut être chargée à partir des ressources d’application ou à partir d’un fichier de disque.

Si l’ID de page spécifiée par *uiPageID* est -1, le bouton est inséré dans la première page.

Si l’index spécifié par *iInsertAt* est -1, le bouton est ajouté à la fin de la page.

##  <a name="canbeattached"></a>  CMFCOutlookBarPane::CanBeAttached

Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="clearall"></a>  CMFCOutlookBarPane::ClearAll

Libère les ressources utilisées par les images dans le volet de barre Outlook.

```
void ClearAll();
```

### <a name="remarks"></a>Notes

Cette méthode appelle directement [CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), qui est appelée sur les images qui sont utilisées par le volet de barre Outlook.

##  <a name="create"></a>  CMFCOutlookBarPane::Create

Crée le volet de barre Outlook.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
[in] Spécifie la fenêtre parente du contrôle de volet de barre Outlook. Ne doit pas être NULL.

*dwStyle*<br/>
[in] Le style de fenêtre.  Pour obtenir la liste des styles de fenêtre, consultez [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*uiID*<br/>
[in] L’ID du contrôle. Doit être unique pour activer l’enregistrement de l’état du contrôle.

*dwControlBarStyle*<br/>
[in] Spécifie les styles spéciaux qui définissent le comportement du contrôle de volet de barre Outlook lorsqu’elle est détachée de la barre Outlook.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Pour construire un `CMFCOutlookBarPane` de l’objet, tout d’abord appeler le constructeur, puis appelez `Create`, qui crée le contrôle de volet de barre Outlook et l’attache à la `CMFCOutlookBarPane` objet.

Pour plus d’informations sur `dwControlBarStyle` consultez [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

##  <a name="enablecontextmenuitems"></a>  CMFCOutlookBarPane::EnableContextMenuItems

Spécifie les éléments de menu de raccourci sont affichées dans le mode de personnalisation.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>Paramètres

*pButton*<br/>
[in] Pointeur vers un bouton de barre d’outils sur lequel un utilisateur a cliqué.

*pPopup*<br/>
[in] Pointeur vers le menu contextuel.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le menu contextuel doit être affiché ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Substituez cette méthode pour modifier le menu contextuel standard framework affichée par l’infrastructure dans le mode de personnalisation.

L’implémentation par défaut vérifie le mode de personnalisation ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) et si elle est définie sur TRUE, elle désactive le raccourci de tous les éléments de menu à l’exception **supprimer**. Ensuite, il passe simplement les paramètres d’entrée `CMFCToolBar::EnableContextMenuItems`.

> [!NOTE]
> *Menu contextuel* est un synonyme de menu contextuel.

##  <a name="enablepagescrollmode"></a>  CMFCOutlookBarPane::EnablePageScrollMode

Spécifie si les flèches de défilement dans le volet de barre Outlook passer à la liste des boutons de page par page ou par bouton.

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>Paramètres

*bPageScroll*<br/>
[in] Si la valeur est TRUE, activer le mode de défilement de page. Si la valeur est FALSE, désactivez le mode de défilement.

##  <a name="getregularcolor"></a>  CMFCOutlookBarPane::GetRegularColor

Retourne l’opération standard (autrement dit, non sélectionné) couleur du texte du volet de barre Outlook.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>Valeur de retour

La couleur de texte actuelle avec une valeur de couleur RVB.

### <a name="remarks"></a>Notes

Utilisez [CMFCOutlookBarPane::SetTextColor](#settextcolor) pour définir la couleur de texte (réguliers et sélectionné) en cours de la barre Outlook. Vous pouvez obtenir la couleur du texte par défaut en appelant le [GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor) fonction avec l’index COLOR_WINDOW.

##  <a name="isbackgroundtexture"></a>  CMFCOutlookBarPane::IsBackgroundTexture

Détermine s’il existe une image d’arrière-plan chargée pour le volet de barre Outlook.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si l’image d’arrière-plan à afficher ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Vous pouvez ajouter une image d’arrière-plan en appelant [CMFCOutlookBarPane::SetBackImage](#setbackimage) (fonction).

S’il n’existe aucune image d’arrière-plan, l’arrière-plan est peint avec une couleur spécifiée à l’aide de [CMFCOutlookBarPane::SetBackColor](#setbackcolor).

##  <a name="isdrawshadedhighlight"></a>  CMFCOutlookBarPane::IsDrawShadedHighlight

Détermine si la bordure du bouton est grisée lorsqu’un bouton est mis en surbrillance et une image d’arrière-plan est affichée.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si les bordures du bouton sont grisées ; Sinon, FALSE.

##  <a name="removeallbuttons"></a>  CMFCOutlookBarPane::RemoveAllButtons

Supprime tous les boutons dans le volet de barre Outlook.

```
virtual void RemoveAllButtons();
```

##  <a name="removebutton"></a>  CMFCOutlookBarPane::RemoveButton

Supprime le bouton qui a un ID de commande spécifié.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>Paramètres

*iIdCommand*<br/>
[in] Spécifie l’ID de commande d’un bouton à supprimer.

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton a été supprimé avec succès ; FALSE si l’ID de commande spécifié n’est pas valide.

##  <a name="setbackcolor"></a>  CMFCOutlookBarPane::SetBackColor

Définit la couleur d’arrière-plan de la barre Outlook.

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
[in] Spécifie la nouvelle couleur d’arrière-plan.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir la couleur d’arrière-plan actuelle de la barre Outlook. La couleur d’arrière-plan est utilisée uniquement s’il n’existe aucune image d’arrière-plan.

##  <a name="setbackimage"></a>  CMFCOutlookBarPane::SetBackImage

Définit l’image d’arrière-plan.

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>Paramètres

*uiImageID*<br/>
[in] Spécifie l’ID de ressource d’image.

### <a name="remarks"></a>Notes

Appelez cette méthode pour définir l’Outlook image d’arrière-plan de la barre. La liste des images d’arrière-plan est gérée par l’embedded [cmfctoolbarimages, classe](../../mfc/reference/cmfctoolbarimages-class.md) objet.

##  <a name="setdefaultstate"></a>  CMFCOutlookBarPane::SetDefaultState

Réinitialise le volet de barre Outlook pour le jeu initial de boutons.

```
void SetDefaultState();
```

### <a name="remarks"></a>Notes

Cette méthode restaure les boutons de barre Outlook dans le jeu d’origine. Cette méthode est comparable à `CMFCOutlookBarPane::RestoreOriginalstate`, sauf qu’elle ne déclenche pas d’un nouveau dessin du volet de barre Outlook.

##  <a name="setextraspace"></a>  CMFCOutlookBarPane::SetExtraSpace

Définit le nombre de pixels de remplissage utilisé autour des boutons dans le volet de barre Outlook.

```
void SetExtraSpace()
```

##  <a name="settextcolor"></a>  CMFCOutlookBarPane::SetTextColor

Définit les couleurs de texte standard et en surbrillance dans le volet de barre Outlook.

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>Paramètres

*clrRegText*<br/>
[in] Spécifie la nouvelle couleur du texte non sélectionné.

*clrSelText*<br/>
[in] Spécifie la nouvelle couleur pour le texte sélectionné.

##  <a name="settransparentcolor"></a>  CMFCOutlookBarPane::SetTransparentColor

Définit la couleur transparente pour le volet de barre Outlook.

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
Spécifie la nouvelle couleur transparente.

### <a name="remarks"></a>Notes

Couleur transparente est requis pour afficher des images transparentes. Toute occurrence de cette couleur dans une image est peinte avec la couleur d’arrière-plan à la place.  Il n’existe aucune fusion des images d’arrière-plan et de premier plan.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl, classe](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
