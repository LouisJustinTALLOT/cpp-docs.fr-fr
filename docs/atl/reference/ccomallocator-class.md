---
title: Classe CComAllocator
ms.date: 11/04/2016
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
ms.openlocfilehash: 165cdb8b0b16a4872214f4556c26ee141e6a4d89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321140"
---
# <a name="ccomallocator-class"></a>Classe CComAllocator

Cette classe fournit des méthodes pour gérer la mémoire à l’aide de routines mémoire COM.

## <a name="syntax"></a>Syntaxe

```
class CComAllocator
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComAllocator::Allocate](#allocate)|Appelez cette méthode statique pour allouer la mémoire.|
|[CComAllocator::Gratuit](#free)|Appelez cette méthode statique pour libérer la mémoire allouée.|
|[CComAllocator::Réallocate](#reallocate)|Appelez cette méthode statique pour réaffecter la mémoire.|

## <a name="remarks"></a>Notes

Cette classe est utilisée par [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) pour fournir les routines d’allocation de mémoire COM. La classe de contrepartie, [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), fournit les mêmes méthodes en utilisant les routines CRT.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccomallocatorallocate"></a><a name="allocate"></a>CComAllocator::Allocate

Appelez cette fonction statique pour allouer de la mémoire.

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes (en)*<br/>
Nombre d'octets à allouer.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur void vers l'espace alloué, ou NULL si la mémoire disponible est insuffisante.

### <a name="remarks"></a>Notes

Alloue de la mémoire. Voir [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc) pour plus de détails.

## <a name="ccomallocatorfree"></a><a name="free"></a>CComAllocator::Gratuit

Appelez cette fonction statique à la mémoire libre allouée.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers la mémoire allouée.

### <a name="remarks"></a>Notes

Libère la mémoire allouée. Voir [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree) pour plus de détails.

## <a name="ccomallocatorreallocate"></a><a name="reallocate"></a>CComAllocator::Réallocate

Appelez cette fonction statique pour réallouer de la mémoire.

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers la mémoire allouée.

*nBytes (en)*<br/>
Nombre d'octets à réallouer.

### <a name="return-value"></a>Valeur de retour

Renvoie un pointeur vide à l’espace alloué, ou NULL s’il n’y a pas suffisamment de mémoire

### <a name="remarks"></a>Notes

Redimensionne la quantité de mémoire allouée. Voir [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc) pour plus de détails.

## <a name="see-also"></a>Voir aussi

[Classe CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Classe CCRTAllocator](../../atl/reference/ccrtallocator-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
