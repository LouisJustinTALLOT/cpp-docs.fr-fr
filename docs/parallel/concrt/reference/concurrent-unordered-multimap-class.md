---
title: concurrent_unordered_multimap, classe
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_multimap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::concurrent_unordered_multimap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_multimap class
ms.assetid: 4dada5d7-15df-4382-b9c9-348e75b2f3c1
ms.openlocfilehash: fb03d368b7c9cced8961dbd77f22ab6bec40bc0d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230322"
---
# <a name="concurrent_unordered_multimap-class"></a>concurrent_unordered_multimap, classe

La classe `concurrent_unordered_multimap` est un conteneur d'accès concurrentiel sécurisé qui contrôle une séquence à longueur variable d'éléments de type `std::pair<const K, _Element_type>`. La séquence est représentée d'une manière à permettre les opérations d'ajout d'accès concurrentiel sécurisé, d'accès à un élément, d'accès à un itérateur et de traversée d'itérateur. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_multimap : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
details::_Hash_compare<K,
    _Hasher,
key_equality>,
    _Allocator_type,
true>>;
```

### <a name="parameters"></a>Paramètres

*DK*<br/>
Type de clé.

*_Element_type*<br/>
Type mappé.

*_Hasher*<br/>
Type d’objet de la fonction de hachage. Cet argument est facultatif et sa valeur par défaut est `std::hash<K>`.

*key_equality*<br/>
Type d’objet de fonction de comparaison d’égalité. Cet argument est facultatif et sa valeur par défaut est `std::equal_to<K>`.

*_Allocator_type*<br/>
Type qui représente l’objet allocateur stocké qui encapsule des détails sur l’allocation et la désallocation de mémoire pour le vecteur simultané. Cet argument est facultatif et la valeur par défaut est `std::allocator<std::pair<K` , `_Element_type>>` .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`allocator_type`|Type d’un allocateur pour la gestion du stockage.|
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
|`mapped_type`|Type d'une valeur mappée associée à chaque clé.|
|`pointer`|Type d'un pointeur vers un élément.|
|`reference`|Type d'une référence à un élément.|
|`size_type`|Type d'une distance non signée entre deux éléments.|
|`value_type`|Type d’un élément.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[concurrent_unordered_multimap](#ctor)|Surchargé. Construit un Multimap non ordonné simultané.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[hash_function](#hash_function)|Retourne l’objet de fonction de hachage stocké.|
|[insert](#insert)|Surchargé. Ajoute des éléments à l' `concurrent_unordered_multimap` objet.|
|[key_eq](#key_eq)|Retourne l’objet de fonction de comparaison d’égalité stocké.|
|[swap](#swap)|Échange le contenu de deux objets `concurrent_unordered_multimap`. Cette méthode n’est pas sécurisée pour la concurrence.|
|[unsafe_erase](#unsafe_erase)|Surchargé. Supprime des éléments du `concurrent_unordered_multimap` à des positions spécifiées. Cette méthode n’est pas sécurisée pour la concurrence.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur =](#operator_eq)|Surchargé. Assigne le contenu d’un autre `concurrent_unordered_multimap` objet à celui-ci. Cette méthode n’est pas sécurisée pour la concurrence.|

## <a name="remarks"></a>Notes

Pour plus d’informations sur la `concurrent_unordered_multimap` classe, consultez [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_multimap`

## <a name="requirements"></a>Spécifications

**En-tête :** concurrent_unordered_map. h

**Espace de noms :** concurrence

## <a name="begin"></a><a name="begin"></a>commencer

Retourne un itérateur pointant vers le premier élément du conteneur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur vers le premier élément du conteneur simultané.

## <a name="cbegin"></a><a name="cbegin"></a>cbegin

Retourne un itérateur const pointant vers le premier élément du conteneur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur const vers le premier élément du conteneur simultané.

## <a name="cend"></a><a name="cend"></a>CEND

Retourne un itérateur const pointant vers l’emplacement qui suit le dernier élément du conteneur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur const vers l’emplacement qui suit le dernier élément du conteneur simultané.

## <a name="clear"></a><a name="clear"></a>effacé

Efface tous les éléments dans le conteneur simultané. Cette fonction n’est pas sécurisée pour l’accès concurrentiel.

```cpp
void clear();
```

## <a name="concurrent_unordered_multimap"></a><a name="ctor"></a>concurrent_unordered_multimap

Construit un Multimap non ordonné simultané.

