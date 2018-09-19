---
title: concurrent_vector, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::assign
- CONCURRENT_VECTOR/concurrency::concurrent_vector::at
- CONCURRENT_VECTOR/concurrency::concurrent_vector::back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::begin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::capacity
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::clear
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::empty
- CONCURRENT_VECTOR/concurrency::concurrent_vector::end
- CONCURRENT_VECTOR/concurrency::concurrent_vector::front
- CONCURRENT_VECTOR/concurrency::concurrent_vector::get_allocator
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_by
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_to_at_least
- CONCURRENT_VECTOR/concurrency::concurrent_vector::max_size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::push_back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::reserve
- CONCURRENT_VECTOR/concurrency::concurrent_vector::resize
- CONCURRENT_VECTOR/concurrency::concurrent_vector::shrink_to_fit
- CONCURRENT_VECTOR/concurrency::concurrent_vector::size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::swap
dev_langs:
- C++
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe5ac6d819ed6f068095fe2abda5363686ed7dbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117424"
---
# <a name="concurrentvector-class"></a>Classe concurrent_vector
La classe `concurrent_vector` est une classe de conteneur de séquence qui autorise un accès aléatoire à tout élément. Elle permet les opérations d'ajout d'accès concurrentiel sécurisé, d'accès à un élément, d'accès à un itérateur et de traversée d'itérateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
 private details::_Concurrent_vector_base_v4;
