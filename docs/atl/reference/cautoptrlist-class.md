---
title: Cautoptrlist, classe
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
ms.openlocfilehash: a7e5c2db31100da8901deaae61527c65655faa7e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551409"
---
# <a name="cautoptrlist-class"></a>Cautoptrlist, classe

Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs intelligents.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename E>
class CAutoPtrList :
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>Paramètres

*E*<br/>
Le type de pointeur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|Constructeur.|

## <a name="remarks"></a>Notes

Cette classe fournit un constructeur et est dérivée des méthodes à partir de [CAtlList](../../atl/reference/catllist-class.md) et [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) afin de faciliter la création d’un objet de liste stocker les pointeurs intelligents. La classe [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) fournit une fonction similaire pour un objet de tableau.

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CAtlList](../../atl/reference/catllist-class.md)

`CAutoPtrList`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

##  <a name="cautoptrlist"></a>  CAutoPtrList::CAutoPtrList

Constructeur.

```
CAutoPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
La taille de bloc, avec une valeur par défaut de 10.

### <a name="remarks"></a>Notes

La taille de bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Tailles de bloc supérieures réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources.

## <a name="see-also"></a>Voir aussi

[CAtlList, classe](../../atl/reference/catllist-class.md)<br/>
[CAutoPtrElementTraits, classe](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
