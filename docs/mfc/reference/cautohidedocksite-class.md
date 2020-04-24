---
title: Classe CAutoHideDockSite
ms.date: 11/04/2016
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
ms.openlocfilehash: 1f23729ced02a151c6186bdcc72cb8938416be46
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753002"
---
# <a name="cautohidedocksite-class"></a>Classe CAutoHideDockSite

Le `CAutoHideDockSite` prolongement de la [classe CDockSite](../../mfc/reference/cdocksite-class.md) pour mettre en œuvre des vitres de quai auto-cacher.

## <a name="syntax"></a>Syntaxe

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|||
|-|-|
|Nom|Description|
|`CAutoHideDockSite::CAutoHideDockSite`|Construit un objet `CAutoHideDockSite`.|
|`CAutoHideDockSite::~CAutoHideDockSite`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|Nom|Description|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Indique si `CAutoHideDockSite` le est affiché sur le menu de la vitre.|
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|Détermine si un objet de vitre de base est dérivé de la [classe CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md).|
|[CAutoHideDockSite::DockPane](#dockpane)|Docks une vitre `CAuotHideDockSite` à cet objet.|
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|Récupère la taille du site du quai dans les coordonnées de l’écran.|
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|Redessiner la vitre `CAutoHideDockSite` avec les marges globales et l’espacement des boutons.|
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|Définit la marge sur le côté gauche de la barre d’amarrage.|
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|Définit la marge sur le côté droit de la barre d’amarrage.|
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|Appelle [CMFCAutoHideBar:UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) pour les `CAutoHideDockSite`objets sur le .|

### <a name="data-members"></a>Données membres

|||
|-|-|
|Nom|Description|
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|Définit la taille de l’espace entre les barres d’outils et le bord de la barre d’amarrage. Cet espace est mesuré à partir du bord gauche ou du bord supérieur, en fonction de l’alignement de l’espace du quai.|

## <a name="remarks"></a>Notes

Lorsque vous appelez [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes), `CAutoHideDockSite` le cadre crée automatiquement un objet. Dans la plupart des cas, vous ne devriez pas avoir à instantané ou utiliser cette classe directement.

La barre d’amarrage est l’espace entre le côté gauche de la vitre du quai et le côté gauche de la [classe CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CAutoHideDockSite` récupérer `CMFCAutoHideBar` un objet à partir d’un objet, et comment définir les marges gauche et droite de la barre d’amarrage.

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête:** afxautohidedocksite.h

## <a name="cautohidedocksitecanacceptpane"></a><a name="canacceptpane"></a>CAutoHideDockSite::CanAcceptPane

Détermine si un volet de base est un objet [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) ou dérivé de `CMFCAutoHideBar`.

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pBar (pBar)*|[dans] Le volet de base que le cadre teste.|

### <a name="return-value"></a>Valeur de retour

VRAI si *pBar* `CMFCAutoHideBar`est dérivé de ; FALSE autrement.

### <a name="remarks"></a>Notes

Si un objet de vitre `CMFCAutoHideBar`de base `CAutoHideDockSite`est dérivé, il peut contenir un .

## <a name="cautohidedocksitedockpane"></a><a name="dockpane"></a>CAutoHideDockSite::DockPane

Docks un volet à cet objet [CAutoHideDockSite.](../../mfc/reference/cautohidedocksite-class.md)

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*Pwnd*|[dans] La vitre que le cadre docks.|
|*dockMethod*|[dans] Options d’amarrage pour la vitre.|
|*lpRect*|[dans] Un rectangle qui spécifie les limites de la vitre amarré.|

### <a name="remarks"></a>Notes

L’implémentation par défaut n’utilise pas le *paramètre dockMethod*, qui est prévu pour une utilisation future.

Si *lpRect* est NULL, le cadre met la vitre dans l’emplacement par défaut sur le site du quai. Si le site du quai est horizontal, l’emplacement par défaut se trouve à l’extrême gauche du quai. Dans le cas contraire, l’emplacement par défaut se trouve en haut du site du quai.

## <a name="cautohidedocksitegetalignrect"></a><a name="getalignrect"></a>CAutoHideDockSite::GetAlignRect

Récupère la taille du site du quai dans les coordonnées de l’écran.

```cpp
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*Rect*|[dans] Une référence à un rectangle. La méthode stocke la taille du site du quai dans ce rectangle.|

### <a name="remarks"></a>Notes

Le rectangle est ajusté pour les marges offset de sorte qu’ils ne sont pas inclus.

## <a name="cautohidedocksitem_nextraspace"></a><a name="m_nextraspace"></a>CAutoHideDockSite::m_nExtraSpace

La taille de l’espace entre les bords de la [classe CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) et les objets de classe [CMFCAutoHideBar.](../../mfc/reference/cmfcautohidebar-class.md)

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>Notes

Lorsqu’un `CMFCAutoHideBar` est amarré à un, `CAutoHideDockSite`il ne doit pas occuper l’ensemble du site du quai. Cette variable globale contrôle l’espace supplémentaire entre `CMFCAutoHideBar` la `CAutoHideDockSite` bordure gauche ou supérieure du bord et le bord correspondant. L’utilisation du bord supérieur ou gauche dépend de l’alignement actuel.

## <a name="cautohidedocksitesetoffsetleft"></a><a name="setoffsetleft"></a>CAutoHideDockSite::SetOffsetLeft

Définit la marge sur le côté gauche de la barre d’amarrage.

```cpp
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>Paramètres

*nOffset (en anglais)*<br/>
[dans] Le nouveau décalage.

### <a name="remarks"></a>Notes

Les objets [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) sont positionnés statiquement sur l’objet. `CAutoHideDockSite` Cela signifie que l’utilisateur ne `CMFCAutoHideBar` peut pas modifier manuellement l’emplacement des objets. La `SetOffsetLeft` méthode contrôle l’espacement entre le côté `CMFCAutoHideBar` gauche de la `CAutoHideDockSite`gauche-le plus et le côté gauche de la .

## <a name="cautohidedocksitesetoffsetright"></a><a name="setoffsetright"></a>CAutoHideDockSite::SetOffsetRight

Définit la marge sur le côté droit de la barre d’amarrage.

```cpp
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>Paramètres

*nOffset (en anglais)*<br/>
[dans] Le nouveau décalage.

### <a name="remarks"></a>Notes

Les objets [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) sont positionnés statiquement sur l’objet. `CAutoHideDockSite` Cela signifie que l’utilisateur ne peut `CMFCAutoHideBar` pas modifier manuellement l’emplacement des objets. La `SetOffsetRight` méthode contrôle l’espacement entre le côté `CMFCAutoHideBar` droit de la `CAutoHideDockSite`partie droite et le côté droit de la .

## <a name="cautohidedocksiterepositionpanes"></a><a name="repositionpanes"></a>CAutoHideDockSite::RepositionPanes

Redessaille les vitres sur le [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md).

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*rectNewClientArea*|[dans] Une valeur réservée.|

### <a name="remarks"></a>Notes

La mise en œuvre par défaut n’utilise pas *rectNewClientArea*. Il redessiner les vitres avec les marges globales des barres d’outils et l’espacement des boutons.

## <a name="cautohidedocksiteunsetautohidemode"></a><a name="unsetautohidemode"></a>CAutoHideDockSite::UnSetAutoHideMode

Appelle [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) pour les objets sur le site du quai.

```cpp
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pAutoHideToolbar*|[dans] Un pointeur à un volet d’objet [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) situé sur le `CAutoHideDockSite`.|

### <a name="remarks"></a>Notes

Cette méthode recherche la ligne qui contient *pAutoHideToolbar*. Il `CMFCAutoHideBar.UnSetAutoHideMode` appelle tous `CMFCAutoHideBar` les objets de cette rangée. Si *pAutoHideToolbar* n’est pas trouvé ou `CMFCAutoHideBar.UnSetAutoHideMode` il `CMFCAutoHideBar` est NULL, cette méthode nécessite tous les objets sur le `CAutoHideDockSite`.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite, classe](../../mfc/reference/cdocksite-class.md)