```  
  
#### <a name="parameters"></a>Paramètres  
*T*<br/>
Le type de données des éléments à stocker dans le vecteur.  
  
*_Ax*<br/>
Type qui représente l’objet allocateur stocké qui encapsule des informations détaillées sur l’allocation et la désallocation de mémoire pour le vecteur simultané. Cet argument est facultatif et sa valeur par défaut est `allocator<T>`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`allocator_type`|Type qui représente la classe d’allocateur pour le vecteur simultané.|  
|`const_iterator`|Type qui fournit un itérateur à accès aléatoire qui peut lire un `const` élément dans un vecteur simultané.|  
|`const_pointer`|Un type qui fournit un pointeur vers un `const` élément dans un vecteur simultané.|  
|`const_reference`|Type qui fournit une référence à un `const` élément stocké dans un vecteur simultané pour la lecture et l’exécution `const` operations.|  
|`const_reverse_iterator`|Type qui fournit un itérateur à accès aléatoire qui peut lire un `const` élément dans le vecteur simultané.|  
|`difference_type`|Type qui fournit la distance signée entre deux éléments dans un vecteur simultané.|  
|`iterator`|Type qui fournit un itérateur à accès aléatoire qui peut lire n’importe quel élément dans un vecteur simultané. Modification d’un élément à l’aide de l’itérateur n’est pas concurrentiel.|  
|`pointer`|Type qui fournit un pointeur vers un élément dans un vecteur simultané.|  
|`reference`|Type qui fournit une référence à un élément stocké dans un vecteur simultané.|  
|`reverse_iterator`|Type qui fournit un itérateur à accès aléatoire qui peut lire n’importe quel élément d’un vecteur inversé simultané. Modification d’un élément à l’aide de l’itérateur n’est pas concurrentiel.|  
|`size_type`|Type qui compte le nombre d’éléments dans un vecteur simultané.|  
|`value_type`|Type qui représente le type de données stocké dans un vecteur simultané.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[concurrent_vector](#ctor)|Surchargé. Construit un vecteur simultané.|  
|[~ concurrent_vector, destructeur](#dtor)|Efface tous les éléments et détruit ce vecteur simultané.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[assign](#assign)|Surchargé. Efface les éléments du vecteur simultané et lui attribue `_N` copies de `_Item`, ou les valeurs spécifiées par la plage d’itérateurs [ `_Begin`, `_End`). Cette méthode n’est pas concurrentiel.|  
|[at](#at)|Surchargé. Fournit l’accès à l’élément à l’index donné dans le vecteur simultané. Cette méthode est concurrentiel pour les opérations de lecture, ainsi que pendant l’augmentation du vecteur, tant que vous avez vérifié que la valeur `_Index` est inférieure à la taille du vecteur simultané.|  
|[back](#back)|Surchargé. Retourne une référence ou une `const` faire référence au dernier élément dans le vecteur simultané. Si le vecteur simultané est vide, la valeur de retour est indéfinie. Cette méthode est concurrentiel.|  
|[begin](#begin)|Surchargé. Retourne un itérateur de type `iterator` ou `const_iterator` au début du vecteur simultané. Cette méthode est concurrentiel.|  
|[capacity](#capacity)|Retourne la taille maximale que le vecteur simultané peut atteindre sans avoir à allouer davantage de mémoire. Cette méthode est concurrentiel.|  
|[cbegin](#cbegin)|Retourne un itérateur de type `const_iterator` au début du vecteur simultané. Cette méthode est concurrentiel.|  
|[cend](#cend)|Retourne un itérateur de type `const_iterator` à la fin du vecteur simultané. Cette méthode est concurrentiel.|  
|[clear](#clear)|Efface tous les éléments dans le vecteur simultané. Cette méthode n’est pas concurrentiel.|  
|[crbegin](#crbegin)|Retourne un itérateur de type `const_reverse_iterator` au début du vecteur simultané. Cette méthode est concurrentiel.|  
|[crend](#crend)|Retourne un itérateur de type `const_reverse_iterator` à la fin du vecteur simultané. Cette méthode est concurrentiel.|  
|[empty](#empty)|Teste si le vecteur simultané est vide au moment où cette méthode est appelée. Cette méthode est concurrentiel.|  
|[end](#end)|Surchargé. Retourne un itérateur de type `iterator` ou `const_iterator` à la fin du vecteur simultané. Cette méthode est concurrentiel.|  
|[front](#front)|Surchargé. Retourne une référence ou une `const` référence au premier élément dans le vecteur simultané. Si le vecteur simultané est vide, la valeur de retour est indéfinie. Cette méthode est concurrentiel.|  
|[get_allocator](#get_allocator)|Retourne une copie de l’allocateur utilisé pour construire le vecteur simultané. Cette méthode est concurrentiel.|  
|[grow_by](#grow_by)|Surchargé. Augmente ce vecteur simultané par `_Delta` éléments. Cette méthode est concurrentiel.|  
|[grow_to_at_least](#grow_to_at_least)|Augmente ce vecteur simultané jusqu'à ce qu’elle ait au moins `_N` éléments. Cette méthode est concurrentiel.|  
|[max_size](#max_size)|Retourne le nombre maximal d’éléments que le vecteur simultané peut contenir. Cette méthode est concurrentiel.|  
|[push_back](#push_back)|Surchargé. Ajoute l’élément donné à la fin du vecteur simultané. Cette méthode est concurrentiel.|  
|[rbegin](#rbegin)|Surchargé. Retourne un itérateur de type `reverse_iterator` ou `const_reverse_iterator` au début du vecteur simultané. Cette méthode est concurrentiel.|  
|[rend](#rend)|Surchargé. Retourne un itérateur de type `reverse_iterator` ou `const_reverse_iterator` à la fin du vecteur simultané. Cette méthode est concurrentiel.|  
|[reserve](#reserve)|Alloue suffisamment d’espace pour augmenter le vecteur simultané à taille `_N` sans avoir à allouer davantage de mémoire plus tard. Cette méthode n’est pas concurrentiel.|  
|[resize](#resize)|Surchargé. Modifie la taille du vecteur simultané à la taille demandée, en supprimant ou en ajoutant des éléments en fonction des besoins. Cette méthode n’est pas concurrentiel.|  
|[shrink_to_fit](#shrink_to_fit)|Compacte la représentation interne du vecteur simultané pour réduire la fragmentation et optimiser l’utilisation de la mémoire. Cette méthode n’est pas concurrentiel.|  
|[size](#size)|Retourne le nombre d’éléments dans le vecteur simultané. Cette méthode est concurrentiel.|  
|[swap](#swap)|Échange le contenu de deux vecteurs simultanés. Cette méthode n’est pas concurrentiel.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator[]](#operator_at)|Surchargé. Fournit l’accès à l’élément à l’index donné dans le vecteur simultané. Cette méthode est concurrentiel pour les opérations de lecture, ainsi que pendant l’augmentation du vecteur, tant que vous avez vérifié que la valeur `_Index` est inférieure à la taille du vecteur simultané.|  
|[operator=](#operator_eq)|Surchargé. Assigne le contenu d’un autre `concurrent_vector` objet à celui-ci. Cette méthode n’est pas concurrentiel.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la `concurrent_vector` de classe, consultez [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `_Concurrent_vector_base_v4`  
  
 `_Allocator_base`  
  
 `concurrent_vector`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** concurrent_vector.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="assign"></a> Affecter 

 Efface les éléments du vecteur simultané et lui attribue `_N` copies de `_Item`, ou les valeurs spécifiées par la plage d’itérateurs [ `_Begin`, `_End`). Cette méthode n’est pas concurrentiel.  
  
```
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```  
  
### <a name="parameters"></a>Paramètres  
*_InputIterator*<br/>
Le type de l’itérateur spécifié.  
  
*_N*<br/>
Le nombre d’éléments à copier dans le vecteur simultané.  
  
*É_lément*<br/>
Référence à une valeur utilisée pour remplir le vecteur simultané.  
  
*_Commencer l'*<br/>
Un itérateur au premier élément de la plage source.  
  
*_Mettre fin à*<br/>
Un itérateur vers l’élément suivant le dernier élément de la plage source.  
  
### <a name="remarks"></a>Notes  
 `assign` n’est pas concurrentiel. Vous devez vous assurer qu’aucun autre thread n’est appel de méthodes sur le vecteur simultané lorsque vous appelez cette méthode.  
  
##  <a name="at"></a> à 

 Fournit l’accès à l’élément à l’index donné dans le vecteur simultané. Cette méthode est concurrentiel pour les opérations de lecture, ainsi que pendant l’augmentation du vecteur, tant que vous avez vérifié que la valeur `_Index` est inférieure à la taille du vecteur simultané.  
  
```
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```  
  
### <a name="parameters"></a>Paramètres  
*_Index*<br/>
L’index de l’élément à récupérer.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à l’élément à l’index donné.  
  
### <a name="remarks"></a>Notes  
 La version de la fonction `at` qui retourne un non - `const` référence ne peut pas être utilisée pour écrire simultanément dans l’élément à partir de différents threads. Un objet de synchronisation différent doit être utilisé pour synchroniser la lecture simultanée et d’opérations d’écriture sur le même élément de données.  
  
 La méthode lève `out_of_range` si `_Index` est supérieur ou égal à la taille du vecteur simultané, et `range_error` si l’index est pour une partie rompue du vecteur. Pour plus d’informations sur la façon dont un vecteur peut être endommagé, consultez [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
##  <a name="back"></a> Précédent 

 Retourne une référence ou une `const` faire référence au dernier élément dans le vecteur simultané. Si le vecteur simultané est vide, la valeur de retour est indéfinie. Cette méthode est concurrentiel.  
  
```
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence ou une `const` faire référence au dernier élément dans le vecteur simultané.  
  
