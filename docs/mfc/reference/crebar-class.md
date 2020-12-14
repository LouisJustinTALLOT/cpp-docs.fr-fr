---
description: 'En savoir plus sur : CReBar, classe'
title: CReBar (classe)
ms.date: 11/19/2018
f1_keywords:
- CReBar
- AFXEXT/CReBar
- AFXEXT/CReBar::AddBar
- AFXEXT/CReBar::Create
- AFXEXT/CReBar::GetReBarCtrl
helpviewer_keywords:
- CReBar [MFC], AddBar
- CReBar [MFC], Create
- CReBar [MFC], GetReBarCtrl
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
ms.openlocfilehash: 138add510b76f21f5776f809b1551eb35d554d68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343125"
---
# <a name="crebar-class"></a>CReBar (classe)

Barre de contrôles qui fournit des informations de disposition, de persistance et d'état pour les contrôles rebar.

## <a name="syntax"></a>Syntaxe

```
class CReBar : public CControlBar
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CReBar :: AddBar](#addbar)|Ajoute une bande à un Rebar.|
|[CReBar :: Create](#create)|Crée le contrôle rebar et l’attache à l' `CReBar` objet.|
|[CReBar :: GetReBarCtrl](#getrebarctrl)|Autorise l’accès direct au contrôle commun sous-jacent.|

## <a name="remarks"></a>Notes

Un objet rebar peut contenir plusieurs fenêtres enfants, généralement d'autres contrôles, notamment des zones d'édition, des barres d'outils et des zones de liste. Un objet rebar peut afficher les fenêtres enfants sur une image bitmap spécifiée. Votre application peut redimensionner automatiquement le rebar, ou l’utilisateur peut redimensionner manuellement le rebar en cliquant ou en faisant glisser sa barre de redimensionnement.

![Exemple de RebarMenu](../../mfc/reference/media/vc4sc61.gif "Exemple de RebarMenu")

## <a name="rebar-control"></a>Contrôle rebar

Un objet Rebar se comporte de la même façon qu’un objet Toolbar. Un Rebar utilise le mécanisme de glisser-déplacer pour redimensionner ses bandes. Un contrôle rebar peut contenir une ou plusieurs bandes, chaque bande ayant n’importe quelle combinaison d’une barre de redimensionnement, d’une image bitmap, d’une étiquette de texte et d’une fenêtre enfant. Toutefois, les bandes ne peuvent pas contenir plus d’une fenêtre enfant.

`CReBar` utilise la classe [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) pour fournir son implémentation. Vous pouvez accéder au contrôle rebar via [GetReBarCtrl](#getrebarctrl) pour tirer parti des options de personnalisation du contrôle. Pour plus d’informations sur les contrôles rebar, consultez `CReBarCtrl` . Pour plus d’informations sur l’utilisation des contrôles rebar, consultez [utilisation de CReBarCtrl](../../mfc/using-crebarctrl.md).

> [!CAUTION]
> Les objets Rebar et Rebar Control ne prennent pas en charge l’ancrage de la barre de contrôle MFC. Si `CRebar::EnableDocking` est appelé, votre application effectue une assertion.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

## <a name="crebaraddbar"></a><a name="addbar"></a> CReBar :: AddBar

Appelez cette fonction membre pour ajouter une bande au Rebar.

```
BOOL AddBar(
    CWnd* pBar,
    LPCTSTR pszText = NULL,
    CBitmap* pbmp = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,
    COLORREF clrFore,
    COLORREF clrBack,
    LPCTSTR pszText = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
Pointeur vers un `CWnd` objet qui est la fenêtre enfant à insérer dans le rebar. L’objet référencé doit avoir un WS_CHILD.

*lpszText*<br/>
Pointeur vers une chaîne contenant le texte à afficher sur le rebar. NULL par défaut. Le texte contenu dans *lpszText* ne fait pas partie de la fenêtre enfant ; Il se trouve sur le rebar lui-même.

*pbmp*<br/>
Pointeur vers un `CBitmap` objet à afficher sur l’arrière-plan du Rebar. NULL par défaut.

*dwStyle*<br/>
Valeur DWORD contenant le style à appliquer au Rebar. Pour obtenir la `fStyle` liste complète des styles de bande, consultez la description de la fonction dans la structure Win32 [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) .

*clrFore*<br/>
Valeur COLORREF qui représente la couleur de premier plan du Rebar.

*clrBack*<br/>
Valeur COLORREF qui représente la couleur d’arrière-plan du Rebar.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

## <a name="crebarcreate"></a><a name="create"></a> CReBar :: Create

Appelez cette fonction membre pour créer un Rebar.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers l' `CWnd` objet dont la fenêtre Windows est le parent de la barre d’État. Normalement, votre fenêtre frame.

*dwCtrlStyle*<br/>
Style de contrôle rebar. Par défaut, RBS_BANDBORDERS, qui affiche des lignes étroites pour séparer les bandes adjacentes dans le contrôle rebar. Pour obtenir la liste des styles, consultez [styles de contrôle rebar](/windows/win32/Controls/rebar-control-styles) dans le SDK Windows.

*dwStyle*<br/>
Styles de fenêtre Rebar.

*nID*<br/>
ID de la fenêtre enfant du Rebar.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CReBar :: AddBar](#addbar).

## <a name="crebargetrebarctrl"></a><a name="getrebarctrl"></a> CReBar :: GetReBarCtrl

Cette fonction membre autorise un accès direct au contrôle commun sous-jacent.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Valeur renvoyée

Référence à un objet [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) .

### <a name="remarks"></a>Notes

Appelez cette fonction membre pour tirer parti des fonctionnalités du contrôle commun Rebar de Windows dans personnalisation de votre Rebar. Quand vous appelez `GetReBarCtrl` , elle retourne un objet de référence à l' `CReBarCtrl` objet afin que vous puissiez utiliser l’un ou l’autre ensemble de fonctions membres.

Pour plus d’informations sur l’utilisation `CReBarCtrl` de pour personnaliser votre rebar, consultez [utilisation de CReBarCtrl](../../mfc/using-crebarctrl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC, exemple MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (classe)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
