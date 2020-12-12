---
description: 'En savoir plus sur : classe CMFCHeaderCtrl'
title: CMFCHeaderCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::EnableMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::GetColumnState
- AFXHEADERCTRL/CMFCHeaderCtrl::GetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::IsAscending
- AFXHEADERCTRL/CMFCHeaderCtrl::IsDialogControl
- AFXHEADERCTRL/CMFCHeaderCtrl::IsMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::RemoveSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::SetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawItem
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawSortArrow
- AFXHEADERCTRL/CMFCHeaderCtrl::OnFillBackground
helpviewer_keywords:
- CMFCHeaderCtrl [MFC], CMFCHeaderCtrl
- CMFCHeaderCtrl [MFC], EnableMultipleSort
- CMFCHeaderCtrl [MFC], GetColumnState
- CMFCHeaderCtrl [MFC], GetSortColumn
- CMFCHeaderCtrl [MFC], IsAscending
- CMFCHeaderCtrl [MFC], IsDialogControl
- CMFCHeaderCtrl [MFC], IsMultipleSort
- CMFCHeaderCtrl [MFC], RemoveSortColumn
- CMFCHeaderCtrl [MFC], SetSortColumn
- CMFCHeaderCtrl [MFC], OnDrawItem
- CMFCHeaderCtrl [MFC], OnDrawSortArrow
- CMFCHeaderCtrl [MFC], OnFillBackground
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
ms.openlocfilehash: a6be476e095dc4a013705657e259a90d7cafe0d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265374"
---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl Class

La `CMFCHeaderCtrl` classe prend en charge le tri de plusieurs colonnes dans un contrôle header.

## <a name="syntax"></a>Syntaxe

