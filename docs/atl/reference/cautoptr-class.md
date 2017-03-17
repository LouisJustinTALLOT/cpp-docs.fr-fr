---
title: Classe de CAutoPtr | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 309a3d0ddceab2995c85e156c7db09ddd7edfa86
ms.lasthandoff: 02/24/2017

---
# <a name="cautoptr-class"></a>CAutoPtr (classe)
Cette classe représente un objet pointeur intelligent.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>  
class CAutoPtr
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de pointeur.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAutoPtr::CAutoPtr](#cautoptr)|Constructeur.|  
|[CAutoPtr :: ~ CAutoPtr](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAutoPtr::Attach](#attach)|Appelez cette méthode pour prendre possession d’un pointeur existant.|  
|[CAutoPtr::Detach](#detach)|Appelez cette méthode pour libérer la possession d’un pointeur.|  
|[CAutoPtr::Free](#free)|Appelez cette méthode pour supprimer un objet vers lequel pointé un `CAutoPtr`.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAutoPtr::operator T *](#operator_t_star)|L’opérateur de cast.|  
|[CAutoPtr::operator =](#operator_eq)|L’opérateur d’assignation.|  
|[CAutoPtr::operator->](#operator_ptr)|Opérateur pointeur vers membre.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAutoPtr::m_p](#m_p)|La variable de membre de données de pointeur.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit des méthodes pour créer et gérer un pointeur intelligent, ce qui vous permettra de protéger contre les fuites de mémoire en libérant les ressources d’automatiquement lorsqu’elle se trouve hors de portée.  
  
 En outre, `CAutoPtr`du constructeur de copie et de transférer la propriété affectation opérateur du pointeur, copie le pointeur de la source vers le pointeur de destination et définition du pointeur de source avec la valeur NULL. Il est donc impossible d’avoir deux `CAutoPtr` objets chacun stockant le même pointeur, et cela réduit la probabilité de la suppression de deux fois le même pointeur.  
  
 `CAutoPtr`simplifie également la création de collections de pointeurs. Au lieu de dériver une classe de collection et en remplaçant le destructeur, il est plus simple de créer une collection de `CAutoPtr` objets. Lorsque la collection est supprimée, le `CAutoPtr` objets seront hors de portée et se supprime automatiquement.  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md) et variantes fonctionnent de la même façon que `CAutoPtr`, sauf qu’elles allouer et libérer de la mémoire à l’aide des fonctions du tas différents au lieu de C++ **nouveau** et **supprimer** opérateurs. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) est similaire à `CAutoPtr`, la seule différence étant qu’il utilise **vector new []** et **vecteur delete []** pour allouer et libérer de la mémoire.  
  
 Voir aussi [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) et [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) lorsque des tableaux ou des listes de pointeurs intelligents sont requises.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  
  
## <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities&#74;](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]  
  
##  <a name="attach"></a>CAutoPtr::Attach  
 Appelez cette méthode pour prendre possession d’un pointeur existant.  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Le `CAutoPtr` objet prendra possession de ce pointeur.  
  
### <a name="remarks"></a>Notes  
 Lorsqu’un `CAutoPtr` objet prend possession du pointeur, il supprime automatiquement le pointeur et les données allouées lorsqu’il devient hors de portée. Si [CAutoPtr::Detach](#detach) est appelée, le programmeur à nouveau avec la responsabilité de libérer les ressources est alloué.  
  
 Dans les versions debug, un échec d’assertion se produit si le [CAutoPtr::m_p](#m_p) membre de données pointe actuellement à une valeur ; autrement dit, il n’est pas égal à NULL.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple dans le [CAutoPtr présentation](../../atl/reference/cautoptr-class.md).  
  
##  <a name="cautoptr"></a>CAutoPtr::CAutoPtr  
 Constructeur.  
  
```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<> 
CAutoPtr(CAutoPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Un pointeur existant.  
  
 `TSrc`  
 Le type géré par un autre `CAutoPtr`, utilisé pour initialiser l’objet actif.  
  
### <a name="remarks"></a>Remarques  
 Le `CAutoPtr` objet peut être créé à l’aide d’un pointeur existant, auquel cas il transfère la propriété du pointeur.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple dans le [CAutoPtr présentation](../../atl/reference/cautoptr-class.md).  
  
##  <a name="dtor"></a>CAutoPtr :: ~ CAutoPtr  
 Destructeur.  
  
```
~CAutoPtr() throw();
```  
  
### <a name="remarks"></a>Remarques  
 Libère toutes les ressources allouées. Appels [CAutoPtr::Free](#free).  
  
##  <a name="detach"></a>CAutoPtr::Detach  
 Appelez cette méthode pour libérer la possession d’un pointeur.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une copie du pointeur.  
  
### <a name="remarks"></a>Remarques  
 Libère la possession d’un pointeur, définit les [CAutoPtr::m_p](#m_p) variable de membre de données avec la valeur NULL et retourne une copie du pointeur. Après avoir appelé **détachement**, il jusqu’au programmeur pour libérer les ressources est allouée sur laquelle le `CAutoPtr` objet peut avoir précédemment supposé reponsibility.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple dans le [CAutoPtr présentation](../../atl/reference/cautoptr-class.md).  
  
##  <a name="free"></a>CAutoPtr::Free  
 Appelez cette méthode pour supprimer un objet vers lequel pointé un `CAutoPtr`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Notes  
 L’objet pointé par le `CAutoPtr` est libéré et la [CAutoPtr::m_p](#m_p) variable de membre de données est définie sur NULL.  
  
##  <a name="m_p"></a>CAutoPtr::m_p  
 La variable de membre de données de pointeur.  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>Notes  
 Cette variable membre conserve les informations de pointeur.  
  
##  <a name="operator_eq"></a>CAutoPtr::operator =  
 L’opérateur d’assignation.  
  
```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```  
  
### <a name="parameters"></a>Paramètres  
 `p`  
 Un pointeur.  
  
 `TSrc`  
 Un type de classe.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une référence à un **CAutoPtr\< T >**.  
  
### <a name="remarks"></a>Notes  
 Détache de l’opérateur d’assignation de la `CAutoPtr` objet à partir de n’importe quel pointeur actuel et attache le nouveau pointeur, `p`, à la place.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple dans le [CAutoPtr présentation](../../atl/reference/cautoptr-class.md).  
  
##  <a name="operator_ptr"></a>CAutoPtr::operator-&gt;  
 Opérateur pointeur vers membre.  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de la [CAutoPtr::m_p](#m_p) variable de membre de données.  
  
### <a name="remarks"></a>Notes  
 Utilisez cet opérateur pour appeler une méthode dans une classe vers laquelle pointée le `CAutoPtr` objet. Dans les versions debug, un échec d’assertion se produit si le `CAutoPtr` pointe sur la valeur NULL.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple dans le [CAutoPtr présentation](../../atl/reference/cautoptr-class.md).  
  
##  <a name="operator_t_star"></a>CAutoPtr::operator T *  
 L’opérateur de cast.  
  
```  
operator T* () const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le type de données objet défini dans le modèle de classe.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple dans le [CAutoPtr présentation](../../atl/reference/cautoptr-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CHeapPtr (classe)](../../atl/reference/cheapptr-class.md)   
 [CAutoVectorPtr (classe)](../../atl/reference/cautovectorptr-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)

