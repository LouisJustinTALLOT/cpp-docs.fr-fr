---
title: concurrent_unordered_map, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::at
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::unsafe_erase
dev_langs: C++
helpviewer_keywords: concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 29eae25b01dcb3b76a6c3c13a8675b92048b2d22
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="concurrentunorderedmap-class"></a>concurrent_unordered_map, classe
La classe `concurrent_unordered_map` est un conteneur d'accès concurrentiel sécurisé qui contrôle une séquence à longueur variable d'éléments de type `std::pair<const K, _Element_type>`. La séquence est représentée d'une manière à permettre les opérations d'ajout d'accès concurrentiel sécurisé, d'accès à un élément, d'accès à un itérateur et de traversée d'itérateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
 typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_map : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
 details::_Hash_compare<K,
    _Hasher,
 key_equality>,
    _Allocator_type,
 false>>;
```  
  
#### <a name="parameters"></a>Paramètres  
 `K`  
 Type de clé.  
  
 `_Element_type`  
 Type mappé.  
  
 `_Hasher`  
 Type d'objet de la fonction de hachage. Cet argument est facultatif et sa valeur par défaut est `std::hash<K>`.  
  
 `key_equality`  
 Type d’objet de fonction de comparaison d’égalité. Cet argument est facultatif et sa valeur par défaut est `std::equal_to<K>`.  
  
 `_Allocator_type`  
 Type qui représente l’objet allocateur stocké qui contient des informations sur l’allocation et la désallocation de mémoire pour l’objet Unordered simultanée. Cet argument est facultatif et la valeur par défaut est `std::allocator<std::pair<K`, `_Element_type>>`.  
  
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
|`mapped_type`|Type d'une valeur mappée associée à chaque clé.|  
|`pointer`|Type d'un pointeur vers un élément.|  
|`reference`|Type d'une référence à un élément.|  
|`size_type`|Type d'une distance non signée entre deux éléments.|  
|`value_type`|Type d’un élément.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[concurrent_unordered_map](#ctor)|Surchargé. Construit un objet Unordered simultanée.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[at](#at)|Surchargé. Recherche un élément dans un `concurrent_unordered_map` avec une valeur de clé spécifiée... Cette méthode est concurrentiel.|  
|[hash_function](#hash_function)|Obtient l'objet de fonction de hachage stocké.|  
|[insert](#insert)|Surchargé. Ajoute des éléments à la `concurrent_unordered_map` objet.|  
|[key_eq](#key_eq)|Obtient l’objet de fonction de comparaison d’égalité stockée.|  
|[swap](#swap)|Échange le contenu de deux `concurrent_unordered_map` objets. Cette méthode n’est pas d’accès concurrentiel sécurisé.|  
|[unsafe_erase](#unsafe_erase)|Surchargé. Supprime les éléments à partir de la `concurrent_unordered_map` positions spécifiées. Cette méthode n’est pas d’accès concurrentiel sécurisé.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator]](#operator_at)|Surchargé. Recherche ou insère un élément avec la clé spécifiée. Cette méthode est concurrentiel.|  
|[operator=](#operator_eq)|Surchargé. Assigne le contenu d’un autre `concurrent_unordered_map` objet à celui-ci. Cette méthode n’est pas d’accès concurrentiel sécurisé.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la `concurrent_unordered_map` de classe, consultez [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_map`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** concurrent_unordered_map.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="at"></a>à 

 Recherche un élément dans un `concurrent_unordered_map` avec une valeur de clé spécifiée... Cette méthode est concurrentiel.  
  
