---
description: 'En savoir plus sur : classe Cd2drectf,'
title: CD2DRectF, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 273a3d07f152f8b24a24175c0f466c8969830ebd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136017"
---
# <a name="cd2drectf-class"></a>CD2DRectF, classe

Wrapper pour `D2D1_RECT_F`.

## <a name="syntax"></a>Syntaxe

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2drectf, :: Cd2drectf,](#cd2drectf)|Surchargé. Construit un `CD2DRectF` objet à partir de l' `D2D1_RECT_F` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2drectf, :: IsNull](#isnull)|Retourne une valeur **booléenne** qui indique si une expression ne contient pas de données valides (null).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2drectf, :: Operator CRect](#operator_crect)|Convertit `CD2DRectF` en `CRect` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2drectfcd2drectf"></a><a name="cd2drectf"></a> Cd2drectf, :: Cd2drectf,

Construit un objet Cd2drectf, à partir de l’objet CRect.

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
rectangle source

*fLeft*<br/>
coordonnée gauche source

*fTop*<br/>
coordonnée supérieure source

*fRight*<br/>
coordonnée droite source

*fBottom*<br/>
coordonnée inférieure source

## <a name="cd2drectfisnull"></a><a name="isnull"></a> Cd2drectf, :: IsNull

Retourne une valeur booléenne qui indique si une expression ne contient pas de données valides (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si les valeurs supérieure, gauche, inférieure et droite du rectangle sont toutes égales à 0 ; Sinon, FALSe.

## <a name="cd2drectfoperator-crect"></a><a name="operator_crect"></a> Cd2drectf, :: Operator CRect

Convertit Cd2drectf, en objet CRect.

```
operator CRect();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur actuelle du rectangle D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
