---
title: concurrent_queue, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
ms.openlocfilehash: 4e913af40b2218da5699da2659ec2e9189e32994
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143201"
---
# <a name="concurrent_queue-class"></a>concurrent_queue, classe

La classe `concurrent_queue` est une classe de conteneur de séquence qui autorise un accès Premier entré, premier sorti à ses éléments. Elle permet un ensemble limité d'opérations d'accès concurrentiel sécurisé, comme `push` et `try_pop`. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données des éléments à stocker dans la file d’attente.

*_Ax*<br/>
Type qui représente l’objet allocateur stocké qui encapsule des détails sur l’allocation et la désallocation de mémoire pour cette file d’attente simultanée. Cet argument est facultatif et sa valeur par défaut est `allocator<T>`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`allocator_type`|Type qui représente la classe Allocator pour la file d’attente simultanée.|
|`const_iterator`|Type qui représente un itérateur de `const` non thread-safe sur les éléments d’une file d’attente simultanée.|
|`const_reference`|Type qui fournit une référence à un élément `const` stocké dans une file d’attente simultanée pour la lecture et l’exécution d’opérations de `const`.|
|`difference_type`|Type qui fournit la distance signée entre deux éléments dans une file d’attente simultanée.|
|`iterator`|Type qui représente un itérateur non thread-safe sur les éléments dans une file d’attente simultanée.|
|`reference`|Type qui fournit une référence à un élément stocké dans une file d’attente simultanée.|
|`size_type`|Type qui compte le nombre d’éléments dans une file d’attente simultanée.|
|`value_type`|Type qui représente le type de données stocké dans une file d’attente simultanée.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[concurrent_queue](#ctor)|Surchargé. Construit une file d’attente simultanée.|
|[Destructeur ~ concurrent_queue](#dtor)|Détruit la file d’attente simultanée.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[clear](#clear)|Efface la file d’attente simultanée, en détruisant les éléments actuellement mis en file d’attente. Cette méthode n’est pas sécurisée pour la concurrence.|
|[empty](#empty)|Teste si la file d’attente simultanée est vide au moment où cette méthode est appelée. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[get_allocator](#get_allocator)|Retourne une copie de l’allocateur utilisé pour construire la file d’attente simultanée. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[push](#push)|Surchargé. Met en file d’attente un élément à la fin de la file d’attente simultanée. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[try_pop](#try_pop)|Met en file d’attente un élément de la file d’attente, le cas échéant. Cette méthode est sécurisée pour l’accès concurrentiel.|
|[unsafe_begin](#unsafe_begin)|Surchargé. Retourne un itérateur de type `iterator` ou `const_iterator` au début de la file d’attente simultanée. Cette méthode n’est pas sécurisée pour la concurrence.|
|[unsafe_end](#unsafe_end)|Surchargé. Retourne un itérateur de type `iterator` ou `const_iterator` à la fin de la file d’attente simultanée. Cette méthode n’est pas sécurisée pour la concurrence.|
|[unsafe_size](#unsafe_size)|Retourne le nombre d’éléments dans la file d’attente. Cette méthode n’est pas sécurisée pour la concurrence.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`concurrent_queue`

## <a name="requirements"></a>Spécifications

**En-tête :** concurrent_queue. h

**Espace de noms :** concurrency

## <a name="clear"></a>effacé

Efface la file d’attente simultanée, en détruisant les éléments actuellement mis en file d’attente. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
void clear();
```

## <a name="ctor"></a>concurrent_queue

Construit une file d’attente simultanée.

```cpp
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

*_InputIterator*<br/>
Type de l’itérateur d’entrée qui spécifie une plage de valeurs.

*_Al*<br/>
Classe allocator à utiliser avec cet objet.

*_OtherQ*<br/>
Objet `concurrent_queue` source à partir duquel copier ou déplacer des éléments.

*_Begin*<br/>
Position du premier élément dans la plage d'éléments à copier.

*_End*<br/>
Position du premier élément suivant la fin de la plage d'éléments à copier.

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un objet allocateur `_Al` et initialisent la file d’attente.

Le premier constructeur spécifie une file d’attente initiale vide et spécifie explicitement le type d’allocateur à utiliser.

Le deuxième constructeur spécifie une copie de la file d’attente simultanée `_OtherQ`.

Le troisième constructeur spécifie un déplacement de la file d’attente simultanée `_OtherQ`.

Le quatrième constructeur spécifie les valeurs fournies par la plage d’itérateurs [`_Begin`, `_End`).

## <a name="dtor"></a>~ concurrent_queue

Détruit la file d’attente simultanée.

```cpp
~concurrent_queue();
```

## <a name="empty"></a>vidé

Teste si la file d’attente simultanée est vide au moment où cette méthode est appelée. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si la file d’attente simultanée était vide au moment où nous avons regardé, sinon **false** .

### <a name="remarks"></a>Notes

Bien que cette méthode soit sécurisée pour l’accès concurrentiel en ce qui concerne les appels aux méthodes `push`, `try_pop`et `empty`, la valeur retournée peut être incorrecte au moment où elle est inspectée par le thread appelant.

## <a name="get_allocator"></a>get_allocator

Retourne une copie de l’allocateur utilisé pour construire la file d’attente simultanée. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valeur de retour

Copie de l’allocateur utilisé pour construire la file d’attente simultanée.

## <a name="push"></a>souleve

Met en file d’attente un élément à la fin de la file d’attente simultanée. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
void push(const T& _Src);

void push(T&& _Src);
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
Élément à ajouter à la file d’attente.

### <a name="remarks"></a>Notes

`push` est protégé contre la simultanéité en ce qui concerne les appels aux méthodes `push`, `try_pop`et `empty`.

## <a name="try_pop"></a>try_pop

Met en file d’attente un élément de la file d’attente, le cas échéant. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
bool try_pop(T& _Dest);
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Référence à un emplacement pour stocker l’élément déplacé dans la file d’attente.

### <a name="return-value"></a>Valeur de retour

**true** si un élément a été correctement supprimé de la file d’attente ; sinon, **false** .

### <a name="remarks"></a>Notes

Si un élément a été correctement supprimé de la file d’attente, le paramètre `_Dest` reçoit la valeur déplacée dans la file d’attente, la valeur d’origine contenue dans la file d’attente est détruite et cette fonction retourne **true**. S’il n’y a aucun élément à défiler, cette fonction retourne `false` sans blocage, et le contenu du paramètre `_Dest` n’est pas défini.

`try_pop` est protégé contre la simultanéité en ce qui concerne les appels aux méthodes `push`, `try_pop`et `empty`.

## <a name="unsafe_begin"></a>unsafe_begin

Retourne un itérateur de type `iterator` ou `const_iterator` au début de la file d’attente simultanée. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur de type `iterator` ou `const_iterator` au début de l’objet de file d’attente simultané.

### <a name="remarks"></a>Notes

Les itérateurs de la classe `concurrent_queue` sont principalement destinés au débogage, car ils sont lents, et l’itération n’est pas sécurisée pour les autres opérations de file d’attente.

## <a name="unsafe_end"></a>unsafe_end

Retourne un itérateur de type `iterator` ou `const_iterator` à la fin de la file d’attente simultanée. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
iterator unsafe_end();

const_iterator unsafe_end() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur de type `iterator` ou `const_iterator` à la fin de la file d’attente simultanée.

### <a name="remarks"></a>Notes

Les itérateurs de la classe `concurrent_queue` sont principalement destinés au débogage, car ils sont lents, et l’itération n’est pas sécurisée pour les autres opérations de file d’attente.

## <a name="unsafe_size"></a>unsafe_size

Retourne le nombre d’éléments dans la file d’attente. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
size_type unsafe_size() const;
```

### <a name="return-value"></a>Valeur de retour

Taille de la file d’attente simultanée.

### <a name="remarks"></a>Notes

`unsafe_size` n’est pas sécurisé pour la concurrence et peut produire des résultats incorrects si elle est appelée simultanément avec des appels aux méthodes `push`, `try_pop`et `empty`.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
