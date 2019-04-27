---
title: Cmfcribbonminitoolbar, classe
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
ms.openlocfilehash: 394182aa0f9c967524ed0db510d0b9cc0739118e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151888"
---
# <a name="cmfcribbonminitoolbar-class"></a>Cmfcribbonminitoolbar, classe

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
|`CMFCRibbonMiniToolBar::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|
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

## <a name="requirements"></a>Configuration requise

**En-tête :** afxRibbonMiniToolBar.h

##  <a name="setcommands"></a>  CMFCRibbonMiniToolBar::SetCommands

Définit la liste des commandes à afficher sur la barre d'outils.

```
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>Paramètres

*pRibbonBar*<br/>
[in] La barre du ruban qui consiste à rechercher la mini-barre d’outils pour les boutons à afficher.

*lstCommands*<br/>
[in] La liste des commandes à afficher sur la mini-barre d’outils. Toutes les catégories de ruban sont explorés pour rechercher les boutons associés.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour définir la liste des commandes à afficher dans la mini-barre d’outils.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le `SetCommands` méthode de la `CMFCRibbonMiniToolBar` classe. Cet extrait de code fait partie de la [exemple de démonstration de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

##  <a name="show"></a>  CMFCRibbonMiniToolBar::Show

Affiche la mini-barre d'outils au niveau des coordonnées d'écran spécifiées.

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
[in] Spécifie la position horizontale de la mini-barre d’outils en coordonnées d’écran.

*y*<br/>
[in] Spécifie la position verticale de la mini-barre d’outils en coordonnées d’écran.

### <a name="return-value"></a>Valeur de retour

TRUE si la mini-barre d’outils a été affiché avec succès ; Sinon, FALSE.

##  <a name="showwithcontextmenu"></a>  CMFCRibbonMiniToolBar::ShowWithContextMenu

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
[in] Spécifie la position horizontale du menu contextuel en coordonnées d’écran.

*y*<br/>
[in] Spécifie la position verticale du menu contextuel en coordonnées d’écran.

*uiMenuResID*<br/>
[in] Spécifie l’ID de ressource du menu contextuel à afficher.

*pWndOwner*<br/>
[in] Identifie la fenêtre qui reçoit des messages dans le menu contextuel.

### <a name="return-value"></a>Valeur de retour

TRUE si le menu contextuel a été affiché avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour afficher une mini-barre d’outils qui a un menu contextuel. Le menu contextuel est positionnés 15 pixels sous la mini barre d’outils.

##  <a name="iscontextmenumode"></a>  CMFCRibbonMiniToolBar::IsContextMenuMode

Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="isribbonminitoolbar"></a>  CMFCRibbonMiniToolBar::IsRibbonMiniToolBar

Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
