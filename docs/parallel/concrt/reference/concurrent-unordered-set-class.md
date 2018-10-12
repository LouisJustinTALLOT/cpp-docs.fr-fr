---
title: concurrent_unordered_set, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::hash_function
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::insert
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::key_eq
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::swap
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::unsafe_erase
dev_langs:
- C++
helpviewer_keywords:
- concurrent_unordered_set class
ms.assetid: c61f9a9a-4fd9-491a-9251-e300737ecf4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8b8d1e80103784260250c396fceeb7032f6414b9
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163970"
---
# <a name="concurrentunorderedset-class"></a>concurrent_unordered_set, classe

Le `concurrent_unordered_set` classe est un conteneur d’accès concurrentiel sécurisé qui contrôle une séquence de longueur variable constituée d’éléments de type K. La séquence est représentée d’une façon qui permet l’accès concurrentiel sécurisé Ajout, l’accès à un élément, itérateurs et opérations de traversée d’itérateur.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>
>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>> class concurrent_unordered_set : public details::_Concurrent_hash<details::_Concurrent_unordered_set_traits<K,
    details::_Hash_compare<K,
_Hasher,
    key_equality>,
_Allocator_type,
    false>>;
```

#### <a name="parameters"></a>Paramètres

*K*<br/>
Type de clé.

*_Hasher*<br/>
Type d'objet de la fonction de hachage. Cet argument est facultatif et sa valeur par défaut est `std::hash<K>`.

*key_equality*<br/>
Type d’objet de fonction de comparaison d’égalité. Cet argument est facultatif et sa valeur par défaut est `std::equal_to<K>`.

*_Allocator_type*<br/>
Type qui représente l’objet allocateur stocké qui encapsule des informations détaillées sur l’allocation et la désallocation de mémoire pour l’ensemble non trié simultanée. Cet argument est facultatif et sa valeur par défaut est `std::allocator<K>`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`allocator_type`|Type d'un allocateur pour la gestion du stockage.|
|`const_iterator`|Type d'un itérateur constant pour la séquence contrôlée.|
|`const_local_iterator`|Type d’un itérateur de compartiment constant pour la séquence contrôlée.|
|`const_pointer`|Type d'un pointeur constant vers un élément.|
|`const_reference`|Type d'une référence constante à un élément.|
|`difference_type`|Type d'une distance signée entre deux éléments.|
|`hasher`|Type de la fonction de hachage.|
|`iterator`|Type d'un itérateur pour la séquence contrôlée.|
|`key_equal`|Type de la fonction de comparaison.|
|`key_type`|Type d'une clé de tri.|
|`local_iterator`|Type d'un itérateur de compartiment pour la séquence contrôlée.|
|`pointer`|Type d'un pointeur vers un élément.|
|`reference`|Type d'une référence à un élément.|
|`size_type`|Type d'une distance non signée entre deux éléments.|
|`value_type`|Type d’un élément.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[concurrent_unordered_set](#ctor)|Surchargé. Construit un jeu non ordonné simultané.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[hash_function](#hash_function)|Retourne l’objet de fonction de hachage stocké.|
|[insert](#insert)|Surchargé. Ajoute des éléments à la `concurrent_unordered_set` objet.|
|[key_eq](#key_eq)|Retourne l’objet de fonction de comparaison d’égalité stocké.|
|[swap](#swap)|Échange le contenu de deux `concurrent_unordered_set` objets. Cette méthode n’est pas concurrentiel.|
|[unsafe_erase](#unsafe_erase)|Surchargé. Supprime les éléments de la `concurrent_unordered_set` aux positions spécifiées. Cette méthode n’est pas concurrentiel.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[operator=](#operator_eq)|Surchargé. Assigne le contenu d’un autre `concurrent_unordered_set` objet à celui-ci. Cette méthode n’est pas concurrentiel.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur la `concurrent_unordered_set` de classe, consultez [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_set`

## <a name="requirements"></a>Configuration requise

**En-tête :** concurrent_unordered_set.h

**Espace de noms :** concurrency

##  <a name="begin"></a> commencer

Retourne un itérateur qui pointe vers le premier élément dans le conteneur simultané. Cette méthode est sécurisée l’accès concurrentiel.

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Valeur de retour

Un itérateur au premier élément dans le conteneur simultané.

##  <a name="cbegin"></a> cbegin

Retourne un itérateur const qui pointe vers le premier élément dans le conteneur simultané. Cette méthode est sécurisée l’accès concurrentiel.

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Un itérateur const vers le premier élément dans le conteneur simultané.

##  <a name="cend"></a> cend

