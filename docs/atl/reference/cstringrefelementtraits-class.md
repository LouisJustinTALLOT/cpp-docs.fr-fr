---
title: Classe CStringRefElementTraits
ms.date: 11/04/2016
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
ms.openlocfilehash: b4dd76b9592b255a1553be3ca7a249f58fb2672e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330578"
---
# <a name="cstringrefelementtraits-class"></a>Classe CStringRefElementTraits

Cette classe fournit des fonctions statiques liées aux cordes stockées dans des objets de classe de collection. Les objets à cordes sont traités comme des références.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CStringRefElementTraits : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStringRefElementTraits::CompareElements](#compareelements)|Appelez cette fonction statique pour comparer deux éléments de chaîne pour l’égalité.|
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Appelez cette fonction statique pour comparer deux éléments de chaîne.|
|[CStringRefElementTraits::Hash](#hash)|Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de chaîne donné.|

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions statiques pour comparer les cordes et pour créer une valeur de hachage. Ces fonctions sont utiles lors de l’utilisation d’une classe de collecte pour stocker des données à base de chaînes. Contrairement à [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) et [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` fait passer les `CString` arguments comme des références **const.** `CString&`

Pour plus d’informations, voir [cours de collecte ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="cstringrefelementtraitscompareelements"></a><a name="compareelements"></a>CStringRefElementTraits::CompareElements

Appelez cette fonction statique pour comparer deux éléments de chaîne pour l’égalité.

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>Paramètres

*élément1*<br/>
Le premier élément de chaîne.

*élément2*<br/>
Le deuxième élément de chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si les éléments sont égaux, faux autrement.

## <a name="cstringrefelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringRefElementTraits::CompareElementsOrdered

Appelez cette fonction statique pour comparer deux éléments de chaîne.

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

## <a name="cstringrefelementtraitshash"></a><a name="hash"></a>CStringRefElementTraits::Hash

Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de chaîne donné.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
L’élément de chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne une valeur de hachage, calculée à l’aide du contenu de la chaîne.

## <a name="see-also"></a>Voir aussi

[Classe CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