##  <a name="begin"></a> commencer 

 Retourne un itérateur de type `iterator` ou `const_iterator` au début du vecteur simultané. Cette méthode est concurrentiel.  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur de type `iterator` ou `const_iterator` au début du vecteur simultané.  
  
##  <a name="capacity"></a> capacité 

 Retourne la taille maximale que le vecteur simultané peut atteindre sans avoir à allouer davantage de mémoire. Cette méthode est concurrentiel.  
  
```
size_type capacity() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 La taille maximale que le vecteur simultané peut atteindre sans avoir à allouer davantage de mémoire.  
  
### <a name="remarks"></a>Notes  
 Contrairement à une bibliothèque Standard C++ `vector`, un `concurrent_vector` objet ne déplace pas les éléments existants s’il alloue plus de mémoire.  
  
##  <a name="cbegin"></a> cbegin 

 Retourne un itérateur de type `const_iterator` au début du vecteur simultané. Cette méthode est concurrentiel.  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur de type `const_iterator` au début du vecteur simultané.  
  
##  <a name="cend"></a> cend 

 Retourne un itérateur de type `const_iterator` à la fin du vecteur simultané. Cette méthode est concurrentiel.  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur de type `const_iterator` à la fin du vecteur simultané.  
  
##  <a name="clear"></a> Effacer 

 Efface tous les éléments dans le vecteur simultané. Cette méthode n’est pas concurrentiel.  
  
```
void clear();
```  
  
### <a name="remarks"></a>Notes  
 `clear` n’est pas concurrentiel. Vous devez vous assurer qu’aucun autre thread n’est appel de méthodes sur le vecteur simultané lorsque vous appelez cette méthode. `clear` ne libère pas de tableaux internes. Pour libérer des tableaux internes, appelez la fonction `shrink_to_fit` après `clear`.  
  
##  <a name="ctor"></a> concurrent_vector 

 Construit un vecteur simultané.  
  
```
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```  
  
### <a name="parameters"></a>Paramètres  
*M*<br/>
Le type d’allocateur du vecteur source.  
  
*_InputIterator*<br/>
Type de l'itérateur d'entrée.  
  
*_Al*<br/>
Classe allocator à utiliser avec cet objet.  
  
*_Vector*<br/>
La source `concurrent_vector` objet à copier ou déplacer des éléments à partir de.  
  
*_N*<br/>
La capacité initiale de la `concurrent_vector` objet.  
  
*É_lément*<br/>
La valeur des éléments dans l’objet construit.  
  
*_Commencer l'*<br/>
Position du premier élément dans la plage d'éléments à copier.  
  
*_Mettre fin à*<br/>
Position du premier élément suivant la fin de la plage d'éléments à copier.  
  
### <a name="remarks"></a>Notes  
 Tous les constructeurs stockent un objet allocateur `_Al` et initialisent le vecteur.  
  
 Le premier constructeur, spécifiez un vecteur initial vide et spécifie explicitement le type d’allocateur. à utiliser.  
  
 Les deuxième et troisième constructeurs spécifient une copie du vecteur simultané `_Vector`.  
  
 Le quatrième constructeur spécifie un déplacement du vecteur simultané `_Vector`.  
  
 Le cinquième constructeur spécifie une répétition d’un nombre spécifié ( `_N`) d’éléments de la valeur par défaut pour la classe `T`.  
  
 Le sixième constructeur spécifie une répétition des ( `_N`) éléments ayant la valeur `_Item`.  
  
 Le dernier constructeur spécifie les valeurs fournies par la plage d’itérateurs [ `_Begin`, `_End`).  
  
##  <a name="dtor"></a> ~concurrent_vector 

 Efface tous les éléments et détruit ce vecteur simultané.  
  
```
~concurrent_vector();
```  
  
##  <a name="crbegin"></a> crbegin 

 Retourne un itérateur de type `const_reverse_iterator` au début du vecteur simultané. Cette méthode est concurrentiel.  
  
```
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur de type `const_reverse_iterator` au début du vecteur simultané.  
  
