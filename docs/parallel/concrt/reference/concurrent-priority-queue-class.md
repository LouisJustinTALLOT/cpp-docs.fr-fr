---
title: concurrent_priority_queue, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::clear
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::empty
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::get_allocator
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::push
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::size
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::swap
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::try_pop
dev_langs:
- C++
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
caps.latest.revision: 9
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 95b52911135513b0b1e4d84509c80ed3262c1765
ms.lasthandoff: 03/17/2017

---
# <a name="concurrentpriorityqueue-class"></a>concurrent_priority_queue, classe
La classe `concurrent_priority_queue` est un conteneur qui permet à plusieurs threads d'appeler simultanément des méthodes Push et Pop sur des éléments. Les éléments sont dépilés dans l’ordre de priorité dans lequel la priorité est déterminée par un functor fourni comme argument de modèle.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de données des éléments à stocker dans la file d’attente de priorité.  
  
 `_Compare`  
 Le type de l’objet de fonction qui peut comparer deux valeurs d’éléments comme clés de tri pour déterminer leur ordre relatif dans la file d’attente de priorité. Cet argument est facultatif et le prédicat binaire `less<``T``>` est la valeur par défaut.  
  
 `_Ax`  
 Type qui représente l’objet allocateur stocké qui contient des informations sur l’allocation et la désallocation de mémoire pour la file d’attente de priorité simultanées. Cet argument est facultatif et sa valeur par défaut est `allocator<``T``>`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`allocator_type`|Type qui représente la classe d’allocateur pour la file d’attente de priorité simultanées.|  
