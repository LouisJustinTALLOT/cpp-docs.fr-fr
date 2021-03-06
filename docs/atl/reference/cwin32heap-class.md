---
description: 'En savoir plus sur : classe CWin32Heap'
title: CWin32Heap, classe
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
ms.openlocfilehash: a19c7f01a572bad46dbbab2925104d4dfcf569be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140203"
---
# <a name="cwin32heap-class"></a>CWin32Heap, classe

Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions d’allocation du tas Win32.

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
|[CWin32Heap :: CWin32Heap](#cwin32heap)|Constructeur.|
|[CWin32Heap :: ~ CWin32Heap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWin32Heap :: Allocate](#allocate)|Alloue un bloc de mémoire à partir de l'objet de tas.|
|[CWin32Heap :: Attach](#attach)|Attache l’objet segment de mémoire à un tas existant.|
|[CWin32Heap ::D Etach](#detach)|Détache l’objet segment de mémoire d’un tas existant.|
|[CWin32Heap :: Free](#free)|Libère la mémoire précédemment allouée à partir du tas.|
|[CWin32Heap :: est à obtenir](#getsize)|Retourne la taille d’un bloc de mémoire alloué à partir de l’objet de tas.|
|[CWin32Heap :: Reallocation](#reallocate)|Réalloue un bloc de mémoire à partir de l'objet de tas.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CWin32Heap :: m_bOwnHeap](#m_bownheap)|Indicateur utilisé pour déterminer la propriété actuelle du handle du tas.|
|[CWin32Heap :: m_hHeap](#m_hheap)|Handle de l’objet de segment de mémoire.|

## <a name="remarks"></a>Notes

`CWin32Heap` implémente des méthodes d’allocation de mémoire à l’aide des fonctions d’allocation du tas Win32, notamment [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc) et [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree). Contrairement aux autres classes de tas, `CWin32Heap` requiert un handle de tas valide pour être fourni avant l’allocation de mémoire : les autres classes utilisent par défaut le tas de processus. Le handle peut être fourni au constructeur ou à la méthode [CWin32Heap :: Attach](#attach) . Pour plus d’informations, consultez la méthode [CWin32Heap :: CWin32Heap](#cwin32heap) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>Spécifications

**En-tête :** atlmem. h

## <a name="cwin32heapallocate"></a><a name="allocate"></a> CWin32Heap :: Allocate

Alloue un bloc de mémoire à partir de l'objet de tas.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers le bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [CWin32Heap :: Free](#free) ou [CWin32Heap :: Allocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide de [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc).

## <a name="cwin32heapattach"></a><a name="attach"></a> CWin32Heap :: Attach

Attache l’objet segment de mémoire à un tas existant.

```cpp
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>Paramètres

*hHeap*<br/>
Handle de tas existant.

*bTakeOwnership*<br/>
Indicateur qui spécifie si l' `CWin32Heap` objet doit prendre possession des ressources du tas.

### <a name="remarks"></a>Notes

Si *bTakeOwnership* a la valeur true, l' `CWin32Heap` objet est chargé de supprimer le descripteur du tas.

## <a name="cwin32heapcwin32heap"></a><a name="cwin32heap"></a> CWin32Heap :: CWin32Heap

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

*hHeap*<br/>
Objet de tas existant.

*dwFlags*<br/>
Indicateurs utilisés pour créer le tas.

*nInitialSize*<br/>
Taille initiale du tas.

*nMaxSize*<br/>
Taille maximale du tas.

### <a name="remarks"></a>Notes

Avant d'allouer de la mémoire, il est nécessaire de fournir à l'objet `CWin32Heap` un handle de tas valide. La façon la plus simple d'y parvenir consiste à utiliser le tas du processus :

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

Il est également possible de fournir un handle de tas existant au constructeur, auquel cas le nouvel objet ne prend pas possession du tas. Le handle de tas d'origine est toujours valide lorsque l'objet `CWin32Heap` est supprimé.

Un tas existant peut également être attaché au nouvel objet à l’aide de [CWin32Heap :: Attach](#attach).

Si un tas est requis lorsque des opérations sont toutes exécutées à partir d'un seul thread, il est préférable de créer l'objet comme suit :

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

Le paramètre HEAP_NO_SERIALIZE spécifie que l'exclusion mutuelle ne doit pas être utilisée lorsque les fonctions de tas allouent et libèrent de la mémoire, avec une augmentation correspondante des performances.

Le troisième paramètre est 0 par défaut, ce qui permet au tas de s'accroître en fonction des besoins. Pour obtenir une explication des tailles et des indicateurs de mémoire, consultez [HeapCreate](/windows/win32/api/heapapi/nf-heapapi-heapcreate) .

## <a name="cwin32heapcwin32heap"></a><a name="dtor"></a> CWin32Heap :: ~ CWin32Heap

Destructeur.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>Notes

Détruit le handle de segment de mémoire si l' `CWin32Heap` objet a la propriété du tas.

## <a name="cwin32heapdetach"></a><a name="detach"></a> CWin32Heap ::D Etach

Détache l’objet segment de mémoire d’un tas existant.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le handle du tas auquel l’objet a été précédemment attaché.

## <a name="cwin32heapfree"></a><a name="free"></a> CWin32Heap :: Free

Libère la mémoire précédemment allouée à partir du tas par [CWin32Heap :: Allocate](#allocate) ou [CWin32Heap :: Allocate](#reallocate).

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers le bloc de mémoire à libérer. NULL est une valeur valide et ne fait rien.

## <a name="cwin32heapgetsize"></a><a name="getsize"></a> CWin32Heap :: est à obtenir

Retourne la taille d’un bloc de mémoire alloué à partir de l’objet de tas.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers le bloc de mémoire dont la taille est obtenue par la méthode. Il s’agit d’un pointeur retourné par [CWin32Heap :: Allocate](#allocate) ou [CWin32Heap :: Allocate](#reallocate).

### <a name="return-value"></a>Valeur renvoyée

Retourne la taille, en octets, du bloc de mémoire alloué.

## <a name="cwin32heapm_bownheap"></a><a name="m_bownheap"></a> CWin32Heap :: m_bOwnHeap

Indicateur utilisé pour déterminer la propriété actuelle du handle de tas stocké dans [m_hHeap](#m_hheap).

```
bool m_bOwnHeap;
```

## <a name="cwin32heapm_hheap"></a><a name="m_hheap"></a> CWin32Heap :: m_hHeap

Handle de l’objet de segment de mémoire.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>Notes

Variable utilisée pour stocker un handle vers l’objet segment de mémoire.

## <a name="cwin32heapreallocate"></a><a name="reallocate"></a> CWin32Heap :: Reallocation

Réalloue un bloc de mémoire à partir de l'objet de tas.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers le bloc de mémoire à réallouer.

*nBytes*<br/>
Nouvelle taille en octets du bloc alloué. Le bloc peut être agrandi ou réduit.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers le bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Si *p* est null, il est supposé que le bloc de mémoire n’a pas encore été alloué et [CWin32Heap :: Allocate](#allocate) est appelé, avec un argument de *nBytes*.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[IAtlMemMgr, classe](../../atl/reference/iatlmemmgr-class.md)<br/>
[CLocalHeap, classe](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap, classe](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap, classe](../../atl/reference/ccrtheap-class.md)<br/>
[CComHeap, classe](../../atl/reference/ccomheap-class.md)
