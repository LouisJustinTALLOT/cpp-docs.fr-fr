---
title: Classe de CAutoPtrList | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9101d66de6782d1a060a8acdfb0d02e9971bb9c5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357543"
---
# <a name="cautoptrlist-class"></a>Classe de CAutoPtrList
Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs intelligents.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename E>  
class CAutoPtrList : 
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>Paramètres  
 `E`  
 Le type de pointeur.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|Constructeur.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit un constructeur et dérive des méthodes à partir de [CAtlList](../../atl/reference/catllist-class.md) et [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) à l’aide de la création d’un objet liste de stocker les pointeurs intelligents. La classe [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) fournit une fonction similaire pour un objet tableau.  
  
 Pour plus d’informations, consultez [Classes de Collection ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CAutoPtrList`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcoll.h  
  
##  <a name="cautoptrlist"></a>  CAutoPtrList::CAutoPtrList  
 Constructeur.  
  
```
CAutoPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nBlockSize`  
 La taille du bloc, avec la valeur par défaut est 10.  
  
### <a name="remarks"></a>Notes  
 La taille de bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Tailles de bloc supérieures réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CAtlList](../../atl/reference/catllist-class.md)   
 [Classe de CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
