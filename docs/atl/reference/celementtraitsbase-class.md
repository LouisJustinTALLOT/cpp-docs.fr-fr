---
title: Celementtraitsbase, classe
ms.date: 11/04/2016
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
ms.openlocfilehash: 769fa5abff223ad570847b8bf68378ce85df664e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509014"
---
# <a name="celementtraitsbase-class"></a>Celementtraitsbase, classe

Cette classe fournit par défaut copie et déplacer des méthodes pour une classe de collection.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CElementTraitsBase::INARGTYPE](#inargtype)|Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.|
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CElementTraitsBase::CopyElements](#copyelements)|Appelez cette méthode pour copier des éléments stockés dans un objet de classe de collection.|
|[CElementTraitsBase::RelocateElements](#relocateelements)|Appelez cette méthode pour déplacer des éléments stockés dans un objet de classe de collection.|

## <a name="remarks"></a>Notes

Cette classe de base définit des méthodes pour la copie et déplacement d’éléments dans une classe de collection. Il est utilisé par les classes [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md), et [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

##  <a name="copyelements"></a>  CElementTraitsBase::CopyElements

Appelez cette méthode pour copier des éléments stockés dans un objet de classe de collection.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Paramètres

*pDest*<br/>
Pointeur vers le premier élément qui reçoit les données copiées.

*pSrc*<br/>
Pointeur vers le premier élément à copier.

*nElements*<br/>
Nombre d'éléments à copier.

### <a name="remarks"></a>Notes

Les éléments source et de destination ne doivent pas se chevaucher.

##  <a name="inargtype"></a>  CElementTraitsBase::INARGTYPE

Le type de données à utiliser pour l’ajout d’éléments à la collection.

```
typedef const T& INARGTYPE;
```

##  <a name="outargtype"></a>  CElementTraitsBase::OUTARGTYPE

Le type de données à utiliser pour récupérer des éléments de la collection.

```
typedef T& OUTARGTYPE;
```

##  <a name="relocateelements"></a>  CElementTraitsBase::RelocateElements

Appelez cette méthode pour déplacer des éléments stockés dans un objet de classe de collection.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Paramètres

*pDest*<br/>
Pointeur vers le premier élément qui reçoit les données déplacées.

*pSrc*<br/>
Pointeur vers le premier élément à déplacer.

*nElements*<br/>
Le nombre d’éléments à déplacer.

### <a name="remarks"></a>Notes

Cette méthode appelle [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), ce qui est suffisant pour la plupart des types de données. Si les objets en cours de déplacement contiennent des pointeurs vers leurs propres membres, cette méthode devrez être substituée.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
