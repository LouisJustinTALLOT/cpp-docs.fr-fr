---
title: Classe CCRTHeap
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
ms.openlocfilehash: caf5508079332689c2fff42f130951375dc35512
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327163"
---
# <a name="ccrtheap-class"></a>Classe CCRTHeap

Cette classe met en œuvre [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) en utilisant les fonctions de tas CRT.

## <a name="syntax"></a>Syntaxe

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCRTHeap::Allocate](#allocate)|Appelez cette méthode pour allouer un bloc de mémoire.|
|[CCRTHeap::Gratuit](#free)|Appelez cette méthode pour libérer un bloc de mémoire alloué par ce gestionnaire de mémoire.|
|[CCRTHeap::GetSize](#getsize)|Appelez cette méthode pour obtenir la taille allouée d’un bloc de mémoire alloué par ce gestionnaire de mémoire.|
|[CCRTHeap::Réallocate](#reallocate)|Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.|

## <a name="remarks"></a>Notes

`CCRTHeap`implémente les fonctions d’allocation de mémoire à l’aide des fonctions de tas CRT, y compris [malloc](../../c-runtime-library/reference/malloc.md), [gratuit](../../c-runtime-library/reference/free.md), [réaffecter](../../c-runtime-library/reference/realloc.md), et [_msize](../../c-runtime-library/reference/msize.md).

## <a name="example"></a>Exemple

Voir l’exemple pour [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>Spécifications

**En-tête:** atlmem.h

## <a name="ccrtheapallocate"></a><a name="allocate"></a>CCRTHeap::Allocate

Appelez cette méthode pour allouer un bloc de mémoire.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes (en)*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [CCRTHeap::Free](#free) ou [CCRTHeap::Réallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide [de malloc](../../c-runtime-library/reference/malloc.md).

## <a name="ccrtheapfree"></a><a name="free"></a>CCRTHeap::Gratuit

Appelez cette méthode pour libérer un bloc de mémoire alloué par ce gestionnaire de mémoire.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire. NULL est une valeur valable et ne fait rien.

### <a name="remarks"></a>Notes

Implémenté en utilisant [gratuitement](../../c-runtime-library/reference/free.md).

## <a name="ccrtheapgetsize"></a><a name="getsize"></a>CCRTHeap::GetSize

Appelez cette méthode pour obtenir la taille allouée d’un bloc de mémoire alloué par ce gestionnaire de mémoire.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne la taille du bloc de mémoire alloué dans les octets.

### <a name="remarks"></a>Notes

Implémenté à [l’aide de _msize](../../c-runtime-library/reference/msize.md).

## <a name="ccrtheapreallocate"></a><a name="reallocate"></a>CCRTHeap::Réallocate

Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

*nBytes (en)*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [CCRTHeap::Libre](#free) de libérer la mémoire allouée par cette méthode. Implémenté à l’aide [de réaffectation](../../c-runtime-library/reference/realloc.md).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classe CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Classe CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Classe CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Classe CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Classe IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
