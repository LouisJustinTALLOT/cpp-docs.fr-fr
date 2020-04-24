---
title: Classe CMFCListCtrl
ms.date: 07/30/2019
f1_keywords:
- CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl::EnableMarkSortedColumn
- AFXLISTCTRL/CMFCListCtrl::EnableMultipleSort
- AFXLISTCTRL/CMFCListCtrl::GetHeaderCtrl
- AFXLISTCTRL/CMFCListCtrl::IsMultipleSort
- AFXLISTCTRL/CMFCListCtrl::OnCompareItems
- AFXLISTCTRL/CMFCListCtrl::OnGetCellBkColor
- AFXLISTCTRL/CMFCListCtrl::OnGetCellFont
- AFXLISTCTRL/CMFCListCtrl::OnGetCellTextColor
- AFXLISTCTRL/CMFCListCtrl::RemoveSortColumn
- AFXLISTCTRL/CMFCListCtrl::SetSortColumn
- AFXLISTCTRL/CMFCListCtrl::Sort
helpviewer_keywords:
- CMFCListCtrl [MFC], EnableMarkSortedColumn
- CMFCListCtrl [MFC], EnableMultipleSort
- CMFCListCtrl [MFC], GetHeaderCtrl
- CMFCListCtrl [MFC], IsMultipleSort
- CMFCListCtrl [MFC], OnCompareItems
- CMFCListCtrl [MFC], OnGetCellBkColor
- CMFCListCtrl [MFC], OnGetCellFont
- CMFCListCtrl [MFC], OnGetCellTextColor
- CMFCListCtrl [MFC], RemoveSortColumn
- CMFCListCtrl [MFC], SetSortColumn
- CMFCListCtrl [MFC], Sort
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
ms.openlocfilehash: 099ec086bd95a1180af4cf5a8f6a9fa7f1d099ea
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754231"
---
# <a name="cmfclistctrl-class"></a>Classe CMFCListCtrl

La `CMFCListCtrl` classe étend la fonctionnalité de la classe [CListCtrl Class](../../mfc/reference/clistctrl-class.md) en soutenant la fonctionnalité de contrôle d’en-tête avancée de la [classe CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md).

