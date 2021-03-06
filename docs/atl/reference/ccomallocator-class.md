---
description: 'En savoir plus sur : classe CComAllocator'
title: CComAllocator, classe
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
ms.openlocfilehash: 886692f6a55ac096e51fd6888f941d63bf089263
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146950"
---
# <a name="ccomallocator-class"></a>CComAllocator, classe

Cette classe fournit des méthodes pour gérer la mémoire à l’aide de routines de mémoire COM.

## <a name="syntax"></a>Syntaxe

```
class CComAllocator
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComAllocator :: Allocate](#allocate)|Appelez cette méthode statique pour allouer de la mémoire.|
|[CComAllocator :: Free](#free)|Appelez cette méthode statique pour libérer de la mémoire allouée.|
|[CComAllocator :: Reallocation](#reallocate)|Appelez cette méthode statique pour réallouer la mémoire.|

## <a name="remarks"></a>Notes

Cette classe est utilisée par [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) pour fournir les routines d’allocation de mémoire com. La classe équivalente, [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), fournit les mêmes méthodes à l’aide des routines CRT.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="ccomallocatorallocate"></a><a name="allocate"></a> CComAllocator :: Allocate

Appelez cette fonction statique pour allouer de la mémoire.

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes*<br/>
Nombre d'octets à allouer.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur void vers l'espace alloué, ou NULL si la mémoire disponible est insuffisante.

### <a name="remarks"></a>Notes

Alloue de la mémoire. Pour plus d’informations, consultez [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc) .

## <a name="ccomallocatorfree"></a><a name="free"></a> CComAllocator :: Free

Appelez cette fonction statique pour libérer de la mémoire allouée.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire allouée.

### <a name="remarks"></a>Notes

Libère la mémoire allouée. Pour plus d’informations, consultez [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree) .

## <a name="ccomallocatorreallocate"></a><a name="reallocate"></a> CComAllocator :: Reallocation

Appelez cette fonction statique pour réallouer de la mémoire.

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire allouée.

*nBytes*<br/>
Nombre d'octets à réallouer.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur void vers l’espace alloué, ou NULL si la mémoire est insuffisante

### <a name="remarks"></a>Notes

Redimensionne la quantité de mémoire allouée. Pour plus d’informations, consultez [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc) .

## <a name="see-also"></a>Voir aussi

[CComHeapPtr, classe](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator, classe](../../atl/reference/ccrtallocator-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
