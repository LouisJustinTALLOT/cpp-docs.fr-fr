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
ms.openlocfilehash: be050f98855e5af794166e1f86962111a23bfa2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369064"
---
# <a name="cd2dsizef-class"></a>CD2DSizeF, classe

Un emballage pour D2D1_SIZE_F.

## <a name="syntax"></a>Syntaxe

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Surchargé. Construit un `CD2DSizeF` objet `D2D1_SIZE_F` à partir de l’objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|Renvoie une valeur **boolean** qui indique si une expression ne contient pas de données valides (NULL).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DSizeF::opérateur CSize](#operator_csize)|Convertit `CD2DSizeF` `CSize` en objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dsizefcd2dsizef"></a><a name="cd2dsizef"></a>CD2DSizeF::CD2DSizeF

Construit un objet CD2DSizeF à partir d’un objet CSize.

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>Paramètres

*Taille*<br/>
taille de la source

*Cx*<br/>
largeur de source

*Cy*<br/>
hauteur source

## <a name="cd2dsizefisnull"></a><a name="isnull"></a>CD2DSizeF::IsNull

Renvoie une valeur Boolean qui indique si une expression ne contient pas de données valides (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la largeur et la hauteur sont vides; autrement FALSE.

## <a name="cd2dsizefoperator-csize"></a><a name="operator_csize"></a>CD2DSizeF::opérateur CSize

Convertit CD2DSizeF en objet CSize.

```
operator CSize();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle de la taille D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