##  <a name="crend"></a> crend 

 Retourne un itérateur de type `const_reverse_iterator` à la fin du vecteur simultané. Cette méthode est concurrentiel.  
  
```
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur de type `const_reverse_iterator` à la fin du vecteur simultané.  
  
##  <a name="empty"></a> vide 

 Teste si le vecteur simultané est vide au moment où cette méthode est appelée. Cette méthode est concurrentiel.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le vecteur était vide au moment où la fonction a été appelée, `false` dans le cas contraire.  
  
##  <a name="end"></a> fin 

 Retourne un itérateur de type `iterator` ou `const_iterator` à la fin du vecteur simultané. Cette méthode est concurrentiel.  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur de type `iterator` ou `const_iterator` à la fin du vecteur simultané.  
  
##  <a name="front"></a> front 

 Retourne une référence ou une `const` référence au premier élément dans le vecteur simultané. Si le vecteur simultané est vide, la valeur de retour est indéfinie. Cette méthode est concurrentiel.  
  
```
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence ou une `const` référence au premier élément dans le vecteur simultané.  
  
##  <a name="get_allocator"></a> get_allocator 

 Retourne une copie de l’allocateur utilisé pour construire le vecteur simultané. Cette méthode est concurrentiel.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une copie de l’allocateur utilisé pour construire le `concurrent_vector` objet.  
  
