---
title: Cglobalheap, classe
ms.date: 11/04/2016
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
ms.openlocfilehash: cba15421fd0329df7a66a35979ed54b863b7cca0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278299"
---
# <a name="cglobalheap-class"></a>Cglobalheap, classe

Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) en utilisant les fonctions de tas global Win32.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CGlobalHeap::Allocate](#allocate)|Appelez cette méthode pour allouer un bloc de mémoire.|
|[CGlobalHeap::Free](#free)|Appelez cette méthode pour libérer un bloc de mémoire allouée par ce gestionnaire de mémoire.|
|[CGlobalHeap::GetSize](#getsize)|Appelez cette méthode pour obtenir la taille d’un bloc de mémoire allouée par ce gestionnaire de mémoire allouée.|
|[CGlobalHeap::Reallocate](#reallocate)|Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.|

## <a name="remarks"></a>Notes

`CGlobalHeap` implémente les fonctions d’allocation de mémoire en utilisant les fonctions de tas global Win32.

> [!NOTE]
>  Les fonctions de tas global sont plus lentes que les autres fonctions de gestion de mémoire et ne fournissent pas autant de fonctionnalités. Par conséquent, les nouvelles applications doivent utiliser le [fonctions de tas](/windows/desktop/Memory/heap-functions). Elles sont disponibles dans le [CWin32Heap](../../atl/reference/cwin32heap-class.md) classe. Fonctions globales sont toujours utilisées par DDE et les fonctions de Presse-papiers.

## <a name="example"></a>Exemple

Consultez l’exemple de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>Spécifications

**En-tête :** atlmem.h

##  <a name="allocate"></a>  CGlobalHeap::Allocate

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

Appelez [CGlobalHeap::Free](#free) ou [CGlobalHeap::Reallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) avec un paramètre d’indicateur de GMEM_FIXED.

##  <a name="free"></a>  CGlobalHeap::Free

Appelez cette méthode pour libérer un bloc de mémoire allouée par ce gestionnaire de mémoire.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire. NULL est une valeur valide et ne fait rien.

### <a name="remarks"></a>Notes

Implémenté à l’aide [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree).

##  <a name="getsize"></a>  CGlobalHeap::GetSize

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

Implémenté à l’aide [GlobalSize](/windows/desktop/api/winbase/nf-winbase-globalsize).

##  <a name="reallocate"></a>  CGlobalHeap::Reallocate

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

Appelez [CGlobalHeap::Free](#free) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide [GlobalReAlloc](/windows/desktop/api/winbase/nf-winbase-globalrealloc).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CComHeap, classe](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap, classe](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap, classe](../../atl/reference/clocalheap-class.md)<br/>
[CCRTHeap, classe](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr, classe](../../atl/reference/iatlmemmgr-class.md)
