---
description: 'En savoir plus sur : classe CHeapPtrElementTraits'
title: CHeapPtrElementTraits, classe
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
ms.openlocfilehash: 7ca3d194a284f06e6b5baa0530cb49bc93d8510a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141607"
---
# <a name="cheapptrelementtraits-class"></a>CHeapPtrElementTraits, classe

Cette classe fournit des méthodes, des fonctions statiques et des typedefs utiles lors de la création de collections de pointeurs de tas.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T, class Allocator = ATL::CCRTAllocator>
class CHeapPtrElementTraits :
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type d’objet à stocker dans la classe de collection.

*Allocateur*<br/>
Classe d’allocation de mémoire à utiliser. La valeur par défaut est [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.|
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes, des fonctions statiques et des typedefs pour faciliter la création d’objets de classe de collection contenant des pointeurs de tas. La classe `CHeapPtrList` dérive de `CHeapPtrElementTraits` .

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CHeapPtrElementTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cheapptrelementtraitsinargtype"></a><a name="inargtype"></a> CHeapPtrElementTraits::INARGTYPE

Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.

```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```

## <a name="cheapptrelementtraitsoutargtype"></a><a name="outargtype"></a> CHeapPtrElementTraits::OUTARGTYPE

Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[CDefaultElementTraits, classe](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CComHeapPtr, classe](../../atl/reference/ccomheapptr-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