Retourne un itérateur const qui pointe vers l’emplacement suivant le dernier élément dans le conteneur simultané. Cette méthode est sécurisée l’accès concurrentiel.

```
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur de retour

Un itérateur const à l’emplacement suivant le dernier élément dans le conteneur simultané.

##  <a name="clear"></a> Effacer

Efface tous les éléments dans le conteneur simultané. Cette fonction n’est pas sûr de la concurrence.

```
void clear();
```

##  <a name="ctor"></a> concurrent_unordered_set

Construit un jeu non ordonné simultané.

```
explicit concurrent_unordered_set(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_set(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_set(_Iterator first,
    _Iterator last,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_set(
    const concurrent_unordered_set& _Uset);

concurrent_unordered_set(
    const concurrent_unordered_set& _Uset,
    const allocator_type& _Allocator);

concurrent_unordered_set(
    concurrent_unordered_set&& _Uset);
```

### <a name="parameters"></a>Paramètres

*_Iterator*<br/>
Type de l'itérateur d'entrée.

*_Number_of_buckets*<br/>
Nombre initial de compartiments pour ce jeu non ordonné.

*_Hasher*<br/>
La fonction de hachage pour ce jeu non ordonné.

*key_equality*<br/>
La fonction de comparaison d’égalité pour ce jeu non ordonné.

*_Allocator*<br/>
L’allocateur pour ce jeu non ordonné.

*first*<br/>
*last*<br/>
*_Uset*<br/>
La source `concurrent_unordered_set` objet à copier ou déplacer des éléments à partir de.

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un objet allocateur `_Allocator` et initialiser l’ensemble non trié.

Le premier constructeur spécifie un ensemble initial vide et spécifie explicitement les fonctions de hachage et d’égalité et allocateur tapez le nombre de compartiments, pour être utilisé.

Le deuxième constructeur spécifie un allocateur pour l’ensemble non trié.

Le troisième constructeur spécifie les valeurs fournies par la plage d’itérateurs [ `_Begin`, `_End`).

Les quatrième et cinquième constructeurs spécifient une copie de l’ensemble non trié simultanée `_Uset`.

Le dernier constructeur spécifie un déplacement de l’ensemble non trié simultanée `_Uset`.

##  <a name="count"></a> Nombre

Compte le nombre d’éléments qui correspondent à une clé spécifiée. Cette fonction est l’accès concurrentiel sécurisé.

```
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>Paramètres

*KVal*<br/>
Clé à rechercher.

### <a name="return-value"></a>Valeur de retour

Le nombre de fois le nombre de fois où que la clé s’affiche dans le conteneur.

##  <a name="empty"></a> vide

Vérifie l'absence d'éléments. Cette méthode est sécurisée l’accès concurrentiel.

```
bool empty() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le conteneur simultané est vide, **false** dans le cas contraire.

### <a name="remarks"></a>Notes

En présence d’insertions simultanées, le conteneur simultané soit ou non vide peut changer immédiatement après l’appel de cette fonction, avant que la valeur de retour soit encore lu.

##  <a name="end"></a> fin

Retourne un itérateur qui pointe vers l’emplacement suivant le dernier élément dans le conteneur simultané. Cette méthode est sécurisée l’accès concurrentiel.

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Valeur de retour

Un itérateur vers l’emplacement suivant le dernier élément dans le conteneur simultané.

##  <a name="equal_range"></a> equal_range

Recherche une plage qui correspond à une clé spécifiée. Cette fonction est l’accès concurrentiel sécurisé.

```
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>Paramètres

*KVal*<br/>
La valeur de clé à rechercher.

### <a name="return-value"></a>Valeur de retour

Un [paire](../../../standard-library/pair-structure.md) où le premier élément est un itérateur au début et le deuxième élément est un itérateur à la fin de la plage.

### <a name="remarks"></a>Notes

Il est possible pour les insertions simultanées provoquer des clés supplémentaires à insérer après l’itérateur de début et avant l’itérateur de fin.

##  <a name="find"></a> Rechercher

Recherche un élément qui correspond à une clé spécifiée. Cette fonction est l’accès concurrentiel sécurisé.

```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>Paramètres

*KVal*<br/>
La valeur de clé à rechercher.

### <a name="return-value"></a>Valeur de retour

Un itérateur qui pointe vers l’emplacement du premier élément correspondant à la clé fournie, ou l’itérateur `end()` si cet élément n’existe.

##  <a name="get_allocator"></a> get_allocator

Retourne l’objet allocateur stocké pour ce conteneur simultané. Cette méthode est sécurisée l’accès concurrentiel.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valeur de retour

L’objet allocateur stocké pour ce conteneur simultané.

##  <a name="hash_function"></a> hash_function

Retourne l’objet de fonction de hachage stocké.

```
hasher hash_function() const;
```

### <a name="return-value"></a>Valeur de retour

L’objet de fonction de hachage stocké.

##  <a name="insert"></a> INSERT

Ajoute des éléments à la `concurrent_unordered_set` objet.

```
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```

### <a name="parameters"></a>Paramètres

*_Iterator*<br/>
Le type d’itérateur utilisé pour l’insertion.

*V*<br/>
Le type de la valeur insérée dans le jeu.

*valeur*<br/>
La valeur à insérer.

*_WHERE*<br/>
L’emplacement de départ pour rechercher un point d’insertion.

*first*<br/>
Début de la plage à insérer.

*last*<br/>
La fin de la plage à insérer.

### <a name="return-value"></a>Valeur de retour

Une paire qui contient un itérateur et une valeur booléenne. Consultez la section Notes pour plus d’informations.

### <a name="remarks"></a>Notes

La première fonction membre détermine l’existence d’un élément X dans la séquence dont la clé a un classement équivalent à celui de `value`. Si non, il crée un élément de ce type X et l’initialise avec `value`. La fonction détermine ensuite l’itérateur `where` qui désigne des X. Si une insertion s’est produite, la fonction retourne `std::pair(where, true)`. Sinon, il retourne `std::pair(where, false)`.

La deuxième fonction membre retourne insert ( `value`), à l’aide `_Where` comme point de départ dans la séquence contrôlée pour rechercher le point d’insertion.

La troisième fonction membre insère la séquence de valeurs d’éléments à partir de la plage [ `first`, `last`).

Les deux dernières fonctions membres comportent comme les deux premières, sauf que `value` est utilisé pour construire la valeur insérée.

##  <a name="key_eq"></a> key_eq

Retourne l’objet de fonction de comparaison d’égalité stocké.

```
key_equal key_eq() const;
```

### <a name="return-value"></a>Valeur de retour

L’objet de fonction de comparaison d’égalité stocké.

##  <a name="load_factor"></a> load_factor

Calcule et retourne le facteur de charge actuelle du conteneur. Le facteur de charge est le nombre d’éléments dans le conteneur divisé par le nombre de compartiments.

```
float load_factor() const;
```

### <a name="return-value"></a>Valeur de retour

Le facteur de charge pour le conteneur.

##  <a name="max_load_factor"></a> max_load_factor

Obtient ou définit le facteur de charge maximale du conteneur. Le facteur de charge maximale est le plus grand nombre d’éléments que possible dans chaque compartiment avant le conteneur augmente sa table interne.

```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>Paramètres

`_Newmax`

### <a name="return-value"></a>Valeur de retour

La première fonction membre retourne le facteur de charge maximale stockée. La deuxième fonction membre ne retourne pas de valeur, mais lève une [out_of_range](../../../standard-library/out-of-range-class.md) exception si le facteur de charge fourni n’est pas valide...

##  <a name="max_size"></a> max_size

Retourne la taille maximale du conteneur simultanée, déterminé par l’allocateur. Cette méthode est sécurisée l’accès concurrentiel.

```
size_type max_size() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre maximal d’éléments qui peuvent être insérées dans ce conteneur simultané.

### <a name="remarks"></a>Notes

Cette valeur de limite supérieure peut être supérieure à ce que le conteneur peut réellement contenir.

##  <a name="operator_eq"></a> opérateur =

Assigne le contenu d’un autre `concurrent_unordered_set` objet à celui-ci. Cette méthode n’est pas concurrentiel.

```
concurrent_unordered_set& operator= (const concurrent_unordered_set& _Uset);

concurrent_unordered_set& operator= (concurrent_unordered_set&& _Uset);
```

### <a name="parameters"></a>Paramètres

*_Uset*<br/>
Objet `concurrent_unordered_set` source.

### <a name="return-value"></a>Valeur de retour

Une référence à cet `concurrent_unordered_set` objet.

### <a name="remarks"></a>Notes

Après avoir supprimé les éléments existants dans un jeu non ordonné simultané, `operator=` copie ou déplace le contenu de `_Uset` dans la simultanées désordonnées ensemble.

##  <a name="rehash"></a> rehash

Régénère la table de hachage.

```
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>Paramètres

*_Buckets*<br/>
Le nombre de compartiments souhaité.

### <a name="remarks"></a>Notes

La fonction membre modifie le nombre de compartiments pour qu’il soit au moins égal à `_Buckets` et régénère la table de hachage en fonction des besoins. Le nombre de compartiments doit être une puissance de 2. Si pas une puissance de 2, elle sera arrondie à la plus grande puissance de 2 suivante.

Elle lève une [out_of_range](../../../standard-library/out-of-range-class.md) exception si le nombre de compartiments n’est pas valide (0 ou supérieur au nombre maximal de compartiments).

##  <a name="size"></a> Taille

Retourne le nombre d’éléments dans ce conteneur simultané. Cette méthode est sécurisée l’accès concurrentiel.

```
size_type size() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans le conteneur.

### <a name="remarks"></a>Notes

En présence d’insertions simultanées, le nombre d’éléments dans le conteneur simultané peut changer immédiatement après l’appel de cette fonction, avant que la valeur de retour soit encore lu.

##  <a name="swap"></a> échange

Échange le contenu de deux `concurrent_unordered_set` objets. Cette méthode n’est pas concurrentiel.

```
void swap(concurrent_unordered_set& _Uset);
```

### <a name="parameters"></a>Paramètres

*_Uset*<br/>
Le `concurrent_unordered_set` objet à échanger.

##  <a name="unsafe_begin"></a> unsafe_begin

Retourne un itérateur au premier élément dans ce conteneur pour un compartiment spécifique.

```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>Paramètres

*_Nombre*<br/>
L’index de compartiment.

### <a name="return-value"></a>Valeur de retour

Un itérateur pointant vers le début du compartiment.

##  <a name="unsafe_bucket"></a> unsafe_bucket

Retourne l’index de compartiment correspondant à une clé spécifique dans ce conteneur.

```
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>Paramètres

*KVal*<br/>
La clé de l’élément recherchée.

### <a name="return-value"></a>Valeur de retour

L’index de compartiment pour la clé dans ce conteneur.

##  <a name="unsafe_bucket_count"></a> unsafe_bucket_count

Retourne le nombre actuel de compartiments dans ce conteneur.

```
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre actuel de compartiments dans ce conteneur.

##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size

Retourne le nombre d’éléments dans un compartiment spécifique de ce conteneur.

```
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>Paramètres

*_Nombre*<br/>
Le compartiment à rechercher.

### <a name="return-value"></a>Valeur de retour

Le nombre actuel de compartiments dans ce conteneur.

##  <a name="unsafe_cbegin"></a> unsafe_cbegin

Retourne un itérateur au premier élément dans ce conteneur pour un compartiment spécifique.

```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>Paramètres

*_Nombre*<br/>
L’index de compartiment.

### <a name="return-value"></a>Valeur de retour

Un itérateur pointant vers le début du compartiment.

##  <a name="unsafe_cend"></a> unsafe_cend

Retourne un itérateur vers l’emplacement suivant le dernier élément dans un compartiment spécifique.

```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>Paramètres

*_Nombre*<br/>
L’index de compartiment.

### <a name="return-value"></a>Valeur de retour

Un itérateur pointant vers le début du compartiment.

##  <a name="unsafe_end"></a> unsafe_end

Retourne un itérateur jusqu’au dernier élément dans ce conteneur pour un compartiment spécifique.

```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>Paramètres

*_Nombre*<br/>
L’index de compartiment.

### <a name="return-value"></a>Valeur de retour

Itérateur qui pointe vers la fin du compartiment.

##  <a name="unsafe_erase"></a> unsafe_erase

Supprime les éléments de la `concurrent_unordered_set` aux positions spécifiées. Cette méthode n’est pas concurrentiel.

```
iterator unsafe_erase(
    const_iterator _Where);

size_type unsafe_erase(
    const key_type& KVal);

iterator unsafe_erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Paramètres

*_WHERE*<br/>
La position de l’itérateur à effacer à partir de.

*KVal*<br/>
La valeur de clé à effacer.

*first*<br/>
*last*<br/>
Itérateurs.

### <a name="return-value"></a>Valeur de retour

Les deux premières fonctions membres retournent un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou [fin](#end)() si cet élément n’existe. La troisième fonction membre retourne le nombre d’éléments, qu'il le supprime.

### <a name="remarks"></a>Notes

La première fonction membre supprime l’élément désigné par `_Where`. La deuxième fonction membre supprime les éléments dans la plage [ `_Begin`, `_End`).

La troisième fonction membre supprime les éléments dans la plage délimitée par [equal_range](#equal_range)(KVal).

##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count

Retourne le nombre maximal de compartiments dans ce conteneur.

```
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre maximal de compartiments dans ce conteneur.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md)

