---
description: 'En savoir plus sur : classe CAutoVectorPtrElementTraits'
title: CAutoVectorPtrElementTraits, classe
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
ms.openlocfilehash: 571b85c1b11968289d372f9c349ffcdb754dc381
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147093"
---
# <a name="cautovectorptrelementtraits-class"></a>CAutoVectorPtrElementTraits, classe

Cette classe fournit des méthodes, des fonctions statiques et des typedefs utiles lors de la création de collections de pointeurs intelligents à l’aide d’opérateurs Vector New et DELETE.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CAutoVectorPtrElementTraits :
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de pointeur.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.|
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes, des fonctions statiques et des typedefs pour faciliter la création d’objets de classe de collection contenant des pointeurs intelligents. Contrairement à [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md), cette classe utilise des opérateurs Vector New et DELETE.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoVectorPtrElementTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cautovectorptrelementtraitsinargtype"></a><a name="inargtype"></a> CAutoVectorPtrElementTraits::INARGTYPE

Type de données à utiliser pour ajouter des éléments à l’objet de classe de collection.

```
typedef CAutoVectorPtr<T>& INARGTYPE;
```

## <a name="cautovectorptrelementtraitsoutargtype"></a><a name="outargtype"></a> CAutoVectorPtrElementTraits::OUTARGTYPE

Type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.

```
typedef T*& OUTARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[CDefaultElementTraits, classe](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CAutoVectorPtr, classe](../../atl/reference/cautovectorptr-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
