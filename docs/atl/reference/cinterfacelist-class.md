---
title: Classe de CInterfaceList | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fc523b1eccc88678cda48a0c7e429ea0fc09f9b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362172"
---
# <a name="cinterfacelist-class"></a>Classe de CInterfaceList
Cette classe fournit des méthodes utiles lors de la construction d’une liste de pointeurs d’interface COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class I, const IID* piid =& __uuidof(I)>  
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>Paramètres  
 `I`  
 Une interface COM en spécifiant le type de pointeur à stocker.  
  
 `piid`  
 Un pointeur vers l’IID de `I`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CInterfaceList::CInterfaceList](#cinterfacelist)|Le constructeur de la liste des interfaces.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit un constructeur et les méthodes dérivées pour la création d’une liste de pointeurs d’interface COM. Utilisez [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) lorsqu’un tableau est requis.  
  
 Pour plus d’informations, consultez [Classes de Collection ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcoll.h  
  
##  <a name="cinterfacelist"></a>  CInterfaceList::CInterfaceList  
 Le constructeur de la liste des interfaces.  
  
```
CInterfaceList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nBlockSize`  
 La taille du bloc, avec la valeur par défaut est 10.  
  
### <a name="remarks"></a>Notes  
 La taille de bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Tailles de bloc supérieures réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CAtlList](../../atl/reference/catllist-class.md)   
 [Classe de CComQIPtr](../../atl/reference/ccomqiptr-class.md)   
 [Classe de CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
