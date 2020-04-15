---
title: Classe CCRTAllocator
ms.date: 11/04/2016
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
ms.openlocfilehash: 2f6bae3818fa0f1639e0e3cee4e09121580da768
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327178"
---
# <a name="ccrtallocator-class"></a>Classe CCRTAllocator

Cette classe fournit des méthodes pour gérer la mémoire à l’aide de routines de mémoire CRT.

## <a name="syntax"></a>Syntaxe

```
class ATL::CCRTAllocator
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCRTAllocator::Allocate](#allocate)|(Statique) Appelez cette méthode pour allouer la mémoire.|
|[CCRTAllocator::Gratuit](#free)|(Statique) Appelez cette méthode pour libérer la mémoire.|
|[CCRTAllocator::Réallocate](#reallocate)|(Statique) Appelez cette méthode pour réaffecter la mémoire.|

## <a name="remarks"></a>Notes

Cette classe est utilisée par [CHeapPtr](../../atl/reference/cheapptr-class.md) pour fournir les routines d’allocation de mémoire CRT. La classe de contrepartie, [CComAllocator](../../atl/reference/ccomallocator-class.md), fournit les mêmes méthodes en utilisant les routines COM.

## <a name="requirements"></a>Spécifications

**En-tête:** atlcore.h

## <a name="ccrtallocatorallocate"></a><a name="allocate"></a>CCRTAllocator::Allocate

Appelez cette fonction statique pour allouer de la mémoire.

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes (en)*<br/>
Nombre d'octets à allouer.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur void vers l'espace alloué, ou NULL si la mémoire disponible est insuffisante.

### <a name="remarks"></a>Notes

Alloue de la mémoire. Voir [malloc](../../c-runtime-library/reference/malloc.md) pour plus de détails.

## <a name="ccrtallocatorfree"></a><a name="free"></a>CCRTAllocator::Gratuit

Appelez cette fonction statique à la mémoire libre.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers la mémoire allouée.

### <a name="remarks"></a>Notes

Libère la mémoire allouée. Voir [gratuitement](../../c-runtime-library/reference/free.md) pour plus de détails.

## <a name="ccrtallocatorreallocate"></a><a name="reallocate"></a>CCRTAllocator::Réallocate

Appelez cette fonction statique pour réallouer de la mémoire.

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers la mémoire allouée.

*nBytes (en)*<br/>
Nombre d'octets à réallouer.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur void vers l'espace alloué, ou NULL si la mémoire est insuffisante.

### <a name="remarks"></a>Notes

Redimensionne la quantité de mémoire allouée. Voir [réaffecter](../../c-runtime-library/reference/realloc.md) pour plus de détails.

## <a name="see-also"></a>Voir aussi

[Classe CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Classe CComAllocator](../../atl/reference/ccomallocator-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
