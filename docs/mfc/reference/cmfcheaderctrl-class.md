---
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
ms.openlocfilehash: 5140d02c5acbbc430c3b4d175da1933c79c702b3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752356"
---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl Class

La `CMFCHeaderCtrl` classe prend en charge le tri de plusieurs colonnes dans un contrôle d’en-tête.

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
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|Permet ou désactive le mode *de tri de colonne multiple* pour le contrôle actuel de l’en-tête.|
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Indique si une colonne n’est pas triée ou si elle est triée dans l’ordre ascendant ou descendant.|
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Récupère l’index zéro de la première colonne triée dans le contrôle de l’en-tête.|
|`CMFCHeaderCtrl::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCHeaderCtrl::IsAscending](#isascending)|Indique si une colonne dans le contrôle de l’en-tête est triée dans l’ordre ascendant.|
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|Indique si la fenêtre parente du contrôle actuel de l’en-tête est une boîte de dialogue.|
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Indique si le contrôle d’en-tête actuel est en mode *tri de colonne multiple.*|
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|Supprime la colonne spécifiée de la liste des colonnes de tri.|
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Définit le tri d’ordre d’une colonne spécifiée dans un contrôle d’en-tête.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Appelé par le cadre pour dessiner une colonne de contrôle d’en-tête.|
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Appelé par le cadre pour dessiner la flèche de tri.|
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|Appelé par le cadre pour remplir l’arrière-plan d’une colonne de contrôle d’en-tête.|

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCHeaderCtrl` un objet de la classe, et comment activer le mode *de tri de colonnes multiples* pour le contrôle actuel de l’en-tête.

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>Notes

La `CMFCHeaderCtrl` classe tire une sorte de flèche sur une colonne de contrôle d’en-tête pour indiquer que la colonne est triée. Utilisez plusieurs modes de tri de *colonnes* si un ensemble de colonnes dans le contrôle de liste parent ( [CMFCListCtrl Class](../../mfc/reference/cmfclistctrl-class.md)) peut être trié en même temps.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)

