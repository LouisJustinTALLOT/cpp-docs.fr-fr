---
title: Classe de CInterfaceArray | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36a24eadea87d0d34adf0f577b321fa16a7cfc86
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359460"
---
# <a name="cinterfacearray-class"></a>Classe de CInterfaceArray
Cette classe fournit des méthodes utiles lors de la construction d’un tableau de pointeurs d’interface COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class I, const IID* piid=& __uuidof(I)>  
class CInterfaceArray : 
   public CAtlArray<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Le constructeur pour le tableau de l’interface.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit un constructeur et les méthodes dérivées pour la création d’un tableau de pointeurs d’interface COM. Utilisez [CInterfaceList](../../atl/reference/cinterfacelist-class.md) lorsqu’une liste est requise.  
  
 Pour plus d’informations, consultez [Classes de Collection ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CAtlArray`  
  
 `CInterfaceArray`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcoll.h  
  
##  <a name="cinterfacearray"></a>  CInterfaceArray::CInterfaceArray  
 Constructeur.  
  
```
CInterfaceArray() throw();
```  
  
### <a name="remarks"></a>Notes  
 Initialise le tableau de pointeurs intelligents.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe CAtlArray](../../atl/reference/catlarray-class.md)   
 [Classe de CComQIPtr](../../atl/reference/ccomqiptr-class.md)   
 [Classe de CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
