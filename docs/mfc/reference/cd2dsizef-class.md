---
description: 'En savoir plus sur : classe Cd2dsizef,'
title: CD2DSizeF, classe
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
ms.openlocfilehash: d1416f7cd225be8edf1a7b08f06f611219d7846d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97240557"
---
# <a name="cd2dsizef-class"></a>CD2DSizeF, classe

Wrapper pour D2D1_SIZE_F.

## <a name="syntax"></a>Syntaxe

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dsizef, :: Cd2dsizef,](#cd2dsizef)|Surchargé. Construit un `CD2DSizeF` objet à partir de l' `D2D1_SIZE_F` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dsizef, :: IsNull](#isnull)|Retourne une valeur **booléenne** qui indique si une expression ne contient pas de données valides (null).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dsizef, :: Operator CSize](#operator_csize)|Convertit `CD2DSizeF` en `CSize` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_SIZE_F`

[Cd2dsizef,](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dsizefcd2dsizef"></a><a name="cd2dsizef"></a> Cd2dsizef, :: Cd2dsizef,

Construit un objet Cd2dsizef, à partir de l’objet CSize.

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
taille de la source

*adéquat*<br/>
largeur de la source

*CY*<br/>
hauteur de la source

## <a name="cd2dsizefisnull"></a><a name="isnull"></a> Cd2dsizef, :: IsNull

Retourne une valeur booléenne qui indique si une expression ne contient pas de données valides (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si Width et Height sont vides ; Sinon, FALSe.

## <a name="cd2dsizefoperator-csize"></a><a name="operator_csize"></a> Cd2dsizef, :: Operator CSize

Convertit Cd2dsizef, en objet CSize.

```
operator CSize();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur actuelle de la taille D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
