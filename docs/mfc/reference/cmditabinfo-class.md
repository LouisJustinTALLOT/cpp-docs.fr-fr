---
description: 'En savoir plus sur : classe CMDITabInfo'
title: CMDITabInfo, classe
ms.date: 11/04/2016
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
helpviewer_keywords:
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
ms.openlocfilehash: 4769bedc48e143e2dae6f35c50d2d1fef488e655
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336667"
---
# <a name="cmditabinfo-class"></a>CMDITabInfo, classe

La `CMDITabInfo` classe est utilisée pour passer des paramètres à la méthode [CMDIFrameWndEx :: EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) . Définissez les membres de cette classe de manière à contrôler le comportement des groupes avec onglet MDI.

## <a name="syntax"></a>Syntaxe

```
class CMDITabInfo
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMDITabInfo::CMDITabInfo`|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMDITabInfo :: Serialize](#serialize)|Lit ou écrit cet objet dans une archive.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMDITabInfo :: m_bActiveTabCloseButton ;](#m_bactivetabclosebutton_)|Spécifie si un bouton **Fermer** est affiché sur l’étiquette de l’onglet actif.|
|[CMDITabInfo :: m_bAutoColor](#m_bautocolor)|Spécifie s’il faut colorer les onglets MDI.|
|[CMDITabInfo :: m_bDocumentMenu](#m_bdocumentmenu)|Spécifie si le groupe d’onglets affiche un menu contextuel qui affiche la liste des documents ouverts ou affiche des boutons de défilement.|
|[CMDITabInfo :: m_bEnableTabSwap](#m_benabletabswap)|Spécifie si l’utilisateur peut permuter les positions des onglets en les faisant glisser.|
|[CMDITabInfo :: m_bFlatFrame](#m_bflatframe)|Spécifie si les onglets ont un cadre plat.|
|[CMDITabInfo :: m_bTabCloseButton](#m_btabclosebutton)|Spécifie si chaque étiquette d’onglet affiche un bouton **Fermer** .|
|[CMDITabInfo :: m_bTabCustomTooltips](#m_btabcustomtooltips)|Spécifie si les info-bulles personnalisées sont activées.|
|[CMDITabInfo :: m_bTabIcons](#m_btabicons)|Spécifie s’il faut afficher les icônes sur les onglets MDI.|
|[CMDITabInfo :: m_nTabBorderSize](#m_ntabbordersize)|Spécifie la taille de la bordure de chaque fenêtre d’onglets.|
|[CMDITabInfo :: m_style](#m_style)|Spécifie le style des étiquettes d’onglet.|
|[CMDITabInfo :: m_tabLocation](#m_tablocation)|Spécifie si les étiquettes des onglets sont situées en haut ou en bas de la page.|

## <a name="remarks"></a>Notes

Cette classe spécifie les paramètres des groupes d’onglets MDI créés par l’infrastructure.

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir les valeurs des différentes variables membres dans la `CMDITabInfo` classe.

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxmdiclientareawnd. h

## <a name="cmditabinfom_bactivetabclosebutton"></a><a name="m_bactivetabclosebutton_"></a> CMDITabInfo :: m_bActiveTabCloseButton ;

Spécifie si un bouton **Fermer** est affiché sur l’étiquette de l’onglet actif.

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, l’étiquette de l’onglet actif affiche un bouton **Fermer** . Le bouton **Fermer** sera supprimé du coin supérieur droit de la zone d’onglet. Dans le cas contraire, l’étiquette de l’onglet actif n’affiche pas de bouton **Fermer** . Le bouton **Fermer** s’affiche dans l’angle supérieur droit de la zone d’onglet.

## <a name="cmditabinfom_bautocolor"></a><a name="m_bautocolor"></a> CMDITabInfo :: m_bAutoColor

Spécifie si chaque onglet MDI a sa propre couleur.

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, chaque onglet possède sa propre couleur. L’ensemble de couleurs est géré par la bibliothèque MFC. Dans le cas contraire, les onglets sont affichés en blanc. La valeur par défaut est FALSE.

## <a name="cmditabinfom_bdocumentmenu"></a><a name="m_bdocumentmenu"></a> CMDITabInfo :: m_bDocumentMenu

Spécifie si chaque onglet affiche un menu contextuel qui affiche la liste des documents ouverts sur le bord droit de la zone d’onglet.

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, chaque fenêtre d’onglets affiche un menu contextuel qui affiche la liste des documents ouverts sur le bord droit de la zone d’onglet. Dans le cas contraire, la fenêtre d’onglets affiche des boutons de défilement sur le bord droit de la zone d’onglet. La valeur par défaut est FALSE.

## <a name="cmditabinfom_benabletabswap"></a><a name="m_benabletabswap"></a> CMDITabInfo :: m_bEnableTabSwap

Spécifie si l’utilisateur peut permuter les positions des onglets en les faisant glisser.

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, l’utilisateur peut modifier les positions des onglets en faisant glisser les onglets. Dans le cas contraire, l’utilisateur ne peut pas modifier les positions des onglets. La valeur par défaut est TRUE.

## <a name="cmditabinfom_bflatframe"></a><a name="m_bflatframe"></a> CMDITabInfo :: m_bFlatFrame

Spécifie si chaque fenêtre d’onglets a un cadre plat.

```
BOOL m_bFlatFrame;
```

## <a name="cmditabinfom_btabclosebutton"></a><a name="m_btabclosebutton"></a> CMDITabInfo :: m_bTabCloseButton

Spécifie si chaque fenêtre d’onglets affiche un bouton **Fermer** .

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, chaque fenêtre d’onglet affiche le bouton **Fermer** sur le bord droit de l’onglet. Dans le cas contraire, le bouton **Fermer** n’est pas affiché. La valeur par défaut est TRUE.

## <a name="cmditabinfom_btabcustomtooltips"></a><a name="m_btabcustomtooltips"></a> CMDITabInfo :: m_bTabCustomTooltips

Spécifie si les onglets affichent des info-bulles.

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, l’application envoie un message AFX_WM_ON_GET_TAB_TOOLTIP au frame principal. Vous pouvez gérer ce message à l’aide de la macro ON_REGISTERED_MESSAGE.

## <a name="cmditabinfom_btabicons"></a><a name="m_btabicons"></a> CMDITabInfo :: m_bTabIcons

Spécifie s’il faut afficher les icônes sur les onglets MDI.

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>Notes

Si la valeur est TRUE, les icônes s’affichent sous chaque onglet MDI. Sinon, les icônes ne sont pas affichées sur les onglets. La valeur par défaut est FALSE.

## <a name="cmditabinfom_ntabbordersize"></a><a name="m_ntabbordersize"></a> CMDITabInfo :: m_nTabBorderSize

Spécifie la taille de la bordure, en pixels, de chaque fenêtre d’onglets.

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>Notes

[CMFCVisualManager :: GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) retourne la valeur par défaut.

## <a name="cmditabinfom_style"></a><a name="m_style"></a> CMDITabInfo :: m_style

Spécifie le style des étiquettes d’onglet.

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>Notes

Spécifiez l’un des styles suivants pour les étiquettes d’onglet :

|Macro|Description|
|-|-|
|STYLE_3D|style 3D.  |
|STYLE_3D_ONENOTE|Style Microsoft OneNote.  |
|STYLE_3D_VS2005|Microsoft Visual Studio style 2005.  |
|STYLE_3D_SCROLLED|style 3D avec des étiquettes de tabulation rectangle.  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|Style à deux dimensions avec barre de défilement horizontale partagée.  |
|STYLE_3D_ROUNDED_SCROLL|style 3D avec étiquettes d’onglets arrondis.  |

## <a name="cmditabinfom_tablocation"></a><a name="m_tablocation"></a> CMDITabInfo :: m_tabLocation

Spécifie si les étiquettes des onglets sont situées en haut ou en bas de la page.

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>Notes

Appliquez les onglets à l’un des indicateurs d’emplacement suivants :

- LOCATION_BOTTOM : les étiquettes des onglets sont situées en bas de la page.

- LOCATION_TOP : les étiquettes des onglets sont situées en haut de la page

## <a name="cmditabinfoserialize"></a><a name="serialize"></a> CMDITabInfo :: Serialize

Lit ou écrit cet objet à partir d’une archive ou d’une archive.

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*ar*<br/>
dans Objet de [classe CArchive](../../mfc/reference/carchive-class.md) à sérialiser.

## <a name="see-also"></a>Voir aussi

[CMDIFrameWndEx, classe](../../mfc/reference/cmdiframewndex-class.md)<br/>
[Groupes avec onglet MDI](../../mfc/mdi-tabbed-groups.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
