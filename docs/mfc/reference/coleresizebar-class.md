---
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
ms.openlocfilehash: 0b950e7533ba6f95c76ef8d4569980a9a82ea591
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224408"
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
|[COleResizeBar::COleResizeBar](#coleresizebar)|Construit un objet `COleResizeBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleResizeBar::Create](#create)|Crée et initialise une fenêtre enfant de Windows et l’associe à la `COleResizeBar` objet.|

## <a name="remarks"></a>Notes

`COleResizeBar` les objets apparaissent en tant qu’un [CRectTracker](../../mfc/reference/crecttracker-class.md) avec une bordure hachurée et externe des poignées de redimensionnement.

`COleResizeBar` les objets sont généralement incorporés membres d’objets de fenêtre frame dérivés de la [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) classe.

Pour plus d’informations, consultez l’article [Activation](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxole.h

##  <a name="coleresizebar"></a>  COleResizeBar::COleResizeBar

Construit un objet `COleResizeBar`.

```
COleResizeBar();
```

### <a name="remarks"></a>Notes

Appelez `Create` pour créer l’objet de barre de redimensionnement.

##  <a name="create"></a>  COleResizeBar::Create

Crée une fenêtre enfant et l’associe le `COleResizeBar` objet.

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
Spécifie le [style de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) attributs.

*nID*<br/>
ID de fenêtre enfant de la barre redimensionnement.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la barre de redimensionnement a été créée ; sinon 0.

## <a name="see-also"></a>Voir aussi

[Exemple MFC SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc, classe](../../mfc/reference/coleserverdoc-class.md)
