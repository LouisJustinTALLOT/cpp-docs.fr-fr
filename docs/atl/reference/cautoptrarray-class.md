---
title: Classe de CAutoPtrArray | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b99fe8fde475453c9e6dc0b524a6b1b94821bf75
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358949"
---
# <a name="cautoptrarray-class"></a>Classe de CAutoPtrArray
Cette classe fournit des méthodes utiles lors de la construction d’un tableau de pointeurs intelligents.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>Paramètres  
 `E`  
 Le type de pointeur.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|Constructeur.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit un constructeur et dérive des méthodes à partir de [CAtlArray](../../atl/reference/catlarray-class.md) et [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) à l’aide de la création d’un objet de classe de collection le stockage des pointeurs intelligents.  
  
 Pour plus d’informations, consultez [Classes de Collection ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CAtlArray`  
  
 `CAutoPtrArray`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcoll.h  
  
##  <a name="cautoptrarray"></a>  CAutoPtrArray::CAutoPtrArray  
 Constructeur.  
  
```
CAutoPtrArray() throw();
```  
  
### <a name="remarks"></a>Notes  
 Initialise le tableau de pointeurs intelligents.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe CAtlArray](../../atl/reference/catlarray-class.md)   
 [Classe de CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)   
 [Classe de CAutoPtrList](../../atl/reference/cautoptrlist-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
