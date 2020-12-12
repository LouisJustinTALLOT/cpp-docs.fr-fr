---
description: 'En savoir plus sur : classe Cd2drectu,'
title: CD2DRectU, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
ms.openlocfilehash: dadbaf37f1ed11f96f29c7e4cf78eebf8095590d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301618"
---
# <a name="cd2drectu-class"></a>CD2DRectU, classe

Wrapper pour `D2D1_RECT_U`.

## <a name="syntax"></a>Syntaxe

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2drectu, :: Cd2drectu,](#cd2drectu)|Surchargé. Construit un `CD2DRectU` objet à partir de l' `D2D1_RECT_U` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2drectu, :: IsNull](#isnull)|Retourne une valeur **booléenne** qui indique si une expression ne contient pas de données valides (null).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2drectu, :: Operator CRect](#operator_crect)|Convertit `CD2DRectU` en `CRect` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2drectucd2drectu"></a><a name="cd2drectu"></a> Cd2drectu, :: Cd2drectu,

Construit un objet Cd2drectu, à partir de l’objet CRect.

```
CD2DRectU(const CRect& rect);
CD2DRectU(const D2D1_RECT_U& rect);
CD2DRectU(const D2D1_RECT_U* rect);

CD2DRectU(
    UINT32 uLeft = 0,
    UINT32 uTop = 0,
    UINT32 uRight = 0,
    UINT32 uBottom = 0);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
rectangle source

*uLeft*<br/>
coordonnée gauche source

*uTop*<br/>
coordonnée supérieure source

*uRight*<br/>
coordonnée droite source

*uBottom*<br/>
coordonnée inférieure source

## <a name="cd2drectuisnull"></a><a name="isnull"></a> Cd2drectu, :: IsNull

Retourne une valeur booléenne qui indique si une expression ne contient pas de données valides (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si les valeurs supérieure, gauche, inférieure et droite du rectangle sont toutes égales à 0 ; Sinon, FALSe.

## <a name="cd2drectuoperator-crect"></a><a name="operator_crect"></a> Cd2drectu, :: Operator CRect

Convertit Cd2drectu, en objet CRect.

```
operator CRect();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur actuelle du rectangle D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
