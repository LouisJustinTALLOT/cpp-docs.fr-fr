---
description: 'En savoir plus sur : classe CCRTHeap'
title: CCRTHeap, classe
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
ms.openlocfilehash: c256139f37a4b0caa0a60f1a87fd71b6a3a8de3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142010"
---
# <a name="ccrtheap-class"></a>CCRTHeap, classe

Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions de tas CRT.

## <a name="syntax"></a>Syntaxe

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCRTHeap :: Allocate](#allocate)|Appelez cette méthode pour allouer un bloc de mémoire.|
|[CCRTHeap :: Free](#free)|Appelez cette méthode pour libérer un bloc de mémoire alloué par ce gestionnaire de mémoire.|
|[CCRTHeap :: est à obtenir](#getsize)|Appelez cette méthode pour obtenir la taille allouée d’un bloc de mémoire alloué par ce gestionnaire de mémoire.|
|[CCRTHeap :: Reallocation](#reallocate)|Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.|

## <a name="remarks"></a>Notes

`CCRTHeap` implémente les fonctions d’allocation de mémoire à l’aide des fonctions de tas CRT, y compris [malloc](../../c-runtime-library/reference/malloc.md), [Free](../../c-runtime-library/reference/free.md), [realloc](../../c-runtime-library/reference/realloc.md)et [_msize](../../c-runtime-library/reference/msize.md).

## <a name="example"></a>Exemple

Consultez l’exemple pour [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>Spécifications

**En-tête :** atlmem. h

## <a name="ccrtheapallocate"></a><a name="allocate"></a> CCRTHeap :: Allocate

Appelez cette méthode pour allouer un bloc de mémoire.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [CCRTHeap :: Free](#free) ou [CCRTHeap :: Allocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide de [malloc](../../c-runtime-library/reference/malloc.md).

## <a name="ccrtheapfree"></a><a name="free"></a> CCRTHeap :: Free

Appelez cette méthode pour libérer un bloc de mémoire alloué par ce gestionnaire de mémoire.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire. NULL est une valeur valide et ne fait rien.

### <a name="remarks"></a>Notes

Implémenté à l’aide de [Free](../../c-runtime-library/reference/free.md).

## <a name="ccrtheapgetsize"></a><a name="getsize"></a> CCRTHeap :: est à obtenir

Appelez cette méthode pour obtenir la taille allouée d’un bloc de mémoire alloué par ce gestionnaire de mémoire.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

### <a name="return-value"></a>Valeur renvoyée

Retourne la taille du bloc de mémoire alloué, en octets.

### <a name="remarks"></a>Notes

Implémenté à l’aide de [_msize](../../c-runtime-library/reference/msize.md).

## <a name="ccrtheapreallocate"></a><a name="reallocate"></a> CCRTHeap :: Reallocation

Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

*nBytes*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [CCRTHeap :: Free](#free) pour libérer la mémoire allouée par cette méthode. Implémenté à l’aide de [realloc](../../c-runtime-library/reference/realloc.md).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[CComHeap, classe](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap, classe](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap, classe](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap, classe](../../atl/reference/cglobalheap-class.md)<br/>
[IAtlMemMgr, classe](../../atl/reference/iatlmemmgr-class.md)