```cpp
explicit concurrent_unordered_multimap(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multimap(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_multimap(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multimap(
    const concurrent_unordered_multimap& _Umap);

concurrent_unordered_multimap(
    const concurrent_unordered_multimap& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_multimap(
    concurrent_unordered_multimap&& _Umap);
```

### <a name="parameters"></a>Paramètres

*_Iterator*<br/>
Type de l'itérateur d'entrée.

*_Number_of_buckets*<br/>
Nombre initial de compartiments pour ce Multimap non ordonné.

*_Hasher*<br/>
Fonction de hachage pour ce Multimap non ordonné.

*key_equality*<br/>
Fonction de comparaison d’égalité pour ce Multimap non ordonné.

*_Allocator*<br/>
Allocateur pour ce Multimap non ordonné.

*_Begin*<br/>
Position du premier élément de la plage d'éléments à copier.

*_End*<br/>
Position du premier élément au-delà de la plage d'éléments à copier.

*_Umap*<br/>
Objet source `concurrent_unordered_multimap` à partir duquel copier les éléments.

### <a name="remarks"></a>Notes

Tous les constructeurs stockent un objet allocateur `_Allocator` et initialisent le Multimap non ordonné.

Le premier constructeur spécifie un Multimap initial vide et spécifie explicitement le nombre de compartiments, la fonction de hachage, la fonction d’égalité et le type d’allocateur à utiliser.

Le deuxième constructeur spécifie un allocateur pour le Multimap non ordonné.

Le troisième constructeur spécifie les valeurs fournies par la plage d’itérateurs [ `_Begin` , `_End` ).

Les quatrième et cinquième constructeurs spécifient une copie des Multimap non ordonnés simultanés `_Umap` .

Le dernier constructeur spécifie un déplacement des Multimap non ordonnés simultanés `_Umap` .

## <a name="count"></a><a name="count"></a>saut

Compte le nombre d’éléments qui correspondent à une clé spécifiée. Cette fonction est sécurisée pour l’accès concurrentiel.

```cpp
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>Paramètres

*KVal*<br/>
Clé à rechercher.

### <a name="return-value"></a>Valeur de retour

Nombre de fois où la clé apparaît dans le conteneur.

## <a name="empty"></a><a name="empty"></a>vidé

Vérifie l'absence d'éléments. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si le conteneur simultané est vide ; **`false`** sinon,.

### <a name="remarks"></a>Notes

En présence d’insertions simultanées, si le conteneur simultané est vide, peut changer immédiatement après l’appel de cette fonction, avant que la valeur de retour ne soit même lue.

## <a name="end"></a><a name="end"></a>effet

Retourne un itérateur pointant vers l’emplacement qui suit le dernier élément du conteneur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’emplacement qui suit le dernier élément du conteneur simultané.

## <a name="equal_range"></a><a name="equal_range"></a>equal_range

Recherche une plage qui correspond à une clé spécifiée. Cette fonction est sécurisée pour l’accès concurrentiel.

```cpp
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>Paramètres

*KVal*<br/>
Valeur de clé à rechercher.

### <a name="return-value"></a>Valeur de retour

[Paire](../../../standard-library/pair-structure.md) où le premier élément est un itérateur au début et le deuxième élément est un itérateur à la fin de la plage.

### <a name="remarks"></a>Notes

Il est possible que les insertions simultanées provoquent l’insertion de clés supplémentaires après l’itérateur de début et avant l’itérateur de fin.

## <a name="find"></a><a name="find"></a>trouver

Recherche un élément qui correspond à une clé spécifiée. Cette fonction est sécurisée pour l’accès concurrentiel.

