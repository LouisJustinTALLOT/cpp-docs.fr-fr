---
title: Classe de CHeapPtrList | Documents Microsoft
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
ms.openlocfilehash: dc5b164fda27775a7b3fb272d8718c31815cb1ca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358813"
---
# <a name="cheapptrlist-class"></a>Classe de CHeapPtrList
Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs de tas.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename E, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrList 
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```  
  
#### <a name="parameters"></a>Paramètres  
 `E`  
 Le type d’objet à stocker dans la classe de collection.  
  
 `Allocator`  
 La classe de l’allocation de mémoire à utiliser. La valeur par défaut est [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|Constructeur.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit un constructeur et dérive des méthodes à partir de [CAtlList](../../atl/reference/catllist-class.md) et [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) à l’aide de la création d’un objet de classe de collection stocker des pointeurs de segment de mémoire.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CHeapPtrList`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcoll.h  
  
##  <a name="cheapptrlist"></a>  CHeapPtrList::CHeapPtrList  
 Constructeur.  
  
```
CHeapPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nBlockSize`  
 La taille du bloc.  
  
### <a name="remarks"></a>Notes  
 La taille de bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Tailles de bloc supérieures réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CAtlList](../../atl/reference/catllist-class.md)   
 [Classe de CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Classe de CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
