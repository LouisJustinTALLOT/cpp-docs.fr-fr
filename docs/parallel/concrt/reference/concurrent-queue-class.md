---
title: concurrent_queue, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::clear
- CONCURRENT_QUEUE/concurrency::concurrent_queue::empty
- CONCURRENT_QUEUE/concurrency::concurrent_queue::get_allocator
- CONCURRENT_QUEUE/concurrency::concurrent_queue::push
- CONCURRENT_QUEUE/concurrency::concurrent_queue::try_pop
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_begin
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_end
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_size
dev_langs:
- C++
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9a3ee82b8b81532b4e63f080ad321a93725ce41
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="concurrentqueue-class"></a>concurrent_queue, classe
La classe `concurrent_queue` est une classe de conteneur de séquence qui autorise un accès Premier entré, premier sorti à ses éléments. Elle permet un ensemble limité d'opérations d'accès concurrentiel sécurisé, comme `push` et `try_pop`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de données des éléments à stocker dans la file d’attente.  
  
 `_Ax`  
 Type qui représente l’objet allocateur stocké qui contient des informations sur l’allocation et la désallocation de mémoire pour cette file d’attente simultanée. Cet argument est facultatif et sa valeur par défaut est `allocator<T>`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`allocator_type`|Type qui représente la classe d’allocateur pour la file d’attente simultanée.|  
