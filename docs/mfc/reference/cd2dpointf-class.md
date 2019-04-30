---
title: CD2DPointF, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
ms.openlocfilehash: b8fe808c3147fa52c5041e2988822ace0ba60896
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396338"
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
|[CD2DPointF::CD2DPointF](#cd2dpointf)|Surchargé. Construit un `CD2DPointF` à partir de l’objet `D2D1_POINT_2F` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DPointF::operator CPoint](#operator_cpoint)|Convertit `CD2DPointF` à `CPoint` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="cd2dpointf"></a>  CD2DPointF::CD2DPointF

Construit un objet CD2DPointF à partir de l’objet CPoint.

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
point de code source

*fX*<br/>
source X

*fY*<br/>
source Y

##  <a name="operator_cpoint"></a>  CD2DPointF::operator CPoint

Convertit CD2DPointF en objet CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle du point de D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
