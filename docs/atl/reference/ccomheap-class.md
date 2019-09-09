---
title: CComHeap, classe
ms.date: 11/04/2016
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
ms.openlocfilehash: 1ded73047b895a44a22bdd5730886f7fc088c77a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497347"
---
# <a name="ccomheap-class"></a>CComHeap, classe

Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions d’allocation de mémoire com.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComHeap::Allocate](#allocate)|Appelez cette méthode pour allouer un bloc de mémoire.|
|[CComHeap::Free](#free)|Appelez cette méthode pour libérer un bloc de mémoire alloué par ce gestionnaire de mémoire.|
|[CComHeap::GetSize](#getsize)|Appelez cette méthode pour obtenir la taille allouée d’un bloc de mémoire alloué par ce gestionnaire de mémoire.|
|[CComHeap::Reallocate](#reallocate)|Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.|

## <a name="remarks"></a>Notes

`CComHeap`implémente les fonctions d’allocation de mémoire à l’aide des fonctions d’allocation COM, y compris [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree), [IMalloc ::](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize) [deCoTaskMemRealloc et](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc). La quantité maximale de mémoire qui peut être allouée est égale à INT_MAX (2147483647) octets.

## <a name="example"></a>Exemple

Consultez l’exemple pour [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>Configuration requise

**En-tête :** ATLComMem.h

##  <a name="allocate"></a>  CComHeap::Allocate

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

Appelez [CComHeap :: Free](#free) ou [CComHeap :: Allocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide de [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc).

##  <a name="free"></a>  CComHeap::Free

Appelez cette méthode pour libérer un bloc de mémoire alloué par ce gestionnaire de mémoire.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire. NULL est une valeur valide et ne fait rien.

### <a name="remarks"></a>Notes

Implémenté à l’aide de [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree).

##  <a name="getsize"></a>  CComHeap::GetSize

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

Implémenté à l’aide de [IMalloc ::](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)Deis.

##  <a name="reallocate"></a>  CComHeap::Reallocate

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

Appelez [CComHeap :: Free](#free) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide de [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc).

## <a name="see-also"></a>Voir aussi

[DynamicConsumer, exemple](../../overview/visual-cpp-samples.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CWin32Heap, classe](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap, classe](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap, classe](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap, classe](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr, classe](../../atl/reference/iatlmemmgr-class.md)
