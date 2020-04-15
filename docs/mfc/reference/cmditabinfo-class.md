---
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
ms.openlocfilehash: 0d230d2a3401ab556adc1183f4c4210ec6ff3c29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370029"
---
# <a name="cmditabinfo-class"></a>CMDITabInfo, classe

La `CMDITabInfo` classe est utilisée pour transmettre les paramètres à la méthode [CMDIFrameWndEx::EnableMDITabbedGroups.](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) Définissez les membres de cette classe de manière à contrôler le comportement des groupes avec onglet MDI.

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
|[CMDITabInfo::Serialize](#serialize)|Lit ou écrit cet objet dans une archive.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMDITabInfo:m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Précise si un bouton **Close** est affiché sur l’étiquette de l’onglet actif.|
|[CMDITabInfo:m_bAutoColor](#m_bautocolor)|Précise s’il faut colorer les onglets MDI.|
|[CMDITabInfo:m_bDocumentMenu](#m_bdocumentmenu)|Précise si le groupe d’onglets affiche un menu popup qui affiche une liste de documents ouverts ou affiche des boutons de défilement.|
|[CMDITabInfo:m_bEnableTabSwap](#m_benabletabswap)|Précise si l’utilisateur peut échanger les positions des onglets en faisant glisser.|
|[CMDITabInfo:m_bFlatFrame](#m_bflatframe)|Précise si les onglets ont un cadre plat.|
|[CMDITabInfo:m_bTabCloseButton](#m_btabclosebutton)|Précise si chaque étiquette d’onglet affiche un bouton **Close.**|
|[CMDITabInfo:m_bTabCustomTooltips](#m_btabcustomtooltips)|Précise si les outils personnalisés sont activés.|
|[CMDITabInfo:m_bTabIcons](#m_btabicons)|Précise s’il faut afficher des icônes sur les onglets MDI.|
|[CMDITabInfo:m_nTabBorderSize](#m_ntabbordersize)|Spécifie la taille de la bordure de chaque fenêtre d’onglet.|
|[CMDITabInfo:m_style](#m_style)|Spécifie le style des étiquettes de l’onglet.|
|[CMDITabInfo:m_tabLocation](#m_tablocation)|Précise si les étiquettes d’onglets sont situées en haut ou en bas de la page.|

## <a name="remarks"></a>Notes

Cette classe spécifie les paramètres des groupes d’onglets MDI que le cadre crée.

## <a name="example"></a>Exemple

L’exemple suivant montre comment définir les valeurs `CMDITabInfo` des différentes variables des membres en classe.

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxmdiclientareawnd.h

## <a name="cmditabinfom_bactivetabclosebutton"></a><a name="m_bactivetabclosebutton_"></a>CMDITabInfo:m_bActiveTabCloseButton;

Précise si un bouton **Close** est affiché sur l’étiquette de l’onglet actif.

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>Notes

Si VRAI, l’étiquette de l’onglet actif affichera un bouton **Close.** Le bouton **Close** sera retiré du coin supérieur droit de la zone de l’onglet. Dans le cas contraire, l’étiquette de l’onglet actif n’affichera pas un bouton **Close.** Le bouton **Close** apparaîtra dans le coin supérieur droit de la zone de l’onglet.

## <a name="cmditabinfom_bautocolor"></a><a name="m_bautocolor"></a>CMDITabInfo:m_bAutoColor

Précise si chaque onglet MDI a sa propre couleur.

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>Notes

Si VRAI, chaque onglet aura sa propre couleur. L’ensemble de couleurs est géré par la bibliothèque MFC. Sinon, les onglets sont affichés en blanc. La valeur par défaut est FALSE.

## <a name="cmditabinfom_bdocumentmenu"></a><a name="m_bdocumentmenu"></a>CMDITabInfo:m_bDocumentMenu

Précise si chaque onglet affiche un menu popup qui affiche une liste de documents ouverts sur le bord droit de la zone de l’onglet.

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>Notes

Si VRAI, chaque onglet windows affiche un menu popup qui affiche une liste de documents ouverts sur le bord droit de la zone de l’onglet; Sinon, la fenêtre de l’onglet affiche des boutons de défilement sur le bord droit de la zone de l’onglet. La valeur par défaut est FALSE.

## <a name="cmditabinfom_benabletabswap"></a><a name="m_benabletabswap"></a>CMDITabInfo:m_bEnableTabSwap

Précise si l’utilisateur peut échanger les positions des onglets en faisant glisser.

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>Notes

Si VRAI, l’utilisateur peut changer les positions des onglets en faisant glisser les onglets. Dans le cas contraire, l’utilisateur ne peut pas modifier les positions des onglets. La valeur par défaut est TRUE.

## <a name="cmditabinfom_bflatframe"></a><a name="m_bflatframe"></a>CMDITabInfo:m_bFlatFrame

Précise si chaque fenêtre d’onglet a un cadre plat.

```
BOOL m_bFlatFrame;
```

## <a name="cmditabinfom_btabclosebutton"></a><a name="m_btabclosebutton"></a>CMDITabInfo:m_bTabCloseButton

Précise si chaque fenêtre d’onglet affiche un bouton **Close.**

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>Notes

Si TRUE, chaque fenêtre d’onglet affiche le bouton **Fermer** sur le bord droit de l’onglet. Sinon, le bouton **Close** n’est pas affiché. La valeur par défaut est TRUE.

## <a name="cmditabinfom_btabcustomtooltips"></a><a name="m_btabcustomtooltips"></a>CMDITabInfo:m_bTabCustomTooltips

Précise si les onglets affichent des outils.

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>Notes

Si TRUE, l’application envoie un message AFX_WM_ON_GET_TAB_TOOLTIP au cadre principal. Vous pouvez gérer ce message en utilisant la macro ON_REGISTERED_MESSAGE.

## <a name="cmditabinfom_btabicons"></a><a name="m_btabicons"></a>CMDITabInfo:m_bTabIcons

Précise s’il faut afficher des icônes sur les onglets MDI.

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>Notes

Si VRAI, les icônes sont affichées sur chaque onglet MDI. Sinon, les icônes ne sont pas affichées sur les onglets. La valeur par défaut est FALSE.

## <a name="cmditabinfom_ntabbordersize"></a><a name="m_ntabbordersize"></a>CMDITabInfo:m_nTabBorderSize

Spécifie la taille de la bordure, en pixels, de chaque fenêtre d’onglet.

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>Notes

[CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) retourne la valeur par défaut.

## <a name="cmditabinfom_style"></a><a name="m_style"></a>CMDITabInfo:m_style

Spécifie le style des étiquettes de l’onglet.

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>Notes

Spécifier l’un des styles suivants pour les étiquettes de l’onglet :

|||
|-|-|
|STYLE_3D|Style 3D.  |
|STYLE_3D_ONENOTE|Style Microsoft OneNote.  |
|STYLE_3D_VS2005|Microsoft Visual Studio 2005 style.  |
|STYLE_3D_SCROLLED|Style 3D avec étiquettes d’onglet rectangle.  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|Style plat avec barre de défilement horizontal partagé.  |
|STYLE_3D_ROUNDED_SCROLL|Style 3D avec étiquettes d’onglet rond.  |

## <a name="cmditabinfom_tablocation"></a><a name="m_tablocation"></a>CMDITabInfo:m_tabLocation

Précise si les étiquettes d’onglets sont situées en haut ou en bas de la page.

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>Notes

Appliquer sur les onglets l’un des drapeaux de localisation suivants:

- LOCATION_BOTTOM : les étiquettes d’onglets sont situées au bas de la page.

- LOCATION_TOP : les étiquettes d’onglets sont situées en haut de la page

## <a name="cmditabinfoserialize"></a><a name="serialize"></a>CMDITabInfo::Serialize

Lit ou écrit cet objet à partir d’une archive ou d’une archive.

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*Ar*<br/>
[dans] Un objet [de classe CArchive](../../mfc/reference/carchive-class.md) à sérialiser.

## <a name="see-also"></a>Voir aussi

[Classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)<br/>
[Groupes MDI Tabbed](../../mfc/mdi-tabbed-groups.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
