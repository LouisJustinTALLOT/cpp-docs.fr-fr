---
title: Classe du CD2DSizeU | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06008a2826a2ba2d358fcf3469b8a6b5b107e6be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412352"
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
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|Surchargé. Construit un `CD2DSizeU` à partir de l’objet `D2D1_SIZE_U` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DSizeU::IsNull](#isnull)|Retourne un **booléenne** valeur qui indique si une expression ne contient aucune donnée valide (NULL).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DSizeU::operator CSize](#operator_csize)|Convertit `CD2DSizeU` à `CSize` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrendertarget.h

##  <a name="cd2dsizeu"></a>  CD2DSizeU::CD2DSizeU

Construit un objet du CD2DSizeU à partir de l’objet CSize.

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

*CX*<br/>
largeur de la source

*CY*<br/>
hauteur de la source

##  <a name="isnull"></a>  CD2DSizeU::IsNull

Retourne une valeur booléenne qui indique si une expression ne contient aucune donnée valide (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la largeur et la hauteur sont vides ; Sinon, FALSE.

##  <a name="operator_csize"></a>  CD2DSizeU::operator CSize

Convertit du CD2DSizeU en objet CSize.

```
operator CSize();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle de la taille de D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
