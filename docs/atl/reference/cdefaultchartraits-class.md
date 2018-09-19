---
title: Cdefaultchartraits, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69b6a7b94e993641452154ede11d65929424df5e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095753"
---
# <a name="cdefaultchartraits-class"></a>Cdefaultchartraits, classe

Cette classe fournit deux fonctions statiques pour la conversion des caractères entre majuscules et minuscules.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CDefaultCharTraits
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDefaultCharTraits::CharToLower](#chartolower)|(Statique) Appelez cette fonction pour convertir un caractère en majuscules.|
|[CDefaultCharTraits::CharToUpper](#chartoupper)|(Statique) Appelez cette fonction pour convertir un caractère en minuscule.|

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions qui sont utilisées par la classe [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

##  <a name="chartolower"></a>  CDefaultCharTraits::CharToLower

Appelez cette fonction pour convertir un caractère en minuscule.

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Caractère à convertir en minuscule.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

##  <a name="chartoupper"></a>  CDefaultCharTraits::CharToUpper

Appelez cette fonction pour convertir un caractère en majuscules.

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Caractère à convertir en majuscule.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
