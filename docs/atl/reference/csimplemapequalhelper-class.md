---
title: Classe CSimpleMapEqualHelper
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: d137a35a517ea93139f036f6e9a7a8de06d518a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330747"
---
# <a name="csimplemapequalhelper-class"></a>Classe CSimpleMapEqualHelper

Cette classe est une aide pour la classe [CSimpleMap.](../../atl/reference/csimplemap-class.md)

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Paramètres

*TKey*<br/>
L’élément clé.

*TVal (en)*<br/>
L’élément de valeur.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Statique) Teste deux clés pour l’égalité.|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Statique) Teste deux valeurs pour l’égalité.|

## <a name="remarks"></a>Notes

Cette classe de traits `CSimpleMap` est un supplément à la classe. Il fournit des `CSimpleMap` méthodes pour comparer deux éléments d’objet (en particulier, les composants clés et de valeur) pour l’égalité. Par défaut, les clés et les valeurs sont comparées à l’aide de **l’opérateur,** mais si la carte contient des types de données complexes qui n’ont pas leur propre opérateur d’égalité, cette classe peut être remplacée pour fournir les fonctionnalités supplémentaires requises.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsimpcoll.h

## <a name="csimplemapequalhelperisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelper::IsEqualKey

Teste deux clés pour l’égalité.

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>Paramètres

*k1*<br/>
La première clé.

*k2*<br/>
La deuxième clé.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si les touches sont égales, fausses autrement.

## <a name="csimplemapequalhelperisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelper::IsEqualValue

Teste deux valeurs pour l’égalité.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Paramètres

*v1*<br/>
Première valeur.

*v2*<br/>
Seconde valeur.

### <a name="return-value"></a>Valeur de retour

Rendements vrais si les valeurs sont égales, fausses autrement.

## <a name="see-also"></a>Voir aussi

[Classe CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
