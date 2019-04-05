---
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
ms.openlocfilehash: 698e37b2853a2ca3698ee0a426c8ded688c99c58
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776620"
---
# <a name="clistview-class"></a>CListView (classe)

Simplifie l’utilisation du contrôle de liste et de [CListCtrl](../../mfc/reference/clistctrl-class.md), la classe qui encapsule la fonctionnalité de contrôle de liste, avec l’architecture document / vue de MFC.

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
|[CListView::RemoveImageList](#removeimagelist)|Supprime la liste de l’image spécifiée dans la liste.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur cette architecture, consultez la vue d’ensemble pour le [CView](../../mfc/reference/cview-class.md) classe et les références croisées citées il.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcview.h

##  <a name="clistview"></a>  CListView::CListView

Construit un objet `CListView`.

```
CListView();
```

##  <a name="getlistctrl"></a>  CListView::GetListCtrl

Appelez cette fonction membre pour obtenir une référence au contrôle de liste associée à la vue.

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence au contrôle de liste associée à la vue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

##  <a name="removeimagelist"></a>  CListView::RemoveImageList

Supprime la liste de l’image spécifiée dans la liste.

```
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