```
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `KVal`  
 Valeur de clé à rechercher.  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à la valeur de données de l'élément trouvé.  
  
### <a name="remarks"></a>Notes  
 Si la valeur de clé d’argument est introuvable, la fonction lève un objet de classe `out_of_range`.  
  
##  <a name="begin"></a>commencer 

 Retourne un itérateur qui pointe vers le premier élément dans le conteneur simultané. Cette méthode est l’accès concurrentiel sécurisé.  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur au premier élément dans le conteneur simultané.  
  
##  <a name="cbegin"></a>cbegin 

 Retourne un itérateur const qui pointe vers le premier élément dans le conteneur simultané. Cette méthode est l’accès concurrentiel sécurisé.  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur const sur le premier élément dans le conteneur simultané.  
  
##  <a name="cend"></a>cend 

 Retourne un itérateur const qui pointe vers l’emplacement suivant le dernier élément dans le conteneur simultané. Cette méthode est l’accès concurrentiel sécurisé.  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur const à l’emplacement suivant le dernier élément dans le conteneur simultané.  
  
##  <a name="clear"></a>Effacer 

 Efface tous les éléments dans le conteneur simultané. Cette fonction n’est pas sécurisé de concurrence.  
  
```
void clear();
```  
  
##  <a name="ctor"></a>concurrent_unordered_map 

 Construit un objet Unordered simultanée.  
  
```
explicit concurrent_unordered_map(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_map(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap);

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_map(
    concurrent_unordered_map&& _Umap);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Iterator`  
 Type de l'itérateur d'entrée.  
  
 `_Number_of_buckets`  
 Nombre initial de compartiments pour cette carte non triée.  
  
 `_Hasher`  
 La fonction de hachage pour cette carte non triée.  
  
 `key_equality`  
 La fonction de comparaison d’égalité pour cette carte non triée.  
  
 `_Allocator`  
 L’allocateur pour cette carte non triée.  
  
 `_Begin`  
 Position du premier élément de la plage d'éléments à copier.  
  
 `_End`  
 Position du premier élément au-delà de la plage d'éléments à copier.  
  
 `_Umap`  
 La source `concurrent_unordered_map` objet à copier ou déplacer des éléments à partir de.  
  
### <a name="remarks"></a>Notes  
 Tous les constructeurs stockent un objet allocateur `_Allocator` et initialiser l’objet Unordered.  
  
 Le premier constructeur spécifie un mappage initial vide et spécifie explicitement les fonctions de hachage et d’égalité et allocateur tapez le nombre de compartiments, pour être utilisé.  
  
 Le deuxième constructeur spécifie un allocateur pour la carte non triée.  
  
 Le troisième constructeur spécifie les valeurs fournies par la plage d’itérateurs [ `_Begin`, `_End`).  
  
 Les quatrième et cinquième constructeurs spécifient une copie de l’objet Unordered simultanée `_Umap`.  
  
 Le dernier constructeur spécifie un déplacement de l’objet Unordered simultanée `_Umap`.  
  
##  <a name="count"></a>nombre 

 Compte le nombre d’éléments qui correspondent à une clé spécifiée. Cette fonction est un accès concurrentiel sécurisé.  
  
```
size_type count(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `KVal`  
 Clé à rechercher.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de fois où le nombre de fois où que la clé s’affiche dans le conteneur.  
  
##  <a name="empty"></a>vide 

 Vérifie l'absence d'éléments. Cette méthode est l’accès concurrentiel sécurisé.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true`Si le conteneur simultané est vide, `false` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 En présence d’insertions simultanées, ou non le conteneur simultané est vide peut changer immédiatement après l’appel de cette fonction, avant que la valeur de retour soit encore lu.  
  
##  <a name="end"></a>fin 

 Retourne un itérateur pointant vers l’emplacement suivant le dernier élément dans le conteneur simultané. Cette méthode est l’accès concurrentiel sécurisé.  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur vers l’emplacement suivant le dernier élément dans le conteneur simultané.  
  
##  <a name="equal_range"></a>equal_range 

 Recherche une plage qui correspond à une clé spécifiée. Cette fonction est un accès concurrentiel sécurisé.  
  
```
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `KVal`  
 La valeur de clé à rechercher.  
  
### <a name="return-value"></a>Valeur de retour  
 A [paire](http://msdn.microsoft.com/en-us/c5a37023-d939-4eb2-ae24-ce8e0cd4505d) où le premier élément est un itérateur au début et le deuxième élément est un itérateur à la fin de la plage.  
  
### <a name="remarks"></a>Notes  
 Il est possible pour les insertions simultanées à provoquer des clés supplémentaires à insérer après l’itérateur begin et avant l’itérateur de fin.  
  
##  <a name="find"></a>Rechercher 

 Recherche un élément qui correspond à une clé spécifiée. Cette fonction est un accès concurrentiel sécurisé.  
  
```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `KVal`  
 La valeur de clé à rechercher.  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur pointant vers l’emplacement du premier élément correspondant à la clé fournie ou l’itérateur `end()` si cet élément n’existe.  
  
##  <a name="get_allocator"></a>get_allocator 

 Retourne l’objet allocateur stocké pour ce conteneur simultané. Cette méthode est l’accès concurrentiel sécurisé.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’objet allocateur stocké pour ce conteneur simultané.  
  
##  <a name="hash_function"></a>hash_function 

 Obtient l'objet de fonction de hachage stocké.  
  
```
hasher hash_function() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’objet de fonction de hachage stocké.  
  
##  <a name="insert"></a>INSERT 

 Ajoute des éléments à la `concurrent_unordered_map` objet.  
  
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
 `_Iterator`  
 Le type d’itérateur permet l’insertion.  
  
 `V`  
 Le type de la valeur insérée dans la table.  
  
 `value`  
 La valeur à insérer.  
  
 `_Where`  
 L’emplacement de départ pour rechercher un point d’insertion.  
  
 `first`  
 Début de la plage à insérer.  
  
 `last`  
 Fin de la plage à insérer.  
  
### <a name="return-value"></a>Valeur de retour  
 Une paire qui contient un itérateur et une valeur booléenne. Consultez la section Notes pour plus de détails.  
  
### <a name="remarks"></a>Notes  
 La première fonction membre détermine l’existence d’un élément X dans la séquence dont la clé a un classement équivalent à celui de `value`. Si non, il crée un élément de ce type X et l’initialise avec `value`. Ensuite, la fonction détermine l’itérateur `where` qui désigne des X. Si une insertion s’est produite, la fonction retourne `std::pair(where, true)`. Sinon, il retourne `std::pair(where, false)`.  
  
 La deuxième fonction membre retourne insert ( `value`), à l’aide `_Where` comme point de départ dans la séquence contrôlée pour rechercher le point d’insertion.  
  
 La troisième fonction membre insère la séquence de valeurs d’éléments à partir de la plage [ `first`, `last`).  
  
 Les deux dernières fonctions membres comportent comme les deux premières, sauf que `value` est utilisée pour construire la valeur insérée.  
  
##  <a name="key_eq"></a>key_eq 

 Obtient l’objet de fonction de comparaison d’égalité stockée.  
  
```
key_equal key_eq() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’objet de fonction de comparaison d’égalité stockée.  
  
##  <a name="load_factor"></a>load_factor 

 Calcule et retourne le facteur de charge actuelle du conteneur. Le facteur de charge est le nombre d’éléments dans le conteneur divisé par le nombre de compartiments.  
  
```
float load_factor() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le facteur de charge pour le conteneur.  
  
##  <a name="max_load_factor"></a>max_load_factor 

 Obtient ou définit le facteur de charge maximale du conteneur. Le facteur de charge maximale est le plus grand nombre d’éléments que possible dans chaque compartiment avant le conteneur développe sa table interne.  
  
```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Newmax`  
  
### <a name="return-value"></a>Valeur de retour  
 La première fonction membre retourne le facteur de charge maximale stockée. La deuxième fonction membre ne retourne pas de valeur, mais lève une [out_of_range](../../../standard-library/out-of-range-class.md) exception si le facteur de charge fourni n’est pas valide...  
  
##  <a name="max_size"></a>max_size 

 Retourne la taille maximale du conteneur simultanée, déterminé par l’allocateur. Cette méthode est l’accès concurrentiel sécurisé.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre maximal d’éléments qui peuvent être insérées dans ce conteneur simultané.  
  
### <a name="remarks"></a>Notes  
 Cette valeur limite supérieure peut être supérieure à ce que le conteneur peut recevoir réellement.  
  
##  <a name="operator_at"></a>operator] 

 Recherche ou insère un élément avec la clé spécifiée. Cette méthode est concurrentiel.  
  
```
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```  
  
### <a name="parameters"></a>Paramètres  
 `KVal`  
 La valeur de clé  
  
 Rechercher ou à insérer.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à la valeur des données de l’élément trouvé ou insérée.  
  
### <a name="remarks"></a>Notes  
 Si la valeur de clé d’argument est introuvable, elle est insérée avec la valeur par défaut du type de données.  
  
 `operator[]`peut être utilisé pour insérer des éléments dans une carte `m` à l’aide de `m[key] = DataValue;`, où `DataValue` est la valeur de la `mapped_type` de l’élément avec une valeur de clé de `key`.  
  
 Lorsque vous utilisez `operator[]` pour insérer des éléments, la référence retournée n'indique pas si l'insertion va modifier un élément existant ou en créer un nouveau. Les fonctions membres `find` et [insérer](#insert) peut être utilisé pour déterminer si un élément avec une clé spécifiée est déjà présent avant l’insertion.  
  
##  <a name="operator_eq"></a>opérateur = 

 Assigne le contenu d’un autre `concurrent_unordered_map` objet à celui-ci. Cette méthode n’est pas d’accès concurrentiel sécurisé.  
  
```
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Umap`  
 Objet `concurrent_unordered_map` source.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à ce `concurrent_unordered_map` objet.  
  
### <a name="remarks"></a>Notes  
 Après avoir supprimé les éléments existants à un vecteur simultané, `operator=` copie ou déplace le contenu de `_Umap` dans le vecteur simultané.  
  
##  <a name="rehash"></a>rehash) 

 Régénère la table de hachage.  
  
```
void rehash(size_type _Buckets);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Buckets`  
 Le nombre souhaité de compartiments.  
  
### <a name="remarks"></a>Notes  
 La fonction membre modifie le nombre de compartiments pour qu’il soit au moins égal à `_Buckets` et régénère la table de hachage en fonction des besoins. Le nombre de compartiments doit être une puissance de 2. Si pas une puissance de 2, il est arrondi à la plus grande puissance de 2 suivante.  
  
 Elle lève une [out_of_range](../../../standard-library/out-of-range-class.md) exception si le nombre de compartiments n’est pas valide (0 ou supérieur au nombre maximal de compartiments).  
  
##  <a name="size"></a>taille 

 Retourne le nombre d’éléments dans ce conteneur simultané. Cette méthode est l’accès concurrentiel sécurisé.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans le conteneur.  
  
### <a name="remarks"></a>Notes  
 En présence d’insertions simultanées, le nombre d’éléments dans le conteneur simultané peut changer immédiatement après l’appel de cette fonction, avant que la valeur de retour soit encore lu.  
  
##  <a name="swap"></a>swap 

 Échange le contenu de deux `concurrent_unordered_map` objets. Cette méthode n’est pas d’accès concurrentiel sécurisé.  
  
```
void swap(concurrent_unordered_map& _Umap);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Umap`  
 Le `concurrent_unordered_map` objet à échanger.  
  
##  <a name="unsafe_begin"></a>unsafe_begin 

 Retourne un itérateur au premier élément dans ce conteneur pour un compartiment spécifique.  
  
```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Bucket`  
 L’index de compartiment.  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur pointant vers le début de la plage.  
  
##  <a name="unsafe_bucket"></a>unsafe_bucket 

 Retourne l’index de compartiment correspondant à une clé spécifique dans ce conteneur.  
  
```
size_type unsafe_bucket(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `KVal`  
 La clé de l’élément recherchée.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de compartiment pour la clé dans ce conteneur.  
  
##  <a name="unsafe_bucket_count"></a>unsafe_bucket_count 

 Retourne le nombre actuel de compartiments dans ce conteneur.  
  
```
size_type unsafe_bucket_count() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre actuel de compartiments dans ce conteneur.  
  
##  <a name="unsafe_bucket_size"></a>unsafe_bucket_size 

 Retourne le nombre d’éléments dans un compartiment spécifique de ce conteneur.  
  
```
size_type unsafe_bucket_size(size_type _Bucket);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Bucket`  
 Le compartiment à rechercher.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre actuel de compartiments dans ce conteneur.  
  
##  <a name="unsafe_cbegin"></a>unsafe_cbegin 

 Retourne un itérateur au premier élément dans ce conteneur pour un compartiment spécifique.  
  
```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Bucket`  
 L’index de compartiment.  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur pointant vers le début de la plage.  
  
##  <a name="unsafe_cend"></a>unsafe_cend 

 Retourne un itérateur vers l’emplacement suivant le dernier élément dans un compartiment spécifique.  
  
```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Bucket`  
 L’index de compartiment.  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur pointant vers le début de la plage.  
  
##  <a name="unsafe_end"></a>unsafe_end 

 Retourne un itérateur au dernier élément dans ce conteneur pour un compartiment spécifique.  
  
```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Bucket`  
 L’index de compartiment.  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur pointant vers la fin du compartiment.  
  
##  <a name="unsafe_erase"></a>unsafe_erase 

 Supprime les éléments à partir de la `concurrent_unordered_map` positions spécifiées. Cette méthode n’est pas d’accès concurrentiel sécurisé.  
  
```
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator _Begin,
    const_iterator _End);

size_type unsafe_erase(
    const key_type& KVal);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Where`  
 La position de l’itérateur d’effacement de.  
  
 `_Begin`  
 La position du premier élément dans la plage d’éléments à effacer.  
  
 `_End`  
 Position du premier élément au-delà de la plage d’éléments à effacer.  
  
 `KVal`  
 La valeur de clé à effacer.  
  
### <a name="return-value"></a>Valeur de retour  
 Les deux premières fonctions membres retournent un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou `concurrent_unordered_map::end`() si cet élément n’existe. La troisième fonction membre retourne le nombre d’éléments, qu'il le supprime.  
  
### <a name="remarks"></a>Notes  
 La première fonction membre supprime l’élément de la séquence contrôlée vers lequel pointé `_Where`. La deuxième fonction membre supprime les éléments de la plage [ `_Begin`, `_End`).  
  
 La troisième fonction membre supprime les éléments de la plage délimitée par `concurrent_unordered_map::equal_range`(KVal).  
  
##  <a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count 

 Retourne le nombre maximal de compartiments dans ce conteneur.  
  
```
size_type unsafe_max_bucket_count() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre maximal de compartiments dans ce conteneur.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [Conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md)