##  <a name="grow_by"></a> grow_by 

 Augmente ce vecteur simultané par `_Delta` éléments. Cette méthode est concurrentiel.  
  
```
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```  
  
### <a name="parameters"></a>Paramètres  
*_Delta*<br/>
Le nombre d’éléments à ajouter à l’objet.  
  
*É_lément*<br/>
La valeur pour initialiser les nouveaux éléments avec.  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur au premier élément ajouté.  
  
### <a name="remarks"></a>Notes  
 Si `_Item` n’est pas spécifié, les nouveaux éléments sont construits par défaut.  
  
##  <a name="grow_to_at_least"></a> grow_to_at_least 

 Augmente ce vecteur simultané jusqu'à ce qu’elle ait au moins `_N` éléments. Cette méthode est concurrentiel.  
  
```
iterator grow_to_at_least(size_type _N);
```  
  
### <a name="parameters"></a>Paramètres  
*_N*<br/>
La nouvelle taille minimale pour le `concurrent_vector` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur qui pointe vers le début de la séquence ajoutée, ou à l’élément à l’index `_N` si aucun élément ont été ajoutés.  
  
##  <a name="max_size"></a> max_size 

 Retourne le nombre maximal d’éléments que le vecteur simultané peut contenir. Cette méthode est concurrentiel.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre maximal d’éléments le `concurrent_vector` objet peut contenir.  
  
##  <a name="operator_eq"></a> opérateur = 

 Assigne le contenu d’un autre `concurrent_vector` objet à celui-ci. Cette méthode n’est pas concurrentiel.  
  
```
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```  
  
### <a name="parameters"></a>Paramètres  
*M*<br/>
Le type d’allocateur du vecteur source.  
  
*_Vector*<br/>
Objet `concurrent_vector` source.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à cet `concurrent_vector` objet.  
  
##  <a name="operator_at"></a> operator] 

 Fournit l’accès à l’élément à l’index donné dans le vecteur simultané. Cette méthode est concurrentiel pour les opérations de lecture, ainsi que pendant l’augmentation du vecteur, tant que vous avez vérifié que la valeur `_Index` est inférieure à la taille du vecteur simultané.  
  
```
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```  
  
### <a name="parameters"></a>Paramètres  
*_Index*<br/>
L’index de l’élément à récupérer.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à l’élément à l’index donné.  
  
### <a name="remarks"></a>Notes  
 La version de `operator []` qui retourne un non - `const` référence ne peut pas être utilisée pour écrire simultanément dans l’élément à partir de différents threads. Un objet de synchronisation différent doit être utilisé pour synchroniser la lecture simultanée et d’opérations d’écriture sur le même élément de données.  
  
 Aucune vérification est effectuée pour vous assurer que des limites `_Index` est un index valide dans le vecteur simultané.  
  
##  <a name="push_back"></a> push_back 

 Ajoute l’élément donné à la fin du vecteur simultané. Cette méthode est concurrentiel.  
  
```
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```  
  
### <a name="parameters"></a>Paramètres  
*É_lément*<br/>
La valeur à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur vers l’élément ajouté.  
  
##  <a name="rbegin"></a> rbegin 

 Retourne un itérateur de type `reverse_iterator` ou `const_reverse_iterator` au début du vecteur simultané. Cette méthode est concurrentiel.  
  
