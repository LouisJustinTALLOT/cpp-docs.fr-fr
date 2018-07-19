---
title: Ccomallocator, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9dbaa4631e50b14131418b902dd008e74060dbf6
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881921"
---
# <a name="ccomallocator-class"></a>Ccomallocator, classe
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
|[CComAllocator::Free](#free)|Appelez cette méthode statique pour libérer la mémoire allouée.|  
|[CComAllocator::Reallocate](#reallocate)|Appelez cette méthode statique pour réallouer la mémoire.|  
  
## <a name="remarks"></a>Notes  
 Cette classe est utilisée par [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) pour fournir des routines d’allocation de la mémoire COM. La classe équivalent, [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), fournit les mêmes méthodes à l’aide des routines CRT.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h  
  
##  <a name="allocate"></a>  CComAllocator::Allocate  
 Appelez cette fonction statique pour allouer de la mémoire.  
  
```
static void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *nBytes*  
 Nombre d'octets à allouer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur void vers l'espace alloué, ou NULL si la mémoire disponible est insuffisante.  
  
### <a name="remarks"></a>Notes  
 Alloue de la mémoire. Consultez [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727) pour plus d’informations.  
  
##  <a name="free"></a>  CComAllocator::Free  
 Appelez cette fonction statique pour libérer la mémoire allouée.  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *p*  
 Pointeur vers la mémoire allouée.  
  
### <a name="remarks"></a>Notes  
 Libère la mémoire allouée. Consultez [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722) pour plus d’informations.  
  
##  <a name="reallocate"></a>  CComAllocator::Reallocate  
 Appelez cette fonction statique pour réallouer de la mémoire.  
  
```
static void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *p*  
 Pointeur vers la mémoire allouée.  
  
 *nBytes*  
 Nombre d'octets à réallouer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur void vers l’espace alloué, ou NULL si la mémoire est insuffisante  
  
### <a name="remarks"></a>Notes  
 Redimensionne la quantité de mémoire allouée. Consultez [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [CComHeapPtr, classe](../../atl/reference/ccomheapptr-class.md)   
 [Ccrtallocator, classe](../../atl/reference/ccrtallocator-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
