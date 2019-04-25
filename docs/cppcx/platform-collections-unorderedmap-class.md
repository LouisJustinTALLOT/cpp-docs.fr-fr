---
title: Platform::Collections::UnorderedMap, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: 7790b363ef3f30b0ad0602568190ab443a2c1401
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161730"
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap, classe

Représente une *carte*non triée qui est une collection de paires clé-valeur.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename K,
   typename V,
   typename C = std::equal_to<K>
>
ref class Map sealed;
```

#### <a name="parameters"></a>Paramètres

*K*<br/>
Type de la clé dans la paire clé-valeur.

*V*<br/>
Type de la valeur dans la paire clé-valeur.

*C*<br/>
Type qui fournit un objet de fonction qui peut comparer deux valeurs d'élément comme des clés de tri pour déterminer leur ordre relatif dans le Map. Par défaut, [std::equal_to\<K >](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Notes

Les types autorisés sont les suivants :

- Entiers

- classe interface ^

- Classe ref publique ^

- value struct

- classe d'énumération publique

**UnorderedMap** est essentiellement un wrapper pour [std::unordered_map](../standard-library/unordered-map-class.md) qui prend en charge le stockage des types Windows Runtime. Il est l’une implémentation concrète de la [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) et [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) interfaces de types qui sont passés à travers public Windows Runtime. Si vous tentez d'utiliser un type `Platform::Collections::UnorderedMap` dans une valeur de retour ou un paramètre public, l'erreur de compilateur C3986 est générée. Vous pouvez corriger l’erreur en modifiant le type du paramètre ou la valeur de retour par [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Pour plus d’informations, consultez [Collections](../cppcx/collections-c-cx.md).

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[UnorderedMap::UnorderedMap](#ctor)|Initialise une nouvelle instance de la classe Map.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[UnorderedMap::Clear](#clear)|Supprime toutes les paires clé-valeur de l'objet Map actuel.|
|[UnorderedMap::First](#first)|Retourne un itérateur qui spécifie le premier élément de la carte.|
|[UnorderedMap::GetView](#getview)|Retourne une vue en lecture seule de la carte active, soit une classe Platform::Collections::UnorderedMapView.|
|[UnorderedMap::HasKey](#haskey)|Détermine si le Map actuel contient la clé spécifiée.|
|[UnorderedMap::Insert](#insert)|Ajoute une paire clé-valeur spécifiée à l'objet Map actuel.|
|[UnorderedMap::Lookup](#lookup)|Récupère l'élément à la clé spécifiée dans l'objet Map actuel.|
|[UnorderedMap::Remove](#remove)|Supprime la paire clé-valeur spécifiée de l'objet Map actuel.|
|[UnorderedMap::Size](#size)|Retourne le nombre d'éléments dans l'objet Map actuel.|

### <a name="events"></a>Événements

|||
|-|-|
|Nom|Description|
|[Map::MapChanged](#mapchanged) event|Se produit lorsque l'objet Map est modifié.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`UnorderedMap`

### <a name="requirements"></a>Configuration requise

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="clear"></a>  Unorderedmap::Clear, méthode

Supprime toutes les paires clé-valeur de l'objet UnorderedMap actif.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="first"></a>  Unorderedmap::First, méthode

Retourne un itérateur qui spécifie le premier [Windows::Foundation::Collections::IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) élément dans la carte non triée.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui spécifie le premier élément de la carte.

### <a name="remarks"></a>Notes

Un moyen pratique de contenir l’itérateur retourné par First() consiste à attribuer la valeur de retour à une variable est déclarée avec le **automatique** mot clé de déduction de type. Par exemple, `auto x = myUnorderedMap->First();`.

## <a name="getview"></a>  Unorderedmap::GetView, méthode

Retourne une vue en lecture seule de l’objet UnorderedMap actif ; Autrement dit, un [classe Platform::Collections :: unorderedmapview](../cppcx/platform-collections-unorderedmapview-class.md) qui implémente le [interface Windows::Foundation::Collections::IMapView::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_).

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Valeur de retour

Objet `UnorderedMapView`.

## <a name="haskey"></a>  Unorderedmap::haskey, méthode

Détermine si le UnorderedMap actif contient la clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé utilisée pour rechercher l'élément UnorderedMap. Le type de *clé* est typename *K*.

### <a name="return-value"></a>Valeur de retour

**true** si la clé est trouvée ; sinon, **false**.

## <a name="insert"></a>  UnorderedMap::Insert Method

Ajoute une paire clé-valeur spécifiée à l'objet UnorderedMap actif.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Partie de clé de la paire clé-valeur. Le type de *clé* est typename *K*.

*value*<br/>
Partie de valeur de la paire clé-valeur. Le type de *valeur* est typename *V*.

### <a name="return-value"></a>Valeur de retour

**true** si la clé d’un élément existant dans l’objet Map actuel correspond à *clé* et la partie de la valeur de cet élément est définie sur *valeur*. **false** si aucun élément existant dans l’objet Map actuel correspond à *clé* et *clé* et *valeur* paramètres sont transformés en paire clé-valeur, puis ajoutés à la UnorderedMap actif.

## <a name="lookup"></a>  UnorderedMap::Lookup Method

Récupère la valeur du type V associé à la clé spécifiée de type K.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé utilisée pour rechercher un élément dans l'objet UnorderedMap. Le type de *clé* est typename *K*.

### <a name="return-value"></a>Valeur de retour

La valeur qui est associée à la *clé*. Le type de la valeur de retour est typename *V*.

## <a name="mapchanged"></a>  UnorderedMap::MapChanged

Se déclenche lorsqu'un élément est inséré ou supprimé dans le mappage.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Un [MapChangedEventHandler\<K, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) qui contient des informations sur l’objet qui a déclenché l’événement et le type de modification qui s’est produite. Voir aussi [IMapChangedEventArgs\<K >](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) et [énumération CollectionChange](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Équivalent .NET Framework

Les applications Windows Runtime qui nous c# ou Visual Basic projet IMap\<K, V > comme IDictionary\<K, V >.

## <a name="remove"></a>  Unorderedmap::Remove, méthode

Supprime la paire clé-valeur spécifiée de l'objet UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Partie de clé de la paire clé-valeur. Le type de *clé* est typename *K*.

## <a name="size"></a>  Unorderedmap::Size, méthode

Retourne le nombre de [Windows::Foundation::Collections::IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) éléments de l’objet UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments contenus dans l'objet Unordered.

## <a name="ctor"></a>  UnorderedMap::UnorderedMap, constructeur

Initialise une nouvelle instance de la classe UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
UnorderedMap();

explicit UnorderedMap(
    size_t n
    );

UnorderedMap(
    size_t n,
    const H& h
    );

UnorderedMap(
    size_t n,
    const H& h,
    const P& p
    );

explicit UnorderedMap(
    const std::unordered_map<K, V, H, P>& m
    );

explicit UnorderedMap(
    std::unordered_map<K, V, H, P>&& m
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p
    );
```

