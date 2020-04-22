---
title: Classe CListView
ms.date: 11/04/2016
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
helpviewer_keywords:
- CListView [MFC], CListView
- CListView [MFC], GetListCtrl
- CListView [MFC], RemoveImageList
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
ms.openlocfilehash: d7f3b7c43d98c4f2c42d0c27c8e224f33e4b3301
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749126"
---
# <a name="clistview-class"></a>Classe CListView

Simplifie l’utilisation du contrôle de liste et de [CListCtrl](../../mfc/reference/clistctrl-class.md), la classe qui encapsule la fonctionnalité de contrôle de liste, avec l’architecture de vision des documents de MFC.

## <a name="syntax"></a>Syntaxe

```
class CListView : public CCtrlView
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CListView::CListView](#clistview)|Construit un objet `CListView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CListView::GetListCtrl](#getlistctrl)|Retourne le contrôle de liste associé à la vue.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CListView::RemoveImageList](#removeimagelist)|Supprime la liste d’images spécifiée de la vue de liste.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur cette architecture, consultez la classe [CView](../../mfc/reference/cview-class.md) et les références croisées citées là-bas.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>Spécifications

**En-tête:** afxcview.h

## <a name="clistviewclistview"></a><a name="clistview"></a>CListView::CListView

Construit un objet `CListView`.

```
CListView();
```

## <a name="clistviewgetlistctrl"></a><a name="getlistctrl"></a>CListView::GetListCtrl

Appelez cette fonction de membre pour obtenir une référence au contrôle de liste associé à la vue.

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence au contrôle de liste associé à la vue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

## <a name="clistviewremoveimagelist"></a><a name="removeimagelist"></a>CListView::RemoveImageList

Supprime la liste d’images spécifiée de la vue de liste.

```cpp
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>Paramètres

*nImageList*<br/>
L’index zéro de l’image à supprimer.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon ROWLIST](../../overview/visual-cpp-samples.md)<br/>
[Classe CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CCtrlView](../../mfc/reference/cctrlview-class.md)
