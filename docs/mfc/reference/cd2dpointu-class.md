---
description: 'En savoir plus sur : classe Cd2dpointu,'
title: CD2DPointU, classe
ms.date: 08/29/2019
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: 04c1c366f3026e4a621892fc1c7617707c33d23d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250996"
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
|[Cd2dpointu, :: Cd2dpointu,](#cd2dpointu)|Surchargé. Construit un `CD2DPointU` objet à partir de l’objet `D2D1_POINT_2U` .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dpointu, :: Operator CPoint](#operator_cpoint)|Convertit `CD2DPointU` en `CPoint` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dpointucd2dpointu"></a><a name="cd2dpointu"></a> Cd2dpointu, :: Cd2dpointu,

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

*Expérience utilisateur*<br/>
source X

*uY*<br/>
source Y

## <a name="cd2dpointuoperator-cpoint"></a><a name="operator_cpoint"></a> Cd2dpointu, :: Operator CPoint

Convertit Cd2dpointu, en objet CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur actuelle du point D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
