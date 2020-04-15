---
title: Classe CWin32Heap
ms.date: 11/04/2016
f1_keywords:
- CWin32Heap
- ATLMEM/ATL::CWin32Heap
- ATLMEM/ATL::CWin32Heap::CWin32Heap
- ATLMEM/ATL::CWin32Heap::Allocate
- ATLMEM/ATL::CWin32Heap::Attach
- ATLMEM/ATL::CWin32Heap::Detach
- ATLMEM/ATL::CWin32Heap::Free
- ATLMEM/ATL::CWin32Heap::GetSize
- ATLMEM/ATL::CWin32Heap::Reallocate
- ATLMEM/ATL::CWin32Heap::m_bOwnHeap
- ATLMEM/ATL::CWin32Heap::m_hHeap
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
ms.openlocfilehash: fbdb77e7f52e858401c87e1cd8782b59cc6ebcea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330462"
---
# <a name="cwin32heap-class"></a>Classe CWin32Heap

Cette classe met en œuvre [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) en utilisant les fonctions d’attribution de tas Win32.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CWin32Heap::CWin32Heap](#cwin32heap)|Constructeur.|
|[CWin32Heap::CWin32Heap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWin32Heap::Allocate](#allocate)|Alloue un bloc de mémoire à partir de l'objet de tas.|
|[CWin32Heap::Attach](#attach)|Attache l’objet de tas à un tas existant.|
|[CWin32Heap::Detach](#detach)|Détache l’objet de tas d’un tas existant.|
|[CWin32Heap::Gratuit](#free)|Libère la mémoire précédemment allouée à partir du tas.|
|[CWin32Heap::GetSize](#getsize)|Retourne la taille d’un bloc de mémoire alloué à partir de l’objet de tas.|
|[CWin32Heap::Réallocate](#reallocate)|Réalloue un bloc de mémoire à partir de l'objet de tas.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Un drapeau utilisé pour déterminer la propriété actuelle de la poignée de tas.|
|[CWin32Heap::m_hHeap](#m_hheap)|Poignée à l’objet de tas.|

## <a name="remarks"></a>Notes

`CWin32Heap`implémente des méthodes d’allocation de mémoire à l’aide des fonctions d’allocation de tas Win32, y compris [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc) et [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree). Contrairement à d’autres classes de tas, `CWin32Heap` nécessite une poignée de tas valide pour être fourni avant que la mémoire soit allouée: les autres classes par défaut à l’utilisation du tas de processus. Le manche peut être fourni au constructeur ou à la méthode [CWin32Heap::Attach.](#attach) Voir le [CWin32Heap:CWin32Heap](#cwin32heap) méthode pour plus de détails.

## <a name="example"></a>Exemple

Voir l’exemple pour [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>Spécifications

**En-tête:** atlmem.h

## <a name="cwin32heapallocate"></a><a name="allocate"></a>CWin32Heap::Allocate

Alloue un bloc de mémoire à partir de l'objet de tas.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes (en)*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [CWin32Heap::Free](#free) ou [CWin32Heap::Réallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide [de HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc).

## <a name="cwin32heapattach"></a><a name="attach"></a>CWin32Heap::Attach

Attache l’objet de tas à un tas existant.

```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>Paramètres

*hHeap (en)*<br/>
Une poignée de tas existante.

*bTakeOwnership (en)*<br/>
Un drapeau indiquant `CWin32Heap` si l’objet doit s’approprier les ressources du tas.

### <a name="remarks"></a>Notes

Si *bTakeOwnership* est `CWin32Heap` VRAI, l’objet est responsable de la suppression de la poignée de tas.

## <a name="cwin32heapcwin32heap"></a><a name="cwin32heap"></a>CWin32Heap::CWin32Heap

Constructeur.

```
CWin32Heap() throw();
CWin32Heap( HANDLE  hHeap) throw();
CWin32Heap(
    DWORD  dwFlags,
    size_t nInitialSize,
    size_t nMaxSize = 0);
```

### <a name="parameters"></a>Paramètres

*hHeap (en)*<br/>
Objet de tas existant.

*dwFlags*<br/>
Indicateurs utilisés pour créer le tas.

*nInitialSize*<br/>
Taille initiale du tas.

*nMaxSize (en)*<br/>
Taille maximale du tas.

### <a name="remarks"></a>Notes

Avant d'allouer de la mémoire, il est nécessaire de fournir à l'objet `CWin32Heap` un handle de tas valide. La façon la plus simple d'y parvenir consiste à utiliser le tas du processus :

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

Il est également possible de fournir un handle de tas existant au constructeur, auquel cas le nouvel objet ne prend pas possession du tas. Le handle de tas d'origine est toujours valide lorsque l'objet `CWin32Heap` est supprimé.

Un tas existant peut également être fixé au nouvel objet, à l’aide [de CWin32Heap::Attach](#attach).

Si un tas est requis lorsque des opérations sont toutes exécutées à partir d'un seul thread, il est préférable de créer l'objet comme suit :

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

Le paramètre HEAP_NO_SERIALIZE spécifie que l'exclusion mutuelle ne doit pas être utilisée lorsque les fonctions de tas allouent et libèrent de la mémoire, avec une augmentation correspondante des performances.

Le troisième paramètre est 0 par défaut, ce qui permet au tas de s'accroître en fonction des besoins. Voir [HeapCreate](/windows/win32/api/heapapi/nf-heapapi-heapcreate) pour une explication des tailles de mémoire et des drapeaux.

## <a name="cwin32heapcwin32heap"></a><a name="dtor"></a>CWin32Heap::CWin32Heap

Destructeur.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>Notes

Détruit la poignée de `CWin32Heap` tas si l’objet a la propriété du tas.

## <a name="cwin32heapdetach"></a><a name="detach"></a>CWin32Heap::Detach

Détache l’objet de tas d’un tas existant.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la poignée au tas auquel l’objet était précédemment attaché.

## <a name="cwin32heapfree"></a><a name="free"></a>CWin32Heap::Gratuit

Frees mémoire précédemment allouée à partir du tas par [CWin32Heap:Allocate](#allocate) ou [CWin32Heap:Reallocate](#reallocate).

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers le bloc de mémoire pour libérer. NULL est une valeur valable et ne fait rien.

## <a name="cwin32heapgetsize"></a><a name="getsize"></a>CWin32Heap::GetSize

Retourne la taille d’un bloc de mémoire alloué à partir de l’objet de tas.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers le bloc de mémoire dont la taille de la méthode obtiendra. Il s’agit d’un pointeur retourné par [CWin32Heap:Allocate](#allocate) ou [CWin32Heap:Reallocate](#reallocate).

### <a name="return-value"></a>Valeur de retour

Retourne la taille, dans les octets, du bloc mémoire alloué.

## <a name="cwin32heapm_bownheap"></a><a name="m_bownheap"></a>CWin32Heap::m_bOwnHeap

Un drapeau utilisé pour déterminer la propriété actuelle de la poignée de tas stockée dans [m_hHeap](#m_hheap).

```
bool m_bOwnHeap;
```

## <a name="cwin32heapm_hheap"></a><a name="m_hheap"></a>CWin32Heap::m_hHeap

Poignée à l’objet de tas.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>Notes

Une variable utilisée pour stocker une poignée à l’objet de tas.

## <a name="cwin32heapreallocate"></a><a name="reallocate"></a>CWin32Heap::Réallocate

Réalloue un bloc de mémoire à partir de l'objet de tas.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Pointeur vers le bloc de mémoire à réallouer.

*nBytes (en)*<br/>
Nouvelle taille en octets du bloc alloué. Le bloc peut être agrandi ou réduit.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Si *p* est NULL, il est supposé que le bloc de mémoire n’a pas encore été alloué et [CWin32Heap::Allocate](#allocate) est appelé, avec un argument de *nBytes*.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classe IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)<br/>
[Classe CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Classe CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Classe CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Classe CComHeap](../../atl/reference/ccomheap-class.md)
