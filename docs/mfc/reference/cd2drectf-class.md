---
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
ms.openlocfilehash: 33d3c5f9e795ad6c91b689436e8a3b1b56966dce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369120"
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
|[CD2DRectF::CD2DRectF](#cd2drectf)|Surchargé. Construit un `CD2DRectF` objet `D2D1_RECT_F` à partir de l’objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DRectF::IsNull](#isnull)|Renvoie une valeur **boolean** qui indique si une expression ne contient pas de données valides (NULL).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DRectF::opérateur CRect](#operator_crect)|Convertit `CD2DRectF` `CRect` en objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2drectfcd2drectf"></a><a name="cd2drectf"></a>CD2DRectF::CD2DRectF

Construit un objet CD2DRectF à partir de l’objet CRect.

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

*Rect*<br/>
rectangle source

*fLeft*<br/>
source gauche de coordonnées

*fTop*<br/>
coordonnées de la source supérieure

*Peur*<br/>
source de coordination à droite

*fBottom*<br/>
coordonnées inférieures de source

## <a name="cd2drectfisnull"></a><a name="isnull"></a>CD2DRectF::IsNull

Renvoie une valeur Boolean qui indique si une expression ne contient pas de données valides (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si les valeurs supérieures, gauche, inférieures et droites du rectangle sont toutes égales à 0; autrement FALSE.

## <a name="cd2drectfoperator-crect"></a><a name="operator_crect"></a>CD2DRectF::opérateur CRect

Convertit CD2DRectF en objet CRect.

```
operator CRect();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle du rectangle D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
