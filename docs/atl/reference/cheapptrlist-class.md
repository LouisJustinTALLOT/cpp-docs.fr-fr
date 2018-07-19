---
title: Cheapptrlist, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd3342e7c64a13761830073cd3ed82b627b8c407
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879294"
---
# <a name="cheapptrlist-class"></a>Cheapptrlist, classe
Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs de tas.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename E, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrList 
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```  
  
#### <a name="parameters"></a>Paramètres  
 *E*  
 Le type d’objet à stocker dans la classe de collection.  
  
 *Allocateur*  
 La classe d’allocation de mémoire à utiliser. La valeur par défaut est [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|Constructeur.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit un constructeur et est dérivée des méthodes à partir de [CAtlList](../../atl/reference/catllist-class.md) et [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) afin de faciliter la création d’un objet de classe de collection stocker des pointeurs de tas.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CHeapPtrList`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlcoll.h  
  
##  <a name="cheapptrlist"></a>  CHeapPtrList::CHeapPtrList  
 Constructeur.  
  
```
CHeapPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *nBlockSize*  
 La taille du bloc.  
  
### <a name="remarks"></a>Notes  
 La taille de bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Tailles de bloc supérieures réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources.  
  
## <a name="see-also"></a>Voir aussi  
 [CAtlList, classe](../../atl/reference/catllist-class.md)   
 [Cheapptr, classe](../../atl/reference/cheapptr-class.md)   
 [Cheapptrelementtraits, classe](../../atl/reference/cheapptrelementtraits-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
