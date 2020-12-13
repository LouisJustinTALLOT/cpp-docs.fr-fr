---
description: 'En savoir plus sur : classe CPrimitiveElementTraits'
title: CPrimitiveElementTraits, classe
ms.date: 11/04/2016
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
ms.openlocfilehash: a9a47d9e6268ee6cc858d85e9236b00c270e8841
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141074"
---
# <a name="cprimitiveelementtraits-class"></a>CPrimitiveElementTraits, classe

Cette classe fournit des méthodes et des fonctions par défaut pour une classe de collection composée de types de données primitifs.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données à stocker dans l’objet de classe de collection.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.|
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions et des méthodes statiques par défaut pour déplacer, copier, comparer et hacher des éléments de type de données primitifs stockés dans un objet de classe de collection.

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CPrimitiveElementTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cprimitiveelementtraitsinargtype"></a><a name="inargtype"></a> CPrimitiveElementTraits::INARGTYPE

Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.

```
typedef T INARGTYPE;
```

## <a name="cprimitiveelementtraitsoutargtype"></a><a name="outargtype"></a> CPrimitiveElementTraits::OUTARGTYPE

Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[CDefaultElementTraits, classe](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
