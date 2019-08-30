---
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
ms.openlocfilehash: df895c278003e2c71f37a00af6bf14912756701a
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177199"
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
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Surchargé. Construit un `CD2DSizeF` objet à partir `D2D1_SIZE_F` de l’objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|Retourne une valeur **booléenne** qui indique si une expression ne contient pas de données valides (null).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Cd2dsizef,:: Operator CSize](#operator_csize)|Convertit `CSize`enobjet `CD2DSizeF` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête:** afxrendertarget. h

##  <a name="cd2dsizef"></a>  CD2DSizeF::CD2DSizeF

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

*cx*<br/>
largeur de la source

*cy*<br/>
hauteur de la source

##  <a name="isnull"></a>Cd2dsizef,:: IsNull

Retourne une valeur booléenne qui indique si une expression ne contient pas de données valides (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si Width et Height sont vides; Sinon, FALSe.

##  <a name="operator_csize"></a>Cd2dsizef,:: Operator CSize

Convertit Cd2dsizef, en objet CSize.

```
operator CSize();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle de la taille D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
