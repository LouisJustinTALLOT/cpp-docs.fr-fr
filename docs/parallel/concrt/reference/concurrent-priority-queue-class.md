---
title: concurrent_priority_queue, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
ms.openlocfilehash: 024bd2a100b8a0b871d98a5e6001858b55977565
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230361"
---
# <a name="concurrent_priority_queue-class"></a>concurrent_priority_queue, classe

La classe `concurrent_priority_queue` est un conteneur qui permet à plusieurs threads d'appeler simultanément des méthodes Push et Pop sur des éléments. Les éléments sont dépilés dans l'ordre de priorité dans lequel la priorité est déterminée par un functor fourni comme argument de modèle.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données des éléments à stocker dans la file d’attente de priorité.

*_Compare*<br/>
Type de l’objet de fonction qui peut comparer deux valeurs d’éléments comme clés de tri pour déterminer leur ordre relatif dans la file d’attente de priorité. Cet argument est facultatif et le prédicat binaire `less<T>` est la valeur par défaut.

*_Ax*<br/>
Type qui représente l’objet allocateur stocké qui encapsule des détails sur l’allocation et la désallocation de mémoire pour la file d’attente de priorité simultanée. Cet argument est facultatif et sa valeur par défaut est `allocator<T>`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`allocator_type`|Type qui représente la classe Allocator pour la file d’attente de priorité simultanée.|
|`const_reference`|Type qui représente une référence const à un élément du type stocké dans une file d’attente de priorité simultanée.|
|`reference`|Type qui représente une référence à un élément du type stocké dans une file d’attente de priorité simultanée.|
|`size_type`|Type qui compte le nombre d’éléments dans une file d’attente de priorité simultanée.|
|`value_type`|Type qui représente le type de données stocké dans une file d’attente de priorité simultanée.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|Surchargé. Construit une file d’attente de priorité simultanée.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[clear](#clear)|Efface tous les éléments dans la priorité simultanée. Cette méthode n’est pas sécurisée pour la concurrence.|
|[empty](#empty)|Teste si la file d’attente de priorité simultanée est vide au moment où cette méthode est appelée. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[get_allocator](#get_allocator)|Retourne une copie de l’allocateur utilisé pour construire la file d’attente de priorité simultanée. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[push](#push)|Surchargé. Ajoute un élément à la file d’attente de priorité simultanée. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[size](#size)|Retourne le nombre d’éléments dans la file d’attente de priorité simultanée. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[swap](#swap)|Échange le contenu de deux files d’attente à priorité simultanée. Cette méthode n’est pas sécurisée pour la concurrence.|
|[try_pop](#try_pop)|Supprime et retourne l’élément de priorité la plus élevée de la file d’attente si la file d’attente n’est pas vide. Cette méthode est sécurisée pour l’accès concurrentiel.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur =](#operator_eq)|Surchargé. Assigne le contenu d’un autre `concurrent_priority_queue` objet à celui-ci. Cette méthode n’est pas sécurisée pour la concurrence.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur la `concurrent_priority_queue` classe, consultez [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`concurrent_priority_queue`

## <a name="requirements"></a>Spécifications

**En-tête :** concurrent_priority_queue. h

**Espace de noms :** concurrence

## <a name="clear"></a><a name="clear"></a>effacé

Efface tous les éléments dans la priorité simultanée. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
void clear();
```

### <a name="remarks"></a>Notes

`clear`n’est pas protégé contre la concurrence. Vous devez vous assurer qu’aucun autre thread n’appelle de méthodes sur la file d’attente de priorité simultanée lorsque vous appelez cette méthode. `clear`ne libère pas de mémoire.

## <a name="concurrent_priority_queue"></a><a name="ctor"></a>concurrent_priority_queue

Construit une file d’attente de priorité simultanée.

```cpp
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

*_InputIterator*<br/>
Type de l'itérateur d'entrée.

*_Al*<br/>
Classe allocator à utiliser avec cet objet.

*_Init_capacity*<br/>
Capacité initiale de l' `concurrent_priority_queue` objet.

*_Begin*<br/>
Position du premier élément de la plage d'éléments à copier.

*_End*<br/>
Position du premier élément au-delà de la plage d'éléments à copier.

*_Src*<br/>
Objet source `concurrent_priority_queue` à partir duquel copier ou déplacer des éléments.

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un objet allocateur `_Al` et initialisent la file d’attente de priorité.

Le premier constructeur spécifie une file d’attente de priorité initiale vide et spécifie éventuellement un allocateur.

Le deuxième constructeur spécifie une file d’attente de priorité avec une capacité initiale `_Init_capacity` et spécifie éventuellement un allocateur.

Le troisième constructeur spécifie les valeurs fournies par la plage d’itérateurs [ `_Begin` , `_End` ) et spécifie éventuellement un allocateur.

Les quatrième et cinquième constructeurs spécifient une copie de la file d’attente de priorité `_Src` .

Les sixième et septième constructeurs spécifient un déplacement de la file d’attente de priorité `_Src` .

## <a name="empty"></a><a name="empty"></a>vidé

Teste si la file d’attente de priorité simultanée est vide au moment où cette méthode est appelée. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si la file d’attente de priorité était vide au moment où la fonction a été appelée, **`false`** sinon.

## <a name="get_allocator"></a><a name="get_allocator"></a>get_allocator

Retourne une copie de l’allocateur utilisé pour construire la file d’attente de priorité simultanée. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valeur de retour

Copie de l’allocateur utilisé pour construire l' `concurrent_priority_queue` objet.

## <a name="operator"></a><a name="operator_eq"></a>opérateur =

Assigne le contenu d’un autre `concurrent_priority_queue` objet à celui-ci. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
Objet `concurrent_priority_queue` source.

### <a name="return-value"></a>Valeur de retour

Référence à cet `concurrent_priority_queue` objet.

## <a name="push"></a><a name="push"></a>souleve

Ajoute un élément à la file d’attente de priorité simultanée. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>Paramètres

*_Elem*<br/>
Élément à ajouter à la file d’attente de priorité simultanée.

## <a name="size"></a><a name="size"></a>corps

Retourne le nombre d’éléments dans la file d’attente de priorité simultanée. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans cet `concurrent_priority_queue` objet.

### <a name="remarks"></a>Notes

La taille retournée inclut tous les éléments ajoutés par les appels à la fonction `push` . Toutefois, il peut ne pas refléter les résultats des opérations simultanées en attente.

## <a name="swap"></a><a name="swap"></a>échange

Échange le contenu de deux files d’attente à priorité simultanée. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>Paramètres

*_Queue*<br/>
Objet `concurrent_priority_queue` avec lequel échanger le contenu.

## <a name="try_pop"></a><a name="try_pop"></a>try_pop

Supprime et retourne l’élément de priorité la plus élevée de la file d’attente si la file d’attente n’est pas vide. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>Paramètres

*_Elem*<br/>
Référence à une variable qui sera remplie avec l’élément dont la priorité est la plus élevée, si la file d’attente n’est pas vide.

### <a name="return-value"></a>Valeur de retour

**`true`** Si une valeur a été dépilée ; **`false`** sinon,.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md)
