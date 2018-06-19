---
title: Classe de CPrimitiveElementTraits | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bec944c4b9a505cc817dbe7aa3ce09a317954f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359141"
---
# <a name="cprimitiveelementtraits-class"></a>Classe de CPrimitiveElementTraits
Cette classe fournit des méthodes par défaut et des fonctions pour une classe de collection composée des types de données primitifs.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>  
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de données à stocker dans l’objet de classe de collection.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.|  
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit les fonctions statiques par défaut et les méthodes pour déplacer, copier, comparaison et hachage des éléments de type de données primitif stockées dans un objet de classe de collection.  
  
 Pour plus d’informations, consultez [Classes de Collection ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CPrimitiveElementTraits`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcoll.h  
  
##  <a name="inargtype"></a>  CPrimitiveElementTraits::INARGTYPE  
 Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.  
  
```
typedef T INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CPrimitiveElementTraits::OUTARGTYPE  
 Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
