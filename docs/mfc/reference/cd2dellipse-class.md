---
title: CD2DEllipse, classe
ms.date: 08/29/2019
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
ms.openlocfilehash: 82ad2fbfb8558486134f85d7ec9bcaa6eb4e7507
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369260"
---
# <a name="cd2dellipse-class"></a>CD2DEllipse, classe

Wrapper pour `D2D1_ELLIPSE`.

## <a name="syntax"></a>Syntaxe

```
class CD2DEllipse : public D2D1_ELLIPSE;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|Surchargé. Construit un `CD2DEllipse` objet `D2D1_ELLIPSE` à partir de l’objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dellipsecd2dellipse"></a><a name="cd2dellipse"></a>CD2DEllipse::CD2DEllipse

Construit un objet CD2DEllipse à partir d’un objet CD2DRectF.

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
CD2DEllipse(const D2D1_ELLIPSE* ellipse);

CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
rectangle source

*ellipse*<br/>
source ellipse

*ptCenter (ptCenter)*<br/>
Le point central de l’ellipse.

*tailleRadius*<br/>
Le rayon X et le rayon Y de l’ellipse.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
