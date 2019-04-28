---
title: Clocalheap, classe
ms.date: 11/04/2016
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
ms.openlocfilehash: 53288bea8a50f62437eab4dd81d5d816abf78f44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258830"
---
# <a name="clocalheap-class"></a>Clocalheap, classe

Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) en utilisant les fonctions de tas local de Win32.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CLocalHeap::Allocate](#allocate)|Appelez cette méthode pour allouer un bloc de mémoire.|
|[CLocalHeap::Free](#free)|Appelez cette méthode pour libérer un bloc de mémoire allouée par ce gestionnaire de mémoire.|
|[CLocalHeap::GetSize](#getsize)|Appelez cette méthode pour obtenir la taille d’un bloc de mémoire allouée par ce gestionnaire de mémoire allouée.|
|[CLocalHeap::Reallocate](#reallocate)|Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.|

## <a name="remarks"></a>Notes

`CLocalHeap` implémente les fonctions d’allocation de mémoire en utilisant les fonctions de tas local de Win32.

> [!NOTE]
>  Les fonctions du tas local sont plus lentes que les autres fonctions de gestion de mémoire et ne fournissent pas autant de fonctionnalités. Par conséquent, les nouvelles applications doivent utiliser le [fonctions de tas](/windows/desktop/Memory/heap-functions). Elles sont disponibles dans le [CWin32Heap](../../atl/reference/cwin32heap-class.md) classe.

## <a name="example"></a>Exemple

Consultez l’exemple de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlmem.h

##  <a name="allocate"></a>  CLocalHeap::Allocate

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

Appelez [CLocalHeap::Free](#free) ou [CLocalHeap::Reallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc) avec un paramètre d’indicateur de LMEM_FIXED.

##  <a name="free"></a>  CLocalHeap::Free

Appelez cette méthode pour libérer un bloc de mémoire allouée par ce gestionnaire de mémoire.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire. NULL est une valeur valide et ne fait rien.

### <a name="remarks"></a>Notes

Implémenté à l’aide [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree).

##  <a name="getsize"></a>  CLocalHeap::GetSize

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

Implémenté à l’aide [LocalSize](/windows/desktop/api/winbase/nf-winbase-localsize).

##  <a name="reallocate"></a>  CLocalHeap::Reallocate

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

Appelez [CLocalHeap::Free](#free) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide [LocalReAlloc](/windows/desktop/api/winbase/nf-winbase-localrealloc).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CComHeap, classe](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap, classe](../../atl/reference/cwin32heap-class.md)<br/>
[CGlobalHeap, classe](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap, classe](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr, classe](../../atl/reference/iatlmemmgr-class.md)
