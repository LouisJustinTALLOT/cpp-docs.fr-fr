---
title: Cstringrefelementtraits, classe
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
ms.openlocfilehash: c57fda64689a80dfa548977e56b0416641bb4360
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277407"
---
# <a name="cstringrefelementtraits-class"></a>Cstringrefelementtraits, classe

Cette classe fournit des fonctions statiques relatives aux chaînes stockées dans les objets de classe de collection. Les objets de chaîne sont traitées en tant que références.

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
|[CStringRefElementTraits::Hash](#hash)|Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de la chaîne donnée.|

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions statiques pour la comparaison de chaînes et pour la création d’une valeur de hachage. Ces fonctions sont utiles lorsque vous utilisez une classe de collection pour stocker des données basé sur chaîne. Contrairement aux [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) et [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` provoque la `CString` arguments à passer en tant que **const** `CString&` fait référence.

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

##  <a name="compareelements"></a>  CStringRefElementTraits::CompareElements

Appelez cette fonction statique pour comparer deux éléments de chaîne pour l’égalité.

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>Paramètres

*element1*<br/>
La première chaîne d’élément.

*element2*<br/>
Le deuxième élément de chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si les éléments sont égaux, sinon false.

##  <a name="compareelementsordered"></a>  CStringRefElementTraits::CompareElementsOrdered

Appelez cette fonction statique pour comparer deux éléments de chaîne.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
La première chaîne d’élément.

*str2*<br/>
Le deuxième élément de chaîne.

### <a name="return-value"></a>Valeur de retour

Zéro si les chaînes sont identiques, < 0 si *str1* est inférieure à *str2*, ou 0 > Si *str1* est supérieur à *str2*. Le [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) méthode est utilisée pour exécuter les comparaisons.

##  <a name="hash"></a>  CStringRefElementTraits::Hash

Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de la chaîne donnée.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Paramètres

*str*<br/>
L’élément de la chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne une valeur de hachage calculée à l’aide du contenu de la chaîne.

## <a name="see-also"></a>Voir aussi

[CElementTraitsBase, classe](../../atl/reference/celementtraitsbase-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
