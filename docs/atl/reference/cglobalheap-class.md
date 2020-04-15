---
title: Classe CGlobalHeap
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
ms.openlocfilehash: d596fd51c1bf33f606c1f14c9e8dbd2f1926c7f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326939"
---
# <a name="cglobalheap-class"></a>Classe CGlobalHeap

Cette classe met en œuvre [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) en utilisant les fonctions de tas mondial Win32.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CGlobalHeap::Allocate](#allocate)|Appelez cette méthode pour allouer un bloc de mémoire.|
|[CGlobalHeap::Gratuit](#free)|Appelez cette méthode pour libérer un bloc de mémoire alloué par ce gestionnaire de mémoire.|
|[CGlobalHeap::GetSize](#getsize)|Appelez cette méthode pour obtenir la taille allouée d’un bloc de mémoire alloué par ce gestionnaire de mémoire.|
|[CGlobalHeap::Réallocate](#reallocate)|Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.|

## <a name="remarks"></a>Notes

`CGlobalHeap`implémente les fonctions d’allocation de mémoire à l’aide des fonctions globales de tas Win32.

> [!NOTE]
> Les fonctions globales de tas sont plus lentes que d’autres fonctions de gestion de mémoire et ne fournissent pas autant de fonctionnalités. Par conséquent, les nouvelles applications devraient utiliser les [fonctions de tas](/windows/win32/Memory/heap-functions). Ceux-ci sont disponibles dans la classe [CWin32Heap.](../../atl/reference/cwin32heap-class.md) Les fonctions globales sont encore utilisées par DDE et les fonctions de presse-papiers.

## <a name="example"></a>Exemple

Voir l’exemple pour [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>Spécifications

**En-tête:** atlmem.h

## <a name="cglobalheapallocate"></a><a name="allocate"></a>CGlobalHeap::Allocate

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

Appelez [CGlobalHeap::Free](#free) ou [CGlobalHeap::Réallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide [de GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) avec un paramètre de drapeau de GMEM_FIXED.

## <a name="cglobalheapfree"></a><a name="free"></a>CGlobalHeap::Gratuit

Appelez cette méthode pour libérer un bloc de mémoire alloué par ce gestionnaire de mémoire.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire. NULL est une valeur valable et ne fait rien.

### <a name="remarks"></a>Notes

Implémenté à l’aide [de GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree).

## <a name="cglobalheapgetsize"></a><a name="getsize"></a>CGlobalHeap::GetSize

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

Mis en œuvre à l’aide [de GlobalSize](/windows/win32/api/winbase/nf-winbase-globalsize).

## <a name="cglobalheapreallocate"></a><a name="reallocate"></a>CGlobalHeap::Réallocate

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

Appelez [CGlobalHeap::Libre](#free) de libérer la mémoire allouée par cette méthode.

Implémenté à l’aide [de GlobalReAlloc](/windows/win32/api/winbase/nf-winbase-globalrealloc).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classe CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Classe CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Classe CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Classe CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Classe IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