[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxheaderctrl.h

## <a name="cmfcheaderctrlcmfcheaderctrl"></a><a name="cmfcheaderctrl"></a>CMFCHeaderCtrl::CMFCHeaderCtrl

Construit un objet `CMFCHeaderCtrl`.

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>Notes

Ce constructeur initialise les variables membres suivantes aux valeurs spécifiées :

|Variable membre|Valeur|
|---------------------|-----------|
|`m_bIsMousePressed`|FALSE|
|`m_bMultipleSort`|FALSE|
|`m_bAscending`|TRUE|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|FALSE|
|`m_bIsDlgControl`|FALSE|
|`m_hFont`|NULL|

## <a name="cmfcheaderctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCHeaderCtrl::EnableMultipleSort

Permet ou désactive le mode *de tri de colonne multiple* pour le contrôle actuel de l’en-tête.

```cpp
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour activer le mode de tri de colonne multiple ; FALSE pour désactiver le mode de tri de colonnes multiples et pour supprimer toutes les colonnes de la liste des colonnes triées. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour activer ou désactiver le mode de tri de colonnes multiples. Deux colonnes ou plus peuvent participer à une sorte si le contrôle de l’en-tête est en mode tri de colonne multiple.

## <a name="cmfcheaderctrlgetcolumnstate"></a><a name="getcolumnstate"></a>CMFCHeaderCtrl::GetColumnState

Indique si une colonne n’est pas triée ou est triée dans l’ordre ascendant ou descendant.

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>Paramètres

*iColumn iColumn*<br/>
[dans] L’indice zéro d’une colonne.

### <a name="return-value"></a>Valeur de retour

Une valeur qui indique le type d’état de la colonne spécifiée. Le tableau suivant répertorie les valeurs de sortie possibles :

|Valeur|Description|
|-----------|-----------------|
|-1|Trié dans l’ordre décroissant.|
|0|Pas trié.|
|1|Trié dans l’ordre ascendant.|

### <a name="remarks"></a>Notes

## <a name="cmfcheaderctrlgetsortcolumn"></a><a name="getsortcolumn"></a>CMFCHeaderCtrl::GetSortColumn

Récupère l’index zéro de la première colonne triée dans le contrôle de l’en-tête.

```
int GetSortColumn() const;
```

### <a name="return-value"></a>Valeur de retour

L’index d’une colonne triée, ou -1 si aucune colonne triée n’est trouvée.

### <a name="remarks"></a>Notes

Si le contrôle de l’en-tête est en mode *tri de colonne multiple* et que vous avez compilé l’application en mode débogé, cette méthode vous affirme et vous conseille d’utiliser la méthode [CMFCHeaderCtrl:GetColumnState](#getcolumnstate) à la place. Si le contrôle de l’en-tête est en mode tri de colonne multiple et que vous avez compilé l’application en mode vente au détail, cette méthode renvoie -1.

## <a name="cmfcheaderctrlisascending"></a><a name="isascending"></a>CMFCHeaderCtrl::IsAscending

Indique si une colonne dans le contrôle de l’en-tête est triée dans l’ordre ascendant.

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si une colonne dans le contrôle de l’en-tête est triée dans l’ordre ascendant; autrement, FALSE.

### <a name="remarks"></a>Notes

La valeur que cette méthode renvoie est utilisée pour afficher la flèche de tri appropriée sur l’élément de commande d’en-tête. Utilisez la méthode [CMFCHeaderCtrl::SetSortColumn](#setsortcolumn) pour définir l’ordre de tri.

## <a name="cmfcheaderctrlisdialogcontrol"></a><a name="isdialogcontrol"></a>CMFCHeaderCtrl::IsDialogControl

Indique si la fenêtre parente du contrôle actuel de l’en-tête est une boîte de dialogue.

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre parente du contrôle actuel de l’en-tête est une boîte de dialogue; autrement, FALSE.

## <a name="cmfcheaderctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCHeaderCtrl::IsMultipleSort

Indique si le contrôle d’en-tête actuel est en mode *tri de colonne multiple.*

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le mode de tri de colonne multiple est activé ; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez la méthode [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) pour activer ou désactiver le mode de tri de colonnes multiples. Deux colonnes ou plus peuvent participer à une sorte si le contrôle de l’en-tête est en mode tri de colonne multiple.

## <a name="cmfcheaderctrlondrawitem"></a><a name="ondrawitem"></a>CMFCHeaderCtrl::OnDrawItem

Appelé par le cadre pour dessiner une colonne de contrôle d’en-tête.

```
virtual void OnDrawItem(
    CDC* pDC,
    int iItem,
    CRect rect,
    BOOL bIsPressed,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*iItem*<br/>
[dans] L’indice zéro de l’élément à dessiner.

*Rect*<br/>
[dans] Le rectangle de délimitation de l’élément à dessiner.

*bIsPressed*<br/>
[dans] VRAI pour dessiner l’article à l’état pressé; autrement, FALSE.

*bIsHighlighted*<br/>
[dans] VRAI pour dessiner l’élément en état de mise en évidence; autrement, FALSE.

## <a name="cmfcheaderctrlondrawsortarrow"></a><a name="ondrawsortarrow"></a>CMFCHeaderCtrl::OnDrawSortArrow

Appelé par le cadre pour dessiner la flèche de tri.

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

*rectArrow*<br/>
[dans] Le rectangle de délimitation de la sorte de flèche.

## <a name="cmfcheaderctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCHeaderCtrl::OnFillBackground

Appelé par le cadre pour remplir l’arrière-plan d’une colonne de contrôle d’en-tête.

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

### <a name="remarks"></a>Notes

## <a name="cmfcheaderctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCHeaderCtrl::RemoveSortColumn

Supprime la colonne spécifiée de la liste des colonnes de tri.

```cpp
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Paramètres

*iColumn iColumn*<br/>
[dans] L’index zéro de la colonne à supprimer.

## <a name="cmfcheaderctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCHeaderCtrl::SetSortColumn

Définit le tri d’ordre d’une colonne spécifiée dans un contrôle d’en-tête.

```cpp
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>Paramètres

*iColumn iColumn*<br/>
[dans] L’index à base zéro d’une colonne de contrôle d’en-tête. Si ce paramètre est inférieur à zéro, cette méthode supprime toutes les colonnes de la liste des colonnes de tri.

*bAscending*<br/>
[dans] Spécifie le tri d’ordre de la colonne que le paramètre *iColumn* spécifie. VRAI pour fixer l’ordre ascendant; FALSE pour définir l’ordre décroissant. La valeur par défaut est TRUE.

*Badd*<br/>
[dans] VRAI pour définir le tri d’ordre de la colonne que le paramètre *iColumn* spécifie.

Si le contrôle d’en-tête actuel est en mode *de tri de colonne multiple,* cette méthode ajoute la colonne spécifiée à la liste des colonnes de tri. Utilisez [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) pour définir plusieurs mode de tri de colonne.

Si le mode de tri de colonne multiple n’est pas défini et que cette méthode est compilée en mode débogé, cette méthode l’affirme. Si le mode de tri de colonnes multiples n’est pas défini et que cette méthode est compilée en mode vente au détail, cette méthode supprime d’abord toutes les colonnes de la liste des colonnes de tri, puis ajoute la colonne spécifiée à la liste.

FALSE pour d’abord supprimer toutes les colonnes de la liste des colonnes de tri, puis ajouter la colonne spécifiée à la liste. La valeur par défaut est FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir le tri d’ordre d’une colonne. Si nécessaire, cette méthode ajoute la colonne à la liste des colonnes de tri. Le contrôle de l’en-tête utilise l’ordre de tri pour dessiner une sorte de flèche qui pointe vers le haut ou vers le bas.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)
