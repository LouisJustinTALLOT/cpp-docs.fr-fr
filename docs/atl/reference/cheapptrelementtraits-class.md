---
title: Classe de CHeapPtrElementTraits | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa4b29f5893a0b1536a087b0c516e6340eca8449
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360075"
---
# <a name="cheapptrelementtraits-class"></a>Classe de CHeapPtrElementTraits
Cette classe fournit des méthodes, les fonctions statiques et typedefs utiles lors de la création de collections de pointeurs de tas.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrElementTraits : 
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type d’objet à stocker dans la classe de collection.  
  
 `Allocator`  
 La classe de l’allocation de mémoire à utiliser. La valeur par défaut est [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.|  
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit des méthodes, les fonctions statiques et typedefs pour contribuer à la création d’objets de classe de collection qui contient les pointeurs de segment de mémoire. La classe `CHeapPtrList` dérive `CHeapPtrElementTraits`.  
  
 Pour plus d’informations, consultez [Classes de Collection ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CHeapPtrElementTraits`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcoll.h  
  
##  <a name="inargtype"></a>  CHeapPtrElementTraits::INARGTYPE  
 Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.  
  
```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CHeapPtrElementTraits::OUTARGTYPE  
 Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.  
  
```
typedef T *& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Classe de CComHeapPtr](../../atl/reference/ccomheapptr-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