|`const_iterator`|Un type qui représente un non thread-safe `const` itérateur sur les éléments dans une file d’attente simultanée.|  
|`const_reference`|Type qui fournit une référence à un `const` élément stocké dans une file d’attente simultanée pour la lecture et l’exécution `const` operations.|  
|`difference_type`|Type qui fournit la distance signée entre deux éléments dans une file d’attente simultanée.|  
|`iterator`|Type qui représente un itérateur non thread-safe sur les éléments d’une file d’attente simultanée.|  
|`reference`|Type qui fournit une référence à un élément stocké dans une file d’attente simultanée.|  
|`size_type`|Type qui compte le nombre d’éléments dans une file d’attente simultanée.|  
|`value_type`|Type qui représente le type de données stocké dans une file d’attente simultanée.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[concurrent_queue](#ctor)|Surchargé. Construit une file d’attente simultanée.|  
|[~ concurrent_queue, destructeur](#dtor)|Détruit la file d’attente simultanée.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[clear](#clear)|Efface la file d’attente simultanée, en détruisant les actuellement les éléments en file d’attente. Cette méthode n’est pas d’accès concurrentiel sécurisé.|  
|[empty](#empty)|Vérifie si la file d’attente simultanée est vide au moment où cette méthode est appelée. Cette méthode est concurrentiel.|  
|[get_allocator](#get_allocator)|Retourne une copie de l’allocateur utilisé pour construire la file d’attente simultanée. Cette méthode est concurrentiel.|  
|[push](#push)|Surchargé. Place un élément à la fin de la file d’attente simultanée. Cette méthode est concurrentiel.|  
|[try_pop](#try_pop)|Enlève un élément à partir de la file d’attente si celle-ci est disponible. Cette méthode est concurrentiel.|  
|[unsafe_begin](#unsafe_begin)|Surchargé. Retourne un itérateur de type `iterator` ou `const_iterator` au début de la file d’attente simultanée. Cette méthode n’est pas d’accès concurrentiel sécurisé.|  
|[unsafe_end](#unsafe_end)|Surchargé. Retourne un itérateur de type `iterator` ou `const_iterator` à la fin de la file d’attente simultanée. Cette méthode n’est pas d’accès concurrentiel sécurisé.|  
|[unsafe_size](#unsafe_size)|Retourne le nombre d’éléments dans la file d’attente. Cette méthode n’est pas d’accès concurrentiel sécurisé.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `concurrent_queue`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concurrent_queue.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="clear"></a> Effacer 

 Efface la file d’attente simultanée, en détruisant les actuellement les éléments en file d’attente. Cette méthode n’est pas d’accès concurrentiel sécurisé.  
  
```
void clear();
```  
  
##  <a name="ctor"></a> concurrent_queue 

 Construit une file d’attente simultanée.  
  
```
explicit concurrent_queue(
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    const concurrent_queue& _OtherQ,
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    concurrent_queue&& _OtherQ,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_queue(_InputIterator _Begin,
    _InputIterator _End);
```  
  
### <a name="parameters"></a>Paramètres  
 `_InputIterator`  
 Le type de l’itérateur d’entrée qui spécifie une plage de valeurs.  
  
 `_Al`  
 Classe allocator à utiliser avec cet objet.  
  
 `_OtherQ`  
 La source `concurrent_queue` objet à copier ou déplacer des éléments à partir de.  
  
 `_Begin`  
 Position du premier élément dans la plage d'éléments à copier.  
  
 `_End`  
 Position du premier élément suivant la fin de la plage d'éléments à copier.  
  
### <a name="remarks"></a>Notes  
 Tous les constructeurs stockent un objet allocateur `_Al` et d’initialiser la file d’attente.  
  
 Le premier constructeur spécifie une file d’attente initiale vide et spécifie explicitement le type d’allocateur à utiliser.  
  
 Le deuxième constructeur spécifie une copie de la file d’attente simultanée `_OtherQ`.  
  
 Le troisième constructeur spécifie un déplacement de la file d’attente simultanée `_OtherQ`.  
  
 Le quatrième constructeur spécifie les valeurs fournies par la plage d’itérateurs [ `_Begin`, `_End`).  
  
##  <a name="dtor"></a> ~concurrent_queue 

 Détruit la file d’attente simultanée.  
  
```
~concurrent_queue();
```  
  
##  <a name="empty"></a> vide 

 Vérifie si la file d’attente simultanée est vide au moment où cette méthode est appelée. Cette méthode est concurrentiel.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si la file d’attente simultanée était vide au moment où nous avons, `false` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Si cette méthode est concurrentiel en ce qui concerne les appels aux méthodes `push`, `try_pop`, et `empty`, la valeur retournée peut être incorrecte au moment où elle est inspectée par le thread appelant.  
  
##  <a name="get_allocator"></a> get_allocator 

 Retourne une copie de l’allocateur utilisé pour construire la file d’attente simultanée. Cette méthode est concurrentiel.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une copie de l’allocateur utilisé pour construire la file d’attente simultanée.  
  
##  <a name="push"></a> Push 

 Place un élément à la fin de la file d’attente simultanée. Cette méthode est concurrentiel.  
  
```
void push(const T& _Src);

void push(T&& _Src);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Src`  
 L’élément à ajouter à la file d’attente.  
  
### <a name="remarks"></a>Notes  
 `push` est accès concurrentiel en ce qui concerne les appels aux méthodes `push`, `try_pop`, et `empty`.  
  
##  <a name="try_pop"></a> try_pop 

 Enlève un élément à partir de la file d’attente si celle-ci est disponible. Cette méthode est concurrentiel.  
  
```
bool try_pop(T& _Dest);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Dest`  
 Une référence à un emplacement pour stocker l’élément de file d’attente.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si un élément a été correctement file d’attente, `false` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Si un élément a été correctement file d’attente, le paramètre `_Dest` reçoit la valeur correspondante, la valeur d’origine contenue dans la file d’attente est détruite et cette fonction retourne `true`. Il n’existait aucun élément de la file d’attente, cette fonction retourne `false` sans blocage et le contenu de le `_Dest` paramètre ne sont pas définis.  
  
 `try_pop` est accès concurrentiel en ce qui concerne les appels aux méthodes `push`, `try_pop`, et `empty`.  
  
##  <a name="unsafe_begin"></a> unsafe_begin 

 Retourne un itérateur de type `iterator` ou `const_iterator` au début de la file d’attente simultanée. Cette méthode n’est pas d’accès concurrentiel sécurisé.  
  
```
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur de type `iterator` ou `const_iterator` au début de l’objet de file d’attente simultanée.  
  
### <a name="remarks"></a>Notes  
 Les itérateurs pour la `concurrent_queue` classe sont principalement pour le débogage, comme ils sont lents et itération n’est pas d’accès concurrentiel-safe en ce qui concerne les autres opérations de file d’attente.  
  
##  <a name="unsafe_end"></a> unsafe_end 

 Retourne un itérateur de type `iterator` ou `const_iterator` à la fin de la file d’attente simultanée. Cette méthode n’est pas d’accès concurrentiel sécurisé.  
  
```
iterator unsafe_end();

const_iterator unsafe_end() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur de type `iterator` ou `const_iterator` à la fin de la file d’attente simultanée.  
  
### <a name="remarks"></a>Notes  
 Les itérateurs pour la `concurrent_queue` classe sont principalement pour le débogage, comme ils sont lents et itération n’est pas d’accès concurrentiel-safe en ce qui concerne les autres opérations de file d’attente.  
  
##  <a name="unsafe_size"></a> unsafe_size 

 Retourne le nombre d’éléments dans la file d’attente. Cette méthode n’est pas d’accès concurrentiel sécurisé.  
  
```
size_type unsafe_size() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 La taille de la file d’attente simultanée.  
  
### <a name="remarks"></a>Notes  
 `unsafe_size` n’est pas sécurisé d’accès concurrentiel et peut produire des résultats incorrects si elle est appelée en même temps que les appels aux méthodes `push`, `try_pop`, et `empty`.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)
