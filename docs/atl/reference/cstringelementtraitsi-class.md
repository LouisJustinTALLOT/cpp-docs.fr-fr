---
description: 'En savoir plus sur : classe CStringElementTraitsI'
title: CStringElementTraitsI, classe
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
ms.openlocfilehash: 0a626677f4a62805933b2effb4811394626374a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140399"
---
# <a name="cstringelementtraitsi-class"></a>CStringElementTraitsI, classe

Cette classe fournit des fonctions statiques liées aux chaînes stockées dans des objets de classe de collection. Elle est similaire à [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), mais effectue des comparaisons qui ne respectent pas la casse.

## <a name="syntax"></a>Syntaxe

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CStringElementTraitsI::INARGTYPE](#inargtype)|Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.|
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStringElementTraitsI::CompareElements](#compareelements)|Appelez cette fonction statique pour comparer l’égalité de deux éléments de chaîne, en ignorant les différences au cas.|
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Appelez cette fonction statique pour comparer deux éléments de chaîne, en ignorant les différences au sein de la casse.|
|[CStringElementTraitsI :: Hash](#hash)|Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de chaîne donné.|

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions statiques pour comparer des chaînes et pour créer une valeur de hachage. Ces fonctions sont utiles lors de l’utilisation d’une classe de collection pour stocker des données basées sur une chaîne. Utilisez [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) lorsque les objets String doivent être traités comme des références.

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cstringelementtraitsicompareelements"></a><a name="compareelements"></a> CStringElementTraitsI::CompareElements

Appelez cette fonction statique pour comparer l’égalité de deux éléments de chaîne, en ignorant les différences au cas.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier élément de chaîne.

*répartition*<br/>
Deuxième élément de chaîne.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si les éléments sont égaux, sinon false.

### <a name="remarks"></a>Notes

Les comparaisons ne respectent pas la casse.

## <a name="cstringelementtraitsicompareelementsordered"></a><a name="compareelementsordered"></a> CStringElementTraitsI::CompareElementsOrdered

Appelez cette fonction statique pour comparer deux éléments de chaîne, en ignorant les différences au sein de la casse.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier élément de chaîne.

*répartition*<br/>
Deuxième élément de chaîne.

### <a name="return-value"></a>Valeur renvoyée

Zéro si les chaînes sont identiques, < 0 si *str1* est inférieur à *str2*, ou > 0 si *str1* est supérieur à *str2*. La méthode [CStringT :: compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) est utilisée pour effectuer les comparaisons.

### <a name="remarks"></a>Notes

Les comparaisons ne respectent pas la casse.

## <a name="cstringelementtraitsihash"></a><a name="hash"></a> CStringElementTraitsI :: Hash

Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de chaîne donné.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Élément String.

### <a name="return-value"></a>Valeur renvoyée

Retourne une valeur de hachage, calculée à l’aide du contenu de la chaîne.

## <a name="cstringelementtraitsiinargtype"></a><a name="inargtype"></a> CStringElementTraitsI::INARGTYPE

Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsioutargtype"></a><a name="outargtype"></a> CStringElementTraitsI::OUTARGTYPE

Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[CElementTraitsBase, classe](../../atl/reference/celementtraitsbase-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[CStringElementTraits, classe](../../atl/reference/cstringelementtraits-class.md)
