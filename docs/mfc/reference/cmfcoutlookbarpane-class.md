---
title: Classe CMFCOutlookBarPane
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
ms.openlocfilehash: 82d8f1da0640e5b487a06585c72279e7d7ffdf99
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369644"
---
# <a name="cmfcoutlookbarpane-class"></a>Classe CMFCOutlookBarPane

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

Un contrôle dérivé de [la classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) qui peut être inséré dans une barre Outlook [(classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)). Le volet de barre Outlook contient une colonne de grands boutons. L'utilisateur peut faire défiler vers le haut ou vers le bas la liste des boutons si elle est plus grande que le volet. Lorsque l'utilisateur détache un volet de barre Outlook de la barre Outlook, il peut flotter ou s'ancrer à la fenêtre frame principale.

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
|[CMFCOutlookBarPane::AddButton](#addbutton)|Ajoute un bouton à la vitre de barre Outlook.|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Détermine si la vitre peut être amarrée à une autre vitre ou à une fenêtre de cadre. (Overrides [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|
|`CMFCOutlookBarPane::CanBeRestored`|Détermine si le système peut restaurer une barre d’outils à son état d’origine après la personnalisation. (Overrides [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCOutlookBarPane::ClearAll](#clearall)|Libère les ressources utilisées par les images dans le volet barre Outlook.|
|[CMFCOutlookBarPane::Créer](#create)|Crée le volet barre Outlook.|
|`CMFCOutlookBarPane::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCOutlookBarPane::Dock`|Appelé par le cadre pour amarrer le volet barre Outlook. (Substitue `CPane::Dock`.)|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Précise si les flèches de défilement sur le volet de barre Outlook avancent la liste des boutons par page, ou par bouton.|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Retourne la couleur de texte régulière (non sélectionnée) du volet barre Outlook.|
|`CMFCOutlookBarPane::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Détermine s’il y a une image de fond chargée pour la vitre de barre Outlook.|
|`CMFCOutlookBarPane::IsChangeState`|Détermine si une vitre flottante peut être amarré. (Substitue `CPane::IsChangeState`.)|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Détermine si la bordure du bouton est ombragée lorsqu’un bouton est surligné et qu’une image de fond est affichée.|
|`CMFCOutlookBarPane::OnBeforeFloat`|Appelé par le cadre quand une vitre est sur le point de flotter. (Overrides [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Supprime le bouton qui a une pièce d’identité de commande spécifiée.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|Restaure l'état initial d'une barre d'outils. (Overrides [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Définit la couleur de fond.|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Définit l’image de fond.|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Réinitialise le volet à barres Outlook sur l’ensemble original de boutons.|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Définit le nombre de pixels de rembourrage utilisés autour des boutons dans la vitre de la barre Outlook.|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Définit les couleurs du texte régulier et mis en surbrillance dans le volet barre Outlook.|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Définit la couleur transparente pour le volet barre Outlook.|
|`CMFCOutlookBarPane::SmartUpdate`|Utilisé en interne pour mettre à jour la barre Outlook. (Substitue `CMFCToolBar::SmartUpdate`.)|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Précise quels éléments de menu raccourcis sont affichés en mode personnalisation.|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Supprime tous les boutons de la vitre de la barre Outlook. (Overrides [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|

## <a name="remarks"></a>Notes

Pour plus d’informations sur la façon de mettre en œuvre une barre Outlook, voir [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

Par exemple, consultez le projet d’exemple OutlookDemo.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser `CMFCOutlookBarPane` diverses méthodes de la classe. L’exemple montre comment créer un volet à barres Outlook, activer le mode défilement de page, activer l’amarrage et définir la couleur de fond de la barre Outlook. Cet extrait de code fait partie de [l’échantillon Outlook Multi Views](../../overview/visual-cpp-samples.md).

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

**En-tête:** afxoutlookbarpane.h

## <a name="cmfcoutlookbarpaneaddbutton"></a><a name="addbutton"></a>CMFCOutlookBarPane::AddButton

Ajoute un bouton à la vitre de barre Outlook.

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

*Uiimage*<br/>
[dans] Spécifie l’identifiant de ressource d’un bitmap.

*lpszLabel*<br/>
[dans] Spécifie le texte du bouton.

*iIdCommand (en)*<br/>
[dans] Spécifie l’ID du contrôle du bouton.

*iInsertAt*<br/>
[dans] Spécifie l’index zéro sur la page de la barre de perspectives à laquelle insérer le bouton.

*uiLabel (en)*<br/>
[dans] Une pièce d’identité de ressource de chaîne.

*szBmpFileName*<br/>
[dans] Spécifie le nom du fichier d’image du disque à charger.

*szLabel (en)*<br/>
[dans] Spécifie le texte du bouton.

*hBmp (en)*<br/>
[dans] Une poignée à la bitmap d’un bouton.

*hIcon (en)*<br/>
[dans] Une poignée à l’icône d’un bouton.

### <a name="return-value"></a>Valeur de retour

VRAI si un bouton a été ajouté avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour insérer un nouveau bouton dans la page d’une barre Outlook. L’image du bouton peut être chargée à partir des ressources d’application ou à partir d’un fichier disque.

Si l’ID de page spécifié par *uiPageID* est de -1, le bouton est inséré dans la première page.

Si l’index spécifié par *iInsertAt* est de -1, le bouton est ajouté à la fin de la page.

## <a name="cmfcoutlookbarpanecanbeattached"></a><a name="canbeattached"></a>CMFCOutlookBarPane::CanBeAttached

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcoutlookbarpaneclearall"></a><a name="clearall"></a>CMFCOutlookBarPane::ClearAll

Libère les ressources utilisées par les images sur le volet barre Outlook.

```
void ClearAll();
```

### <a name="remarks"></a>Notes

Cette méthode appelle directement [CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), qui est appelé sur les images qui sont utilisés par le volet barre Outlook.

## <a name="cmfcoutlookbarpanecreate"></a><a name="create"></a>CMFCOutlookBarPane::Créer

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
[dans] Spécifie la fenêtre parente du contrôle de la vitre de barre Outlook. Ne doit pas être NULL.

*dwStyle (en)*<br/>
[dans] Le style de fenêtre.  Pour une liste de styles de fenêtre, voir [Windows Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*uiID*<br/>
[dans] L’ID de contrôle. Doit être unique pour permettre l’économie de l’état du contrôle.

*dwControlBarStyle (en)*<br/>
[dans] Spécifie les styles spéciaux qui définissent le comportement du contrôle de la vitre de barre Outlook lorsqu’il est détaché de la barre Outlook.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode a été réussie; autrement FALSE.

### <a name="remarks"></a>Notes

Pour construire `CMFCOutlookBarPane` un objet, appelez d’abord `Create`le constructeur, puis appelez, ce qui `CMFCOutlookBarPane` crée le contrôle de la barre Outlook et le fixe à l’objet.

Pour plus `dwControlBarStyle` d’informations sur voir [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

## <a name="cmfcoutlookbarpaneenablecontextmenuitems"></a><a name="enablecontextmenuitems"></a>CMFCOutlookBarPane::EnableContextMenuItems

Précise quels éléments de menu raccourcis sont affichés en mode personnalisation.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>Paramètres

*pButton*<br/>
[dans] Un pointeur sur un bouton de barre d’outils qu’un utilisateur a cliqué.

*pPopup (en)*<br/>
[dans] Un pointeur vers le menu raccourci.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le menu raccourci doit être affiché; autrement FALSE.

### <a name="remarks"></a>Notes

Remplacer cette méthode pour modifier le menu de raccourcis standard-cadre que le cadre affiche en mode personnalisation.

La implémentation par défaut vérifie le mode de personnalisation ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) et s’il est réglé sur TRUE, désactive tous les éléments de menu raccourci, sauf **Supprimer**. Ensuite, il passe juste les `CMFCToolBar::EnableContextMenuItems`paramètres d’entrée à .

> [!NOTE]
> *Le menu contextuelle* est synonyme de menu raccourci.

## <a name="cmfcoutlookbarpaneenablepagescrollmode"></a><a name="enablepagescrollmode"></a>CMFCOutlookBarPane::EnablePageScrollMode

Précise si les flèches de défilement sur le volet de barre Outlook avancent la liste des boutons page par page, ou bouton par bouton.

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>Paramètres

*bPageScroll (en)*<br/>
[dans] Si TRUE, activez le mode défilement de page. Si FALSE, désactiver le mode de défilement de page.

## <a name="cmfcoutlookbarpanegetregularcolor"></a><a name="getregularcolor"></a>CMFCOutlookBarPane::GetRegularColor

Retourne la couleur de texte régulière (c’est-à-dire non sélectionnée) du volet barre Outlook.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>Valeur de retour

La couleur de texte actuelle comme une valeur de couleur RGB.

### <a name="remarks"></a>Notes

Utilisez [CMFCOutlookBarPane::SetTextColor](#settextcolor) pour définir la couleur de texte actuelle (régulière et sélectionnée) de la barre Outlook. Vous pouvez obtenir la couleur de texte par défaut en appelant la fonction [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) avec l’indice COLOR_WINDOW.

## <a name="cmfcoutlookbarpaneisbackgroundtexture"></a><a name="isbackgroundtexture"></a>CMFCOutlookBarPane::IsBackgroundTexture

Détermine s’il y a une image de fond chargée pour la vitre de barre Outlook.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI s’il y a une image de fond à afficher; autrement FALSE.

### <a name="remarks"></a>Notes

Vous pouvez ajouter une image de fond en appelant [CMFCOutlookBarPane::SetBackImage](#setbackimage) fonction.

S’il n’y a pas d’image de fond, l’arrière-plan est peint avec une couleur spécifiée en utilisant [CMFCOutlookBarPane::SetBackColor](#setbackcolor).

## <a name="cmfcoutlookbarpaneisdrawshadedhighlight"></a><a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::IsDrawShadedHighlight

Détermine si la bordure du bouton est ombragée lorsqu’un bouton est surligné et qu’une image de fond est affichée.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si les bordures du bouton sont ombragées; autrement FALSE.

## <a name="cmfcoutlookbarpaneremoveallbuttons"></a><a name="removeallbuttons"></a>CMFCOutlookBarPane::RemoveAllButtons

Supprime tous les boutons de la vitre de la barre Outlook.

```
virtual void RemoveAllButtons();
```

## <a name="cmfcoutlookbarpaneremovebutton"></a><a name="removebutton"></a>CMFCOutlookBarPane::RemoveButton

Supprime le bouton qui a une pièce d’identité de commande spécifiée.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>Paramètres

*iIdCommand (en)*<br/>
[dans] Spécifie l’ID de commande d’un bouton à supprimer.

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton a été supprimé avec succès; FALSE si l’ID de commande spécifié n’est pas valide.

## <a name="cmfcoutlookbarpanesetbackcolor"></a><a name="setbackcolor"></a>CMFCOutlookBarPane::SetBackColor

Définit la couleur de fond de la barre Outlook.

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
[dans] Spécifie la nouvelle couleur de fond.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir la couleur de fond actuelle pour la barre Outlook. La couleur de fond n’est utilisée que s’il n’y a pas d’image de fond.

## <a name="cmfcoutlookbarpanesetbackimage"></a><a name="setbackimage"></a>CMFCOutlookBarPane::SetBackImage

Définit l’image de fond.

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>Paramètres

*uiImageID*<br/>
[dans] Spécifie l’ID de la ressource d’image.

### <a name="remarks"></a>Notes

Appelez cette méthode pour définir l’image de fond de la barre Outlook. La liste des images de fond est gérée par l’objet intégré [de classe CMFCToolBarImages.](../../mfc/reference/cmfctoolbarimages-class.md)

## <a name="cmfcoutlookbarpanesetdefaultstate"></a><a name="setdefaultstate"></a>CMFCOutlookBarPane::SetDefaultState

Réinitialise le volet à barres Outlook sur l’ensemble original de boutons.

```
void SetDefaultState();
```

### <a name="remarks"></a>Notes

Cette méthode restaure les boutons de barre Outlook à l’ensemble d’origine. Cette méthode `CMFCOutlookBarPane::RestoreOriginalstate`est comme , sauf qu’il ne déclenche pas un redessin de la vitre barre Outlook.

## <a name="cmfcoutlookbarpanesetextraspace"></a><a name="setextraspace"></a>CMFCOutlookBarPane::SetExtraSpace

Définit le nombre de pixels de rembourrage utilisés autour des boutons dans la vitre de la barre Outlook.

```
void SetExtraSpace()
```

## <a name="cmfcoutlookbarpanesettextcolor"></a><a name="settextcolor"></a>CMFCOutlookBarPane::SetTextColor

Définit les couleurs du texte régulier et mis en surbrillance dans le volet barre Outlook.

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>Paramètres

*clrRegText*<br/>
[dans] Spécifie la nouvelle couleur du texte non sélectionné.

*clrSelText*<br/>
[dans] Spécifie la nouvelle couleur pour le texte sélectionné.

## <a name="cmfcoutlookbarpanesettransparentcolor"></a><a name="settransparentcolor"></a>CMFCOutlookBarPane::SetTransparentColor

Définit la couleur transparente pour le volet barre Outlook.

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
Spécifie la nouvelle couleur transparente.

### <a name="remarks"></a>Notes

La couleur transparente est nécessaire pour afficher des images transparentes. Toute occurrence de cette couleur dans une image est peinte avec la couleur de fond à la place.  Il n’y a pas de mélange d’images de fond et de premier plan.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl, classe](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
