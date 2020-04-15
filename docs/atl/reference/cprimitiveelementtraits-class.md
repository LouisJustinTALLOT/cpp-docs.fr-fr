---
title: Classe CPrimitiveElementTraits
ms.date: 11/04/2016
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
ms.openlocfilehash: 6b45d93420d1832091cc451a3e6eb309f61d07a3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331439"
---
# <a name="cprimitiveelementtraits-class"></a>Classe CPrimitiveElementTraits

Cette classe fournit des méthodes et des fonctions par défaut pour une classe de collecte composée de types de données primitives.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données à stocker dans l’objet de classe de collecte.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|Le type de données à utiliser pour ajouter des éléments à l’objet de classe de collecte.|
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collecte.|

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions statiques par défaut et des méthodes pour déplacer, copier, comparer et hachage des éléments de type de données primitifs stockés dans un objet de classe de collecte.

Pour plus d’informations, voir [cours de collecte ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CPrimitiveElementTraits`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="cprimitiveelementtraitsinargtype"></a><a name="inargtype"></a>CPrimitiveElementTraits::INARGTYPE

Le type de données à utiliser pour ajouter des éléments à l’objet de classe de collecte.

```
typedef T INARGTYPE;
```

## <a name="cprimitiveelementtraitsoutargtype"></a><a name="outargtype"></a>CPrimitiveElementTraits::OUTARGTYPE

Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collecte.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[Classe CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
