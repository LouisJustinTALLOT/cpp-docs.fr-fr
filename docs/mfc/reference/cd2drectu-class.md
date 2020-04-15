---
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
ms.openlocfilehash: 26e647ae01a498a6ad8ca2d7c866f33b01910881
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369108"
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
|[CD2DRectU::CD2DRectU](#cd2drectu)|Surchargé. Construit un `CD2DRectU` objet `D2D1_RECT_U` à partir de l’objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DRectU::Isnull](#isnull)|Renvoie une valeur **boolean** qui indique si une expression ne contient pas de données valides (NULL).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DRectU::opérateur CRect](#operator_crect)|Convertit `CD2DRectU` `CRect` en objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2drectucd2drectu"></a><a name="cd2drectu"></a>CD2DRectU::CD2DRectU

Construit un objet CD2DRectU à partir de l’objet CRect.

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

*Rect*<br/>
rectangle source

*uLeft*<br/>
source gauche de coordonnées

*uTop*<br/>
coordonnées de la source supérieure

*uRight*<br/>
source de coordination à droite

*uBottom*<br/>
coordonnées inférieures de source

## <a name="cd2drectuisnull"></a><a name="isnull"></a>CD2DRectU::Isnull

Renvoie une valeur Boolean qui indique si une expression ne contient pas de données valides (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si les valeurs supérieures, gauche, inférieures et droites du rectangle sont toutes égales à 0; autrement FALSE.

## <a name="cd2drectuoperator-crect"></a><a name="operator_crect"></a>CD2DRectU::opérateur CRect

Convertit CD2DRectU en objet CRect.

```
operator CRect();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle du rectangle D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
