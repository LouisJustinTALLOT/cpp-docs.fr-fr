---
description: 'En savoir plus sur : classe COleResizeBar'
title: COleResizeBar, classe
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
ms.openlocfilehash: bdd97e854257e2f858b52ed45f4066b26c71394d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226712"
---
# <a name="coleresizebar-class"></a>COleResizeBar, classe

Type de barre de contrôle qui prend en charge le redimensionnement des éléments OLE sur place.

## <a name="syntax"></a>Syntaxe

```
class COleResizeBar : public CControlBar
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleResizeBar :: COleResizeBar](#coleresizebar)|Construit un objet `COleResizeBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleResizeBar :: Create](#create)|Crée et Initialise une fenêtre enfant Windows et l’associe à l' `COleResizeBar` objet.|

## <a name="remarks"></a>Notes

`COleResizeBar` les objets apparaissent sous la forme d’un [CRectTracker](../../mfc/reference/crecttracker-class.md) avec une bordure hachurée et des poignées de redimensionnement externe.

`COleResizeBar` les objets sont généralement des membres incorporés des objets de fenêtre frame dérivés de la classe [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) .

Pour plus d’informations, consultez l’article [activation](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXOLE. h

## <a name="coleresizebarcoleresizebar"></a><a name="coleresizebar"></a> COleResizeBar :: COleResizeBar

Construit un objet `COleResizeBar`.

```
COleResizeBar();
```

### <a name="remarks"></a>Notes

Appelez `Create` pour créer l’objet de barre de redimensionnement.

## <a name="coleresizebarcreate"></a><a name="create"></a> COleResizeBar :: Create

Crée une fenêtre enfant et l’associe à l' `COleResizeBar` objet.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers la fenêtre parente de la barre de redimensionnement.

*dwStyle*<br/>
Spécifie les attributs de [style de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) .

*nID*<br/>
ID de fenêtre enfant de la barre de redimensionnement.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la barre de redimensionnement a été créée ; Sinon, 0.

## <a name="see-also"></a>Voir aussi

[Exemple MFC SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (classe)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc, classe](../../mfc/reference/coleserverdoc-class.md)
