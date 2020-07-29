---
title: CStringRefElementTraits, classe
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
ms.openlocfilehash: 6fa8772033a5a82940cf30b2a73d6ea356269d67
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226553"
---
# <a name="cstringrefelementtraits-class"></a>CStringRefElementTraits, classe

Cette classe fournit des fonctions statiques liées aux chaînes stockées dans des objets de classe de collection. Les objets String sont traités comme des références.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CStringRefElementTraits : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStringRefElementTraits::CompareElements](#compareelements)|Appelez cette fonction statique pour comparer l’égalité de deux éléments de chaîne.|
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Appelez cette fonction statique pour comparer deux éléments de chaîne.|
|[CStringRefElementTraits :: Hash](#hash)|Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de chaîne donné.|

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions statiques pour comparer des chaînes et pour créer une valeur de hachage. Ces fonctions sont utiles lors de l’utilisation d’une classe de collection pour stocker des données basées sur une chaîne. Contrairement à [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) et [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` les `CString` arguments sont passés en tant que **`const`** `CString&` références.

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cstringrefelementtraitscompareelements"></a><a name="compareelements"></a>CStringRefElementTraits::CompareElements

Appelez cette fonction statique pour comparer l’égalité de deux éléments de chaîne.

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>Paramètres

*Élément1*<br/>
Premier élément de chaîne.

*élément2*<br/>
Deuxième élément de chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si les éléments sont égaux, sinon false.

## <a name="cstringrefelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringRefElementTraits::CompareElementsOrdered

Appelez cette fonction statique pour comparer deux éléments de chaîne.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier élément de chaîne.

*répartition*<br/>
Deuxième élément de chaîne.

### <a name="return-value"></a>Valeur de retour

Zéro si les chaînes sont identiques, < 0 si *str1* est inférieur à *str2*, ou > 0 si *str1* est supérieur à *str2*. La méthode [CStringT :: compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) est utilisée pour effectuer les comparaisons.

## <a name="cstringrefelementtraitshash"></a><a name="hash"></a>CStringRefElementTraits :: Hash

Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de chaîne donné.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Élément String.

### <a name="return-value"></a>Valeur de retour

Retourne une valeur de hachage, calculée à l’aide du contenu de la chaîne.

## <a name="see-also"></a>Voir aussi

[CElementTraitsBase, classe](../../atl/reference/celementtraitsbase-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
