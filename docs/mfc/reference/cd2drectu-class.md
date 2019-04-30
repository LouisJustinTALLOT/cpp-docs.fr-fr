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
ms.openlocfilehash: feb8af3992b9f56164ded0e3b6a4529a46fe2a1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396286"
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
|[CD2DRectU::CD2DRectU](#cd2drectu)|Surchargé. Construit un `CD2DRectU` à partir de l’objet `D2D1_RECT_U` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DRectU::IsNull](#isnull)|Retourne un **booléenne** valeur qui indique si une expression ne contient aucune donnée valide (NULL).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DRectU::operator CRect](#operator_crect)|Convertit `CD2DRectU` à `CRect` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="cd2drectu"></a>  CD2DRectU::CD2DRectU

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

*rect*<br/>
rectangle source

*uLeft*<br/>
Coordonnée gauche source

*uTop*<br/>
coordonnée supérieure source

*uRight*<br/>
coordonnée droite source

*uBottom*<br/>
Coordonnée inférieure source

##  <a name="isnull"></a>  CD2DRectU::IsNull

Retourne une valeur booléenne qui indique si une expression ne contient aucune donnée valide (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le du rectangle haut, gauche, bas et valeurs appropriées sont toujours égaux à 0 ; Sinon, FALSE.

##  <a name="operator_crect"></a>  CD2DRectU::operator CRect

Convertit CD2DRectU en objet CRect.

```
operator CRect();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle du rectangle de D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
