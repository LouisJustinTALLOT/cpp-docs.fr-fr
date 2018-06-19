---
title: Classe de CStringElementTraitsI | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1544a2fec1c4567c301eb2c051f7455c8ca393c2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362103"
---
# <a name="cstringelementtraitsi-class"></a>Classe de CStringElementTraitsI
Cette classe fournit des fonctions statiques relatives aux chaînes stockées dans les objets de classe de collection. Il est similaire à [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), mais effectue des comparaisons sans respecter la casse.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>  
class CStringElementTraitsI : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de données à stocker dans la collection.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CStringElementTraitsI::INARGTYPE](#inargtype)|Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.|  
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CStringElementTraitsI::CompareElements](#compareelements)|Appelez cette fonction statique pour comparer deux éléments de chaîne sont égales, en ignorant les différences de casse.|  
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Appelez cette fonction statique pour comparer deux éléments de chaîne, en ignorant les différences de casse.|  
|[CStringElementTraitsI::Hash](#hash)|Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de la chaîne donnée.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit des fonctions statiques pour la comparaison de chaînes et pour la création d’une valeur de hachage. Ces fonctions sont utiles lors de l’utilisation d’une classe de collection pour stocker les données de type chaîne. Utilisez [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) lorsque les objets de chaîne sont avec agira en tant que références.  
  
 Pour plus d’informations, consultez [Classes de Collection ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringElementTraitsI`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcoll.h  
  
##  <a name="compareelements"></a>  CStringElementTraitsI::CompareElements  
 Appelez cette fonction statique pour comparer deux éléments de chaîne sont égales, en ignorant les différences de casse.  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `str1`  
 Le premier élément de chaîne.  
  
 `str2`  
 Le deuxième élément de chaîne.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si les éléments sont égaux, false dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Les comparaisons respectent la casse.  
  
##  <a name="compareelementsordered"></a>  CStringElementTraitsI::CompareElementsOrdered  
 Appelez cette fonction statique pour comparer deux éléments de chaîne, en ignorant les différences de casse.  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `str1`  
 Le premier élément de chaîne.  
  
 `str2`  
 Le deuxième élément de chaîne.  
  
### <a name="return-value"></a>Valeur de retour  
 Zéro si les chaînes sont identiques, < 0 si `str1` est inférieure à `str2`, ou 0 > Si `str1` est supérieur à `str2`. Le [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) méthode est utilisée pour effectuer des comparaisons.  

  
### <a name="remarks"></a>Notes  
 Les comparaisons respectent la casse.  
  
##  <a name="hash"></a>  CStringElementTraitsI::Hash  
 Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de la chaîne donnée.  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `str`  
 L’élément de la chaîne.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de hachage calculée à l’aide du contenu de la chaîne.  
  
##  <a name="inargtype"></a>  CStringElementTraitsI::INARGTYPE  
 Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CStringElementTraitsI::OUTARGTYPE  
 Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [CStringElementTraits, classe](../../atl/reference/cstringelementtraits-class.md)
