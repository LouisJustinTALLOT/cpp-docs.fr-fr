---
title: Classe de CLocalHeap | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 299c672d65d7568539473dfc284833c2583a2220
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363556"
---
# <a name="clocalheap-class"></a>Classe de CLocalHeap
Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) en utilisant les fonctions de tas local Win32.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
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
 `CLocalHeap` implémente des fonctions d’allocation de mémoire en utilisant les fonctions de tas local Win32.  
  
> [!NOTE]
>  Les fonctions de tas local sont plus lentes que les autres fonctions de gestion de mémoire et ne fournissent pas autant de fonctionnalités. Par conséquent, les nouvelles applications doivent utiliser le [fonctions de tas](http://msdn.microsoft.com/library/windows/desktop/aa366711). Ils sont disponibles dans le [CWin32Heap](../../atl/reference/cwin32heap-class.md) classe.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IAtlMemMgr`  
  
 `CLocalHeap`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlmem.h  
  
##  <a name="allocate"></a>  CLocalHeap::Allocate  
 Appelez cette méthode pour allouer un bloc de mémoire.  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nBytes`  
 Nombre demandé d'octets dans le nouveau bloc de mémoire.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.  
  
### <a name="remarks"></a>Notes  
 Appelez [CLocalHeap::Free](#free) ou [CLocalHeap::Reallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.  
  
 Implémentation à l’aide [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723) avec un paramètre d’indicateur de **LMEM_FIXED**.  
  
##  <a name="free"></a>  CLocalHeap::Free  
 Appelez cette méthode pour libérer un bloc de mémoire allouée par ce gestionnaire de mémoire.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire. NULL est une valeur valide et ne fait rien.  
  
### <a name="remarks"></a>Notes  
 Implémentation à l’aide [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730).  
  
##  <a name="getsize"></a>  CLocalHeap::GetSize  
 Appelez cette méthode pour obtenir la taille d’un bloc de mémoire allouée par ce gestionnaire de mémoire allouée.  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la taille du bloc de mémoire allouée en octets.  
  
### <a name="remarks"></a>Notes  
 Implémentation à l’aide [LocalSize](http://msdn.microsoft.com/library/windows/desktop/aa366745).  
  
##  <a name="reallocate"></a>  CLocalHeap::Reallocate  
 Appelez cette méthode pour réallouer la mémoire allouée par ce gestionnaire de mémoire.  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire.  
  
 `nBytes`  
 Nombre demandé d'octets dans le nouveau bloc de mémoire.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.  
  
### <a name="remarks"></a>Notes  
 Appelez [CLocalHeap::Free](#free) pour libérer la mémoire allouée par cette méthode.  
  
 Implémentation à l’aide [LocalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366742).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Classe de CComHeap](../../atl/reference/ccomheap-class.md)   
 [Classe de CWin32Heap](../../atl/reference/cwin32heap-class.md)   
 [Classe de CGlobalHeap](../../atl/reference/cglobalheap-class.md)   
 [Classe de CCRTHeap](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr, classe](../../atl/reference/iatlmemmgr-class.md)