|`const_reference`|Type qui représente une référence const vers un élément du type stocké dans une file d’attente de priorité simultanées.|  
|`reference`|Type qui représente une référence à un élément du type stocké dans une file d’attente de priorité simultanées.|  
|`size_type`|Type qui compte le nombre d’éléments dans une file d’attente de priorité simultanées.|  
|`value_type`|Type qui représente le type de données stocké dans une file d’attente de priorité simultanées.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[concurrent_priority_queue](#ctor)|Surchargé. Construit une file d’attente de priorité simultanées.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[clear](#clear)|Efface tous les éléments dans l’ordre de priorité simultanée. Cette méthode n’est pas concurrentiel.|  
|[empty](#empty)|Vérifie si la file d’attente de priorité simultanées est vide au moment où cette méthode est appelée. Cette méthode est concurrentiel.|  
|[get_allocator](#get_allocator)|Retourne une copie de l’allocateur utilisé pour construire la file d’attente de priorité simultanées. Cette méthode est concurrentiel.|  
|[push](#push)|Surchargé. Ajoute un élément à la file d’attente de priorité simultanées. Cette méthode est concurrentiel.|  
|[size](#size)|Retourne le nombre d’éléments dans la file d’attente de priorité simultanées. Cette méthode est concurrentiel.|  
|[swap](#swap)|Échange le contenu de deux files d’attente simultanées. Cette méthode n’est pas concurrentiel.|  
|[try_pop](#try_pop)|Supprime et retourne l’élément de priorité la plus élevée de la file d’attente si la file d’attente est vide. Cette méthode est concurrentiel.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator=](#operator_eq)|Surchargé. Assigne le contenu d’un autre `concurrent_priority_queue` objet à celui-ci. Cette méthode n’est pas concurrentiel.|  
  
## <a name="remarks"></a>Remarques  
 Pour plus d’informations sur la `concurrent_priority_queue` de classe, consultez la page [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 `concurrent_priority_queue`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concurrent_priority_queue.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="clear"></a>Effacer 

 Efface tous les éléments dans l’ordre de priorité simultanée. Cette méthode n’est pas concurrentiel.  
  
```
void clear();
```  
  
### <a name="remarks"></a>Remarques  
 `clear`n’est pas concurrentiel. Vous devez vous assurer qu’aucun autre thread n’est appel de méthodes sur la file d’attente de priorité simultanées lorsque vous appelez cette méthode. `clear`ne libère pas de mémoire.  
  
##  <a name="ctor"></a>concurrent_priority_queue 

 Construit une file d’attente de priorité simultanées.  
  
```
explicit concurrent_priority_queue(
    const allocator_type& _Al = allocator_type());

explicit concurrent_priority_queue(
    size_type _Init_capacity,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_priority_queue(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());

concurrent_priority_queue(
    const concurrent_priority_queue& _Src);

concurrent_priority_queue(
    const concurrent_priority_queue& _Src,
    const allocator_type& _Al);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src,
    const allocator_type& _Al);
```  
  
### <a name="parameters"></a>Paramètres  
 `_InputIterator`  
 Type de l'itérateur d'entrée.  
  
 `_Al`  
 Classe allocator à utiliser avec cet objet.  
  
 `_Init_capacity`  
 La capacité initiale de la `concurrent_priority_queue` objet.  
  
 `_Begin`  
 Position du premier élément de la plage d'éléments à copier.  
  
 `_End`  
 Position du premier élément au-delà de la plage d'éléments à copier.  
  
 `_Src`  
 La source `concurrent_priority_queue` objet à copier ou déplacer des éléments à partir de.  
  
### <a name="remarks"></a>Remarques  
 Tous les constructeurs stockent un objet allocateur `_Al` et d’initialiser la file d’attente de priorité.  
  
 Le premier constructeur spécifie une file d’attente de priorité initiale vide et spécifie éventuellement un allocateur.  
  
 Le deuxième constructeur spécifie une file d’attente de priorité avec une capacité initiale `_Init_capacity` et spécifie éventuellement un allocateur.  
  
 Le troisième constructeur spécifie les valeurs fournies par la plage d’itérateurs [ `_Begin`, `_End`) et spécifie éventuellement un allocateur.  
  
 Les quatrième et cinquième constructeurs spécifient une copie de la file d’attente de priorité `_Src`.  
  
 Les constructeurs sixième et septième spécifient un déplacement de la file d’attente de priorité `_Src`.  
  
##  <a name="empty"></a>vide 

 Vérifie si la file d’attente de priorité simultanées est vide au moment où cette méthode est appelée. Cette méthode est concurrentiel.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true`Si la file d’attente de priorité était vide au moment où la fonction a été appelée, `false` dans le cas contraire.  
  
##  <a name="get_allocator"></a>get_allocator 

 Retourne une copie de l’allocateur utilisé pour construire la file d’attente de priorité simultanées. Cette méthode est concurrentiel.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une copie de l’allocateur utilisé pour construire le `concurrent_priority_queue` objet.  
  
##  <a name="operator_eq"></a>opérateur = 

 Assigne le contenu d’un autre `concurrent_priority_queue` objet à celui-ci. Cette méthode n’est pas concurrentiel.  
  
```
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Src`  
 Objet `concurrent_priority_queue` source.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à ce `concurrent_priority_queue` objet.  
  
##  <a name="push"></a>push 

 Ajoute un élément à la file d’attente de priorité simultanées. Cette méthode est concurrentiel.  
  
```
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Elem`  
 L’élément à ajouter à la file d’attente de priorité simultanées.  
  
##  <a name="size"></a>taille 

 Retourne le nombre d’éléments dans la file d’attente de priorité simultanées. Cette méthode est concurrentiel.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans ce `concurrent_priority_queue` objet.  
  
### <a name="remarks"></a>Remarques  
 La taille retournée est garantie pour inclure tous les éléments ajoutés par les appels à la fonction `push`. Toutefois, il ne reflète pas les résultats d’opérations simultanées en attente.  
  
##  <a name="swap"></a>échange 

 Échange le contenu de deux files d’attente simultanées. Cette méthode n’est pas concurrentiel.  
  
```
void swap(concurrent_priority_queue& _Queue);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Queue`  
 Le `concurrent_priority_queue` objet échanger le contenu avec.  
  
##  <a name="try_pop"></a>try_pop 

 Supprime et retourne l’élément de priorité la plus élevée de la file d’attente si la file d’attente est vide. Cette méthode est concurrentiel.  
  
```
bool try_pop(reference _Elem);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Elem`  
 Une référence à une variable qui contiendra l’élément de priorité la plus élevée, si la file d’attente est vide.  
  
### <a name="return-value"></a>Valeur de retour  
 `true`Si une valeur a été retirée, `false` dans le cas contraire.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [Conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md)




