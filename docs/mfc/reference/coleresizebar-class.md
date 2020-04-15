---
title: Classe COleResizeBar
ms.date: 11/04/2016
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
ms.openlocfilehash: beb0c37b6ac23310b7d5c8506fbdaf677dd74d8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376156"
---
# <a name="coleresizebar-class"></a>Classe COleResizeBar

Type de barre de contrôle qui prend en charge le redimensionnement des éléments OLE sur place.

## <a name="syntax"></a>Syntaxe

```
class COleResizeBar : public CControlBar
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleResizeBar::COleResizeBar](#coleresizebar)|Construit un objet `COleResizeBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleResizeBar::Créer](#create)|Crée et initialise une fenêtre d’enfant `COleResizeBar` Windows et l’associe à l’objet.|

## <a name="remarks"></a>Notes

`COleResizeBar`les objets apparaissent comme un [CRectTracker](../../mfc/reference/crecttracker-class.md) avec une bordure éclose et des poignées de resize extérieures.

`COleResizeBar`les objets sont généralement des membres intégrés d’objets de fenêtre de cadre dérivés de la classe [COleIPFrameWnd.](../../mfc/reference/coleipframewnd-class.md)

Pour plus d’informations, voir l’article [Activation](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar (en)](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="coleresizebarcoleresizebar"></a><a name="coleresizebar"></a>COleResizeBar::COleResizeBar

Construit un objet `COleResizeBar`.

```
COleResizeBar();
```

### <a name="remarks"></a>Notes

Appelez `Create` pour créer l’objet de barre de resize.

## <a name="coleresizebarcreate"></a><a name="create"></a>COleResizeBar::Créer

Crée une fenêtre pour enfant `COleResizeBar` et l’associe à l’objet.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers la fenêtre parente de la barre de resize.

*dwStyle (en)*<br/>
Spécifie les attributs de [style de fenêtre.](../../mfc/reference/styles-used-by-mfc.md#window-styles)

*nID*<br/>
L’id de fenêtre pour enfants de la barre de resize.

### <a name="return-value"></a>Valeur de retour

Nonzero si la barre de resize a été créée; sinon 0.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc, classe](../../mfc/reference/coleserverdoc-class.md)
