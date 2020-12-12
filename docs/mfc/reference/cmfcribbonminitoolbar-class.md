---
description: 'En savoir plus sur : classe CMFCRibbonMiniToolBar'
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
ms.openlocfilehash: 7215349323f8039bccb24860e4e5ad663bd24bcd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273941"
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
|`CMFCRibbonMiniToolBar::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
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

**En-tête :** afxRibbonMiniToolBar. h

## <a name="cmfcribbonminitoolbarsetcommands"></a><a name="setcommands"></a> CMFCRibbonMiniToolBar::SetCommands

Définit la liste des commandes à afficher sur la barre d'outils.

```cpp
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>Paramètres

*pRibbonBar*<br/>
dans Barre du ruban dans laquelle la mini-barre d’outils recherche les boutons à afficher.

*lstCommands*<br/>
dans Liste des commandes à afficher dans la mini-barre d’outils. Toutes les catégories de ruban sont recherchées pour trouver les boutons associés.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour définir la liste des commandes à afficher dans la mini-barre d’outils.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `SetCommands` méthode de la `CMFCRibbonMiniToolBar` classe. Cet extrait de code fait partie de l' [exemple de démonstration de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

## <a name="cmfcribbonminitoolbarshow"></a><a name="show"></a> CMFCRibbonMiniToolBar :: Show

Affiche la mini-barre d'outils au niveau des coordonnées d'écran spécifiées.

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Spécifie la position horizontale de la mini-barre d’outils en coordonnées d’écran.

*y*<br/>
dans Spécifie la position verticale de la mini-barre d’outils en coordonnées d’écran.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la mini-barre d’outils a été correctement affichée ; Sinon, FALSe.

## <a name="cmfcribbonminitoolbarshowwithcontextmenu"></a><a name="showwithcontextmenu"></a> CMFCRibbonMiniToolBar::ShowWithContextMenu

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
dans Spécifie la position horizontale du menu contextuel en coordonnées d’écran.

*y*<br/>
dans Spécifie la position verticale du menu contextuel en coordonnées d’écran.

*uiMenuResID*<br/>
dans Spécifie l’ID de ressource du menu contextuel à afficher.

*pWndOwner*<br/>
dans Identifie la fenêtre qui reçoit des messages à partir du menu contextuel.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le menu contextuel a été correctement affiché ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour afficher une mini-barre d’outils avec un menu contextuel. Le menu contextuel est positionné à 15 pixels sous la mini-barre d’outils.

## <a name="cmfcribbonminitoolbariscontextmenumode"></a><a name="iscontextmenumode"></a> CMFCRibbonMiniToolBar::IsContextMenuMode

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonminitoolbarisribbonminitoolbar"></a><a name="isribbonminitoolbar"></a> CMFCRibbonMiniToolBar::IsRibbonMiniToolBar

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
