---
title: Classe de CAutoVectorPtrElementTraits | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 52c450a1a261224cf87ea125a6f01259da0e9f1b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357881"
---
# <a name="cautovectorptrelementtraits-class"></a>Classe de CAutoVectorPtrElementTraits
Cette classe fournit des méthodes, les fonctions statiques et typedefs utiles lors de la création de collections de pointeurs intelligents à l’aide de nouveau vecteur et supprimer des opérateurs.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>  
class CAutoVectorPtrElementTraits : 
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```    
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de pointeur.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.|  
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit des méthodes, les fonctions statiques et typedefs pour contribuer à la création d’objets de classe de collection qui contient des pointeurs intelligents. Contrairement aux [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md), cette classe vector nouveaux et supprimer des opérateurs.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoVectorPtrElementTraits`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcoll.h  
  
##  <a name="inargtype"></a>  CAutoVectorPtrElementTraits::INARGTYPE  
 Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.  
  
```
typedef CAutoVectorPtr<T>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CAutoVectorPtrElementTraits::OUTARGTYPE  
 Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.  
  
```
typedef T*& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Classe de CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
