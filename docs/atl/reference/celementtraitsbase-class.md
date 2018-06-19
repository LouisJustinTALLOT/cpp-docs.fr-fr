---
title: Classe de CElementTraitsBase | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
dev_langs:
- C++
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a0b9f3945d9bcfa0c77855c94ec7247cb9804cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359592"
---
# <a name="celementtraitsbase-class"></a>Classe de CElementTraitsBase
Cette classe fournit la copie de la valeur par défaut et les méthodes d’une classe de collection de déplacement.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T>  
class CElementTraitsBase
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de données à stocker dans la collection.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CElementTraitsBase::INARGTYPE](#inargtype)|Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.|  
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CElementTraitsBase::CopyElements](#copyelements)|Appelez cette méthode pour copier les éléments stockés dans un objet de classe de collection.|  
|[CElementTraitsBase::RelocateElements](#relocateelements)|Appelez cette méthode pour déplacer des éléments stockés dans un objet de classe de collection.|  
  
## <a name="remarks"></a>Notes  
 Cette classe de base définit des méthodes pour la copie et déplacement des éléments dans une classe de collection. Il est utilisé par les classes [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md), et [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).  
  
 Pour plus d’informations, consultez [Classes de Collection ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcoll.h  
  
##  <a name="copyelements"></a>  CElementTraitsBase::CopyElements  
 Appelez cette méthode pour copier les éléments stockés dans un objet de classe de collection.  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDest`  
 Pointeur vers le premier élément qui reçoit les données copiées.  
  
 `pSrc`  
 Pointeur vers le premier élément à copier.  
  
 `nElements`  
 Nombre d'éléments à copier.  
  
### <a name="remarks"></a>Notes  
 Les éléments source et de destination ne doivent pas se chevaucher.  
  
##  <a name="inargtype"></a>  CElementTraitsBase::INARGTYPE  
 Le type de données à utiliser pour ajouter des éléments à la collection.  
  
```
typedef const T& INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CElementTraitsBase::OUTARGTYPE  
 Le type de données à utiliser pour récupérer des éléments de la collection.  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>  CElementTraitsBase::RelocateElements  
 Appelez cette méthode pour déplacer des éléments stockés dans un objet de classe de collection.  
  
```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDest`  
 Pointeur vers le premier élément qui reçoit les données déplacées.  
  
 `pSrc`  
 Pointeur vers le premier élément à déplacer.  
  
 `nElements`  
 Le nombre d’éléments à déplacer.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), ce qui est suffisant pour la plupart des types de données. Si les objets en cours de déplacement contiennent des pointeurs vers leurs propre membres, cette méthode devrez être substituée.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
