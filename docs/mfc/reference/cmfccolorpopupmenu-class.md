---
title: Classe CMFCColorPopupMenu
ms.date: 11/04/2016
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
ms.openlocfilehash: 901a44c8f5fdecd1b277ebdecc995722a3afe9a3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752494"
---
# <a name="cmfccolorpopupmenu-class"></a>Classe CMFCColorPopupMenu

Représente un menu pop-up que les utilisateurs utilisent pour sélectionner des couleurs dans un document ou une application.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|||
|-|-|
|Nom|Description|
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|Construit un objet `CMFCColorPopupMenu`.|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|Nom|Description|
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Crée une barre de couleur larmes à quai. (Overrides [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Retourne le [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) qui est intégré dans le menu pop-up. (Overrides [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|
|`CMFCColorPopupMenu::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Définit l’objet de contrôle `CMFCColorBar` du réseau de propriété de l’objet embarqué.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|Nom|Description|
|`m_bEnabledInCustomizeMode`|Une valeur Boolean qui détermine s’il faut montrer la barre de couleur.|
|`m_wndColorBar`|L’objet `CMFCColorBar` qui fournit la sélection des couleurs.|

### <a name="remarks"></a>Notes

Cette classe hérite de la fonctionnalité `CMFCPopupMenu` du menu `CMFCColorBar` pop-up de la classe et gère un objet qui fournit la sélection des couleurs. Lorsque le cadre de la barre `m_bEnabledInCustomizeMode` d’outils est en mode personnalisation et que le membre est réglé sur FALSE, l’objet de barre de couleur n’est pas affiché. Pour plus d’informations sur le mode de personnalisation, voir [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

Pour plus `CMFCColorBar`d’informations sur , voir [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxcolorpopupmenu.h

## <a name="cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a>CMFCColorPopupMenu::CMFCColorPopupMenu

Construit un objet `CMFCColorPopupMenu`.

```
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    int nHorzDockRows,
    int nVertDockColumns,
    COLORREF colorAutomatic,
    UINT uiCommandID,
    BOOL bStdColorDlg = FALSE);

CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic);

CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*les couleurs*<br/>
[dans] Un tableau de couleurs que le cadre affiche sur le menu pop-up.

*Couleur*<br/>
[dans] La couleur sélectionnée par défaut.

*lpszAutoColor*<br/>
[dans] L’étiquette de texte du bouton *couleur automatique* (par défaut) ou NULL.

L’étiquette standard pour le bouton automatique est **automatique**.

*lpszOtherColor*<br/>
[dans] L’étiquette de texte de *l’autre* bouton, qui affiche plus de choix de couleurs, ou NULL.

L’étiquette standard pour l’autre bouton est **Plus de couleurs...**.

*lpszDocColors*<br/>
[dans] L’étiquette de texte du bouton de couleur de document. La palette de couleurs de document répertorie toutes les couleurs que le document utilise actuellement.

*lstDocColors (en)*<br/>
[dans] Une liste de couleurs que le document utilise actuellement.

*nColumns*<br/>
[dans] Le nombre de colonnes que la gamme de couleurs a.

*nHorzDockRows*<br/>
[dans] Le nombre de lignes que la barre de couleur a quand il est amarré horizontalement.

*nVertDockColumns (en)*<br/>
[dans] Le nombre de colonnes que la barre de couleur a quand il est amarré verticalement.

*couleurAutomatique*<br/>
[dans] La couleur par défaut que le cadre s’applique lorsque vous cliquez sur le bouton automatique.

*uiCommandID*<br/>
[dans] L’ID de commande de barre de couleur.

*bStdColorDlg*<br/>
[dans] Un Boolean qui indique s’il faut montrer la boîte de dialogue couleur système standard ou la boîte de dialogue [CMFCColorDialog.](../../mfc/reference/cmfccolordialog-class.md)

*pParentBtn*<br/>
[dans] Un pointeur sur un bouton parent.

*nID*<br/>
[dans] L’id de commande.

### <a name="remarks"></a>Notes

Chaque constructeur surchargé met `m_bEnabledInCustomizeMode` le membre à FALSE.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCColorPopupMenu` construire un objet.

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

## <a name="cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a>CMFCColorPopupMenu::CreateTearOffBar

Crée une barre de couleur larmes à quai.

```
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,
    UINT uiID,
    LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pWndMain (en)*|[dans] Pointeur vers la fenêtre parente de la barre de déchirure.|
|*uiID*|[dans] L’id de commande de la barre de déchirure.|
|*lpszName (en)*|[dans] Le texte de la fenêtre de la barre de déchirure.|

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le nouvel objet de barre de contrôle déchirant.

### <a name="remarks"></a>Notes

Cette méthode crée un objet [cmFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md) et le jette sur un pointeur [de classe CPane.](../../mfc/reference/cpane-class.md) Vous pouvez remettre cette valeur à un pointeur [de classe CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) en utilisant l’une des macros de coulée décrites dans [type casting des objets de classe MFC](../../mfc/reference/type-casting-of-mfc-class-objects.md).

## <a name="cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a>CMFCColorPopupMenu::GetMenuBar

Retourne le [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) qui est intégré dans le menu pop-up.

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CMFCPopupMenuBar`à la embarquée .

### <a name="remarks"></a>Notes

Le menu pop-up couleur dispose d’un objet [intégré cmFCPopupMenuBar Classe.](../../mfc/reference/cmfcpopupmenubar-class.md) Remplacer cette méthode dans une classe dérivée si votre application utilise un type intégré différent.

## <a name="cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a>CMFCColorPopupMenu::SetPropList

Définit l’objet de contrôle `CMFCColorBar` du réseau de propriété de l’objet embarqué.

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Paramètres

*pWndList (en)*<br/>
[dans] Pointeur vers un objet de contrôle de grille de propriété.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
