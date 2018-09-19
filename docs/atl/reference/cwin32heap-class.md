---
title: Classe de CWin32Heap | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3b10648a3251a705085e31559a98b6ee4957c72
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088473"
---
# <a name="cwin32heap-class"></a>Classe de CWin32Heap

Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions d’allocation du tas Win32.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CWin32Heap::CWin32Heap](#cwin32heap)|Constructeur.|
|[CWin32Heap :: ~ CWin32Heap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWin32Heap::Allocate](#allocate)|Alloue un bloc de mémoire à partir de l'objet de tas.|
|[CWin32Heap::Attach](#attach)|Attache l’objet de tas à un tas existant.|
|[CWin32Heap::Detach](#detach)|Détache l’objet de tas à partir d’un tas existant.|
|[CWin32Heap::Free](#free)|Libère la mémoire précédemment allouée à partir du tas.|
|[CWin32Heap::GetSize](#getsize)|Retourne la taille d’un bloc de mémoire alloué à partir de l’objet de tas.|
|[CWin32Heap::Reallocate](#reallocate)|Réalloue un bloc de mémoire à partir de l'objet de tas.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Indicateur utilisé pour déterminer le propriétaire actuel de la poignée de segments de mémoire.|
|[CWin32Heap::m_hHeap](#m_hheap)|Handle de l’objet de segment de mémoire.|

## <a name="remarks"></a>Notes

`CWin32Heap` implémente les méthodes d’allocation de mémoire à l’aide des fonctions d’allocation de tas Win32, y compris [HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc) et [HeapFree](/windows/desktop/api/heapapi/nf-heapapi-heapfree). Contrairement aux autres classes de tas, `CWin32Heap` nécessite un handle de tas valide doit être fourni avant que la mémoire est allouée : l’autres classes utilisent par défaut le tas du processus. Le handle peut être fourni au constructeur ou à la [CWin32Heap::Attach](#attach) (méthode). Consultez le [CWin32Heap::CWin32Heap](#cwin32heap) (méthode) pour plus d’informations.

## <a name="example"></a>Exemple

Consultez l’exemple de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlmem.h

##  <a name="allocate"></a>  CWin32Heap::Allocate

Alloue un bloc de mémoire à partir de l'objet de tas.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes*<br/>
Nombre demandé d'octets dans le nouveau bloc de mémoire.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Appelez [CWin32Heap::Free](#free) ou [CWin32Heap::Reallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.

Implémenté à l’aide [HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc).

##  <a name="attach"></a>  CWin32Heap::Attach

Attache l’objet de tas à un tas existant.

```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>Paramètres

*hHeap*<br/>
Un handle de tas existant.

*bTakeOwnership*<br/>
Une qui indique si le `CWin32Heap` objet consiste à prendre possession des ressources du tas.

### <a name="remarks"></a>Notes

Si *bTakeOwnership* a la valeur TRUE, le `CWin32Heap` objet est chargé de supprimer le handle de tas.

##  <a name="cwin32heap"></a>  CWin32Heap::CWin32Heap

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

Un tas existant peut également être joint au nouvel objet, à l’aide de [CWin32Heap::Attach](#attach).

Si un tas est requis lorsque des opérations sont toutes exécutées à partir d'un seul thread, il est préférable de créer l'objet comme suit :

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

Le paramètre HEAP_NO_SERIALIZE Spécifie que l’exclusion mutuelle ne sera pas utilisée lorsque les fonctions du tas allouent et libérer la mémoire, avec une augmentation des performances.

Le troisième paramètre est 0 par défaut, ce qui permet au tas de s'accroître en fonction des besoins. Consultez [HeapCreate](/windows/desktop/api/heapapi/nf-heapapi-heapcreate) pour une explication sur les tailles de mémoire et les indicateurs.

##  <a name="dtor"></a>  CWin32Heap :: ~ CWin32Heap

Destructeur.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>Notes

Détruit le handle de tas si la `CWin32Heap` objet a la propriété du tas.

##  <a name="detach"></a>  CWin32Heap::Detach

Détache l’objet de tas à partir d’un tas existant.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le handle vers le segment de mémoire à laquelle l’objet a été attachée précédemment.

##  <a name="free"></a>  CWin32Heap::Free

Libère la mémoire précédemment allouée à partir du tas par [CWin32Heap::Allocate](#allocate) ou [CWin32Heap::Reallocate](#reallocate).

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers le bloc de mémoire à libérer. NULL est une valeur valide et ne fait rien.

##  <a name="getsize"></a>  CWin32Heap::GetSize

Retourne la taille d’un bloc de mémoire alloué à partir de l’objet de tas.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers le bloc de mémoire dont la méthode obtient la taille. Il s’agit d’un pointeur retourné par [CWin32Heap::Allocate](#allocate) ou [CWin32Heap::Reallocate](#reallocate).

### <a name="return-value"></a>Valeur de retour

Retourne la taille, en octets, du bloc de mémoire alloué.

##  <a name="m_bownheap"></a>  CWin32Heap::m_bOwnHeap

Un indicateur utilisé pour déterminer le propriétaire actuel de la poignée de segments de mémoire stockée dans [m_hHeap](#m_hheap).

```
bool m_bOwnHeap;
```

##  <a name="m_hheap"></a>  CWin32Heap::m_hHeap

Handle de l’objet de segment de mémoire.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>Notes

Une variable utilisée pour stocker un handle de l’objet de tas.

##  <a name="reallocate"></a>  CWin32Heap::Reallocate

Réalloue un bloc de mémoire à partir de l'objet de tas.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur vers le bloc de mémoire à réallouer.

*nBytes*<br/>
Nouvelle taille en octets du bloc alloué. Le bloc peut être agrandi ou réduit.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le bloc de mémoire nouvellement alloué.

### <a name="remarks"></a>Notes

Si *p* est NULL, il est supposé que le bloc de mémoire n’a pas encore été alloué et [CWin32Heap::Allocate](#allocate) est appelée avec un argument de *nBytes*.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[IAtlMemMgr, classe](../../atl/reference/iatlmemmgr-class.md)<br/>
[CLocalHeap, classe](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap, classe](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap, classe](../../atl/reference/ccrtheap-class.md)<br/>
[CComHeap, classe](../../atl/reference/ccomheap-class.md)
