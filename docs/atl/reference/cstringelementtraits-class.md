---
title: Cstringelementtraits, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0c6ed9fb68e685a7b8a59b049277e61f41fd2ce
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885723"
---
# <a name="cstringelementtraits-class"></a>Cstringelementtraits, classe
Cette classe fournit des fonctions statiques utilisées par les classes de collection stockage `CString` objets.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>  
class CStringElementTraits
```  
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 Le type de données à stocker dans la collection.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CStringElementTraits::INARGTYPE](#inargtype)|Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.|  
|[CStringElementTraits::OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CStringElementTraits::CompareElements](#compareelements)|(Statique) Appelez cette fonction pour comparer deux éléments de chaîne pour l’égalité.|  
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|(Statique) Appelez cette fonction pour comparer deux éléments de chaîne.|  
|[CStringElementTraits::CopyElements](#copyelements)|(Statique) Appelez cette fonction pour copier `CString` éléments stockés dans un objet de classe de collection.|  
|[CStringElementTraits::Hash](#hash)|(Statique) Appelez cette fonction pour calculer une valeur de hachage pour l’élément de la chaîne donnée.|  
|[CStringElementTraits::RelocateElements](#relocateelements)|(Statique) Appelez cette fonction pour déplacer `CString` éléments stockés dans un objet de classe de collection.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit des fonctions statiques pour la copie, le déplacement et comparaison de chaînes et pour la création d’une valeur de hachage. Ces fonctions sont utiles lorsque vous utilisez une classe de collection pour stocker des données basé sur chaîne. Utilisez [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) lorsque des comparaisons sans respecter la casse sont requises. Utilisez [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) lorsque les objets de chaîne doivent être traitées en tant que références.  
  
 Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** cstringt.h  
  
##  <a name="compareelements"></a>  CStringElementTraits::CompareElements  
 Appelez cette fonction statique pour comparer deux éléments de chaîne pour l’égalité.  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>Paramètres  
 *str1*  
 La première chaîne d’élément.  
  
 *str2*  
 Le deuxième élément de chaîne.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si les éléments sont égaux, sinon false.  
  
##  <a name="compareelementsordered"></a>  CStringElementTraits::CompareElementsOrdered  
 Appelez cette fonction statique pour comparer deux éléments de chaîne.  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>Paramètres  
 *str1*  
 La première chaîne d’élément.  
  
 *str2*  
 Le deuxième élément de chaîne.  
  
### <a name="return-value"></a>Valeur de retour  
 Zéro si les chaînes sont identiques, < 0 si *str1* est inférieure à *str2*, ou 0 > Si *str1* est supérieur à *str2*. Le [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) méthode est utilisée pour exécuter les comparaisons.  

  
##  <a name="copyelements"></a>  CStringElementTraits::CopyElements  
 Appelez cette fonction statique pour copier `CString` éléments stockés dans un objet de classe de collection.  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDest*  
 Pointeur vers le premier élément qui reçoit les données copiées.  
  
 *pSrc*  
 Pointeur vers le premier élément à copier.  
  
 *nElements*  
 Nombre d'éléments à copier.  
  
### <a name="remarks"></a>Notes  
 Les éléments source et de destination ne doivent pas se chevaucher.  
  
##  <a name="hash"></a>  CStringElementTraits::Hash  
 Appelez cette fonction statique pour calculer une valeur de hachage pour l’élément de la chaîne donnée.  
  
```
static ULONG Hash(INARGTYPE str);
```  
  
### <a name="parameters"></a>Paramètres  
 *str*  
 L’élément de la chaîne.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de hachage calculée à l’aide du contenu de la chaîne.  
  
##  <a name="inargtype"></a>  CStringElementTraits::INARGTYPE  
 Le type de données à utiliser pour l’ajout d’éléments à l’objet de classe de collection.  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CStringElementTraits::OUTARGTYPE  
 Le type de données à utiliser pour récupérer des éléments de l’objet de classe de collection.  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>  CStringElementTraits::RelocateElements  
 Appelez cette fonction statique pour déplacer `CString` éléments stockés dans un objet de classe de collection.  
  
```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDest*  
 Pointeur vers le premier élément qui reçoit les données déplacées.  
  
 *pSrc*  
 Pointeur vers le premier élément à déplacer.  
  
 *nElements*  
 Le nombre d’éléments à déplacer.  
  
### <a name="remarks"></a>Notes  
 Appelle cette fonction statique [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), ce qui est suffisant pour la plupart des types de données. Si les objets en cours de déplacement contiennent des pointeurs vers leurs propres membres, cette fonction statique devrez être substituée.  
  
## <a name="see-also"></a>Voir aussi  
 [Celementtraitsbase, classe](../../atl/reference/celementtraitsbase-class.md)   
 [Cstringelementtraitsi, classe](../../atl/reference/cstringelementtraitsi-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
