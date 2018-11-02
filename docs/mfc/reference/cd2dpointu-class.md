---
title: CD2DPointU, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: 138916efe781d8bef69a1c4eb61a73c5a405be67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551851"
---
# <a name="cd2dpointu-class"></a>CD2DPointU, classe

Wrapper pour `D2D1_POINT_2U`.

## <a name="syntax"></a>Syntaxe

```
class CD2DPointU : public D2D1_POINT_2U;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DPointU::CD2DPointU](#cd2dpointu)|Surchargé. Construit un `CD2DPointU` à partir de l’objet `D2D1_POINT_2U` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DPointU::operator CPoint](#operator_cpoint)|Convertit `CD2DPointU` à `CPoint` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="cd2dpointu"></a>  CD2DPointU::CD2DPointU

Construit un objet CD2DPointU à partir de l’objet CPoint.

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
  CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
point de code source

*expérience utilisateur*<br/>
source X

*uY*<br/>
source Y

##  <a name="operator_cpoint"></a>  CD2DPointU::operator CPoint

Convertit CD2DPointU en objet CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle du point de D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
