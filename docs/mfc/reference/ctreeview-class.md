---
title: Classe CTreeView
ms.date: 11/04/2016
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
ms.openlocfilehash: 2ef93152c83d3bbec2b89ada0596ee612b24701b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373295"
---
# <a name="ctreeview-class"></a>Classe CTreeView

Simplifie l’utilisation du contrôle des arbres et de [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), la classe qui encapsule la fonctionnalité de contrôle des arbres, avec l’architecture de vision des documents de MFC.

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
|[CTreeView::GetTreeCtrl](#gettreectrl)|Retourne le contrôle de l’arbre associé à la vue.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur cette architecture, consultez la classe [CView](../../mfc/reference/cview-class.md) et les références croisées citées là-bas.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>Spécifications

**En-tête:** afxcview.h

## <a name="ctreeviewctreeview"></a><a name="ctreeview"></a>CTreeView::CTreeView

Construit un objet `CTreeView`.

```
CTreeView();
```

## <a name="ctreeviewgettreectrl"></a><a name="gettreectrl"></a>CTreeView::GetTreeCtrl

Renvoie une référence au contrôle de l’arbre associé à la vue.

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>Voir aussi

[Classe CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CView](../../mfc/reference/cview-class.md)<br/>
[Classe CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl, classe](../../mfc/reference/ctreectrl-class.md)
