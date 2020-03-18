---
title: Classe concurrent_vector
ms.date: 11/04/2016
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
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
ms.openlocfilehash: 002f1e3f691de3315810efed8f7d8f6c547cf653
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417249"
---
# <a name="concurrent_vector-class"></a>Classe concurrent_vector

La classe `concurrent_vector` est une classe de conteneur de séquence qui autorise un accès aléatoire à tout élément. Elle permet les opérations d'ajout d'accès concurrentiel sécurisé, d'accès à un élément, d'accès à un itérateur et de traversée d'itérateur. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données des éléments à stocker dans le vecteur.

*_Ax*<br/>
Type qui représente l’objet allocateur stocké qui encapsule des détails sur l’allocation et la désallocation de mémoire pour le vecteur simultané. Cet argument est facultatif et sa valeur par défaut est `allocator<T>`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`allocator_type`|Type qui représente la classe Allocator pour le vecteur simultané.|
|`const_iterator`|Type qui fournit un itérateur à accès aléatoire capable de lire un élément `const` dans un vecteur simultané.|
|`const_pointer`|Type qui fournit un pointeur vers un élément `const` dans un vecteur simultané.|
|`const_reference`|Type qui fournit une référence à un élément `const` stocké dans un vecteur simultané pour la lecture et l’exécution d’opérations de `const`.|
|`const_reverse_iterator`|Type qui fournit un itérateur à accès aléatoire qui peut lire n’importe quel élément `const` dans le vecteur simultané.|
|`difference_type`|Type qui fournit la distance signée entre deux éléments dans un vecteur simultané.|
|`iterator`|Type qui fournit un itérateur à accès aléatoire capable de lire un élément dans un vecteur simultané. La modification d’un élément à l’aide de l’itérateur n’est pas sécurisée pour la concurrence.|
|`pointer`|Type qui fournit un pointeur vers un élément d’un vecteur simultané.|
|`reference`|Type qui fournit une référence à un élément stocké dans un vecteur simultané.|
|`reverse_iterator`|Type qui fournit un itérateur à accès aléatoire capable de lire un élément dans un vecteur simultané inversé. La modification d’un élément à l’aide de l’itérateur n’est pas sécurisée pour la concurrence.|
|`size_type`|Type qui compte le nombre d’éléments dans un vecteur simultané.|
|`value_type`|Type qui représente le type de données stocké dans un vecteur simultané.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[concurrent_vector](#ctor)|Surchargé. Construit un vecteur simultané.|
|[Destructeur ~ concurrent_vector](#dtor)|Efface tous les éléments et détruit ce vecteur simultané.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[assign](#assign)|Surchargé. Efface les éléments du vecteur simultané et les assigne `_N` des copies de `_Item`ou des valeurs spécifiées par la plage d’itérateurs [`_Begin`, `_End`). Cette méthode n’est pas sécurisée pour la concurrence.|
|[at](#at)|Surchargé. Fournit l’accès à l’élément à l’index donné dans le vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel pour les opérations de lecture, tout en augmentant le vecteur, à condition que vous ayez vérifié que la valeur `_Index` est inférieure à la taille du vecteur simultané.|
|[back](#back)|Surchargé. Retourne une référence ou une référence `const` au dernier élément du vecteur simultané. Si le vecteur simultané est vide, la valeur de retour n’est pas définie. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[begin](#begin)|Surchargé. Retourne un itérateur de type `iterator` ou `const_iterator` au début du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[capacité](#capacity)|Retourne la taille maximale que peut atteindre le vecteur simultané sans avoir à allouer davantage de mémoire. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[cbegin](#cbegin)|Retourne un itérateur de type `const_iterator` au début du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[cend](#cend)|Retourne un itérateur de type `const_iterator` à la fin du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[clear](#clear)|Efface tous les éléments dans le vecteur simultané. Cette méthode n’est pas sécurisée pour la concurrence.|
|[crbegin](#crbegin)|Retourne un itérateur de type `const_reverse_iterator` au début du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[crend](#crend)|Retourne un itérateur de type `const_reverse_iterator` à la fin du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[empty](#empty)|Teste si le vecteur simultané est vide au moment où cette méthode est appelée. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[end](#end)|Surchargé. Retourne un itérateur de type `iterator` ou `const_iterator` à la fin du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[front](#front)|Surchargé. Retourne une référence ou une `const` référence au premier élément dans le vecteur simultané. Si le vecteur simultané est vide, la valeur de retour n’est pas définie. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[get_allocator](#get_allocator)|Retourne une copie de l’allocateur utilisé pour construire le vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[grow_by](#grow_by)|Surchargé. Augmente ce vecteur simultané en `_Delta` éléments. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[grow_to_at_least](#grow_to_at_least)|Augmente ce vecteur simultané jusqu’à ce qu’il ait au moins `_N` éléments. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[max_size](#max_size)|Retourne le nombre maximal d’éléments que le vecteur simultané peut contenir. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[push_back](#push_back)|Surchargé. Ajoute l’élément donné à la fin du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[rbegin](#rbegin)|Surchargé. Retourne un itérateur de type `reverse_iterator` ou `const_reverse_iterator` au début du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[rend](#rend)|Surchargé. Retourne un itérateur de type `reverse_iterator` ou `const_reverse_iterator` à la fin du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[reserve](#reserve)|Alloue suffisamment d’espace pour augmenter la taille du vecteur simultané `_N` sans avoir à allouer plus de mémoire ultérieurement. Cette méthode n’est pas sécurisée pour la concurrence.|
|[resize](#resize)|Surchargé. Modifie la taille du vecteur simultané à la taille demandée, en supprimant ou en ajoutant des éléments selon les besoins. Cette méthode n’est pas sécurisée pour la concurrence.|
|[shrink_to_fit](#shrink_to_fit)|Compacte la représentation interne du vecteur simultané pour réduire la fragmentation et optimiser l’utilisation de la mémoire. Cette méthode n’est pas sécurisée pour la concurrence.|
|[size](#size)|Retourne le nombre d’éléments dans le vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[swap](#swap)|Échange le contenu de deux vecteurs simultanés. Cette méthode n’est pas sécurisée pour la concurrence.|

### <a name="public-operators"></a>Opérateurs publics

|Name|Description|
|----------|-----------------|
|[operator\[\]](#operator_at)|Surchargé. Fournit l’accès à l’élément à l’index donné dans le vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel pour les opérations de lecture, tout en augmentant le vecteur, à condition que vous ayez vérifié que la valeur `_Index` est inférieure à la taille du vecteur simultané.|
|[operator=](#operator_eq)|Surchargé. Assigne le contenu d’un autre objet `concurrent_vector` à celui-ci. Cette méthode n’est pas sécurisée pour la concurrence.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur la classe `concurrent_vector`, consultez [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>Spécifications

**En-tête :** concurrent_vector. h

**Espace de noms :** concurrency

## <a name="assign"></a>assignés

Efface les éléments du vecteur simultané et les assigne `_N` des copies de `_Item`ou des valeurs spécifiées par la plage d’itérateurs [`_Begin`, `_End`). Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>Paramètres

*_InputIterator*<br/>
Type de l’itérateur spécifié.

*_N*<br/>
Nombre d’éléments à copier dans le vecteur simultané.

*_Item*<br/>
Référence à une valeur utilisée pour remplir le vecteur simultané.

*_Begin*<br/>
Itérateur vers le premier élément de la plage source.

*_End*<br/>
Itérateur à un après le dernier élément de la plage source.

### <a name="remarks"></a>Notes

`assign` n’est pas sécurisé pour l’accès concurrentiel. Vous devez vous assurer qu’aucun autre thread n’appelle de méthodes sur le vecteur simultané quand vous appelez cette méthode.

## <a name="at"></a>à

Fournit l’accès à l’élément à l’index donné dans le vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel pour les opérations de lecture, tout en augmentant le vecteur, à condition que vous ayez vérifié que la valeur `_Index` est inférieure à la taille du vecteur simultané.

```cpp
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index de l’élément à récupérer.

### <a name="return-value"></a>Valeur de retour

Référence à l’élément à l’index donné.

### <a name="remarks"></a>Notes

La version de la fonction `at` qui retourne une référence non `const` ne peut pas être utilisée pour écrire simultanément dans l’élément à partir de différents threads. Un objet de synchronisation différent doit être utilisé pour synchroniser les opérations de lecture et d’écriture simultanées avec le même élément de données.

La méthode lève `out_of_range` si `_Index` est supérieure ou égale à la taille du vecteur simultané, et `range_error` si l’index est pour une partie cassée du vecteur. Pour plus d’informations sur la façon dont un vecteur peut être endommagé, consultez [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="back"></a>Précédent

Retourne une référence ou une référence `const` au dernier élément du vecteur simultané. Si le vecteur simultané est vide, la valeur de retour n’est pas définie. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence ou une `const` référence au dernier élément du vecteur simultané.

## <a name="begin"></a>commencer

Retourne un itérateur de type `iterator` ou `const_iterator` au début du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur de type `iterator` ou `const_iterator` au début du vecteur simultané.

## <a name="capacity"></a>maximale

Retourne la taille maximale que peut atteindre le vecteur simultané sans avoir à allouer davantage de mémoire. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Valeur de retour

Taille maximale que le vecteur simultané peut atteindre sans avoir à allouer davantage de mémoire.

### <a name="remarks"></a>Notes

Contrairement à C++ une bibliothèque standard `vector`, un objet `concurrent_vector` ne déplace pas les éléments existants s’il alloue plus de mémoire.

## <a name="cbegin"></a>cbegin

Retourne un itérateur de type `const_iterator` au début du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur de type `const_iterator` au début du vecteur simultané.

## <a name="cend"></a>CEND

Retourne un itérateur de type `const_iterator` à la fin du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur de type `const_iterator` à la fin du vecteur simultané.

## <a name="clear"></a>effacé

Efface tous les éléments dans le vecteur simultané. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
void clear();
```

### <a name="remarks"></a>Notes

`clear` n’est pas sécurisé pour l’accès concurrentiel. Vous devez vous assurer qu’aucun autre thread n’appelle de méthodes sur le vecteur simultané quand vous appelez cette méthode. `clear` ne libère pas les tableaux internes. Pour libérer des tableaux internes, appelez la fonction `shrink_to_fit` après `clear`.

## <a name="ctor"></a>concurrent_vector

Construit un vecteur simultané.

```cpp
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
Type d’allocateur du vecteur source.

*_InputIterator*<br/>
Type de l'itérateur d'entrée.

*_Al*<br/>
Classe allocator à utiliser avec cet objet.

*_Vector*<br/>
Objet `concurrent_vector` source à partir duquel copier ou déplacer des éléments.

*_N*<br/>
Capacité initiale de l’objet `concurrent_vector`.

*_Item*<br/>
Valeur des éléments de l’objet construit.

*_Begin*<br/>
Position du premier élément dans la plage d'éléments à copier.

*_End*<br/>
Position du premier élément suivant la fin de la plage d'éléments à copier.

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un objet allocateur `_Al` et initialisent le vecteur.

Le premier constructeur spécifie un vecteur initial vide et spécifie explicitement le type d’allocateur. à utiliser.

Les deuxième et troisième constructeurs spécifient une copie du vecteur simultané `_Vector`.

Le quatrième constructeur spécifie un déplacement du vecteur simultané `_Vector`.

Le cinquième constructeur spécifie une répétition d’un nombre spécifié (`_N`) d’éléments de la valeur par défaut pour la classe `T`.

Le sixième constructeur spécifie une répétition d’éléments (`_N`) de valeur `_Item`.

Le dernier constructeur spécifie les valeurs fournies par la plage d’itérateurs [`_Begin`, `_End`).

## <a name="dtor"></a>~ concurrent_vector

Efface tous les éléments et détruit ce vecteur simultané.

```cpp
~concurrent_vector();
```

## <a name="crbegin"></a>crbegin

Retourne un itérateur de type `const_reverse_iterator` au début du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur de type `const_reverse_iterator` au début du vecteur simultané.

## <a name="crend"></a>crend

Retourne un itérateur de type `const_reverse_iterator` à la fin du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur de type `const_reverse_iterator` à la fin du vecteur simultané.

## <a name="empty"></a>vidé

Teste si le vecteur simultané est vide au moment où cette méthode est appelée. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le vecteur est vide au moment où la fonction a été appelée ; sinon, **false** .

## <a name="end"></a>effet

Retourne un itérateur de type `iterator` ou `const_iterator` à la fin du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur de type `iterator` ou `const_iterator` à la fin du vecteur simultané.

## <a name="front"></a>frontal

Retourne une référence ou une `const` référence au premier élément dans le vecteur simultané. Si le vecteur simultané est vide, la valeur de retour n’est pas définie. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence ou une `const` référence au premier élément dans le vecteur simultané.

## <a name="get_allocator"></a>get_allocator

Retourne une copie de l’allocateur utilisé pour construire le vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valeur de retour

Copie de l’allocateur utilisé pour construire l’objet `concurrent_vector`.

## <a name="grow_by"></a>grow_by

Augmente ce vecteur simultané en `_Delta` éléments. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>Paramètres

*_Delta*<br/>
Nombre d’éléments à ajouter à l’objet.

*_Item*<br/>
Valeur avec laquelle initialiser les nouveaux éléments.

### <a name="return-value"></a>Valeur de retour

Itérateur vers le premier élément ajouté.

### <a name="remarks"></a>Notes

Si `_Item` n’est pas spécifié, les nouveaux éléments sont construits par défaut.

## <a name="grow_to_at_least"></a>grow_to_at_least

Augmente ce vecteur simultané jusqu’à ce qu’il ait au moins `_N` éléments. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>Paramètres

*_N*<br/>
Nouvelle taille minimale pour l’objet `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

Itérateur qui pointe vers le début de la séquence ajoutée, ou vers l’élément au niveau de l’index `_N` si aucun élément n’a été ajouté.

## <a name="max_size"></a>max_size

Retourne le nombre maximal d’éléments que le vecteur simultané peut contenir. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre maximal d’éléments que l’objet `concurrent_vector` peut contenir.

## <a name="operator_eq"></a>opérateur =

Assigne le contenu d’un autre objet `concurrent_vector` à celui-ci. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
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
Type d’allocateur du vecteur source.

*_Vector*<br/>
Objet `concurrent_vector` source.

### <a name="return-value"></a>Valeur de retour

Référence à cet objet `concurrent_vector`.

## <a name="operator_at"></a>[], opérateur

Fournit l’accès à l’élément à l’index donné dans le vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel pour les opérations de lecture, tout en augmentant le vecteur, à condition que vous ayez vérifié que la valeur `_Index` est inférieure à la taille du vecteur simultané.

```cpp
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index de l’élément à récupérer.

### <a name="return-value"></a>Valeur de retour

Référence à l’élément à l’index donné.

### <a name="remarks"></a>Notes

La version de `operator []` qui retourne une référence non `const` ne peut pas être utilisée pour écrire simultanément dans l’élément à partir de différents threads. Un objet de synchronisation différent doit être utilisé pour synchroniser les opérations de lecture et d’écriture simultanées avec le même élément de données.

Aucune vérification des limites n’est effectuée pour s’assurer que `_Index` est un index valide dans le vecteur simultané.

## <a name="push_back"></a>push_back

Ajoute l’élément donné à la fin du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>Paramètres

*_Item*<br/>
Valeur à ajouter.

### <a name="return-value"></a>Valeur de retour

Itérateur à ajouter à l’élément.

## <a name="rbegin"></a>rbegin

Retourne un itérateur de type `reverse_iterator` ou `const_reverse_iterator` au début du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur de type `reverse_iterator` ou `const_reverse_iterator` au début du vecteur simultané.

## <a name="rend"></a>rend

Retourne un itérateur de type `reverse_iterator` ou `const_reverse_iterator` à la fin du vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur de type `reverse_iterator` ou `const_reverse_iterator` à la fin du vecteur simultané.

## <a name="reserve"></a>réserver

Alloue suffisamment d’espace pour augmenter la taille du vecteur simultané `_N` sans avoir à allouer plus de mémoire ultérieurement. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
void reserve(size_type _N);
```

### <a name="parameters"></a>Paramètres

*_N*<br/>
Nombre d’éléments pour lesquels réserver de l’espace.

### <a name="remarks"></a>Notes

`reserve` n’est pas sécurisé pour l’accès concurrentiel. Vous devez vous assurer qu’aucun autre thread n’appelle de méthodes sur le vecteur simultané quand vous appelez cette méthode. La capacité du vecteur simultané après le retour de la méthode peut être supérieure à la réservation demandée.

## <a name="resize"></a>redimensionner

Modifie la taille du vecteur simultané à la taille demandée, en supprimant ou en ajoutant des éléments selon les besoins. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```

### <a name="parameters"></a>Paramètres

*_N*<br/>
Nouvelle taille du concurrent_vector.

*val*<br/>
Valeur des nouveaux éléments ajoutés au vecteur si la nouvelle taille est supérieure à la taille d’origine. Si la valeur est omise, la valeur par défaut de son type est assignée aux nouveaux objets.

### <a name="remarks"></a>Notes

Si la taille du conteneur est inférieure à la taille demandée, les éléments sont ajoutés au vecteur jusqu’à ce qu’il atteigne la taille demandée. Si la taille du conteneur est supérieure à la taille demandée, les éléments les plus proches de la fin du conteneur sont supprimés jusqu’à ce que le conteneur atteigne la taille `_N`. Si la taille actuelle du conteneur est égale à la taille demandée, aucune action n'est effectuée.

`resize` n’est pas sécurisé pour l’accès concurrentiel. Vous devez vous assurer qu’aucun autre thread n’appelle de méthodes sur le vecteur simultané quand vous appelez cette méthode.

## <a name="shrink_to_fit"></a>shrink_to_fit

Compacte la représentation interne du vecteur simultané pour réduire la fragmentation et optimiser l’utilisation de la mémoire. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Notes

Cette méthode réalloue en interne les éléments de déplacement de mémoire autour de, invalidant ainsi tous les itérateurs. `shrink_to_fit` n’est pas sécurisé pour l’accès concurrentiel. Vous devez vous assurer qu’aucun autre thread n’appelle de méthodes sur le vecteur simultané quand vous appelez cette fonction.

## <a name="size"></a>corps

Retourne le nombre d’éléments dans le vecteur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans cet objet `concurrent_vector`.

### <a name="remarks"></a>Notes

La taille retournée est garantie pour inclure tous les éléments ajoutés par les appels à la fonction `push_back`, ou augmenter les opérations qui sont terminées avant d’appeler cette méthode. Toutefois, il peut également inclure des éléments qui sont alloués mais qui sont toujours en cours de construction par des appels simultanés à n’importe quelle méthode de croissance.

## <a name="swap"></a>échange

Échange le contenu de deux vecteurs simultanés. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>Paramètres

*_Vector*<br/>
Objet `concurrent_vector` avec lequel échanger le contenu.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md)
