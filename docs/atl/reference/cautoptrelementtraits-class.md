---
title: Cautoptrelementtraits, classe
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
ms.openlocfilehash: 4d13ca8e3de00a49e15e5acbc35c6301b9d7eae2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476519"
---
# <a name="cautoptrelementtraits-class"></a>Cautoptrelementtraits, classe

Cette classe fournit des méthodes, les fonctions statiques et les typedefs utiles lors de la création de collections de pointeurs intelligents.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CAutoPtrElementTraits
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de pointeur.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.|
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes, les fonctions statiques et les typedefs pour contribuer à la création d’objets de classe de collection qui contient des pointeurs intelligents. Les classes [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) et [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) dérivent `CAutoPtrElementTraits`. Si la création d’une collection de pointeurs intelligents requiert new (vecteur) et les opérateurs de suppression, utilisez [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) à la place.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

##  <a name="inargtype"></a>  CAutoPtrElementTraits::INARGTYPE

Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.

```
typedef CAutoPtr<T>& INARGTYPE;
```

##  <a name="outargtype"></a>  CAutoPtrElementTraits::OUTARGTYPE

Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[CDefaultElementTraits, classe](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
