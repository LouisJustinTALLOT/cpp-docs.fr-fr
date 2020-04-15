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
ms.openlocfilehash: a5b87fe2ddd8fb32ddbbb2884c630952afdb079c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359291"
---
# <a name="cd2dsizeu-class"></a>CD2DSizeU, classe

Un emballage pour D2D1_SIZE_U.

## <a name="syntax"></a>Syntaxe

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|Surchargé. Construit un `CD2DSizeU` objet `D2D1_SIZE_U` à partir de l’objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CD2DSizeU::Isnull](#isnull)|Renvoie une valeur **boolean** qui indique si une expression ne contient pas de données valides (NULL).|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CD2DSizeU::opérateur CSize](#operator_csize)|Convertit `CD2DSizeU` `CSize` en objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`D2D1_SIZE_U`

[CD2DSizeU (en anglais)](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxrendertarget.h

## <a name="cd2dsizeucd2dsizeu"></a><a name="cd2dsizeu"></a>CD2DSizeU::CD2DSizeU

Construit un objet CD2DSizeU à partir d’un objet CSize.

```
CD2DSizeU(const CSize& size);
CD2DSizeU(const D2D1_SIZE_U& size);
CD2DSizeU(const D2D1_SIZE_U* size);

CD2DSizeU(
    UINT32 cx = 0,
    UINT32 cy = 0);
```

### <a name="parameters"></a>Paramètres

*Taille*<br/>
taille de la source

*Cx*<br/>
largeur de source

*Cy*<br/>
hauteur source

## <a name="cd2dsizeuisnull"></a><a name="isnull"></a>CD2DSizeU::Isnull

Renvoie une valeur Boolean qui indique si une expression ne contient pas de données valides (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la largeur et la hauteur sont vides; autrement FALSE.

## <a name="cd2dsizeuoperator-csize"></a><a name="operator_csize"></a>CD2DSizeU::opérateur CSize

Convertit CD2DSizeU en objet CSize.

```
operator CSize();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle de la taille D2D.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
