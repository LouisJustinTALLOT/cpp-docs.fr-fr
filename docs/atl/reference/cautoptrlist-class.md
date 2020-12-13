---
description: 'En savoir plus sur : classe CAutoPtrList'
title: CAutoPtrList, classe
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
ms.openlocfilehash: 51544d464904d0ebfd31b82152088a0dfa638969
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152514"
---
# <a name="cautoptrlist-class"></a>CAutoPtrList, classe

Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs intelligents.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename E>
class CAutoPtrList :
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>Paramètres

*E*<br/>
Type de pointeur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|Constructeur.|

## <a name="remarks"></a>Notes

Cette classe fournit un constructeur et dérive les méthodes de [CAtlList](../../atl/reference/catllist-class.md) et [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) pour faciliter la création d’un objet de liste qui stocke les pointeurs intelligents. La classe [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) fournit une fonction similaire pour un objet tableau.

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CAtlList](../../atl/reference/catllist-class.md)

`CAutoPtrList`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cautoptrlistcautoptrlist"></a><a name="cautoptrlist"></a> CAutoPtrList::CAutoPtrList

Constructeur.

```
CAutoPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
Taille de bloc, avec 10 comme valeur par défaut.

### <a name="remarks"></a>Notes

La taille de bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Les tailles de bloc plus volumineuses réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources.

## <a name="see-also"></a>Voir aussi

[CAtlList, classe](../../atl/reference/catllist-class.md)<br/>
[CAutoPtrElementTraits, classe](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