```
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur de type `reverse_iterator` ou `const_reverse_iterator` au début du vecteur simultané.  
  
##  <a name="rend"></a> rend 

 Retourne un itérateur de type `reverse_iterator` ou `const_reverse_iterator` à la fin du vecteur simultané. Cette méthode est concurrentiel.  
  
```
reverse_iterator rend();

const_reverse_iterator rend() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur de type `reverse_iterator` ou `const_reverse_iterator` à la fin du vecteur simultané.  
  
##  <a name="reserve"></a> réserver 

 Alloue suffisamment d’espace pour augmenter le vecteur simultané à taille `_N` sans avoir à allouer davantage de mémoire plus tard. Cette méthode n’est pas concurrentiel.  
  
```
void reserve(size_type _N);
```  
  
### <a name="parameters"></a>Paramètres  
*_N*<br/>
Le nombre d’éléments à réserver pour un espace.  
  
### <a name="remarks"></a>Notes  
 `reserve` n’est pas concurrentiel. Vous devez vous assurer qu’aucun autre thread n’est appel de méthodes sur le vecteur simultané lorsque vous appelez cette méthode. La capacité du vecteur simultané après que la méthode peut être plus grande que la réservation demandée.  
  
##  <a name="resize"></a> redimensionner 

 Modifie la taille du vecteur simultané à la taille demandée, en supprimant ou en ajoutant des éléments en fonction des besoins. Cette méthode n’est pas concurrentiel.  
  
```
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```  
  
### <a name="parameters"></a>Paramètres  
*_N*<br/>
La nouvelle taille de la concurrent_vector.  
  
*Val*<br/>
La valeur des nouveaux éléments ajoutés au vecteur si la nouvelle taille est supérieure à la taille d’origine. Si la valeur est omise, les nouveaux objets sont affectés à la valeur par défaut pour leur type.  
  
### <a name="remarks"></a>Notes  
 Si la taille du conteneur est inférieure à la taille demandée, les éléments sont ajoutés au vecteur jusqu'à ce qu’il atteigne la taille demandée. Si la taille du conteneur est supérieure à la taille demandée, les éléments le plus proche de la fin du conteneur sont supprimés jusqu'à ce que le conteneur atteigne la taille `_N`. Si la taille actuelle du conteneur est égale à la taille demandée, aucune action n'est effectuée.  
  
 `resize` n’est pas l’accès concurrentiel sécurisé. Vous devez vous assurer qu’aucun autre thread n’est appel de méthodes sur le vecteur simultané lorsque vous appelez cette méthode.  
  
##  <a name="shrink_to_fit"></a> shrink_to_fit 

 Compacte la représentation interne du vecteur simultané pour réduire la fragmentation et optimiser l’utilisation de la mémoire. Cette méthode n’est pas concurrentiel.  
  
```
void shrink_to_fit();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode sera en interne réallouez éléments du déplacement de mémoire, invalidant tous les itérateurs. `shrink_to_fit` n’est pas concurrentiel. Vous devez vous assurer qu’aucun autre thread n’est appel de méthodes sur le vecteur simultané lorsque vous appelez cette fonction.  
  
##  <a name="size"></a> Taille 

 Retourne le nombre d’éléments dans le vecteur simultané. Cette méthode est concurrentiel.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans cette `concurrent_vector` objet.  
  
### <a name="remarks"></a>Notes  
 La taille retournée est garantie pour inclure tous les éléments ajoutés par les appels à la fonction `push_back`, ou d’augmenter les opérations terminées avant d’appeler cette méthode. Toutefois, il peut également inclure des éléments qui sont allouées, mais toujours en cours de construction par les appels simultanés aux méthodes de croissance.  
  
##  <a name="swap"></a> échange 

 Échange le contenu de deux vecteurs simultanés. Cette méthode n’est pas concurrentiel.  
  
```
void swap(concurrent_vector& _Vector);
```  
  
### <a name="parameters"></a>Paramètres  
*_Vector*<br/>
Le `concurrent_vector` objet échanger le contenu avec.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [Conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md)



