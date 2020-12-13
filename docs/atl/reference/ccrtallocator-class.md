---
description: 'En savoir plus sur : classe CCRTAllocator'
title: CCRTAllocator, classe
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
ms.openlocfilehash: 378a1c27a6c2dde9fbcb24eb9b51b64c3af7e8aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142062"
---
# <a name="ccrtallocator-class"></a>CCRTAllocator, classe

Cette classe fournit des méthodes pour gérer la mémoire à l’aide de routines de mémoire CRT.

## <a name="syntax"></a>Syntaxe

```
class ATL::CCRTAllocator
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCRTAllocator :: Allocate](#allocate)|Statique Appelez cette méthode pour allouer de la mémoire.|
|[CCRTAllocator :: Free](#free)|Statique Appelez cette méthode pour libérer de la mémoire.|
|[CCRTAllocator :: Reallocation](#reallocate)|Statique Appelez cette méthode pour réallouer la mémoire.|

## <a name="remarks"></a>Notes

Cette classe est utilisée par [CHeapPtr](../../atl/reference/cheapptr-class.md) pour fournir les routines d’allocation de mémoire CRT. La classe équivalente, [CComAllocator](../../atl/reference/ccomallocator-class.md), fournit les mêmes méthodes à l’aide de routines com.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcore. h

## <a name="ccrtallocatorallocate"></a><a name="allocate"></a> CCRTAllocator :: Allocate

Appelez cette fonction statique pour allouer de la mémoire.

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes*<br/>
Nombre d'octets à allouer.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur void vers l'espace alloué, ou NULL si la mémoire disponible est insuffisante.

### <a name="remarks"></a>Notes

Alloue de la mémoire. Pour plus d’informations, consultez [malloc](../../c-runtime-library/reference/malloc.md) .

## <a name="ccrtallocatorfree"></a><a name="free"></a> CCRTAllocator :: Free

Appelez cette fonction statique pour libérer de la mémoire.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire allouée.

### <a name="remarks"></a>Notes

Libère la mémoire allouée. Pour plus d’informations, consultez la page [gratuite](../../c-runtime-library/reference/free.md) .

## <a name="ccrtallocatorreallocate"></a><a name="reallocate"></a> CCRTAllocator :: Reallocation

Appelez cette fonction statique pour réallouer de la mémoire.

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire allouée.

*nBytes*<br/>
Nombre d'octets à réallouer.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur void vers l'espace alloué, ou NULL si la mémoire est insuffisante.

### <a name="remarks"></a>Notes

Redimensionne la quantité de mémoire allouée. Pour plus d’informations, consultez [realloc](../../c-runtime-library/reference/realloc.md) .

## <a name="see-also"></a>Voir aussi

[CHeapPtr, classe](../../atl/reference/cheapptr-class.md)<br/>
[CComAllocator, classe](../../atl/reference/ccomallocator-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
