---
title: Classe CStringElementTraits
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
ms.openlocfilehash: 078cfd5ff93bfcd8acc747904ea05e6a2e762bc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330618"
---
# <a name="cstringelementtraits-class"></a>Classe CStringElementTraits

Cette classe fournit des fonctions `CString` statiques utilisées par les classes de collecte stockant des objets.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CStringElementTraits
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CStringElementTraits::INARGTYPE](#inargtype)|Le type de données à utiliser pour ajouter des éléments à l’objet de classe de collecte.|
|[CStringElementTraits::OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collecte.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStringElementTraits::CompareElements](#compareelements)|(Statique) Appelez cette fonction pour comparer deux éléments de chaîne pour l’égalité.|
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|(Statique) Appelez cette fonction pour comparer deux éléments de chaîne.|
|[CStringElementTraits::CopyElements](#copyelements)|(Statique) Appelez cette fonction `CString` pour copier les éléments stockés dans un objet de classe de collection.|
|[CStringElementTraits::Hash](#hash)|(Statique) Appelez cette fonction pour calculer une valeur de hachage pour l’élément de chaîne donné.|
|[CStringElementTraits::RelocateElements](#relocateelements)|(Statique) Appelez cette fonction `CString` pour déplacer les éléments stockés dans un objet de classe de collection.|

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions statiques pour copier, déplacer et comparer les cordes et pour créer une valeur de hachage. Ces fonctions sont utiles lors de l’utilisation d’une classe de collecte pour stocker des données à base de chaînes. Utilisez [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) lorsque des comparaisons insensibles au cas sont nécessaires. Utilisez [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) lorsque les objets à cordes doivent être traités comme des références.

Pour plus d’informations, voir [cours de collecte ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête:** cstringt.h

## <a name="cstringelementtraitscompareelements"></a><a name="compareelements"></a>CStringElementTraits::CompareElements

Appelez cette fonction statique pour comparer deux éléments de chaîne pour l’égalité.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Le premier élément de chaîne.

*str2*<br/>
Le deuxième élément de chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si les éléments sont égaux, faux autrement.

## <a name="cstringelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraits::CompareElementsOrdered

Appelez cette fonction statique pour comparer deux éléments de chaîne.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Le premier élément de chaîne.

*str2*<br/>
Le deuxième élément de chaîne.

### <a name="return-value"></a>Valeur de retour

Zéro si les cordes sont identiques, < 0 si *str1* est inférieur à *str2*, ou > 0 si *str1* est plus grand que *str2*. Le [CStringT::La](../../atl-mfc-shared/reference/cstringt-class.md#compare) méthode de comparaison est utilisée pour effectuer les comparaisons.

## <a name="cstringelementtraitscopyelements"></a><a name="copyelements"></a>CStringElementTraits::CopyElements

Appelez cette fonction `CString` statique pour copier les éléments stockés dans un objet de classe de collection.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Paramètres

*pDest*<br/>
Pointeur vers le premier élément qui recevra les données copiées.

*pSrc (en)*<br/>
Pointeur vers le premier élément à copier.

*nElements*<br/>
Nombre d’éléments à copier.

### <a name="remarks"></a>Notes

Les éléments de source et de destination ne doivent pas se chevaucher.

## <a name="cstringelementtraitshash"></a><a name="hash"></a>CStringElementTraits::Hash

Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de chaîne donné.

```
static ULONG Hash(INARGTYPE str);
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
L’élément de chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne une valeur de hachage, calculée à l’aide du contenu de la chaîne.

## <a name="cstringelementtraitsinargtype"></a><a name="inargtype"></a>CStringElementTraits::INARGTYPE

Le type de données à utiliser pour ajouter des éléments à l’objet de classe de collecte.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsoutargtype"></a><a name="outargtype"></a>CStringElementTraits::OUTARGTYPE

Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collecte.

```
typedef T& OUTARGTYPE;
```

## <a name="cstringelementtraitsrelocateelements"></a><a name="relocateelements"></a>CStringElementTraits::RelocateElements

Appelez cette fonction statique `CString` pour déplacer les éléments stockés dans un objet de classe de collection.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Paramètres

*pDest*<br/>
Pointeur vers le premier élément qui recevra les données relocalisées.

*pSrc (en)*<br/>
Pointeur vers le premier élément à déplacer.

*nElements*<br/>
Le nombre d’éléments à déplacer.

### <a name="remarks"></a>Notes

Cette fonction statique appelle [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), ce qui est suffisant pour la plupart des types de données. Si les objets déplacés contiennent des indications à leurs propres membres, cette fonction statique devra être remplacée.

## <a name="see-also"></a>Voir aussi

[Classe CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Classe CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
