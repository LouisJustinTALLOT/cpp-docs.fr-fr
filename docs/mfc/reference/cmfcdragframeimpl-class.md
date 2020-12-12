---
description: 'En savoir plus sur : classe CMFCDragFrameImpl'
title: CMFCDragFrameImpl, classe
ms.date: 10/18/2018
f1_keywords:
- CMFCDragFrameImpl
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
ms.openlocfilehash: 9885b750ace86d11ca573f23c7ee1c03d8926921
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294052"
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl, classe

La `CMFCDragFrameImpl` classe dessine le rectangle de glissement qui apparaît lorsque l’utilisateur fait glisser un volet en mode d’ancrage standard.
Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>Notes

Un objet de cette classe est incorporé dans chaque objet de [classe CPane](../../mfc/reference/cpane-class.md) . Ainsi, chaque volet qui utilise la `CanFloat` méthode affiche un rectangle de glissement lorsque l’utilisateur le fait glisser.

Vous pouvez contrôler l’épaisseur du rectangle de glissement à l’aide de [AFX_GLOBAL_DATA :: m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) et [AFX_GLOBAL_DATA :: m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxdragframeimpl. h

## <a name="cmfcdragframeimplenddrawdragframe"></a><a name="enddrawdragframe"></a> CMFCDragFrameImpl::EndDrawDragFrame

```cpp
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>Paramètres

dans *bClearInternalRects*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdragframeimplinit"></a><a name="init"></a> CMFCDragFrameImpl :: init

```cpp
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>Paramètres

dans *pDraggedWnd*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdragframeimplmovedragframe"></a><a name="movedragframe"></a> CMFCDragFrameImpl::MoveDragFrame

```cpp
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>Paramètres

dans *bForceMove*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdragframeimplplacetabpredocking"></a><a name="placetabpredocking"></a> CMFCDragFrameImpl ::P laceTabPreDocking

```cpp
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>Paramètres

dans *pTabbedBar*<br/>

dans *bFirstTime*<br/>

dans *pCBarToPlaceOn*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdragframeimplremovetabpredocking"></a><a name="removetabpredocking"></a> CMFCDragFrameImpl::RemoveTabPreDocking

```cpp
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>Paramètres

dans *pOldTargetBar*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdragframeimplresetstate"></a><a name="resetstate"></a> CMFCDragFrameImpl :: ResetState

```cpp
void ResetState();
```

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CPane, classe](../../mfc/reference/cpane-class.md)
