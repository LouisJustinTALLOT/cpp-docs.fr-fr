---
description: 'En savoir plus sur : classe CMFCOutlookBarPane'
title: CMFCOutlookBarPane, classe
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
ms.openlocfilehash: f1bcae298a9541920f6deeb9a3bce22e49222cb0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265023"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane, classe

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

Contrôle dérivé de la [classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) qui peut être inséré dans une barre Outlook ( [classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)). Le volet de barre Outlook contient une colonne de grands boutons. L'utilisateur peut faire défiler vers le haut ou vers le bas la liste des boutons si elle est plus grande que le volet. Lorsque l'utilisateur détache un volet de barre Outlook de la barre Outlook, il peut flotter ou s'ancrer à la fenêtre frame principale.

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
|[CMFCOutlookBarPane :: AddButton](#addbutton)|Ajoute un bouton au volet barre Outlook.|
|[CMFCOutlookBarPane :: CanBeAttached](#canbeattached)|Détermine si le volet peut être ancré à un autre volet ou fenêtre frame. (Substitue [CBasePane :: CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|
|`CMFCOutlookBarPane::CanBeRestored`|Détermine si le système peut restaurer une barre d’outils à son état d’origine après la personnalisation. (Substitue [CMFCToolBar :: CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCOutlookBarPane :: ClearAll](#clearall)|Libère les ressources utilisées par les images dans le volet barre Outlook.|
|[CMFCOutlookBarPane :: Create](#create)|Crée le volet barre Outlook.|
|`CMFCOutlookBarPane::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCOutlookBarPane::Dock`|Appelé par le Framework pour ancrer le volet de barre Outlook. (Substitue `CPane::Dock`.)|
|[CMFCOutlookBarPane :: EnablePageScrollMode](#enablepagescrollmode)|Spécifie si les flèches de défilement sur le volet de barre Outlook affichent la liste des boutons par page ou par bouton.|
|[CMFCOutlookBarPane :: GetRegularColor](#getregularcolor)|Retourne la couleur de texte normale (non sélectionnée) du volet barre Outlook.|
|`CMFCOutlookBarPane::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCOutlookBarPane :: IsBackgroundTexture](#isbackgroundtexture)|Détermine si une image d’arrière-plan est chargée pour le volet de barre Outlook.|
|`CMFCOutlookBarPane::IsChangeState`|Détermine si un volet flottant peut être ancré. (Substitue `CPane::IsChangeState`.)|
|[CMFCOutlookBarPane :: IsDrawShadedHighlight](#isdrawshadedhighlight)|Détermine si la bordure du bouton est grisée lorsqu’un bouton est mis en surbrillance et qu’une image d’arrière-plan est affichée.|
|`CMFCOutlookBarPane::OnBeforeFloat`|Appelé par le Framework quand un volet est sur le paragraphe flottant. (Substitue [CPane :: OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|
|[CMFCOutlookBarPane :: RemoveButton](#removebutton)|Supprime le bouton qui a un ID de commande spécifié.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|Restaure l'état initial d'une barre d'outils. (Substitue [CMFCToolBar :: RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|
|[CMFCOutlookBarPane :: SetBackColor](#setbackcolor)|Définit la couleur d’arrière-plan.|
|[CMFCOutlookBarPane :: SetBackImage](#setbackimage)|Définit l’image d’arrière-plan.|
|[CMFCOutlookBarPane :: SetDefaultState](#setdefaultstate)|Rétablit le volet de barre Outlook à l’ensemble des boutons d’origine.|
|[CMFCOutlookBarPane :: SetExtraSpace](#setextraspace)|Définit le nombre de pixels de remplissage utilisés autour des boutons dans le volet barre Outlook.|
|[CMFCOutlookBarPane :: SetTextColor](#settextcolor)|Définit les couleurs du texte normal et mis en surbrillance dans le volet barre Outlook.|
|[CMFCOutlookBarPane :: SetTransparentColor](#settransparentcolor)|Définit la couleur transparente du volet barre Outlook.|
|`CMFCOutlookBarPane::SmartUpdate`|Utilisé en interne pour mettre à jour la barre Outlook. (Substitue `CMFCToolBar::SmartUpdate`.)|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCOutlookBarPane :: EnableContextMenuItems](#enablecontextmenuitems)|Spécifie les éléments de menu contextuel qui sont affichés en mode de personnalisation.|
|[CMFCOutlookBarPane :: RemoveAllButtons](#removeallbuttons)|Supprime tous les boutons du volet barre Outlook. (Substitue [CMFCToolBar :: RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|

## <a name="remarks"></a>Notes

Pour plus d’informations sur la façon d’implémenter une barre Outlook, consultez [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md).

Pour obtenir un exemple de barre Outlook, consultez l’exemple de projet OutlookDemo.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCOutlookBarPane` classe. L’exemple montre comment créer un volet de barre Outlook, activer le mode de défilement de la page, activer l’ancrage et définir la couleur d’arrière-plan de la barre Outlook. Cet extrait de code fait partie de l' [exemple Outlook multi views](../../overview/visual-cpp-samples.md).

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

## <a name="requirements"></a>Spécifications

**En-tête :** afxoutlookbarpane. h

## <a name="cmfcoutlookbarpaneaddbutton"></a><a name="addbutton"></a> CMFCOutlookBarPane :: AddButton

Ajoute un bouton au volet barre Outlook.

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
dans Spécifie l’identificateur de ressource d’une image bitmap.

*lpszLabel*<br/>
dans Spécifie le texte du bouton.

*iIdCommand*<br/>
dans Spécifie l’ID du contrôle bouton.

*iInsertAt*<br/>
dans Spécifie l’index de base zéro sur la page de la barre Outlook au niveau duquel insérer le bouton.

*uiLabel*<br/>
dans ID de ressource de chaîne.

*szBmpFileName*<br/>
dans Spécifie le nom du fichier image de disque à charger.

*szLabel*<br/>
dans Spécifie le texte du bouton.

*hBmp*<br/>
dans Handle vers l’image bitmap d’un bouton.

*hIcon*<br/>
dans Handle d’une icône de bouton.

### <a name="return-value"></a>Valeur renvoyée

TRUE si un bouton a été ajouté avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour insérer un nouveau bouton dans la page d’une barre Outlook. L’image du bouton peut être chargée soit à partir des ressources de l’application, soit à partir d’un fichier sur disque.

Si l’ID de page spécifié par *uiPageID* est-1, le bouton est inséré dans la première page.

Si l’index spécifié par *iInsertAt* est-1, le bouton est ajouté à la fin de la page.

## <a name="cmfcoutlookbarpanecanbeattached"></a><a name="canbeattached"></a> CMFCOutlookBarPane :: CanBeAttached

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcoutlookbarpaneclearall"></a><a name="clearall"></a> CMFCOutlookBarPane :: ClearAll

Libère les ressources utilisées par les images dans le volet barre Outlook.

```cpp
void ClearAll();
```

### <a name="remarks"></a>Notes

Cette méthode appelle directement [CMFCToolBarImages :: Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), qui est appelée sur les images utilisées par le volet de barre Outlook.

## <a name="cmfcoutlookbarpanecreate"></a><a name="create"></a> CMFCOutlookBarPane :: Create

Crée le volet barre Outlook.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
dans Spécifie la fenêtre parente du contrôle volet de la barre Outlook. Ne doit pas avoir la valeur NULL.

*dwStyle*<br/>
dans Style de la fenêtre.  Pour obtenir la liste des styles de fenêtre, consultez [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*uiID*<br/>
dans ID du contrôle. Doit être unique pour permettre l’enregistrement de l’état du contrôle.

*dwControlBarStyle*<br/>
dans Spécifie des styles spéciaux qui définissent le comportement du contrôle volet de la barre Outlook lorsqu’il est détaché de la barre Outlook.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la méthode a réussi ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Pour construire un `CMFCOutlookBarPane` objet, appelez d’abord le constructeur, puis appelez `Create` , qui crée le contrôle volet de barre Outlook et l’attache à l' `CMFCOutlookBarPane` objet.

Pour plus d’informations sur `dwControlBarStyle` , consultez [CBasePane :: CreateEx](../../mfc/reference/cbasepane-class.md#createex).

## <a name="cmfcoutlookbarpaneenablecontextmenuitems"></a><a name="enablecontextmenuitems"></a> CMFCOutlookBarPane :: EnableContextMenuItems

Spécifie les éléments de menu contextuel qui sont affichés en mode de personnalisation.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>Paramètres

*pButton*<br/>
dans Pointeur vers un bouton de barre d’outils sur lequel un utilisateur a cliqué.

*pPopup*<br/>
dans Pointeur vers le menu contextuel.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si le menu contextuel doit être affiché. Sinon, FALSe.

### <a name="remarks"></a>Notes

Substituez cette méthode pour modifier le menu contextuel de l’infrastructure standard que l’infrastructure affiche en mode de personnalisation.

L’implémentation par défaut vérifie le mode de personnalisation ( [CMFCToolBar :: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) et, si elle est définie sur true, désactive tous les éléments de menu contextuel sauf **Delete**. Ensuite, il passe simplement les paramètres d’entrée à `CMFCToolBar::EnableContextMenuItems` .

> [!NOTE]
> *Menu contextuel* est un synonyme du menu contextuel.

## <a name="cmfcoutlookbarpaneenablepagescrollmode"></a><a name="enablepagescrollmode"></a> CMFCOutlookBarPane :: EnablePageScrollMode

Spécifie si les flèches de défilement sur le volet de barre Outlook affichent la liste des boutons page par page ou bouton par bouton.

```cpp
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>Paramètres

*bPageScroll*<br/>
dans Si la valeur est TRUE, active le mode de défilement de la page. Si la valeur est FALSe, désactivez le mode de défilement de la page.

## <a name="cmfcoutlookbarpanegetregularcolor"></a><a name="getregularcolor"></a> CMFCOutlookBarPane :: GetRegularColor

Retourne la couleur de texte normale (c’est-à-dire non sélectionnée) du volet barre Outlook.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Couleur de texte actuelle en tant que valeur de couleur RVB.

### <a name="remarks"></a>Notes

Utilisez [CMFCOutlookBarPane :: SetTextColor](#settextcolor) pour définir la couleur de texte actuelle (régulière et sélectionnée) de la barre Outlook. Vous pouvez obtenir la couleur de texte par défaut en appelant la fonction [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) avec l’index COLOR_WINDOW.

## <a name="cmfcoutlookbarpaneisbackgroundtexture"></a><a name="isbackgroundtexture"></a> CMFCOutlookBarPane :: IsBackgroundTexture

Détermine si une image d’arrière-plan est chargée pour le volet de barre Outlook.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE s’il y a une image d’arrière-plan à afficher ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Vous pouvez ajouter une image d’arrière-plan en appelant la fonction [CMFCOutlookBarPane :: SetBackImage](#setbackimage) .

S’il n’y a pas d’image d’arrière-plan, l’arrière-plan est peint avec une couleur spécifiée à l’aide de [CMFCOutlookBarPane :: SetBackColor](#setbackcolor).

## <a name="cmfcoutlookbarpaneisdrawshadedhighlight"></a><a name="isdrawshadedhighlight"></a> CMFCOutlookBarPane :: IsDrawShadedHighlight

Détermine si la bordure du bouton est grisée lorsqu’un bouton est mis en surbrillance et qu’une image d’arrière-plan est affichée.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si les bordures du bouton sont grisées ; Sinon, FALSe.

## <a name="cmfcoutlookbarpaneremoveallbuttons"></a><a name="removeallbuttons"></a> CMFCOutlookBarPane :: RemoveAllButtons

Supprime tous les boutons du volet barre Outlook.

```
virtual void RemoveAllButtons();
```

## <a name="cmfcoutlookbarpaneremovebutton"></a><a name="removebutton"></a> CMFCOutlookBarPane :: RemoveButton

Supprime le bouton qui a un ID de commande spécifié.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>Paramètres

*iIdCommand*<br/>
dans Spécifie l’ID de commande d’un bouton à supprimer.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le bouton a été correctement supprimé ; FALSe si l’ID de commande spécifié n’est pas valide.

## <a name="cmfcoutlookbarpanesetbackcolor"></a><a name="setbackcolor"></a> CMFCOutlookBarPane :: SetBackColor

Définit la couleur d’arrière-plan de la barre Outlook.

```cpp
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
dans Spécifie la nouvelle couleur d’arrière-plan.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir la couleur d’arrière-plan actuelle de la barre Outlook. La couleur d’arrière-plan est utilisée uniquement s’il n’y a aucune image d’arrière-plan.

## <a name="cmfcoutlookbarpanesetbackimage"></a><a name="setbackimage"></a> CMFCOutlookBarPane :: SetBackImage

Définit l’image d’arrière-plan.

```cpp
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>Paramètres

*uiImageID*<br/>
dans Spécifie l’ID de ressource de l’image.

### <a name="remarks"></a>Notes

Appelez cette méthode pour définir l’image d’arrière-plan de la barre Outlook. La liste des images d’arrière-plan est gérée par l’objet de [classe CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) incorporé.

## <a name="cmfcoutlookbarpanesetdefaultstate"></a><a name="setdefaultstate"></a> CMFCOutlookBarPane :: SetDefaultState

Rétablit le volet de barre Outlook à l’ensemble des boutons d’origine.

```cpp
void SetDefaultState();
```

### <a name="remarks"></a>Notes

Cette méthode restaure les boutons de la barre Outlook à l’ensemble d’origine. Cette méthode est similaire `CMFCOutlookBarPane::RestoreOriginalstate` à, à ceci près qu’elle ne déclenche pas de redessin du volet barre Outlook.

## <a name="cmfcoutlookbarpanesetextraspace"></a><a name="setextraspace"></a> CMFCOutlookBarPane :: SetExtraSpace

Définit le nombre de pixels de remplissage utilisés autour des boutons dans le volet barre Outlook.

```cpp
void SetExtraSpace()
```

## <a name="cmfcoutlookbarpanesettextcolor"></a><a name="settextcolor"></a> CMFCOutlookBarPane :: SetTextColor

Définit les couleurs du texte normal et mis en surbrillance dans le volet barre Outlook.

```cpp
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>Paramètres

*clrRegText*<br/>
dans Spécifie la nouvelle couleur du texte non sélectionné.

*clrSelText*<br/>
dans Spécifie la nouvelle couleur du texte sélectionné.

## <a name="cmfcoutlookbarpanesettransparentcolor"></a><a name="settransparentcolor"></a> CMFCOutlookBarPane :: SetTransparentColor

Définit la couleur transparente du volet barre Outlook.

```cpp
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*color*<br/>
Spécifie la nouvelle couleur transparente.

### <a name="remarks"></a>Notes

La couleur transparente est requise pour afficher des images transparentes. Toute occurrence de cette couleur dans une image est peinte avec la couleur d’arrière-plan à la place.  Il n’y a aucune fusion d’images d’arrière-plan et de premier plan.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl, classe](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
