---
description: 'En savoir plus sur : classe Cd2dsizeu,'
title: CD2DSizeU, classe
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
ms.openlocfilehash: 0bb2d7cc632012fe8d8c0e3ada09025c2b025e64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154706"
---
# <a name="cd2dsizeu-class"></a>CD2DSizeU, classe

Wrapper pour D2D1_SIZE_U.

## <a name="syntax"></a>Syntaxe

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dsizeu, :: Cd2dsizeu,](#cd2dsizeu)|Surchargé. Construit un `CD2DSizeU` objet à partir de l' `D2D1_SIZE_U` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dsizeu, :: IsNull](#isnull)|Retourne une valeur **booléenne** qui indique si une expression ne contient pas de données valides (null).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dsizeu, :: Operator CSize](#operator_csize)|Convertit `CD2DSizeU` en `CSize` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_SIZE_U`

[Cd2dsizeu,](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxrendertarget. h

## <a name="cd2dsizeucd2dsizeu"></a><a name="cd2dsizeu"></a> Cd2dsizeu, :: Cd2dsizeu,

Construit un objet Cd2dsizeu, à partir de l’objet CSize.

```
CD2DSizeU(const CSize& size);
CD2DSizeU(const D2D1_SIZE_U& size);
CD2DSizeU(const D2D1_SIZE_U* size);

CD2DSizeU(
    UINT32 cx = 0,
    UINT32 cy = 0);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
taille de la source

*adéquat*<br/>
largeur de la source

*CY*<br/>
hauteur de la source

## <a name="cd2dsizeuisnull"></a><a name="isnull"></a> Cd2dsizeu, :: IsNull

Retourne une valeur booléenne qui indique si une expression ne contient pas de données valides (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si Width et Height sont vides ; Sinon, FALSe.

## <a name="cd2dsizeuoperator-csize"></a><a name="operator_csize"></a> Cd2dsizeu, :: Operator CSize

Convertit Cd2dsizeu, en objet CSize.

```
operator CSize();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur actuelle de la taille D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
