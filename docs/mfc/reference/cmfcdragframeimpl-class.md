---
title: Classe CMFCDragFrameImpl
ms.date: 10/18/2018
f1_keywords:
- CMFCDragFrameImpl
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
ms.openlocfilehash: 527fd089962e05c44a7e47b1ae52345116da4470
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752442"
---
# <a name="cmfcdragframeimpl-class"></a>Classe CMFCDragFrameImpl

La `CMFCDragFrameImpl` classe dessine le rectangle de traînée qui apparaît lorsque l’utilisateur traîne une vitre en mode dock standard.
Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>Notes

Un objet de cette classe est intégré dans chaque objet [de classe CPane.](../../mfc/reference/cpane-class.md) Ainsi, chaque volet qui `CanFloat` utilise la méthode affiche un rectangle de traînée lorsque l’utilisateur le traîne.

Vous pouvez contrôler l’épaisseur du rectangle de traînée en utilisant [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) et [AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxdragframeimpl.h

## <a name="cmfcdragframeimplenddrawdragframe"></a><a name="enddrawdragframe"></a>CMFCDragFrameImpl::EndDrawDragFrame

```cpp
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>Paramètres

[dans] *bClearInternalRects (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdragframeimplinit"></a><a name="init"></a>CMFCDragFrameImpl::Init

```cpp
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>Paramètres

[dans] *pDraggedWnd*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdragframeimplmovedragframe"></a><a name="movedragframe"></a>CMFCDragFrameImpl::MoveDragFrame

```cpp
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>Paramètres

[dans] *bForceMove (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdragframeimplplacetabpredocking"></a><a name="placetabpredocking"></a>CMFCDragFrameImpl::PlaceTabPreDocking

```cpp
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>Paramètres

[dans] *pTabbedBar (en)*<br/>

[dans] *bFirstTime (en)*<br/>

[dans] *pCBarToPlaceOn*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdragframeimplremovetabpredocking"></a><a name="removetabpredocking"></a>CMFCDragFrameImpl::RemoveTabPreDocking

```cpp
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>Paramètres

[dans] *pOldTargetBar*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdragframeimplresetstate"></a><a name="resetstate"></a>CMFCDragFrameImpl::ResetState

```cpp
void ResetState();
```

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)