### <a name="parameters"></a>Paramètres

*InIt*<br/>
Nom de type du UnorderedMap actif.

*P*<br/>
Objet de fonction qui peut comparer deux clés pour déterminer si elles sont égales. Ce paramètre par défaut est [std::equal_to\<K >](../standard-library/equal-to-struct.md).

*H*<br/>
Objet de fonction qui génère une valeur de hachage pour les clés. Ce paramètre par défaut est [hash, classe 1](../standard-library/hash-class.md) pour les types de clé qui prend en charge de la classe.

*m*<br/>
Une référence ou [Lvalues et Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) à un [std::unordered_map](../standard-library/unordered-map-class.md) qui est utilisé pour initialiser le UnorderedMap actif.

*il*<br/>
Un [std::initializer_list](../standard-library/initializer-list-class.md) de [std::pair](../standard-library/pair-structure.md) objets qui est utilisé pour initialiser le map.

*first*<br/>
Itérateur d'entrée du premier élément d'une plage d'éléments utilisée pour initialiser le UnorderedMap actif.

*last*<br/>
Itérateur d'entrée du premier élément qui suit une plage d'éléments utilisée pour initialiser le UnorderedMap actif.

## <a name="see-also"></a>Voir aussi

[Plateforme Namespace](platform-namespace-c-cx.md)<br/>
[Platform::Collections, espace de noms](../cppcx/platform-collections-namespace.md)<br/>
[classe Platform::Collections::Map](../cppcx/platform-collections-map-class.md)<br/>
[Platform::Collections::UnorderedMapView, classe](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[Collections](../cppcx/collections-c-cx.md)<br/>
[Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
