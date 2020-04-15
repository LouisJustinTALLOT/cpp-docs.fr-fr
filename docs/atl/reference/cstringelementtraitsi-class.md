---
title: Classe CStringElementTraitsI
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
ms.openlocfilehash: 32980e19443cb17a3a688c85ff21195c60ed2124
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330589"
---
# <a name="cstringelementtraitsi-class"></a>Classe CStringElementTraitsI

Cette classe fournit des fonctions statiques liées aux cordes stockées dans des objets de classe de collection. Il est similaire à [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), mais effectue des comparaisons insensibles aux cas.

## <a name="syntax"></a>Syntaxe

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CStringElementTraitsI::INARGTYPE](#inargtype)|Le type de données à utiliser pour ajouter des éléments à l’objet de classe de collecte.|
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collecte.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStringElementTraitsI::CompareElements](#compareelements)|Appelez cette fonction statique pour comparer deux éléments de chaîne pour l’égalité, ignorant les différences dans le cas.|
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Appelez cette fonction statique pour comparer deux éléments de chaîne, ignorant les différences dans le cas.|
|[CStringElementTraitsI::Hash](#hash)|Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de chaîne donné.|

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions statiques pour comparer les cordes et pour créer une valeur de hachage. Ces fonctions sont utiles lors de l’utilisation d’une classe de collecte pour stocker des données à base de chaînes. Utilisez [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) lorsque les objets à cordes doivent être traités comme des références.

Pour plus d’informations, voir [cours de collecte ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="cstringelementtraitsicompareelements"></a><a name="compareelements"></a>CStringElementTraitsI::CompareElements

Appelez cette fonction statique pour comparer deux éléments de chaîne pour l’égalité, ignorant les différences dans le cas.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Le premier élément de chaîne.

*str2*<br/>
Le deuxième élément de chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si les éléments sont égaux, faux autrement.

### <a name="remarks"></a>Notes

Les comparaisons sont insensibles aux cas.

## <a name="cstringelementtraitsicompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraitsI::CompareElementsOrdered

Appelez cette fonction statique pour comparer deux éléments de chaîne, ignorant les différences dans le cas.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Le premier élément de chaîne.

*str2*<br/>
Le deuxième élément de chaîne.

### <a name="return-value"></a>Valeur de retour

Zéro si les cordes sont identiques, < 0 si *str1* est inférieur à *str2*, ou > 0 si *str1* est plus grand que *str2*. Le [CStringT::La](../../atl-mfc-shared/reference/cstringt-class.md#compare) méthode de comparaison est utilisée pour effectuer les comparaisons.

### <a name="remarks"></a>Notes

Les comparaisons sont insensibles aux cas.

## <a name="cstringelementtraitsihash"></a><a name="hash"></a>CStringElementTraitsI::Hash

Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de chaîne donné.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
L’élément de chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne une valeur de hachage, calculée à l’aide du contenu de la chaîne.

## <a name="cstringelementtraitsiinargtype"></a><a name="inargtype"></a>CStringElementTraitsI::INARGTYPE

Le type de données à utiliser pour ajouter des éléments à l’objet de classe de collecte.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsioutargtype"></a><a name="outargtype"></a>CStringElementTraitsI::OUTARGTYPE

Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collecte.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[Classe CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classe CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)