```cpp
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>Paramètres

*KVal*<br/>
Valeur de clé à rechercher.

### <a name="return-value"></a>Valeur de retour

Itérateur pointant sur l’emplacement du premier élément qui correspond à la clé fournie, ou l’itérateur `end()` si aucun élément de ce type n’existe.

## <a name="get_allocator"></a><a name="get_allocator"></a>get_allocator

Retourne l’objet allocateur stocké pour ce conteneur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valeur de retour

Objet allocateur stocké pour ce conteneur simultané.

## <a name="hash_function"></a><a name="hash_function"></a>hash_function

Retourne l’objet de fonction de hachage stocké.

```cpp
hasher hash_function() const;
```

### <a name="return-value"></a>Valeur de retour

Objet de fonction de hachage stocké.

## <a name="insert"></a><a name="insert"></a>Insérer

Ajoute des éléments à l' `concurrent_unordered_multimap` objet.

```cpp
iterator insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
iterator insert(
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
Type d’itérateur utilisé pour l’insertion.

*V*<br/>
Type de la valeur insérée dans la classe Map.

*value*<br/>
Valeur à insérer.

*_Where*<br/>
Emplacement de départ pour rechercher un point d’insertion.

*first*<br/>
Début de la plage à insérer.

*last*<br/>
Fin de la plage à insérer.

### <a name="return-value"></a>Valeur de retour

Itérateur pointant vers l’emplacement d’insertion.

### <a name="remarks"></a>Notes

La première fonction membre insère l’élément `value` dans la séquence contrôlée, puis retourne l’itérateur qui désigne l’élément inséré.

La deuxième fonction membre retourne Insert ( `value` ), en utilisant `_Where` comme emplacement de départ dans la séquence contrôlée pour rechercher le point d’insertion.

La troisième fonction membre insère la séquence de valeurs d’éléments à partir de la plage [ `first` , `last` ).

Les deux dernières fonctions membres se comportent de la même façon que les deux premières, sauf que `value` est utilisé pour construire la valeur insérée.

## <a name="key_eq"></a><a name="key_eq"></a>key_eq

Retourne l’objet de fonction de comparaison d’égalité stocké.

```cpp
key_equal key_eq() const;
```

### <a name="return-value"></a>Valeur de retour

Objet de fonction de comparaison d’égalité stocké.

## <a name="load_factor"></a><a name="load_factor"></a>load_factor

Calcule et retourne le facteur de charge actuel du conteneur. Le facteur de charge est le nombre d’éléments dans le conteneur divisé par le nombre de compartiments.

```cpp
float load_factor() const;
```

### <a name="return-value"></a>Valeur de retour

Facteur de charge pour le conteneur.

## <a name="max_load_factor"></a><a name="max_load_factor"></a>max_load_factor

Obtient ou définit le facteur de charge maximal du conteneur. Le facteur de charge maximale est le plus grand nombre d’éléments que ne peut être dans un compartiment avant que le conteneur ne développe sa table interne.

```cpp
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>Paramètres

`_Newmax`

### <a name="return-value"></a>Valeur de retour

La première fonction membre retourne le facteur de charge maximale stockée. La deuxième fonction membre ne retourne pas de valeur, mais lève une exception [out_of_range](../../../standard-library/out-of-range-class.md) si le facteur de charge fourni n’est pas valide.

## <a name="max_size"></a><a name="max_size"></a>max_size

Retourne la taille maximale du conteneur simultané, déterminée par l’allocateur. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre maximal d’éléments qui peuvent être insérés dans ce conteneur simultané.

### <a name="remarks"></a>Notes

Cette valeur limite supérieure peut en fait être supérieure à ce que le conteneur peut réellement contenir.

## <a name="operator"></a><a name="operator_eq"></a>opérateur =

Assigne le contenu d’un autre `concurrent_unordered_multimap` objet à celui-ci. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
concurrent_unordered_multimap& operator= (const concurrent_unordered_multimap& _Umap);

concurrent_unordered_multimap& operator= (concurrent_unordered_multimap&& _Umap);
```

### <a name="parameters"></a>Paramètres

*_Umap*<br/>
Objet `concurrent_unordered_multimap` source.

### <a name="return-value"></a>Valeur de retour

Référence à cet `concurrent_unordered_multimap` objet.

### <a name="remarks"></a>Notes

Après l’effacement des éléments existants dans un Multimap non ordonné simultané, `operator=` copie ou déplace le contenu de `_Umap` dans le Multimap simultané non ordonné.

## <a name="rehash"></a><a name="rehash"></a>rehash

Régénère la table de hachage.

```cpp
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>Paramètres

*_Buckets*<br/>
Nombre souhaité de compartiments.

### <a name="remarks"></a>Notes

La fonction membre modifie le nombre de compartiments pour qu’il soit au moins égal à `_Buckets` et régénère la table de hachage en fonction des besoins. Le nombre de compartiments doit être une puissance de 2. S’il ne s’agit pas d’une puissance de 2, il sera arrondi à la puissance de 2 la plus grande.

Elle lève une exception [out_of_range](../../../standard-library/out-of-range-class.md) si le nombre de compartiments n’est pas valide (0 ou supérieur au nombre maximal de compartiments).

## <a name="size"></a><a name="size"></a>corps

Retourne le nombre d’éléments dans ce conteneur simultané. Cette méthode est sécurisée pour l’accès concurrentiel.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans le conteneur.

### <a name="remarks"></a>Notes

En présence d’insertions simultanées, le nombre d’éléments dans le conteneur simultané peut changer immédiatement après l’appel de cette fonction, avant que la valeur de retour soit même lue.

## <a name="swap"></a><a name="swap"></a>échange

Échange le contenu de deux objets `concurrent_unordered_multimap`. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
void swap(concurrent_unordered_multimap& _Umap);
```

### <a name="parameters"></a>Paramètres

*_Umap*<br/>
`concurrent_unordered_multimap`Objet à échanger.

## <a name="unsafe_begin"></a><a name="unsafe_begin"></a>unsafe_begin

Retourne un itérateur au premier élément de ce conteneur pour un compartiment spécifique.

```cpp
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>Paramètres

*_Bucket*<br/>
Index de compartiment.

### <a name="return-value"></a>Valeur de retour

Itérateur pointant vers le début du compartiment.

## <a name="unsafe_bucket"></a><a name="unsafe_bucket"></a>unsafe_bucket

Retourne l’index de compartiment auquel une clé spécifique est mappée dans ce conteneur.

```cpp
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>Paramètres

*KVal*<br/>
Clé d’élément recherchée.

### <a name="return-value"></a>Valeur de retour

Index de compartiment pour la clé dans ce conteneur.

## <a name="unsafe_bucket_count"></a><a name="unsafe_bucket_count"></a>unsafe_bucket_count

Retourne le nombre actuel de compartiments dans ce conteneur.

```cpp
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre actuel de compartiments dans ce conteneur.

## <a name="unsafe_bucket_size"></a><a name="unsafe_bucket_size"></a>unsafe_bucket_size

Retourne le nombre d’éléments dans un compartiment spécifique de ce conteneur.

```cpp
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>Paramètres

*_Bucket*<br/>
Compartiment à rechercher.

### <a name="return-value"></a>Valeur de retour

Nombre actuel de compartiments dans ce conteneur.

## <a name="unsafe_cbegin"></a><a name="unsafe_cbegin"></a>unsafe_cbegin

Retourne un itérateur au premier élément de ce conteneur pour un compartiment spécifique.

```cpp
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>Paramètres

*_Bucket*<br/>
Index de compartiment.

### <a name="return-value"></a>Valeur de retour

Itérateur pointant vers le début du compartiment.

## <a name="unsafe_cend"></a><a name="unsafe_cend"></a>unsafe_cend

Retourne un itérateur à l’emplacement suivant le dernier élément d’un compartiment spécifique.

```cpp
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>Paramètres

*_Bucket*<br/>
Index de compartiment.

### <a name="return-value"></a>Valeur de retour

Itérateur pointant vers le début du compartiment.

## <a name="unsafe_end"></a><a name="unsafe_end"></a>unsafe_end

Retourne un itérateur au dernier élément de ce conteneur pour un compartiment spécifique.

```cpp
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>Paramètres

*_Bucket*<br/>
Index de compartiment.

### <a name="return-value"></a>Valeur de retour

Itérateur pointant vers la fin du compartiment.

## <a name="unsafe_erase"></a><a name="unsafe_erase"></a>unsafe_erase

Supprime des éléments du `concurrent_unordered_multimap` à des positions spécifiées. Cette méthode n’est pas sécurisée pour la concurrence.

```cpp
iterator unsafe_erase(
    const_iterator _Where);

size_type unsafe_erase(
    const key_type& KVal);

iterator unsafe_erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Paramètres

*_Where*<br/>
Position de l’itérateur à partir de laquelle effacer.

*KVal*<br/>
Valeur de clé à supprimer.

*first*<br/>
*last*<br/>
Itérateurs.

### <a name="return-value"></a>Valeur de retour

Les deux premières fonctions membres retournent un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou `concurrent_unordered_multimap::end` () si aucun élément de ce type n’existe. La troisième fonction membre retourne le nombre d’éléments qu’elle supprime.

### <a name="remarks"></a>Notes

La première fonction membre supprime l’élément de la séquence contrôlée pointée par `_Where` . La deuxième fonction membre supprime les éléments de la plage [ `_Begin` , `_End` ).

La troisième fonction membre supprime les éléments de la plage délimitée par `concurrent_unordered_multimap::equal_range` (KVal).

## <a name="unsafe_max_bucket_count"></a><a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count

Retourne le nombre maximal de compartiments dans ce conteneur.

```cpp
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre maximal de compartiments dans ce conteneur.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md)
