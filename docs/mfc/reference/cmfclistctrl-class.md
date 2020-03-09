---
title: CMFCListCtrl, classe
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
ms.openlocfilehash: 599a00af28ee5b8effbabbe5b334022ceb49f91a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78869969"
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl, classe

La classe `CMFCListCtrl` étend les fonctionnalités de la classe de [classe CListCtrl](../../mfc/reference/clistctrl-class.md) en prenant en charge les fonctionnalités de contrôle d’en-tête avancées de la [classe CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md).

## <a name="syntax"></a>Syntaxe

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Permet de marquer une colonne triée avec une couleur d’arrière-plan différente.|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Active le mode de tri multiple.|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Retourne une référence au contrôle d’en-tête souligné.|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Vérifie si le contrôle de liste est en mode de tri multiple.|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Appelé par le Framework quand il doit comparer deux éléments de contrôle de liste.|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Appelé par le Framework quand il doit déterminer la couleur d’arrière-plan d’une cellule individuelle.|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Appelé par le Framework quand il doit obtenir la police pour la cellule qui est dessinée.|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Appelé par le Framework quand il doit déterminer la couleur de texte d’une cellule individuelle.|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Supprime une colonne de tri de la liste des colonnes triées.|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Définit la colonne triée actuelle et l’ordre de tri.|
|[CMFCListCtrl :: sort](#sort)|Trie le contrôle de liste.|

## <a name="remarks"></a>Notes 

`CMFCListCtrl` offre deux améliorations à la classe de [classe CListCtrl](../../mfc/reference/clistctrl-class.md) . Tout d’abord, elle indique que le tri des colonnes est une option disponible en dessinant automatiquement une flèche de tri sur l’en-tête. Deuxièmement, il prend en charge le tri des données sur plusieurs colonnes en même temps.

## <a name="example"></a> Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCListCtrl` . L’exemple montre comment créer un contrôle de liste, insérer des colonnes, insérer des éléments, définir le texte d’un élément et définir la police du contrôle de liste. Cet extrait de code fait partie de l' [exemple de démonstration Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxlistctrl. h

##  <a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn

Marque les colonnes triées avec une couleur d’arrière-plan différente.

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*bMark*<br/>
dans Paramètre booléen qui détermine s’il faut activer une autre couleur d’arrière-plan.

*bRedraw*<br/>
dans Paramètre booléen qui détermine s’il faut redessiner immédiatement le contrôle.

### <a name="remarks"></a>Notes 

`EnableMarkSortedColumn` utilise la méthode `CDrawingManager::PixelAlpha` pour calculer la couleur à utiliser pour les colonnes triées. La couleur choisie est basée sur la couleur d’arrière-plan normale.

##  <a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort

Active le tri des lignes de données dans le contrôle de liste par plusieurs colonnes.

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans Valeur booléenne qui spécifie s’il faut activer le mode de tri sur plusieurs colonnes.

### <a name="remarks"></a>Notes 

Lorsque vous activez le tri basé sur plusieurs colonnes, les colonnes ont une hiérarchie. Les lignes de données sont d’abord triées selon la colonne principale. Toutes les valeurs équivalentes sont ensuite triées par chaque colonne suivante en fonction de la priorité.

##  <a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl

Retourne une référence au contrôle header.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>Valeur de retour

Référence à l’objet [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) sous-jacent.

### <a name="remarks"></a>Notes 

Le contrôle header pour un contrôle List est la fenêtre qui contient les titres des colonnes. Il est généralement placé directement au-dessus des colonnes.

##  <a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort

Vérifie si le contrôle de liste prend actuellement en charge le tri sur plusieurs colonnes.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le contrôle de liste prend en charge plusieurs tris ; FALSe dans le cas contraire.

### <a name="remarks"></a>Notes 

Quand une [classe CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) prend en charge plusieurs tris, l’utilisateur peut trier les données du contrôle de liste sur plusieurs colonnes. Pour activer le tri multiple, appelez [CMFCListCtrl :: EnableMultipleSort](#enablemultiplesort).

##  <a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems

L’infrastructure appelle cette méthode lorsqu’elle compare deux éléments.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Paramètres

*lParam1*<br/>
dans Premier élément à comparer.

*lParam2*<br/>
dans Deuxième élément à comparer.

*iColumn*<br/>
dans Index de la colonne triée par cette méthode.

### <a name="return-value"></a>Valeur de retour

Entier qui indique la position relative des deux éléments. Une valeur négative indique que le premier élément doit précéder le deuxième, une valeur positive indique que le premier élément doit suivre le deuxième, et zéro signifie que les deux éléments sont équivalents.

### <a name="remarks"></a>Notes 

L’implémentation par défaut retourne toujours 0. Substituez cette fonction pour fournir votre propre algorithme de tri.

##  <a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor

L’infrastructure appelle cette méthode lorsqu’elle doit déterminer la couleur d’arrière-plan d’une cellule individuelle.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Paramètres

*nRow*<br/>
dans Ligne de la cellule en question.

*nColumn*<br/>
dans Colonne de la cellule en question.

### <a name="return-value"></a>Valeur de retour

Valeur de COLOREF qui spécifie la couleur d’arrière-plan de la cellule.

### <a name="remarks"></a>Notes 

L’implémentation par défaut de `OnGetCellBkColor` n’utilise pas les paramètres d’entrée fournis et appelle à la place simplement `GetBkColor`. Par conséquent, par défaut, l’ensemble du contrôle de liste aura la même couleur d’arrière-plan. Vous pouvez substituer `OnGetCellBkColor` dans une classe dérivée pour marquer des cellules individuelles avec une couleur d’arrière-plan distincte.

##  <a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont

L’infrastructure appelle cette méthode lorsqu’elle obtient la police pour une cellule individuelle.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>Paramètres

*nRow*<br/>
dans Ligne de la cellule en question.

*nColumn*<br/>
dans Colonne de la cellule en question.

*dwData*<br/>
dans Données définies par l’utilisateur. L’implémentation par défaut n’utilise pas ce paramètre.

### <a name="return-value"></a>Valeur de retour

Handle de la police utilisée pour la cellule active.

### <a name="remarks"></a>Notes 

Par défaut, cette méthode retourne la valeur NULL. Toutes les cellules d’un contrôle List ont la même police. Substituez cette méthode pour fournir des polices différentes pour différentes cellules.

##  <a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor

L’infrastructure appelle cette méthode lorsqu’elle doit déterminer la couleur de texte d’une cellule individuelle.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Paramètres

*nRow*<br/>
dans Ligne de la cellule en question.

*nColumn*<br/>
dans Colonne de la cellule en question.

### <a name="return-value"></a>Valeur de retour

Valeur de COLOREF qui spécifie la couleur de texte de la cellule.

### <a name="remarks"></a>Notes 

Par défaut, cette méthode appelle `GetTextColor` indépendamment des paramètres d’entrée. Le contrôle de liste entier aura la même couleur de texte. Vous pouvez substituer `OnGetCellTextColor` dans une classe dérivée pour marquer des cellules individuelles avec une couleur de texte distincte.

##  <a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn

Supprime une colonne de tri de la liste des colonnes triées.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Paramètres

*iColumn*<br/>
dans Colonne à supprimer.

### <a name="remarks"></a>Notes 

Cette méthode supprime une colonne de tri du contrôle header. Il appelle [CMFCHeaderCtrl :: RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).

##  <a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn

Définit la colonne triée actuelle et l’ordre de tri.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Paramètres

*iColumn*<br/>
dans Colonne à trier.

*bAscending*<br/>
dans Valeur booléenne qui spécifie l’ordre de tri.

*Jout*<br/>
dans Valeur booléenne qui spécifie si la méthode ajoute la colonne indiquée par *IColumn* à la liste des colonnes de tri.

### <a name="remarks"></a>Notes 

Cette méthode passe les paramètres d’entrée au contrôle d’en-tête à l’aide de la méthode [CMFCHeaderCtrl :: SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).

##  <a name="sort"></a>CMFCListCtrl :: sort

Trie le contrôle de liste.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Paramètres

*iColumn*<br/>
dans Colonne à trier.

*bAscending*<br/>
dans Valeur booléenne qui spécifie l’ordre de tri.

*Jout*<br/>
dans Valeur booléenne qui spécifie si cette méthode ajoute la colonne indiquée par *IColumn* à la liste des colonnes de tri.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl, classe](../../mfc/reference/clistctrl-class.md)
