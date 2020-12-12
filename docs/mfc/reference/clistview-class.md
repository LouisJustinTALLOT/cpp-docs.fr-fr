---
description: 'En savoir plus sur : classe CListView'
title: CListView (classe)
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
ms.openlocfilehash: 5576a0997c84e8f5639911a1120a6645e720a7cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259563"
---
# <a name="clistview-class"></a>CListView (classe)

Simplifie l’utilisation du contrôle de liste et de [CListCtrl](../../mfc/reference/clistctrl-class.md), la classe qui encapsule les fonctionnalités de contrôle de liste, avec l’architecture document/vue de MFC.

## <a name="syntax"></a>Syntaxe

```
class CListView : public CCtrlView
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CListView :: CListView](#clistview)|Construit un objet `CListView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CListView :: GetListCtrl](#getlistctrl)|Retourne le contrôle de liste associé à la vue.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CListView :: RemoveImageList](#removeimagelist)|Supprime la liste d’images spécifiée de la vue liste.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur cette architecture, consultez la vue d’ensemble de la classe [CView](../../mfc/reference/cview-class.md) et les références croisées citées ici.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcview. h

## <a name="clistviewclistview"></a><a name="clistview"></a> CListView :: CListView

Construit un objet `CListView`.

```
CListView();
```

## <a name="clistviewgetlistctrl"></a><a name="getlistctrl"></a> CListView :: GetListCtrl

Appelez cette fonction membre pour obtenir une référence au contrôle de liste associé à la vue.

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>Valeur renvoyée

Référence au contrôle de liste associé à la vue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

## <a name="clistviewremoveimagelist"></a><a name="removeimagelist"></a> CListView :: RemoveImageList

Supprime la liste d’images spécifiée de la vue liste.

```cpp
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>Paramètres

*nImageList*<br/>
Index de base zéro de l’image à supprimer.

## <a name="see-also"></a>Voir aussi

[Exemple MFC ROWLIST](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView, classe](../../mfc/reference/cctrlview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCtrlView, classe](../../mfc/reference/cctrlview-class.md)
