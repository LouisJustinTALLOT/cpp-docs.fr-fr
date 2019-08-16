---
title: CLocalHeap, classe
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
ms.openlocfilehash: a302ba4ea55c42ce214c8de4a24be843d6cb1b9f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496746"
---
# <a name="clocalheap-class"></a>CLocalHeap, classe

Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions de tas locales Win32.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CLocalHeap::Allocate](#allocate)|Appelez cette méthode pour allouer un bloc de mémoire.|
|[CLocalHeap::Free](#free)|Appelez cette méthode pour libérer un bloc de mémoire alloué par ce gestionnaire de mémoire.|
|[CLocalHeap::GetSize](#getsize)|Appelez cette méthode pour obtenir la taille allouée d’un bloc de mémoire alloué par ce gestionnaire de mémoire.|
|[CLocalHeap::Reallocate](#reallocate)|Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.|

## <a name="remarks"></a>Notes

`CLocalHeap`implémente les fonctions d’allocation de mémoire à l’aide des fonctions de tas locales Win32.

> [!NOTE]
>  Les fonctions du tas local sont plus lentes que les autres fonctions de gestion de la mémoire et ne fournissent pas autant de fonctionnalités. Par conséquent, les nouvelles applications doivent utiliser les [fonctions de tas](/windows/win32/Memory/heap-functions). Celles-ci sont disponibles dans la classe [CWin32Heap](../../atl/reference/cwin32heap-class.md) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlmem. h

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

Appelez [CLocalHeap:: Free](#free) ou [CLocalHeap::](#reallocate) Allocate pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide de [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) avec un paramètre flag de LMEM_FIXED.

##  <a name="free"></a>  CLocalHeap::Free

Appelez cette méthode pour libérer un bloc de mémoire alloué par ce gestionnaire de mémoire.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire. NULL est une valeur valide et ne fait rien.

### <a name="remarks"></a>Notes

Implémenté à l’aide de [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree).

##  <a name="getsize"></a>  CLocalHeap::GetSize

Appelez cette méthode pour obtenir la taille allouée d’un bloc de mémoire alloué par ce gestionnaire de mémoire.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne la taille du bloc de mémoire alloué, en octets.

### <a name="remarks"></a>Notes

Implémenté à l’aide de [LocalSize](/windows/win32/api/winbase/nf-winbase-localsize).

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

Appelez [CLocalHeap:: Free](#free) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide de [LocalReAlloc](/windows/win32/api/winbase/nf-winbase-localrealloc).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CComHeap, classe](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap, classe](../../atl/reference/cwin32heap-class.md)<br/>
[CGlobalHeap, classe](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap, classe](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr, classe](../../atl/reference/iatlmemmgr-class.md)
