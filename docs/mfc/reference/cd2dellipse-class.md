---
description: 'En savoir plus sur : classe Cd2dellipse,'
title: CD2DEllipse, classe
ms.date: 08/29/2019
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
ms.openlocfilehash: 827ba5515cb4b20cb8e5b10012590a001e01c08f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313058"
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
|[Cd2dellipse, :: Cd2dellipse,](#cd2dellipse)|Surchargé. Construit un `CD2DEllipse` objet à partir de l' `D2D1_ELLIPSE` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dellipsecd2dellipse"></a><a name="cd2dellipse"></a> Cd2dellipse, :: Cd2dellipse,

Construit un objet Cd2dellipse, à partir de l’objet Cd2drectf,.

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
CD2DEllipse(const D2D1_ELLIPSE* ellipse);

CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
rectangle source

*es*<br/>
Ellipse source

*ptCenter*<br/>
Point central de l’ellipse.

*sizeRadius*<br/>
Rayons X et Y de l’ellipse.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
