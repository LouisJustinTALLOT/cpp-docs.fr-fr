---
description: 'En savoir plus sur : classe Cd2dpointf,'
title: CD2DPointF, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
ms.openlocfilehash: 0f63aa35acb33504c96316b67ecc4f885f4f0247
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193355"
---
# <a name="cd2dpointf-class"></a>CD2DPointF, classe

Wrapper pour `D2D1_POINT_2F`.

## <a name="syntax"></a>Syntaxe

```
class CD2DPointF : public D2D1_POINT_2F;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dpointf, :: Cd2dpointf,](#cd2dpointf)|Surchargé. Construit un `CD2DPointF` objet à partir de l' `D2D1_POINT_2F` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dpointf, :: Operator CPoint](#operator_cpoint)|Convertit `CD2DPointF` en `CPoint` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dpointfcd2dpointf"></a><a name="cd2dpointf"></a> Cd2dpointf, :: Cd2dpointf,

Construit un objet Cd2dpointf, à partir de l’objet CPoint.

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
point source

*Rotation*<br/>
source X

*Années*<br/>
source Y

## <a name="cd2dpointfoperator-cpoint"></a><a name="operator_cpoint"></a> Cd2dpointf, :: Operator CPoint

Convertit Cd2dpointf, en objet CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur actuelle du point D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
