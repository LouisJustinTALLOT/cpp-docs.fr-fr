---
title: Classe de CWin32Heap | Documents Microsoft
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
ms.openlocfilehash: 9b26d979ccb99d3d99bc91af03c4836603d31c01
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="cwin32heap-class"></a>Classe de CWin32Heap
Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) à l’aide des fonctions d’allocation du tas Win32.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
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
|[CWin32Heap::Attach](#attach)|Attache l’objet de segment de mémoire à un tas existant.|  
|[CWin32Heap::Detach](#detach)|Détache l’objet de segment de mémoire à partir d’un tas existant.|  
|[CWin32Heap::Free](#free)|Libère la mémoire précédemment allouée à partir du tas.|  
|[CWin32Heap::GetSize](#getsize)|Retourne la taille d’un bloc de mémoire allouée à partir de l’objet de tas.|  
|[CWin32Heap::Reallocate](#reallocate)|Réalloue un bloc de mémoire à partir de l'objet de tas.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Indicateur utilisé pour déterminer le propriétaire actuel de la poignée de segment de mémoire.|  
|[CWin32Heap::m_hHeap](#m_hheap)|Handle vers l’objet de tas.|  
  
## <a name="remarks"></a>Notes  
 `CWin32Heap` implémente les méthodes d’allocation de mémoire à l’aide des fonctions d’allocation de tas Win32, y compris [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597) et [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701). Contrairement aux autres classes de segment de mémoire, `CWin32Heap` requiert un handle de tas valide doit être fourni avant que la mémoire est allouée : l’autres classes valeur par défaut à l’aide du tas du processus. Le handle peut être fourni au constructeur ou à la [CWin32Heap::Attach](#attach) (méthode). Consultez le [CWin32Heap::CWin32Heap](#cwin32heap) méthode pour plus de détails.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IAtlMemMgr`  
  
 `CWin32Heap`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlmem.h  
  
##  <a name="allocate"></a>  CWin32Heap::Allocate  
 Alloue un bloc de mémoire à partir de l'objet de tas.  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nBytes`  
 Nombre demandé d'octets dans le nouveau bloc de mémoire.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le bloc de mémoire nouvellement alloué.  
  
### <a name="remarks"></a>Notes  
 Appelez [CWin32Heap::Free](#free) ou [CWin32Heap::Reallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.  
  
 Implémentation à l’aide [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597).  
  
##  <a name="attach"></a>  CWin32Heap::Attach  
 Attache l’objet de segment de mémoire à un tas existant.  
  
```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `hHeap`  
 Un handle de tas existant.  
  
 `bTakeOwnership`  
 Une qui indique si d’indicateur le `CWin32Heap` objet est de prendre possession des ressources du segment de mémoire.  
  
### <a name="remarks"></a>Notes  
 Si `bTakeOwnership` a la valeur TRUE, le `CWin32Heap` objet est chargé de supprimer le handle de tas.  
  
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
 `hHeap`  
 Objet de tas existant.  
  
 `dwFlags`  
 Indicateurs utilisés pour créer le tas.  
  
 *nInitialSize*  
 Taille initiale du tas.  
  
 `nMaxSize`  
 Taille maximale du tas.  
  
### <a name="remarks"></a>Notes  
 Avant d'allouer de la mémoire, il est nécessaire de fournir à l'objet `CWin32Heap` un handle de tas valide. La façon la plus simple d'y parvenir consiste à utiliser le tas du processus :  
  
 [!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]  
  
 Il est également possible de fournir un handle de tas existant au constructeur, auquel cas le nouvel objet ne prend pas possession du tas. Le handle de tas d'origine est toujours valide lorsque l'objet `CWin32Heap` est supprimé.  
  
 Un tas existant peut également être joint au nouvel objet, à l’aide de [CWin32Heap::Attach](#attach).  
  
 Si un tas est requis lorsque des opérations sont toutes exécutées à partir d'un seul thread, il est préférable de créer l'objet comme suit :  
  
 [!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]  
  
 Le paramètre **HEAP_NO_SERIALIZE** indique que l’exclusion mutuelle n’est pas utilisée lorsque les fonctions de tas allouer et libérer de la mémoire, avec une augmentation des performances.  
  
 Le troisième paramètre est 0 par défaut, ce qui permet au tas de s'accroître en fonction des besoins. Consultez [HeapCreate](http://msdn.microsoft.com/library/windows/desktop/aa366599\(v=vs.85\).aspx) pour une explication de la taille de la mémoire et les indicateurs.  
  
##  <a name="dtor"></a>  CWin32Heap :: ~ CWin32Heap  
 Destructeur.  
  
```
~CWin32Heap() throw();
```  
  
### <a name="remarks"></a>Notes  
 Détruit le handle de tas si la `CWin32Heap` objet est le propriétaire du segment de mémoire.  
  
##  <a name="detach"></a>  CWin32Heap::Detach  
 Détache l’objet de segment de mémoire à partir d’un tas existant.  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le handle vers le segment de mémoire à laquelle l’objet a été précédemment attaché.  
  
##  <a name="free"></a>  CWin32Heap::Free  
 Libère la mémoire précédemment allouée à partir du tas par [CWin32Heap::Allocate](#allocate) ou [CWin32Heap::Reallocate](#reallocate).  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Pointeur vers le bloc de mémoire à libérer. NULL est une valeur valide et ne fait rien.  
  
##  <a name="getsize"></a>  CWin32Heap::GetSize  
 Retourne la taille d’un bloc de mémoire allouée à partir de l’objet de tas.  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Pointeur vers le bloc de mémoire dont la méthode obtient la taille. Il s’agit d’un pointeur retourné par [CWin32Heap::Allocate](#allocate) ou [CWin32Heap::Reallocate](#reallocate).  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la taille, en octets, du bloc de mémoire alloué.  
  
##  <a name="m_bownheap"></a>  CWin32Heap::m_bOwnHeap  
 Indicateur utilisé pour déterminer le propriétaire actuel du handle de tas stocké dans [m_hHeap](#m_hheap).  
  
```
bool m_bOwnHeap;
```  
  
##  <a name="m_hheap"></a>  CWin32Heap::m_hHeap  
 Handle vers l’objet de tas.  
  
```
HANDLE m_hHeap;
```  
  
### <a name="remarks"></a>Notes  
 Une variable est utilisée pour stocker un handle vers l’objet de segment de mémoire.  
  
##  <a name="reallocate"></a>  CWin32Heap::Reallocate  
 Réalloue un bloc de mémoire à partir de l'objet de tas.  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Pointeur vers le bloc de mémoire à réallouer.  
  
 `nBytes`  
 Nouvelle taille en octets du bloc alloué. Le bloc peut être agrandi ou réduit.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le bloc de mémoire nouvellement alloué.  
  
### <a name="remarks"></a>Notes  
 Si `p` est NULL, il est supposé que le bloc de mémoire n’a pas encore été alloué et [CWin32Heap::Allocate](#allocate) est appelée avec un argument de `nBytes`.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Classe de IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)   
 [Classe de CLocalHeap](../../atl/reference/clocalheap-class.md)   
 [Classe de CGlobalHeap](../../atl/reference/cglobalheap-class.md)   
 [Classe de CCRTHeap](../../atl/reference/ccrtheap-class.md)   
 [CComHeap, classe](../../atl/reference/ccomheap-class.md)
