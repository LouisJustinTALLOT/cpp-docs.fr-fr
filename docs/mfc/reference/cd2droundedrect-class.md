---
description: 'En savoir plus sur : classe Cd2droundedrect,'
title: CD2DRoundedRect, classe
ms.date: 11/04/2016
f1_keywords:
- CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect::CD2DRoundedRect
helpviewer_keywords:
- CD2DRoundedRect [MFC], CD2DRoundedRect
ms.assetid: 06207fb5-e92b-41c0-bceb-b45d8f466531
ms.openlocfilehash: 13c1b0910c9d78f615d64e3eecba8bb813916413
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240661"
---
# <a name="cd2droundedrect-class"></a>CD2DRoundedRect, classe

Wrapper pour `D2D1_ROUNDED_RECT`.

## <a name="syntax"></a>Syntaxe

```
class CD2DRoundedRect : public D2D1_ROUNDED_RECT;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2droundedrect, :: Cd2droundedrect,](#cd2droundedrect)|Surchargé. Construit un `CD2DRoundedRect` objet à partir de l' `D2D1_ROUNDED_RECT` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_ROUNDED_RECT`

[Cd2droundedrect,](../../mfc/reference/cd2droundedrect-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2droundedrectcd2droundedrect"></a><a name="cd2droundedrect"></a> Cd2droundedrect, :: Cd2droundedrect,

Construit un objet Cd2droundedrect, à partir de l’objet Cd2drectf,.

```
CD2DRoundedRect(
    const CD2DRectF& rectIn,
    const CD2DSizeF& sizeRadius);

CD2DRoundedRect(const D2D1_ROUNDED_RECT& rectIn);
CD2DRoundedRect(const D2D1_ROUNDED_RECT* rectIn);
```

### <a name="parameters"></a>Paramètres

*recto*<br/>
rectangle source

*sizeRadius*<br/>
taille du rayon

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
