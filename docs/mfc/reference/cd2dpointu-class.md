---
title: CD2DPointU, classe
ms.date: 08/29/2019
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: 6289d33aa0672d1ee423d91b11527dccfc868da7
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177180"
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
|[CD2DPointU::CD2DPointU](#cd2dpointu)|Surchargé. Construit un `CD2DPointU` `D2D1_POINT_2U` objet à partir de l’objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dpointu,:: Operator CPoint](#operator_cpoint)|Convertit `CPoint`enobjet `CD2DPointU` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>Configuration requise

**En-tête:** afxrendertarget. h

##  <a name="cd2dpointu"></a>  CD2DPointU::CD2DPointU

Construit un objet Cd2dpointu, à partir de l’objet CPoint.

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>Paramètres

*pt*<br/>
point source

*uX*<br/>
source X

*uY*<br/>
source Y

##  <a name="operator_cpoint"></a>Cd2dpointu,:: Operator CPoint

Convertit Cd2dpointu, en objet CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle du point D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
