---
title: Cmfclistctrl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e85ba42db937a6b9abf3415115bb301739456bd4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432774"
---
# <a name="cmfclistctrl-class"></a>Cmfclistctrl, classe

Le `CMFCListCtrl` classe étend les fonctionnalités de [classe CListCtrl](../../mfc/reference/clistctrl-class.md) classe en prenant en charge les fonctionnalités de contrôle d’en-tête avancées de la [cmfcheaderctrl, classe](../../mfc/reference/cmfcheaderctrl-class.md).

## <a name="syntax"></a>Syntaxe

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Permet de marquer une colonne triée avec une couleur d’arrière-plan différente.|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Active le mode de tri plusieurs.|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Retourne une référence au contrôle header souligné.|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Vérifie si le contrôle de liste est en mode de tri multiple.|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Appelé par l’infrastructure lorsqu’elle doit comparer deux éléments de contrôle de liste.|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Appelé par l’infrastructure lorsqu’il doit déterminer la couleur d’arrière-plan d’une cellule.|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Appelé par l’infrastructure lorsqu’il doit obtenir de la police pour la cellule qui est dessinée.|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Appelé par l’infrastructure lorsqu’il doit déterminer la couleur du texte d’une cellule.|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Supprime une colonne de tri de la liste des colonnes triées.|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Définit la colonne triée actuelle et l’ordre de tri.|
|[CMFCListCtrl::Sort](#sort)|Trie le contrôle de liste.|

## <a name="remarks"></a>Notes

`CMFCListCtrl` propose deux améliorations [classe CListCtrl](../../mfc/reference/clistctrl-class.md) classe. Tout d’abord, il indique que le tri de colonne est une option disponible en dessinant automatiquement une flèche de tri de l’en-tête. Deuxièmement, il prend en charge le tri sur plusieurs colonnes en même temps des données.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCListCtrl` classe. L’exemple montre comment créer un contrôle de liste, insérer des colonnes, insérer des éléments, définir le texte d’un élément et définir la police du contrôle de liste. Cet extrait de code fait partie de la [exemple de démonstration Visual Studio](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxlistctrl.h

##  <a name="enablemarksortedcolumn"></a>  CMFCListCtrl::EnableMarkSortedColumn

Marque les colonnes triées avec une couleur d’arrière-plan différente.

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*bMark*<br/>
[in] Un paramètre booléen qui détermine s’il faut activer une couleur d’arrière-plan différente.

*bRedraw*<br/>
[in] Un paramètre booléen qui détermine s’il doit redessiner le contrôle immédiatement.

### <a name="remarks"></a>Notes

`EnableMarkSortedColumn` utilise la méthode `CDrawingManager::PixelAlpha` pour calculer quelle couleur pour utiliser pour trier colonnes. La couleur sélectionnée est basée sur la couleur d’arrière-plan normale.

##  <a name="enablemultiplesort"></a>  CMFCListCtrl::EnableMultipleSort

Permet de trier les lignes de données dans le contrôle de liste par plusieurs colonnes.

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bActivez*<br/>
[in] Valeur booléenne qui spécifie s’il faut activer le mode de trier plusieurs colonnes.

### <a name="remarks"></a>Notes

Lorsque vous activez le tri basé sur plusieurs colonnes, les colonnes ont une hiérarchie. Les lignes de données seront tout d’abord être triées par la colonne principale. Les valeurs équivalentes sont ensuite triés par chaque colonne suivante selon la priorité.

##  <a name="getheaderctrl"></a>  CMFCListCtrl::GetHeaderCtrl

Retourne une référence au contrôle header.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>Valeur de retour

Une référence à sous-jacent [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) objet.

### <a name="remarks"></a>Notes

Le contrôle header pour un contrôle de liste est la fenêtre qui contient les titres des colonnes. Il est généralement placé directement au-dessus des colonnes.

##  <a name="ismultiplesort"></a>  CMFCListCtrl::IsMultipleSort

Vérifie si le contrôle de liste actuellement en charge le tri sur plusieurs colonnes.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le contrôle de liste prend en charge le tri sur plusieurs ; FALSE sinon.

### <a name="remarks"></a>Notes

Quand un [cmfclistctrl, classe](../../mfc/reference/cmfclistctrl-class.md) prend en charge plusieurs tri, l’utilisateur peut trier les données dans le contrôle de liste en plusieurs colonnes. Pour activer le tri de plusieurs, appelez [CMFCListCtrl::EnableMultipleSort](#enablemultiplesort).

##  <a name="oncompareitems"></a>  CMFCListCtrl::OnCompareItems

L’infrastructure appelle cette méthode lorsqu’il compare deux éléments.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Paramètres

*lParam1*<br/>
[in] Le premier élément à comparer.

*lParam2*<br/>
[in] Le deuxième élément à comparer.

*iColumn*<br/>
[in] L’index de la colonne de tri de cette méthode.

### <a name="return-value"></a>Valeur de retour

Entier qui indique la position relative des deux éléments. Une valeur négative indique que le premier élément doit précéder la seconde, valeur positive indique que le premier élément doit suivre la seconde, et zéro signifie que les deux éléments sont équivalents.

### <a name="remarks"></a>Notes

La valeur par défaut implémentation retourne toujours 0. Vous devez substituer cette fonction pour fournir un algorithme de tri.

##  <a name="ongetcellbkcolor"></a>  CMFCListCtrl::OnGetCellBkColor

L’infrastructure appelle cette méthode lorsqu’il doit déterminer la couleur d’arrière-plan d’une cellule.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Paramètres

*nRow*<br/>
[in] La ligne de la cellule en question.

*nColumn*<br/>
[in] La colonne de la cellule en question.

### <a name="return-value"></a>Valeur de retour

Une valeur COLOREF qui spécifie la couleur d’arrière-plan de la cellule.

### <a name="remarks"></a>Notes

L’implémentation par défaut de `OnGetCellBkColor` n’utilise pas les paramètres d’entrée fournis et à la place appelle simplement `GetBkColor`. Par conséquent, par défaut, le contrôle de l’intégralité de la liste aura la même couleur d’arrière-plan. Vous pouvez remplacer `OnGetCellBkColor` dans une classe dérivée pour marquer des cellules individuelles avec une couleur d’arrière-plan.

##  <a name="ongetcellfont"></a>  CMFCListCtrl::OnGetCellFont

L’infrastructure appelle cette méthode lorsqu’il obtient la police pour une cellule individuelle.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>Paramètres

*nRow*<br/>
[in] La ligne de la cellule en question.

*nColumn*<br/>
[in] La colonne de la cellule en question.

*dwData*<br/>
[in] Données définies par l’utilisateur. L’implémentation par défaut n’utilise pas ce paramètre.

### <a name="return-value"></a>Valeur de retour

Handle vers la police utilisée pour la cellule active.

### <a name="remarks"></a>Notes

Par défaut, cette méthode retourne NULL. Toutes les cellules dans un contrôle de liste ont la même police. Substituez cette méthode afin de fournir des polices différentes cellules.

##  <a name="ongetcelltextcolor"></a>  CMFCListCtrl::OnGetCellTextColor

L’infrastructure appelle cette méthode lorsqu’il doit déterminer la couleur du texte d’une cellule.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Paramètres

*nRow*<br/>
[in] La ligne de la cellule en question.

*nColumn*<br/>
[in] La colonne de la cellule en question.

### <a name="return-value"></a>Valeur de retour

Une valeur COLOREF qui spécifie la couleur du texte de la cellule.

### <a name="remarks"></a>Notes

Par défaut, cette méthode appelle `GetTextColor` , quel que soit les paramètres d’entrée. Le contrôle de l’intégralité de la liste aura la même couleur de texte. Vous pouvez remplacer `OnGetCellTextColor` dans une classe dérivée pour marquer des cellules individuelles avec une couleur de texte séparé.

##  <a name="removesortcolumn"></a>  CMFCListCtrl::RemoveSortColumn

Supprime une colonne de tri de la liste des colonnes triées.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Paramètres

*iColumn*<br/>
[in] La colonne à supprimer.

### <a name="remarks"></a>Notes

Cette méthode supprime une colonne de tri à partir du contrôle d’en-tête. Il appelle [CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).

##  <a name="setsortcolumn"></a>  CMFCListCtrl::SetSortColumn

Définit la colonne triée actuelle et l’ordre de tri.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Paramètres

*iColumn*<br/>
[in] La colonne à trier.

*bAscending*<br/>
[in] Valeur booléenne qui spécifie l’ordre de tri.

*bAjouter*<br/>
[in] Valeur booléenne qui spécifie si la méthode ajoute la colonne indiquée par *iColumn* à la liste des colonnes de tri.

### <a name="remarks"></a>Notes

Cette méthode passe les paramètres d’entrée au contrôle header, en utilisant la méthode [CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).

##  <a name="sort"></a>  CMFCListCtrl::Sort

Trie le contrôle de liste.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Paramètres

*iColumn*<br/>
[in] La colonne à trier.

*bAscending*<br/>
[in] Valeur booléenne qui spécifie l’ordre de tri.

*bAjouter*<br/>
[in] Valeur booléenne qui spécifie si cette méthode ajoute la colonne indiquée par *iColumn* à la liste des colonnes de tri.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl, classe](../../mfc/reference/clistctrl-class.md)
