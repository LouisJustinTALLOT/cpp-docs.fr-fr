---
title: CAutoHideDockSite, classe
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
ms.openlocfilehash: 2779e643b15179b0017535fbfbb144f94e1aedbe
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562010"
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite, classe

`CAutoHideDockSite`Étend la [classe CDockSite](../../mfc/reference/cdocksite-class.md) pour implémenter les volets d’ancrage à masquage automatique.

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
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Indique si le `CAutoHideDockSite` est affiché dans le menu du volet.|
|[CAutoHideDockSite :: CanAcceptPane](#canacceptpane)|Détermine si un objet volet de base est dérivé de la [classe CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md).|
|[CAutoHideDockSite ::D ockPane](#dockpane)|Ancre un volet à cet `CAuotHideDockSite` objet.|
|[CAutoHideDockSite :: GetAlignRect](#getalignrect)|Récupère la taille du site d’ancrage en coordonnées d’écran.|
|[CAutoHideDockSite :: RepositionPanes](#repositionpanes)|Redessine le volet sur le `CAutoHideDockSite` avec les marges globales et l’espacement du bouton.|
|[CAutoHideDockSite :: SetOffsetLeft](#setoffsetleft)|Définit la marge sur le côté gauche de la barre d’ancrage.|
|[CAutoHideDockSite :: SetOffsetRight](#setoffsetright)|Définit la marge à droite de la barre d’ancrage.|
|[CAutoHideDockSite :: UnSetAutoHideMode](#unsetautohidemode)|Appelle [CMFCAutoHideBar :: UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) pour les objets sur le `CAutoHideDockSite` .|

### <a name="data-members"></a>Données membres

|||
|-|-|
|Nom|Description|
|[CAutoHideDockSite :: m_nExtraSpace](#m_nextraspace)|Définit la taille de l’espace entre les barres d’outils et le bord de la barre d’ancrage. Cet espace est mesuré à partir du bord gauche ou du bord supérieur, en fonction de l’alignement de l’espace d’ancrage.|

## <a name="remarks"></a>Notes

Quand vous appelez [CFrameWndEx :: EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes), l’infrastructure crée automatiquement un `CAutoHideDockSite` objet. Dans la plupart des cas, vous ne devez pas avoir à instancier ou utiliser cette classe directement.

La barre d’ancrage est l’intervalle entre le côté gauche du volet d’ancrage et le côté gauche de la [classe cmfcautohidebutton,](../../mfc/reference/cmfcautohidebutton-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer un `CAutoHideDockSite` objet à partir d' `CMFCAutoHideBar` un objet et comment définir les marges gauche et droite de la barre d’ancrage.

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête :** afxautohidedocksite. h

## <a name="cautohidedocksitecanacceptpane"></a><a name="canacceptpane"></a> CAutoHideDockSite :: CanAcceptPane

Détermine si un volet de base est un objet [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) ou s’il est dérivé de `CMFCAutoHideBar` .

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Paramètres

*pBar*\
dans Volet de base que le Framework teste.

### <a name="return-value"></a>Valeur de retour

TRUE si *pBar* est dérivé de `CMFCAutoHideBar` ; FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Si un objet volet de base est dérivé de `CMFCAutoHideBar` , il peut contenir un `CAutoHideDockSite` .

## <a name="cautohidedocksitedockpane"></a><a name="dockpane"></a> CAutoHideDockSite ::D ockPane

Ancre un volet à cet objet [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) .

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Paramètres

*pWnd*\
dans Volet ancré par le Framework.

*dockMethod*\
dans Options d’ancrage du volet.

*lpRect*\
dans Rectangle qui spécifie les limites du volet ancré.

### <a name="remarks"></a>Notes

L’implémentation par défaut n’utilise pas le paramètre *dockMethod*, qui est fourni pour une utilisation ultérieure.

Si *lpRect* a la valeur null, le Framework place le volet à l’emplacement par défaut sur le site d’ancrage. Si le site d’ancrage est horizontal, l’emplacement par défaut est à l’extrême gauche du site d’accueil. Dans le cas contraire, l’emplacement par défaut se trouve en haut du site d’ancrage.

## <a name="cautohidedocksitegetalignrect"></a><a name="getalignrect"></a> CAutoHideDockSite :: GetAlignRect

Récupère la taille du site d’ancrage en coordonnées d’écran.

```cpp
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>Paramètres

*rectangulaire*\
dans Référence à un rectangle. La méthode stocke la taille du site d’ancrage dans ce rectangle.

### <a name="remarks"></a>Notes

Le rectangle est ajusté pour les marges de décalage afin qu’elles ne soient pas incluses.

## <a name="cautohidedocksitem_nextraspace"></a><a name="m_nextraspace"></a> CAutoHideDockSite :: m_nExtraSpace

Taille de l’espace entre les bords de la [classe CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) et les objets de la [classe CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) .

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>Notes

Lorsqu’un `CMFCAutoHideBar` est ancré à un `CAutoHideDockSite` , il ne doit pas occuper l’intégralité du site d’ancrage. Cette variable globale contrôle l’espace supplémentaire entre la bordure gauche ou supérieure de `CMFCAutoHideBar` et le bord correspondant `CAutoHideDockSite` . Le fait que le bord supérieur ou gauche soit utilisé dépend de l’alignement actuel.

## <a name="cautohidedocksitesetoffsetleft"></a><a name="setoffsetleft"></a> CAutoHideDockSite :: SetOffsetLeft

Définit la marge sur le côté gauche de la barre d’ancrage.

```cpp
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>Paramètres

*nOffset*<br/>
dans Nouvel offset.

### <a name="remarks"></a>Notes

Les objets [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) sont positionnés de manière statique sur l' `CAutoHideDockSite` objet. Cela signifie que l’utilisateur ne peut pas modifier manuellement l’emplacement des `CMFCAutoHideBar` objets. La `SetOffsetLeft` méthode contrôle l’espacement entre le côté gauche du côté gauche `CMFCAutoHideBar` et le côté gauche du `CAutoHideDockSite` .

## <a name="cautohidedocksitesetoffsetright"></a><a name="setoffsetright"></a> CAutoHideDockSite :: SetOffsetRight

Définit la marge à droite de la barre d’ancrage.

```cpp
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>Paramètres

*nOffset*<br/>
dans Nouvel offset.

### <a name="remarks"></a>Notes

Les objets [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) sont positionnés de manière statique sur l' `CAutoHideDockSite` objet. Cela signifie que l’utilisateur ne peut pas modifier manuellement l’emplacement des `CMFCAutoHideBar` objets. La `SetOffsetRight` méthode contrôle l’espacement entre le côté droit du côté droit `CMFCAutoHideBar` et le côté droit du `CAutoHideDockSite` .

## <a name="cautohidedocksiterepositionpanes"></a><a name="repositionpanes"></a> CAutoHideDockSite :: RepositionPanes

Redessine les volets sur le [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md).

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Paramètres

*rectNewClientArea*\
dans Valeur réservée.

### <a name="remarks"></a>Notes

L’implémentation par défaut n’utilise pas *rectNewClientArea*. Il redessine les volets avec les marges et l’espacement de bouton globaux de la barre d’outils.

## <a name="cautohidedocksiteunsetautohidemode"></a><a name="unsetautohidemode"></a> CAutoHideDockSite :: UnSetAutoHideMode

Appelle [CMFCAutoHideBar :: UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) pour les objets sur le site d’ancrage.

```cpp
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>Paramètres

*pAutoHideToolbar*\
dans Pointeur vers un volet objet [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) situé sur le `CAutoHideDockSite` .

### <a name="remarks"></a>Notes

Cette méthode recherche la ligne qui contient *pAutoHideToolbar*. Elle appelle `CMFCAutoHideBar.UnSetAutoHideMode` pour tous les `CMFCAutoHideBar` objets de cette ligne. Si *pAutoHideToolbar* est introuvable ou qu’il a la valeur null, cette méthode appelle `CMFCAutoHideBar.UnSetAutoHideMode` pour tous les `CMFCAutoHideBar` objets sur le `CAutoHideDockSite` .

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite, classe](../../mfc/reference/cdocksite-class.md)
