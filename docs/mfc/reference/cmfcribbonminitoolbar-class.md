---
title: CMFCRibbonMiniToolBar, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
ms.openlocfilehash: 10b1d35c331df6563d09be0bea3c97c73e89acaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375087"
---
# <a name="cmfcribbonminitoolbar-class"></a>CMFCRibbonMiniToolBar, classe

Implémente une barre d'outils contextuelle.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|Constructeur par défaut.|
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCRibbonMiniToolBar::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|(Substitue `CMFCPopupMenu::IsRibbonMiniToolBar`.)|
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|Définit la liste des commandes à afficher sur la barre d'outils.|
|[CMFCRibbonMiniToolBar::Show](#show)|Affiche la mini-barre d'outils au niveau des coordonnées d'écran spécifiées.|
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|Affiche la mini-barre d'outils avec un menu contextuel.|

## <a name="remarks"></a>Notes

La mini-barre d'outils s'affiche généralement après que l'utilisateur sélectionne un objet dans un document. Ainsi, quand l'utilisateur sélectionne un bloc de texte dans un programme de traitement de texte, l'application affiche une mini-barre d'outils qui contient des commandes de mise en forme de texte.

La mini-barre d'outils devient transparente quand le pointeur de la souris sort des limites de la mini-barre d'outils.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

`CMFCRibbonPanelMenu`

[CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxRibbonMiniToolBar.h

## <a name="cmfcribbonminitoolbarsetcommands"></a><a name="setcommands"></a>CMFCRibbonMiniToolBar::SetCommands

Définit la liste des commandes à afficher sur la barre d'outils.

```
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>Paramètres

*pRibbonBar (en)*<br/>
[dans] La barre de ruban que la mini barre d’outils recherche les boutons à afficher.

*lstCommands*<br/>
[dans] La liste des commandes à afficher sur la mini barre d’outils. Toutes les catégories de ruban sont recherchées pour trouver les boutons associés.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour définir la liste des commandes à afficher dans la mini barre d’outils.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `SetCommands` utiliser `CMFCRibbonMiniToolBar` la méthode de la classe. Cet extrait de code fait partie de [l’échantillon de démonstration ms Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

## <a name="cmfcribbonminitoolbarshow"></a><a name="show"></a>CMFCRibbonMiniToolBar::Show

Affiche la mini-barre d'outils au niveau des coordonnées d'écran spécifiées.

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
[dans] Spécifie la position horizontale de la mini barre d’outils dans les coordonnées de l’écran.

*y*<br/>
[dans] Spécifie la position verticale de la mini barre d’outils dans les coordonnées de l’écran.

### <a name="return-value"></a>Valeur de retour

VRAI si la mini barre d’outils a été affichée avec succès; autrement, FALSE.

## <a name="cmfcribbonminitoolbarshowwithcontextmenu"></a><a name="showwithcontextmenu"></a>CMFCRibbonMiniToolBar:ShowWithContextMenu

Affiche la mini-barre d'outils avec un menu contextuel.

```
BOOL ShowWithContextMenu(
    int x,
    int y,
    UINT uiMenuResID,
    CWnd* pWndOwner);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
[dans] Spécifie la position horizontale du menu contexte dans les coordonnées de l’écran.

*y*<br/>
[dans] Spécifie la position verticale du menu contexte dans les coordonnées de l’écran.

*uiMenuResID*<br/>
[dans] Spécifie l’ID de ressources du menu contextuelle à afficher.

*pWndOwner (en)*<br/>
[dans] Identifie la fenêtre qui reçoit des messages du menu contextuel.

### <a name="return-value"></a>Valeur de retour

VRAI si le menu contextuelle a été affiché avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour afficher une mini barre d’outils qui a un menu contextuelle. Le menu contextuelle est positionné à 15 pixels sous la mini barre d’outils.

## <a name="cmfcribbonminitoolbariscontextmenumode"></a><a name="iscontextmenumode"></a>CMFCRibbonMiniToolBar::IsContextMenuMode

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcribbonminitoolbarisribbonminitoolbar"></a><a name="isribbonminitoolbar"></a>CMFCRibbonMiniToolBar::IsRibbonMiniToolBar

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
