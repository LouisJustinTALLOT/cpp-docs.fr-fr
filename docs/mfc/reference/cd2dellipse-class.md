---
title: CD2DEllipse, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
ms.openlocfilehash: 3abf0736884840be7bdcfcd55cb18a0bc8e69195
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270821"
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
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|Surchargé. Construit un `CD2DEllipse` à partir de l’objet `D2D1_ELLIPSE` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget.h

##  <a name="cd2dellipse"></a>  CD2DEllipse::CD2DEllipse

Construit un objet CD2DEllipse à partir de l’objet de CD2DRectF.

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
  CD2DEllipse(const D2D1_ELLIPSE* ellipse);

CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>Paramètres

*rect*<br/>
rectangle source

*ellipse*<br/>
ellipse de source

*ptCenter*<br/>
Le point central de l’ellipse.

*sizeRadius*<br/>
Le rayon X et le rayon Y de l’ellipse.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
