---
title: Classe CReBar
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
ms.openlocfilehash: c1379d1ef8effea0df564da1b43769bb9a11435d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363927"
---
# <a name="crebar-class"></a>Classe CReBar

Barre de contrôles qui fournit des informations de disposition, de persistance et d'état pour les contrôles rebar.

## <a name="syntax"></a>Syntaxe

```
class CReBar : public CControlBar
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CReBar::AddBar](#addbar)|Ajoute une bande à une barre d’armature.|
|[CReBar::Créer](#create)|Crée le contrôle des barres d’armature et le fixe à l’objet. `CReBar`|
|[CReBar::GetReBarCtrl](#getrebarctrl)|Permet un accès direct au contrôle commun sous-jacent.|

## <a name="remarks"></a>Notes

Un objet rebar peut contenir plusieurs fenêtres enfants, généralement d'autres contrôles, notamment des zones d'édition, des barres d'outils et des zones de liste. Un objet rebar peut afficher les fenêtres enfants sur une image bitmap spécifiée. Votre application peut automatiquement resize la barre d’armature, ou l’utilisateur peut resize manuellement la barre d’armature en cliquant ou en faisant glisser sa barre de pincement.

![Exemple de RebarMenu](../../mfc/reference/media/vc4sc61.gif "Exemple de RebarMenu")

## <a name="rebar-control"></a>Contrôle des barres d’armature

Un objet de barre d’armature se comporte de la même façon qu’un objet de barre d’outils. Une barre d’armature utilise le mécanisme de clic et de traînée pour redimensionner ses bandes. Un contrôle des barres d’armature peut contenir une ou plusieurs bandes, chaque bande ayant une combinaison d’une barre de pincement, une bitmap, une étiquette de texte, et une fenêtre pour enfants. Cependant, les bandes ne peuvent pas contenir plus d’une fenêtre d’enfant.

`CReBar`utilise la classe [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) pour fournir sa mise en œuvre. Vous pouvez accéder au contrôle des barres d’armature via [GetReBarCtrl](#getrebarctrl) pour profiter des options de personnalisation du contrôle. Pour plus d’informations sur `CReBarCtrl`les contrôles des barres d’armature, voir . Pour plus d’informations sur l’utilisation des commandes de barres d’armature, voir [Utilisation CReBarCtrl](../../mfc/using-crebarctrl.md).

> [!CAUTION]
> Les objets de commande des barres d’armature et des barres d’armature ne prennent pas en charge l’amarrage des barres de commande MFC. Si `CRebar::EnableDocking` elle est appelée, votre demande s’affirmera.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar (en)](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="crebaraddbar"></a><a name="addbar"></a>CReBar::AddBar

Appelez cette fonction de membre pour ajouter une bande à la barre d’armature.

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

*pBar (pBar)*<br/>
Un pointeur `CWnd` à un objet qui est la fenêtre de l’enfant à insérer dans la barre d’armature. L’objet référencé doit avoir un WS_CHILD.

*lpszText*<br/>
Un pointeur à une chaîne contenant le texte à apparaître sur la barre d’armature. NULL par défaut. Le texte contenu dans *lpszText* ne fait pas partie de la fenêtre de l’enfant; il est sur la barre d’armature elle-même.

*pbmp*<br/>
Un pointeur `CBitmap` d’un objet à afficher sur le fond de la barre d’armature. NULL par défaut.

*dwStyle (en)*<br/>
Un DWORD contenant le style à appliquer sur la barre d’armature. Consultez `fStyle` la description de la fonction dans la structure Win32 [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) pour une liste complète des styles de bande.

*clrFore*<br/>
Une valeur COLORREF qui représente la couleur de premier plan de la barre d’armature.

*clrBack (en)*<br/>
Une valeur COLORREF qui représente la couleur de fond de la barre d’armature.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

## <a name="crebarcreate"></a><a name="create"></a>CReBar::Créer

Appelez cette fonction de membre pour créer une barre d’armature.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur `CWnd` vers l’objet dont la fenêtre Windows est le parent de la barre d’état. Normalement, votre fenêtre de cadre.

*dwCtrlStyle (en)*<br/>
Le style de contrôle des barres d’armature. Par défaut, RBS_BANDBORDERS, qui affiche des lignes étroites pour séparer les bandes adjacentes dans le contrôle des barres d’armature. Consultez [Rebar Control Styles](/windows/win32/Controls/rebar-control-styles) dans le Windows SDK pour une liste de styles.

*dwStyle (en)*<br/>
Les styles de fenêtre de barre d’armature.

*nID*<br/>
L’id de la fenêtre pour enfants de la barre d’armature.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CReBar:AddBar](#addbar).

## <a name="crebargetrebarctrl"></a><a name="getrebarctrl"></a>CReBar::GetReBarCtrl

Cette fonction de membre permet un accès direct au contrôle commun sous-jacent.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence à un objet [CReBarCtrl.](../../mfc/reference/crebarctrl-class.md)

### <a name="remarks"></a>Notes

Appelez cette fonction de membre pour profiter de la fonctionnalité du contrôle commun de barre d’armature de Windows dans la personnalisation de votre barre d’armature. Lorsque vous `GetReBarCtrl`appelez, il renvoie `CReBarCtrl` un objet de référence à l’objet afin que vous puissiez utiliser l’un ou l’autre ensemble des fonctions des membres.

Pour plus d’informations sur l’utilisation `CReBarCtrl` pour personnaliser votre barre d’armature, voir à [l’aide de CReBarCtrl](../../mfc/using-crebarctrl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC, exemple MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
