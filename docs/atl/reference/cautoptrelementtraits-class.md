---
description: 'En savoir plus sur : classe CAutoPtrElementTraits'
title: CAutoPtrElementTraits, classe
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
ms.openlocfilehash: 2478f8251f0094aaa5cabf1c0dcc873c9c526cd8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147132"
---
# <a name="cautoptrelementtraits-class"></a>CAutoPtrElementTraits, classe

Cette classe fournit des méthodes, des fonctions statiques et des typedefs utiles lors de la création de collections de pointeurs intelligents.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CAutoPtrElementTraits
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de pointeur.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.|
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes, des fonctions statiques et des typedefs pour faciliter la création d’objets de classe de collection contenant des pointeurs intelligents. Les classes [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) et [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) dérivent de `CAutoPtrElementTraits` . Si vous générez une collection de pointeurs intelligents qui requièrent des opérateurs Vector New et Delete, utilisez [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) à la place.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cautoptrelementtraitsinargtype"></a><a name="inargtype"></a> CAutoPtrElementTraits::INARGTYPE

Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.

```
typedef CAutoPtr<T>& INARGTYPE;
```

## <a name="cautoptrelementtraitsoutargtype"></a><a name="outargtype"></a> CAutoPtrElementTraits::OUTARGTYPE

Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[CDefaultElementTraits, classe](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
