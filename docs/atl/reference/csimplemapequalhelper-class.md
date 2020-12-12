---
description: 'En savoir plus sur : classe CSimpleMapEqualHelper'
title: CSimpleMapEqualHelper, classe
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: 2b8ff742bf24b6c6c4354cef652e3fc697ffb1d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140606"
---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper, classe

Cette classe est une application d’assistance pour la classe [CSimpleMap](../../atl/reference/csimplemap-class.md) .

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Paramètres

*TKey*<br/>
Élément clé.

*TVal*<br/>
Élément de valeur.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|Statique Teste l’égalité de deux clés.|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|Statique Teste si deux valeurs sont égales.|

## <a name="remarks"></a>Notes

Cette classe de traits est un supplément de la `CSimpleMap` classe. Il fournit des méthodes pour comparer deux `CSimpleMap` éléments objet (en particulier, les composants clé et valeur) pour l’égalité. Par défaut, les clés et les valeurs sont comparées à l’aide de **Operator = = ()**, mais si le mappage contient des types de données complexes qui n’ont pas leur propre opérateur d’égalité, cette classe peut être substituée pour fournir les fonctionnalités supplémentaires requises.

## <a name="requirements"></a>Spécifications

**En-tête :** atlsimpcoll. h

## <a name="csimplemapequalhelperisequalkey"></a><a name="isequalkey"></a> CSimpleMapEqualHelper::IsEqualKey

Teste l’égalité de deux clés.

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>Paramètres

*k1*<br/>
Première clé.

*k2*<br/>
Deuxième clé.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si les clés sont égales ; sinon, false.

## <a name="csimplemapequalhelperisequalvalue"></a><a name="isequalvalue"></a> CSimpleMapEqualHelper::IsEqualValue

Teste si deux valeurs sont égales.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Paramètres

*v1*<br/>
Première valeur.

*v2*<br/>
Seconde valeur.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si les valeurs sont égales ; sinon, false.

## <a name="see-also"></a>Voir aussi

[CSimpleMapEqualHelperFalse, classe](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
