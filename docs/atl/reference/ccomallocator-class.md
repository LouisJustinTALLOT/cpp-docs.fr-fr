---
title: Classe de CComAllocator | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
dev_langs: C++
helpviewer_keywords: CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 370a52e87bcbb4849883ea03016cc462030ad028
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="ccomallocator-class"></a>Classe de CComAllocator
Cette classe fournit des méthodes pour la gestion de la mémoire à l’aide des routines de mémoire COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComAllocator
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComAllocator::Allocate](#allocate)|Appelez cette méthode statique pour allouer de mémoire.|  
|[CComAllocator::Free](#free)|Appelez cette méthode statique pour libérer de la mémoire allouée.|  
|[CComAllocator::Reallocate](#reallocate)|Appelez cette méthode statique pour réallouer la mémoire.|  
  
## <a name="remarks"></a>Notes  
 Cette classe est utilisée par [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) pour fournir des routines d’allocation de la mémoire COM. La classe équivalent, [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), fournit les mêmes méthodes à l’aide des routines CRT.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h  
  
##  <a name="allocate"></a>CComAllocator::Allocate  
 Appelez cette fonction statique pour allouer de la mémoire.  
  
```
static void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nBytes`  
 Nombre d'octets à allouer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur void vers l'espace alloué, ou NULL si la mémoire disponible est insuffisante.  
  
### <a name="remarks"></a>Notes  
 Alloue de la mémoire. Consultez [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727) pour plus d’informations.  
  
##  <a name="free"></a>CComAllocator::Free  
 Appelez cette fonction statique pour libérer de la mémoire allouée.  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Pointeur vers la mémoire allouée.  
  
### <a name="remarks"></a>Notes  
 Libère la mémoire allouée. Consultez [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722) pour plus d’informations.  
  
##  <a name="reallocate"></a>CComAllocator::Reallocate  
 Appelez cette fonction statique pour réallouer de la mémoire.  
  
```
static void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Pointeur vers la mémoire allouée.  
  
 `nBytes`  
 Nombre d'octets à réallouer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur void vers l’espace alloué, ou NULL si la mémoire est insuffisante  
  
### <a name="remarks"></a>Notes  
 Redimensionne la quantité de mémoire allouée. Consultez [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CComHeapPtr](../../atl/reference/ccomheapptr-class.md)   
 [Classe de CCRTAllocator](../../atl/reference/ccrtallocator-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
