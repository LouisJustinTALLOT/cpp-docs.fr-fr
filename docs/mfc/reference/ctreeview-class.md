---
title: CTreeView, classe
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
ms.openlocfilehash: fec8379a3944d981672754274f50dd4e60f71b61
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421428"
---
# <a name="ctreeview-class"></a>CTreeView, classe

Simplifie l’utilisation du contrôle d’arborescence et de [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), la classe qui encapsule les fonctionnalités de contrôle d’arborescence, avec l’architecture document/vue de MFC.

## <a name="syntax"></a>Syntaxe

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CTreeView :: CTreeView](#ctreeview)|Construit un objet `CTreeView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CTreeView :: GetTreeCtrl](#gettreectrl)|Retourne le contrôle d’arborescence associé à la vue.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur cette architecture, consultez la vue d’ensemble de la classe [CView](../../mfc/reference/cview-class.md) et les références croisées citées ici.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcview. h

##  <a name="ctreeview"></a>CTreeView :: CTreeView

Construit un objet `CTreeView`.

```
CTreeView();
```

##  <a name="gettreectrl"></a>CTreeView :: GetTreeCtrl

Retourne une référence au contrôle d’arborescence associé à la vue.

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>Voir aussi

[CCtrlView, classe](../../mfc/reference/cctrlview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)<br/>
[CCtrlView, classe](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)
