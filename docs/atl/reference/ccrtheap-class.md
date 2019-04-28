---
title: Ccrtheap, classe
ms.date: 11/04/2016
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
ms.openlocfilehash: 3c5030b9cfbfd636a783d27bcc8f9469f8348acb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246060"
---
# <a name="ccrtheap-class"></a>Ccrtheap, classe

Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions de tas CRT.

## <a name="syntax"></a>Syntaxe

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCRTHeap::Allocate](#allocate)|Appelez cette méthode pour allouer un bloc de mémoire.|
|[CCRTHeap::Free](#free)|Appelez cette méthode pour libérer un bloc de mémoire allouée par ce gestionnaire de mémoire.|
|[CCRTHeap::GetSize](#getsize)|Appelez cette méthode pour obtenir la taille d’un bloc de mémoire allouée par ce gestionnaire de mémoire allouée.|
|[CCRTHeap::Reallocate](#reallocate)|Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.|

## <a name="remarks"></a>Notes

`CCRTHeap` implémente les fonctions, y compris du segment de mémoire des fonctions d’allocation à l’aide de la bibliothèque CRT de mémoire [malloc](../../c-runtime-library/reference/malloc.md), [gratuit](../../c-runtime-library/reference/free.md), [realloc](../../c-runtime-library/reference/realloc.md), et [_msize](../../c-runtime-library/reference/msize.md).

## <a name="example"></a>Exemple

Consultez l’exemple de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlmem.h

##  <a name="allocate"></a>  CCRTHeap::Allocate

Appelez cette méthode pour allouer un bloc de mémoire.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [CCRTHeap::Free](#free) ou [CCRTHeap::Reallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide [malloc](../../c-runtime-library/reference/malloc.md).

##  <a name="free"></a>  CCRTHeap::Free

Appelez cette méthode pour libérer un bloc de mémoire allouée par ce gestionnaire de mémoire.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire. NULL est une valeur valide et ne fait rien.

### <a name="remarks"></a>Notes

Implémenté à l’aide [gratuit](../../c-runtime-library/reference/free.md).

##  <a name="getsize"></a>  CCRTHeap::GetSize

Appelez cette méthode pour obtenir la taille d’un bloc de mémoire allouée par ce gestionnaire de mémoire allouée.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne la taille de bloc de mémoire alloué en octets.

### <a name="remarks"></a>Notes

Implémenté à l’aide [_msize](../../c-runtime-library/reference/msize.md).

##  <a name="reallocate"></a>  CCRTHeap::Reallocate

Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

*nBytes*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [CCRTHeap::Free](#free) pour libérer la mémoire allouée par cette méthode. Implémenté à l’aide [realloc](../../c-runtime-library/reference/realloc.md).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CComHeap, classe](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap, classe](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap, classe](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap, classe](../../atl/reference/cglobalheap-class.md)<br/>
[IAtlMemMgr, classe](../../atl/reference/iatlmemmgr-class.md)
