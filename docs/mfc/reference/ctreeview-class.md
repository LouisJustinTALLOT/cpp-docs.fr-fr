---
title: La classe CTreeView | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
dev_langs:
- C++
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a760e567718ad7a485ebe469903c7cbd566daccc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375396"
---
# <a name="ctreeview-class"></a>CTreeView (classe)

Simplifie l’utilisation du contrôle d’arborescence et de [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), la classe qui encapsule la fonctionnalité de contrôle d’arborescence, avec l’architecture document / vue de MFC.

## <a name="syntax"></a>Syntaxe

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CTreeView::CTreeView](#ctreeview)|Construit un objet `CTreeView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTreeView::GetTreeCtrl](#gettreectrl)|Retourne le contrôle d’arborescence associé à la vue.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur cette architecture, consultez la vue d’ensemble pour le [CView](../../mfc/reference/cview-class.md) classe et les références croisées citées il.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcview.h

##  <a name="ctreeview"></a>  CTreeView::CTreeView

Construit un objet `CTreeView`.

```
CTreeView();
```

##  <a name="gettreectrl"></a>  CTreeView::GetTreeCtrl

Retourne une référence au contrôle d’arborescence associée à la vue.

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>Voir aussi

[CCtrlView, classe](../../mfc/reference/cctrlview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)<br/>
[CCtrlView, classe](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl, classe](../../mfc/reference/ctreectrl-class.md)