```
class CMFCHeaderCtrl : public CHeaderCtrl
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|Construit un objet `CMFCHeaderCtrl`.|
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|Active ou désactive le mode de *tri sur plusieurs colonnes* pour le contrôle d’en-tête actuel.|
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Indique si une colonne n’est pas triée ou si elle est triée par ordre croissant ou décroissant.|
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Récupère l’index de base zéro de la première colonne triée dans le contrôle header.|
|`CMFCHeaderCtrl::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCHeaderCtrl::IsAscending](#isascending)|Indique si une colonne du contrôle header est triée par ordre croissant.|
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|Indique si la fenêtre parente du contrôle d’en-tête actuel est une boîte de dialogue.|
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Indique si le contrôle d’en-tête actuel est en mode de *tri sur plusieurs colonnes* .|
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|Supprime la colonne spécifiée de la liste des colonnes de tri.|
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Définit l’ordre de tri d’une colonne spécifiée dans un contrôle header.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Appelé par l’infrastructure pour dessiner une colonne de contrôle d’en-tête.|
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Appelé par l’infrastructure pour dessiner la flèche de tri.|
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|Appelé par l’infrastructure pour remplir l’arrière-plan d’une colonne de contrôle d’en-tête.|

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCHeaderCtrl` classe et comment activer le mode de *tri sur plusieurs colonnes* pour le contrôle d’en-tête actuel.

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>Notes

La `CMFCHeaderCtrl` classe dessine une flèche de tri sur une colonne de contrôle d’en-tête pour indiquer que la colonne est triée. Utilisez le mode de *tri sur plusieurs colonnes* si un ensemble de colonnes dans le contrôle de liste parent ( [classe CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)) peut être trié en même temps.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)

[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxheaderctrl. h

## <a name="cmfcheaderctrlcmfcheaderctrl"></a><a name="cmfcheaderctrl"></a> CMFCHeaderCtrl::CMFCHeaderCtrl

Construit un objet `CMFCHeaderCtrl`.

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>Notes

Ce constructeur initialise les variables membres suivantes aux valeurs spécifiées :

|Variable membre|Valeur|
|---------------------|-----------|
|`m_bIsMousePressed`|false|
|`m_bMultipleSort`|false|
|`m_bAscending`|true|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|false|
|`m_bIsDlgControl`|FALSE|
|`m_hFont`|NULL|

## <a name="cmfcheaderctrlenablemultiplesort"></a><a name="enablemultiplesort"></a> CMFCHeaderCtrl::EnableMultipleSort

Active ou désactive le mode de *tri sur plusieurs colonnes* pour le contrôle d’en-tête actuel.

```cpp
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour activer le mode de tri sur plusieurs colonnes ; FALSe pour désactiver le mode de tri sur plusieurs colonnes et supprimer toutes les colonnes de la liste des colonnes triées. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour activer ou désactiver le mode de tri sur plusieurs colonnes. Au moins deux colonnes peuvent participer à un tri si le contrôle d’en-tête est en mode de tri sur plusieurs colonnes.

## <a name="cmfcheaderctrlgetcolumnstate"></a><a name="getcolumnstate"></a> CMFCHeaderCtrl::GetColumnState

Indique si une colonne est non triée ou si elle est triée par ordre croissant ou décroissant.

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>Paramètres

*iColumn*<br/>
dans Index de base zéro d’une colonne.

### <a name="return-value"></a>Valeur renvoyée

Valeur qui indique l’état de tri de la colonne spécifiée. Le tableau suivant répertorie les valeurs de sortie possibles :

|Valeur|Description|
|-----------|-----------------|
|-1|Trié par ordre décroissant.|
|0|Non trié.|
|1|Trié dans l’ordre croissant.|

### <a name="remarks"></a>Notes

## <a name="cmfcheaderctrlgetsortcolumn"></a><a name="getsortcolumn"></a> CMFCHeaderCtrl::GetSortColumn

Récupère l’index de base zéro de la première colonne triée dans le contrôle header.

```
int GetSortColumn() const;
```

### <a name="return-value"></a>Valeur renvoyée

Index d’une colonne triée, ou-1 si aucune colonne triée n’est trouvée.

### <a name="remarks"></a>Notes

Si le contrôle header est en mode de *tri sur plusieurs colonnes* et que vous avez compilé l’application en mode débogage, cette méthode déclare et vous conseille d’utiliser la méthode [CMFCHeaderCtrl :: GetColumnState](#getcolumnstate) à la place. Si le contrôle header est en mode de tri sur plusieurs colonnes et que vous avez compilé l’application en mode de vente au détail, cette méthode retourne-1.

## <a name="cmfcheaderctrlisascending"></a><a name="isascending"></a> CMFCHeaderCtrl::IsAscending

Indique si une colonne du contrôle header est triée par ordre croissant.

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si une colonne du contrôle header est triée par ordre croissant ; Sinon, FALSe.

### <a name="remarks"></a>Notes

La valeur retournée par cette méthode est utilisée pour afficher la flèche de tri appropriée sur l’élément de contrôle d’en-tête. Utilisez la méthode [CMFCHeaderCtrl :: SetSortColumn](#setsortcolumn) pour définir l’ordre de tri.

## <a name="cmfcheaderctrlisdialogcontrol"></a><a name="isdialogcontrol"></a> CMFCHeaderCtrl::IsDialogControl

Indique si la fenêtre parente du contrôle d’en-tête actuel est une boîte de dialogue.

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la fenêtre parente du contrôle d’en-tête actuel est une boîte de dialogue ; Sinon, FALSe.

## <a name="cmfcheaderctrlismultiplesort"></a><a name="ismultiplesort"></a> CMFCHeaderCtrl::IsMultipleSort

Indique si le contrôle d’en-tête actuel est en mode de *tri sur plusieurs colonnes* .

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si le mode de tri sur plusieurs colonnes est activé ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez la méthode [CMFCHeaderCtrl :: EnableMultipleSort](#enablemultiplesort) pour activer ou désactiver le mode de tri de plusieurs colonnes. Au moins deux colonnes peuvent participer à un tri si le contrôle d’en-tête est en mode de tri sur plusieurs colonnes.

## <a name="cmfcheaderctrlondrawitem"></a><a name="ondrawitem"></a> CMFCHeaderCtrl::OnDrawItem

Appelé par l’infrastructure pour dessiner une colonne de contrôle d’en-tête.

```
virtual void OnDrawItem(
    CDC* pDC,
    int iItem,
    CRect rect,
    BOOL bIsPressed,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*iItem*<br/>
dans Index de base zéro de l’élément à dessiner.

*rectangulaire*<br/>
dans Rectangle englobant de l’élément à dessiner.

*bIsPressed*<br/>
dans TRUE pour dessiner l’élément à l’état enfoncé ; Sinon, FALSe.

*bIsHighlighted*<br/>
dans TRUE pour dessiner l’élément en surbrillance ; Sinon, FALSe.

## <a name="cmfcheaderctrlondrawsortarrow"></a><a name="ondrawsortarrow"></a> CMFCHeaderCtrl::OnDrawSortArrow

Appelé par l’infrastructure pour dessiner la flèche de tri.

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

*rectArrow*<br/>
dans Rectangle englobant de la flèche de tri.

## <a name="cmfcheaderctrlonfillbackground"></a><a name="onfillbackground"></a> CMFCHeaderCtrl::OnFillBackground

Appelé par l’infrastructure pour remplir l’arrière-plan d’une colonne de contrôle d’en-tête.

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

### <a name="remarks"></a>Notes

## <a name="cmfcheaderctrlremovesortcolumn"></a><a name="removesortcolumn"></a> CMFCHeaderCtrl::RemoveSortColumn

Supprime la colonne spécifiée de la liste des colonnes de tri.

```cpp
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Paramètres

*iColumn*<br/>
dans Index de base zéro de la colonne à supprimer.

## <a name="cmfcheaderctrlsetsortcolumn"></a><a name="setsortcolumn"></a> CMFCHeaderCtrl::SetSortColumn

Définit l’ordre de tri d’une colonne spécifiée dans un contrôle header.

```cpp
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>Paramètres

*iColumn*<br/>
dans Index de base zéro d’une colonne de contrôle d’en-tête. Si ce paramètre est inférieur à zéro, cette méthode supprime toutes les colonnes de la liste des colonnes de tri.

*bAscending*<br/>
dans Spécifie l’ordre de tri de la colonne que le paramètre *IColumn* spécifie. TRUE pour définir l’ordre croissant ; FALSe pour définir l’ordre décroissant. La valeur par défaut est TRUE.

*Jout*<br/>
dans TRUE pour définir l’ordre de tri de la colonne que le paramètre *IColumn* spécifie.

Si le contrôle d’en-tête actuel est en mode de *tri sur plusieurs colonnes* , cette méthode ajoute la colonne spécifiée à la liste des colonnes de tri. Utilisez [CMFCHeaderCtrl :: EnableMultipleSort](#enablemultiplesort) pour définir plusieurs modes de tri de colonne.

Si le mode de tri sur plusieurs colonnes n’est pas défini et que cette méthode est compilée en mode débogage, cette méthode déclare. Si le mode de tri sur plusieurs colonnes n’est pas défini et que cette méthode est compilée en mode vente au détail, cette méthode supprime tout d’abord toutes les colonnes de la liste des colonnes de tri, puis ajoute la colonne spécifiée à la liste.

FALSe pour supprimer toutes les colonnes de la liste des colonnes de tri, puis ajouter la colonne spécifiée à la liste. La valeur par défaut est FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir l’ordre de tri d’une colonne. Si nécessaire, cette méthode ajoute la colonne à la liste des colonnes de tri. Le contrôle header utilise l’ordre de tri pour dessiner une flèche de tri pointant vers le haut ou vers le bas.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl, classe](../../mfc/reference/cmfclistctrl-class.md)
