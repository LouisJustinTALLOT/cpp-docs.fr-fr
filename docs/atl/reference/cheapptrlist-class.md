---
title: Classe CHeapPtrList
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
ms.openlocfilehash: 0500ab8f76049aeaf1c89355ea5450a93243b734
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326858"
---
# <a name="cheapptrlist-class"></a>Classe CHeapPtrList

Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs de tas.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename E, class Allocator = ATL::CCRTAllocator>
class CHeapPtrList
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```

#### <a name="parameters"></a>Paramètres

*E*<br/>
Le type d’objet à stocker dans la classe de collecte.

*Allocator*<br/>
La classe d’allocation de mémoire à utiliser. La valeur par défaut est [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|Constructeur.|

## <a name="remarks"></a>Notes

Cette classe fournit un constructeur et dérive des méthodes de [CAtlList](../../atl/reference/catllist-class.md) et [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) pour aider à la création d’un objet de classe de collecte stockant des pointeurs de tas.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CAtlList](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="cheapptrlistcheapptrlist"></a><a name="cheapptrlist"></a>CHeapPtrList::CHeapPtrList

Constructeur.

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize (en)*<br/>
Taille du bloc.

### <a name="remarks"></a>Notes

La taille du bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est nécessaire. De plus grandes tailles de blocs réduisent les appels aux routines d’allocation de mémoire, mais utilisent plus de ressources.

## <a name="see-also"></a>Voir aussi

[Classe CAtlList](../../atl/reference/catllist-class.md)<br/>
[Classe CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Classe CHeapPtrElraits](../../atl/reference/cheapptrelementtraits-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
