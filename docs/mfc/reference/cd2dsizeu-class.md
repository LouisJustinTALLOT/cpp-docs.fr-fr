---
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
ms.openlocfilehash: 45625331d0c1be8ca7c663d12c53516dc7bd77c7
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177183"
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
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|Surchargé. Construit un `CD2DSizeU` objet à partir `D2D1_SIZE_U` de l’objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cd2dsizeu,:: IsNull](#isnull)|Retourne une valeur **booléenne** qui indique si une expression ne contient pas de données valides (null).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dsizeu,:: Operator CSize](#operator_csize)|Convertit `CSize`enobjet `CD2DSizeU` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête:** afxrendertarget. h

##  <a name="cd2dsizeu"></a>  CD2DSizeU::CD2DSizeU

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

*cx*<br/>
largeur de la source

*cy*<br/>
hauteur de la source

##  <a name="isnull"></a>Cd2dsizeu,:: IsNull

Retourne une valeur booléenne qui indique si une expression ne contient pas de données valides (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si Width et Height sont vides; Sinon, FALSe.

##  <a name="operator_csize"></a>Cd2dsizeu,:: Operator CSize

Convertit Cd2dsizeu, en objet CSize.

```
operator CSize();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle de la taille D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
