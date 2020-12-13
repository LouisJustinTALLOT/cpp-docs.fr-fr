---
description: 'En savoir plus sur : classe CDefaultCharTraits'
title: CDefaultCharTraits, classe
ms.date: 11/04/2016
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
ms.openlocfilehash: 6d98c6b6ffb527fef1e5b2320b46eda61ec3f670
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141958"
---
# <a name="cdefaultchartraits-class"></a>CDefaultCharTraits, classe

Cette classe fournit deux fonctions statiques pour la conversion de caractères entre majuscules et minuscules.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CDefaultCharTraits
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDefaultCharTraits::CharToLower](#chartolower)|Statique Appelez cette fonction pour convertir un caractère en majuscules.|
|[CDefaultCharTraits::CharToUpper](#chartoupper)|Statique Appelez cette fonction pour convertir un caractère en minuscules.|

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions qui sont utilisées par la classe [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cdefaultchartraitschartolower"></a><a name="chartolower"></a> CDefaultCharTraits::CharToLower

Appelez cette fonction pour convertir un caractère en minuscules.

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Caractère à convertir en minuscule.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

## <a name="cdefaultchartraitschartoupper"></a><a name="chartoupper"></a> CDefaultCharTraits::CharToUpper

Appelez cette fonction pour convertir un caractère en majuscules.

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Caractère à convertir en majuscule.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
