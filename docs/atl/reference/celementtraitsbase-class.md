---
description: 'En savoir plus sur : classe CElementTraitsBase'
title: CElementTraitsBase, classe
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
ms.openlocfilehash: a200517e378cc3c3ca854ff60e9a49ac8e43d215
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141776"
---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase, classe

Cette classe fournit des méthodes de copie et de déplacement par défaut pour une classe de collection.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CElementTraitsBase::INARGTYPE](#inargtype)|Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.|
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CElementTraitsBase::CopyElements](#copyelements)|Appelez cette méthode pour copier des éléments stockés dans un objet de classe de collection.|
|[CElementTraitsBase::RelocateElements](#relocateelements)|Appelez cette méthode pour déplacer des éléments stockés dans un objet de classe de collection.|

## <a name="remarks"></a>Notes

Cette classe de base définit des méthodes pour copier et déplacer des éléments dans une classe de collection. Elle est utilisée par les classes [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)et [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="celementtraitsbasecopyelements"></a><a name="copyelements"></a> CElementTraitsBase::CopyElements

Appelez cette méthode pour copier des éléments stockés dans un objet de classe de collection.

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

## <a name="celementtraitsbaseinargtype"></a><a name="inargtype"></a> CElementTraitsBase::INARGTYPE

Type de données à utiliser pour ajouter des éléments à la collection.

```
typedef const T& INARGTYPE;
```

## <a name="celementtraitsbaseoutargtype"></a><a name="outargtype"></a> CElementTraitsBase::OUTARGTYPE

Type de données à utiliser pour récupérer des éléments de la collection.

```
typedef T& OUTARGTYPE;
```

## <a name="celementtraitsbaserelocateelements"></a><a name="relocateelements"></a> CElementTraitsBase::RelocateElements

Appelez cette méthode pour déplacer des éléments stockés dans un objet de classe de collection.

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

Cette méthode appelle [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), ce qui est suffisant pour la plupart des types de données. Si les objets qui sont déplacés contiennent des pointeurs vers leurs propres membres, cette méthode doit être substituée.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
