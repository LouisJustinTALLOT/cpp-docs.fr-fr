---
title: Classe de CGlobalHeap | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bef811807c90507184690d1a29d4debd00cc6fda
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363332"
---
# <a name="cglobalheap-class"></a>Classe de CGlobalHeap
Cette classe implémente [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) en utilisant les fonctions de tas global Win32.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
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
 `CGlobalHeap` implémente des fonctions d’allocation de mémoire en utilisant les fonctions de tas global Win32.  
  
> [!NOTE]
>  Les fonctions de tas global sont plus lentes que les autres fonctions de gestion de mémoire et ne fournissent pas autant de fonctionnalités. Par conséquent, les nouvelles applications doivent utiliser le [fonctions de tas](http://msdn.microsoft.com/library/windows/desktop/aa366711). Ils sont disponibles dans le [CWin32Heap](../../atl/reference/cwin32heap-class.md) classe. Fonctions globales sont toujours utilisées par DDE et les fonctions du Presse-papiers.  
  
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
 `nBytes`  
 Nombre demandé d'octets dans le nouveau bloc de mémoire.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le début du bloc de mémoire nouvellement alloué.  
  
### <a name="remarks"></a>Notes  
 Appelez [CGlobalHeap::Free](#free) ou [CGlobalHeap::Reallocate](#reallocate) pour libérer la mémoire allouée par cette méthode.  
  
 Implémentation à l’aide [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) avec un paramètre d’indicateur de **GMEM_FIXED**.  
  
##  <a name="free"></a>  CGlobalHeap::Free  
 Appelez cette méthode pour libérer un bloc de mémoire allouée par ce gestionnaire de mémoire.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Pointeur vers la mémoire précédemment allouée par ce gestionnaire de mémoire. NULL est une valeur valide et ne fait rien.  
  
### <a name="remarks"></a>Notes  
 Implémentation à l’aide [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579).  
  
##  <a name="getsize"></a>  CGlobalHeap::GetSize  
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
 Implémentation à l’aide [GlobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593).  
  
##  <a name="reallocate"></a>  CGlobalHeap::Reallocate  
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
 Appelez [CGlobalHeap::Free](#free) pour libérer la mémoire allouée par cette méthode.  
  
 Implémentation à l’aide [GlobalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366590).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Classe de CComHeap](../../atl/reference/ccomheap-class.md)   
 [Classe de CWin32Heap](../../atl/reference/cwin32heap-class.md)   
 [Classe de CLocalHeap](../../atl/reference/clocalheap-class.md)   
 [Classe de CCRTHeap](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr, classe](../../atl/reference/iatlmemmgr-class.md)