## <a name="syntax"></a>Syntaxe

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Permet de marquer une colonne triée avec une couleur de fond différente.|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Permet le mode de tri multiple.|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Renvoie une référence au contrôle de l’en-tête souligné.|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Vérifie si le contrôle de liste est en mode tri multiple.|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Appelé par le cadre quand il doit comparer deux éléments de contrôle de liste.|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Appelé par le cadre quand il doit déterminer la couleur de fond d’une cellule individuelle.|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Appelé par le cadre quand il doit obtenir la police pour la cellule étant tirée.|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Appelé par le cadre quand il doit déterminer la couleur de texte d’une cellule individuelle.|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Supprime une colonne trise de la liste des colonnes triées.|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Définit la colonne triée en cours et l’ordre de tri.|
|[CMFCListCtrl::Sort](#sort)|Trie le contrôle de la liste.|

## <a name="remarks"></a>Notes

`CMFCListCtrl`offre deux améliorations à la [classe CListCtrl Class.](../../mfc/reference/clistctrl-class.md) Tout d’abord, il indique que le tri de colonne est une option disponible en tirant automatiquement une flèche de tri sur l’en-tête. Deuxièmement, il prend en charge le tri des données sur plusieurs colonnes en même temps.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCListCtrl` . L’exemple montre comment créer un contrôle de liste, insérer des colonnes, insérer des éléments, définir le texte d’un élément et définir la police du contrôle de liste. Cet extrait de code fait partie de [l’échantillon Visual Studio Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxlistctrl.h

## <a name="cmfclistctrlenablemarksortedcolumn"></a><a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn

Marque les colonnes triées avec une couleur de fond différente.

```cpp
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*bMark (en)*<br/>
[dans] Un paramètre Boolean qui détermine s’il faut activer une couleur de fond différente.

*bRedraw (en)*<br/>
[dans] Un paramètre Boolean qui détermine s’il faut redessiner le contrôle immédiatement.

### <a name="remarks"></a>Notes

`EnableMarkSortedColumn`utilise la `CDrawingManager::PixelAlpha` méthode pour calculer la couleur à utiliser pour les colonnes triées. La couleur cueillie est basée sur la couleur de fond régulière.

## <a name="cmfclistctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort

Permet de trier les lignes de données dans le contrôle de liste par plusieurs colonnes.

```cpp
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] Un Boolean qui spécifie s’il faut activer plusieurs mode de tri de colonne.

### <a name="remarks"></a>Notes

Lorsque vous activez le tri en fonction de plusieurs colonnes, les colonnes ont une hiérarchie. Les lignes de données seront d’abord triées par la colonne principale. Toutes les valeurs équivalentes sont ensuite triées par chaque colonne ultérieure en fonction de la priorité.

## <a name="cmfclistctrlgetheaderctrl"></a><a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl

Renvoie une référence au contrôle de l’en-tête.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>Valeur de retour

Une référence à l’objet ci-contre-jacent [CMFCHeaderCtrl.](../../mfc/reference/cmfcheaderctrl-class.md)

### <a name="remarks"></a>Notes

Le contrôle de l’en-tête pour un contrôle de liste est la fenêtre qui contient les titres pour les colonnes. Il est généralement positionné directement au-dessus des colonnes.

## <a name="cmfclistctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort

Vérifie si le contrôle de liste prend actuellement en charge le tri sur plusieurs colonnes.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le contrôle de liste prend en charge plusieurs types; FALSE autrement.

### <a name="remarks"></a>Notes

Lorsqu’une [classe CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) prend en charge le tri multiple, l’utilisateur peut trier les données dans le contrôle de liste par plusieurs colonnes. Pour activer le tri multiple, appelez [CMFCListCtrl::EnableMultipleSort](#enablemultiplesort).

## <a name="cmfclistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems

Le cadre appelle cette méthode lorsqu’elle compare deux éléments.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Paramètres

*lParam1*<br/>
[dans] Le premier élément à comparer.

*lParam2*<br/>
[dans] Le deuxième élément à comparer.

*iColumn iColumn*<br/>
[dans] L’index de la colonne que cette méthode est le tri.

### <a name="return-value"></a>Valeur de retour

Un élément qui indique la position relative des deux éléments. Une valeur négative indique que le premier élément doit précéder le second, une valeur positive indique que le premier élément doit suivre le second, et zéro signifie que les deux éléments sont équivalents.

### <a name="remarks"></a>Notes

L’implémentation par défaut renvoie toujours 0. Remplacez cette fonction pour fournir votre propre algorithme de tri.

## <a name="cmfclistctrlongetcellbkcolor"></a><a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor

Le cadre appelle cette méthode lorsqu’elle doit déterminer la couleur de fond d’une cellule individuelle.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Paramètres

*nRow (en)*<br/>
[dans] La rangée de la cellule en question.

*nColumn (en)*<br/>
[dans] La colonne de la cellule en question.

### <a name="return-value"></a>Valeur de retour

Une valeur COLOREF qui spécifie la couleur de fond de la cellule.

### <a name="remarks"></a>Notes

La mise `OnGetCellBkColor` en œuvre par défaut de `GetBkColor`n’utilise pas les paramètres d’entrée fournis et appelle plutôt simplement . Par conséquent, par défaut, l’ensemble du contrôle de liste aura la même couleur de fond. Vous pouvez `OnGetCellBkColor` remplacer dans une classe dérivée pour marquer les cellules individuelles avec une couleur de fond séparée.

## <a name="cmfclistctrlongetcellfont"></a><a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont

Le cadre appelle cette méthode lorsqu’elle obtient la police pour une cellule individuelle.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>Paramètres

*nRow (en)*<br/>
[dans] La rangée de la cellule en question.

*nColumn (en)*<br/>
[dans] La colonne de la cellule en question.

*dwData dwData*<br/>
[dans] Données définies par l’utilisateur. L’implémentation par défaut n’utilise pas ce paramètre.

### <a name="return-value"></a>Valeur de retour

Une poignée à la police qui est utilisée pour la cellule actuelle.

### <a name="remarks"></a>Notes

Par défaut, cette méthode renvoie NULL. Toutes les cellules d’un contrôle de liste ont la même police. Remplacer cette méthode pour fournir différentes polices pour différentes cellules.

## <a name="cmfclistctrlongetcelltextcolor"></a><a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor

Le cadre appelle cette méthode lorsqu’elle doit déterminer la couleur de texte d’une cellule individuelle.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Paramètres

*nRow (en)*<br/>
[dans] La rangée de la cellule en question.

*nColumn (en)*<br/>
[dans] La colonne de la cellule en question.

### <a name="return-value"></a>Valeur de retour

Une valeur COLOREF qui spécifie la couleur de texte de la cellule.

### <a name="remarks"></a>Notes

Par défaut, cette `GetTextColor` méthode appelle indépendamment des paramètres d’entrée. Le contrôle de liste entier aura la même couleur de texte. Vous pouvez `OnGetCellTextColor` remplacer dans une classe dérivée pour marquer les cellules individuelles avec une couleur de texte séparée.

## <a name="cmfclistctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn

Supprime une colonne trise de la liste des colonnes triées.

```cpp
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Paramètres

*iColumn iColumn*<br/>
[dans] La colonne à enlever.

### <a name="remarks"></a>Notes

Cette méthode supprime une colonne de tri du contrôle de l’en-tête. Il appelle [CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).

## <a name="cmfclistctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn

Définit la colonne triée en cours et l’ordre de tri.

```cpp
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Paramètres

*iColumn iColumn*<br/>
[dans] La colonne à trier.

*bAscending*<br/>
[dans] Un Boolean qui spécifie l’ordre de tri.

*Badd*<br/>
[dans] Un Boolean qui précise si la méthode ajoute la colonne indiquée par *iColumn* à la liste des colonnes de tri.

### <a name="remarks"></a>Notes

Cette méthode passe les paramètres d’entrée au contrôle de l’en-tête en utilisant la méthode [CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).

## <a name="cmfclistctrlsort"></a><a name="sort"></a>CMFCListCtrl::Sort

Trie le contrôle de la liste.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Paramètres

*iColumn iColumn*<br/>
[dans] La colonne à trier.

*bAscending*<br/>
[dans] Un Boolean qui spécifie l’ordre de tri.

*Badd*<br/>
[dans] Un Boolean qui précise si cette méthode ajoute la colonne indiquée par *iColumn* à la liste des colonnes de tri.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl, classe](../../mfc/reference/clistctrl-class.md)
