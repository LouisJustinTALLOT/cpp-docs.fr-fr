---
title: Cautovectorptrelementtraits, classe
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
ms.openlocfilehash: 168670709470d7b7fdd77edb3c29d5a9f4049ca3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260082"
---
# <a name="cautovectorptrelementtraits-class"></a>Cautovectorptrelementtraits, classe

Cette classe fournit des méthodes, les fonctions statiques et les typedefs utiles lors de la création de collections de pointeurs intelligents à l’aide de vecteur nouveaux et supprimer des opérateurs.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CAutoVectorPtrElementTraits :
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de pointeur.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.|
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes, les fonctions statiques et les typedefs pour contribuer à la création d’objets de classe de collection qui contient des pointeurs intelligents. Contrairement aux [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md), cette classe utilise vector, nouveaux et supprimer des opérateurs.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoVectorPtrElementTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

##  <a name="inargtype"></a>  CAutoVectorPtrElementTraits::INARGTYPE

Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.

```
typedef CAutoVectorPtr<T>& INARGTYPE;
```

##  <a name="outargtype"></a>  CAutoVectorPtrElementTraits::OUTARGTYPE

Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.

```
typedef T*& OUTARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[CDefaultElementTraits, classe](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CAutoVectorPtr, classe](../../atl/reference/cautovectorptr-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
