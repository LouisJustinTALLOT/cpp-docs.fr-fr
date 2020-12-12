---
description: 'En savoir plus sur : classe CStringElementTraits'
title: CStringElementTraits, classe
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
ms.openlocfilehash: 1e3f6a73e71530250d9dd88408165471028a18e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140489"
---
# <a name="cstringelementtraits-class"></a>CStringElementTraits, classe

Cette classe fournit des fonctions statiques utilisées par les classes de collection qui stockent des `CString` objets.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CStringElementTraits
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CStringElementTraits::INARGTYPE](#inargtype)|Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.|
|[CStringElementTraits::OUTARGTYPE](#outargtype)|Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStringElementTraits::CompareElements](#compareelements)|Statique Appelez cette fonction pour comparer l’égalité de deux éléments de chaîne.|
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|Statique Appelez cette fonction pour comparer deux éléments de chaîne.|
|[CStringElementTraits::CopyElements](#copyelements)|Statique Appelez cette fonction pour copier `CString` des éléments stockés dans un objet de classe de collection.|
|[CStringElementTraits :: Hash](#hash)|Statique Appelez cette fonction pour calculer une valeur de hachage pour l’élément de chaîne donné.|
|[CStringElementTraits::RelocateElements](#relocateelements)|Statique Appelez cette fonction pour déplacer `CString` des éléments stockés dans un objet de classe de collection.|

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions statiques pour copier, déplacer et comparer des chaînes et pour créer une valeur de hachage. Ces fonctions sont utiles lors de l’utilisation d’une classe de collection pour stocker des données basées sur une chaîne. Utilisez [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) lorsque les comparaisons ne respectant pas la casse sont requises. Utilisez [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) lorsque les objets String doivent être traités comme des références.

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête :** CStringT. h

## <a name="cstringelementtraitscompareelements"></a><a name="compareelements"></a> CStringElementTraits::CompareElements

Appelez cette fonction statique pour comparer l’égalité de deux éléments de chaîne.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier élément de chaîne.

*répartition*<br/>
Deuxième élément de chaîne.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si les éléments sont égaux, sinon false.

## <a name="cstringelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a> CStringElementTraits::CompareElementsOrdered

Appelez cette fonction statique pour comparer deux éléments de chaîne.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Paramètres

*str1*<br/>
Premier élément de chaîne.

*répartition*<br/>
Deuxième élément de chaîne.

### <a name="return-value"></a>Valeur renvoyée

Zéro si les chaînes sont identiques, < 0 si *str1* est inférieur à *str2*, ou > 0 si *str1* est supérieur à *str2*. La méthode [CStringT :: compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) est utilisée pour effectuer les comparaisons.

## <a name="cstringelementtraitscopyelements"></a><a name="copyelements"></a> CStringElementTraits::CopyElements

Appelez cette fonction statique pour copier `CString` des éléments stockés dans un objet de classe de collection.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Paramètres

*pDest*<br/>
Pointeur vers le premier élément qui recevra les données copiées.

*pSrc*<br/>
Pointeur vers le premier élément à copier.

*nElements*<br/>
Nombre d’éléments à copier.

### <a name="remarks"></a>Notes

Les éléments source et de destination ne doivent pas se chevaucher.

## <a name="cstringelementtraitshash"></a><a name="hash"></a> CStringElementTraits :: Hash

Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de chaîne donné.

```
static ULONG Hash(INARGTYPE str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Élément String.

### <a name="return-value"></a>Valeur renvoyée

Retourne une valeur de hachage, calculée à l’aide du contenu de la chaîne.

## <a name="cstringelementtraitsinargtype"></a><a name="inargtype"></a> CStringElementTraits::INARGTYPE

Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsoutargtype"></a><a name="outargtype"></a> CStringElementTraits::OUTARGTYPE

Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.

```
typedef T& OUTARGTYPE;
```

## <a name="cstringelementtraitsrelocateelements"></a><a name="relocateelements"></a> CStringElementTraits::RelocateElements

Appelez cette fonction statique pour déplacer `CString` des éléments stockés dans un objet de classe de collection.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Paramètres

*pDest*<br/>
Pointeur vers le premier élément qui recevra les données déplacées.

*pSrc*<br/>
Pointeur vers le premier élément à déplacer.

*nElements*<br/>
Nombre d’éléments à déplacer.

### <a name="remarks"></a>Notes

Cette fonction statique appelle [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), ce qui est suffisant pour la plupart des types de données. Si les objets qui sont déplacés contiennent des pointeurs vers leurs propres membres, cette fonction statique doit être substituée.

## <a name="see-also"></a>Voir aussi

[CElementTraitsBase, classe](../../atl/reference/celementtraitsbase-class.md)<br/>
[CStringElementTraitsI, classe](../../atl/reference/cstringelementtraitsi-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
