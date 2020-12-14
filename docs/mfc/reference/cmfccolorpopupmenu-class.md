---
description: 'En savoir plus sur : classe CMFCColorPopupMenu'
title: CMFCColorPopupMenu, classe
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
ms.openlocfilehash: 1668064fa253ea17bdce1ba393bd892ef8769b71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211828"
---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu, classe

Représente un menu contextuel qui permet aux utilisateurs de sélectionner des couleurs dans un document ou une application.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|-|-|
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|Construit un objet `CMFCColorPopupMenu`.|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|-|-|
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Crée une barre de couleur détachable et Ancrable. (Substitue [CMFCPopupMenu :: CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Retourne le [cmfcpopupmenubar,](../../mfc/reference/cmfcpopupmenubar-class.md) incorporé dans le menu contextuel. (Substitue [CMFCPopupMenu :: GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|
|`CMFCColorPopupMenu::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Définit l’objet de contrôle de grille de propriétés de l’objet incorporé `CMFCColorBar` .|

### <a name="data-members"></a>Données membres

|Nom|Description|
|-|-|
|`m_bEnabledInCustomizeMode`|Valeur booléenne qui détermine s’il faut afficher la barre de couleurs.|
|`m_wndColorBar`|`CMFCColorBar`Objet qui fournit la sélection de couleurs.|

### <a name="remarks"></a>Notes

Cette classe hérite de la fonctionnalité de menu contextuel de la `CMFCPopupMenu` classe et gère un `CMFCColorBar` objet qui fournit la sélection de couleurs. Lorsque l’infrastructure de barre d’outils est en mode de personnalisation et que le `m_bEnabledInCustomizeMode` membre a la valeur false, l’objet de la barre de couleurs n’est pas affiché. Pour plus d’informations sur le mode de personnalisation, consultez [CMFCToolBar :: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

Pour plus d’informations sur `CMFCColorBar` , consultez [CMFCColorBar, classe](../../mfc/reference/cmfccolorbar-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxcolorpopupmenu. h

## <a name="cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a> CMFCColorPopupMenu::CMFCColorPopupMenu

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

*couleurs*<br/>
dans Tableau de couleurs que l’infrastructure affiche dans le menu contextuel.

*color*<br/>
dans Couleur sélectionnée par défaut.

*lpszAutoColor*<br/>
dans Étiquette de texte du bouton de couleur *automatique* (par défaut) ou null.

L’étiquette standard du bouton automatique est **automatique**.

*lpszOtherColor*<br/>
dans Étiquette de texte de l' *autre* bouton, qui affiche plus de choix de couleurs, ou null.

L’étiquette standard de l’autre bouton est **plus de couleurs.**...

*lpszDocColors*<br/>
dans Étiquette de texte du bouton de couleurs du document. La palette de couleurs du document répertorie toutes les couleurs actuellement utilisées par le document.

*lstDocColors*<br/>
dans Liste des couleurs actuellement utilisées par le document.

*nColumns*<br/>
dans Nombre de colonnes que contient le tableau de couleurs.

*nHorzDockRows*<br/>
dans Nombre de lignes que la barre de couleurs a lorsqu’elle est ancrée horizontalement.

*nVertDockColumns*<br/>
dans Nombre de colonnes de la barre de couleurs lorsqu’elle est ancrée verticalement.

*colorAutomatic*<br/>
dans Couleur par défaut appliquée par l’infrastructure lorsque vous cliquez sur le bouton automatique.

*uiCommandID*<br/>
dans ID de commande du contrôle de la barre de couleurs.

*bStdColorDlg*<br/>
dans Valeur booléenne qui indique s’il faut afficher la boîte de dialogue couleur système standard ou la boîte de dialogue [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) .

*pParentBtn*<br/>
dans Pointeur vers un bouton parent.

*nID*<br/>
dans ID de la commande.

### <a name="remarks"></a>Notes

Chaque constructeur surchargé affecte la `m_bEnabledInCustomizeMode` valeur false au membre.

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCColorPopupMenu` objet.

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

## <a name="cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a> CMFCColorPopupMenu::CreateTearOffBar

Crée une barre de couleur détachable et Ancrable.

```
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,
    UINT uiID,
    LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*pWndMain*\
dans Pointeur vers la fenêtre parente de la barre détachée.

*uiID*\
dans ID de commande de la barre détachée.

*lpszName*\
dans Texte de la fenêtre de la barre détachée.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le nouvel objet de barre de contrôle de déchirage.

### <a name="remarks"></a>Notes

Cette méthode crée un objet de [classe CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) et le convertit en pointeur de [classe CPane](../../mfc/reference/cpane-class.md) . Vous pouvez effectuer un cast de cette valeur en un pointeur de [classe CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) à l’aide de l’une des macros de cast décrites dans [type casting des objets de classe MFC](../../mfc/reference/type-casting-of-mfc-class-objects.md).

## <a name="cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a> CMFCColorPopupMenu::GetMenuBar

Retourne le [cmfcpopupmenubar,](../../mfc/reference/cmfcpopupmenubar-class.md) incorporé dans le menu contextuel.

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le incorporé `CMFCPopupMenuBar` .

### <a name="remarks"></a>Notes

Le menu contextuel couleur contient un objet de [classe cmfcpopupmenubar,](../../mfc/reference/cmfcpopupmenubar-class.md) incorporé. Substituez cette méthode dans une classe dérivée si votre application utilise un type incorporé différent.

## <a name="cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a> CMFCColorPopupMenu::SetPropList

Définit l’objet de contrôle de grille de propriétés de l’objet incorporé `CMFCColorBar` .

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Paramètres

*pWndList*<br/>
dans Pointeur vers un objet de contrôle de grille de propriétés.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
