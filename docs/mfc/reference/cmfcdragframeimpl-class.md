---
title: Cmfcdragframeimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDragFrameImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8cf56cec1a9b09a9176577fa7fce58a853a1d3aa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433996"
---
# <a name="cmfcdragframeimpl-class"></a>Cmfcdragframeimpl, classe

Le `CMFCDragFrameImpl` classe dessine le rectangle de glissement qui s’affiche lorsque l’utilisateur fait glisser un volet dans le mode d’ancrage standard.
Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>Notes

Un objet de cette classe est incorporé dans chaque [CPANE, classe](../../mfc/reference/cpane-class.md) objet. Par conséquent, chaque volet qui utilise le `CanFloat` méthode affiche un rectangle de glissement lorsque l’utilisateur fait glisser.

Vous pouvez contrôler l’épaisseur de la faire glisser le rectangle en utilisant [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) et [AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdragframeimpl.h

##  <a name="enddrawdragframe"></a>  CMFCDragFrameImpl::EndDrawDragFrame


```
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>Paramètres

[in] *bClearInternalRects*

### <a name="remarks"></a>Notes

##  <a name="init"></a>  CMFCDragFrameImpl::Init


```
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>Paramètres

[in] *pDraggedWnd*

### <a name="remarks"></a>Notes

##  <a name="movedragframe"></a>  CMFCDragFrameImpl::MoveDragFrame


```
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>Paramètres

[in] *bForceMove*

### <a name="remarks"></a>Notes

##  <a name="placetabpredocking"></a>  CMFCDragFrameImpl::PlaceTabPreDocking


```
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>Paramètres

*pTabbedBar*<br/>
[in] [in] *bFirstTime* [in] *pCBarToPlaceOn*

### <a name="remarks"></a>Notes

##  <a name="removetabpredocking"></a>  CMFCDragFrameImpl::RemoveTabPreDocking


```
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>Paramètres

[in] *pOldTargetBar*

### <a name="remarks"></a>Notes

##  <a name="resetstate"></a>  CMFCDragFrameImpl::ResetState


```
void ResetState();
```

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CPane, classe](../../mfc/reference/cpane-class.md)