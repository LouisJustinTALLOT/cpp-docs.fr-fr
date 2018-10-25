---
title: Classe de CD2DRectU | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3fc66e5cc116ce97a9abead8eeb6607f7a36ef7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052679"
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

*Rect*<br/>
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
