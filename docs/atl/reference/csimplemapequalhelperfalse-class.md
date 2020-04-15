---
title: Classe CSimpleMapEqualHelperFalse
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: b6bf1d4e3be849004e13e593fb5f4b5cb87f8123
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330734"
---
# <a name="csimplemapequalhelperfalse-class"></a>Classe CSimpleMapEqualHelperFalse

Cette classe est une aide pour la classe [CSimpleMap.](../../atl/reference/csimplemap-class.md)

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Statique) Teste deux clés pour l’égalité.|
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Statique) Retourne faux.|

## <a name="remarks"></a>Notes

Cette classe de traits `CSimpleMap` est un supplément à la classe. Il fournit une méthode pour comparer `CSimpleMap` deux éléments contenus dans l’objet, en particulier deux éléments de valeur ou deux éléments clés.

La comparaison de valeur sera toujours de `ATLASSERT` retour faux, et en outre, appellera avec un argument de faux si elle est jamais référencée. Dans les situations où le test d’égalité n’est pas suffisamment défini, cette classe permet à une carte contenant des paires de clés/valeurs de fonctionner correctement pour la plupart des méthodes, mais échoue d’une manière bien définie pour les méthodes qui dépendent de comparaisons telles que [CSimpleMap::FindVal](../../atl/reference/csimplemap-class.md#findval).

## <a name="requirements"></a>Spécifications

**En-tête:** atlsimpcoll.h

## <a name="csimplemapequalhelperfalseisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelperFalse::IsEqualKey

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

### <a name="remarks"></a>Notes

Cette méthode appelle [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md).

## <a name="csimplemapequalhelperfalseisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelperFalse::IsEqualValue

Retourne false.

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>Valeur de retour

Retourne false.

### <a name="remarks"></a>Notes

Cette méthode revient toujours `ATLASSERT` faux, et appellera avec un argument de faux si elle est jamais référencée. Le but `CSimpleMapEqualHelperFalse::IsEqualValue` est de forcer les méthodes utilisant des comparaisons à échouer d’une manière bien définie lorsque les tests d’égalité n’ont pas été correctement définis.

## <a name="see-also"></a>Voir aussi

[Classe CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
