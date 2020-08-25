---
title: Platform::Collections::UnorderedMap, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: ec458f5d4a47b6eced939c4fe346d5d0414ea7c2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839125"
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

*DK*<br/>
Type de la clé dans la paire clé-valeur.

*V*<br/>
Type de la valeur dans la paire clé-valeur.

*C*<br/>
Type qui fournit un objet de fonction qui peut comparer deux valeurs d'élément comme des clés de tri pour déterminer leur ordre relatif dans le Map. Par défaut, [std :: equal_to \<K> ](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Notes

Les types autorisés sont :

- entiers

- classe d’interface ^

- Classe ref publique ^

- value struct

- classe d'énumération publique

**UnorderedMap** est fondamentalement un wrapper pour [std :: unordered_map](../standard-library/unordered-map-class.md) qui prend en charge le stockage de types de Windows Runtime. Il s’agit d’une implémentation concrète des types [Windows :: Foundation :: Collections :: IMap](/uwp/api/windows.foundation.collections.imap-2) et [IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) qui sont passés sur des interfaces Windows Runtime publiques. Si vous tentez d'utiliser un type `Platform::Collections::UnorderedMap` dans une valeur de retour ou un paramètre public, l'erreur de compilateur C3986 est générée. Vous pouvez corriger l’erreur en modifiant le type du paramètre ou la valeur de retour par [Windows::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2).

Pour plus d’informations, consultez [Collections](../cppcx/collections-c-cx.md).

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[UnorderedMap :: UnorderedMap](#ctor)|Initialise une nouvelle instance de la classe Map.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[UnorderedMap :: Clear](#clear)|Supprime toutes les paires clé-valeur de l'objet Map actuel.|
|[UnorderedMap :: First](#first)|Retourne un itérateur qui spécifie le premier élément de la carte.|
|[UnorderedMap :: GetView](#getview)|Retourne une vue en lecture seule de la carte active, soit une classe Platform::Collections::UnorderedMapView.|
|[UnorderedMap :: Haskey,](#haskey)|Détermine si le Map actuel contient la clé spécifiée.|
|[UnorderedMap :: Insert](#insert)|Ajoute une paire clé-valeur spécifiée à l'objet Map actuel.|
|[UnorderedMap :: Lookup](#lookup)|Récupère l'élément à la clé spécifiée dans l'objet Map actuel.|
|[UnorderedMap :: Remove](#remove)|Supprime la paire clé-valeur spécifiée de l'objet Map actuel.|
|[UnorderedMap :: Size](#size)|Retourne le nombre d'éléments dans l'objet Map actuel.|

### <a name="events"></a>Événements

| Nom | Description |
|--|--|
| [Map :: MapChanged](#mapchanged) , événement | Se produit lorsque l'objet Map est modifié. |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`UnorderedMap`

### <a name="requirements"></a>Configuration requise

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="unorderedmapclear-method"></a><a name="clear"></a> UnorderedMap :: Clear, méthode

Supprime toutes les paires clé-valeur de l'objet UnorderedMap actif.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a> UnorderedMap :: First, méthode

Retourne un itérateur qui spécifie le premier élément [Windows :: Foundation :: Collections : \<K,V> : IKeyValuePair](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) dans le mappage non ordonné.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui spécifie le premier élément de la carte.

### <a name="remarks"></a>Notes

Un moyen pratique de contenir l’itérateur retourné par First () consiste à affecter la valeur de retour à une variable déclarée avec le **`auto`** mot clé de déduction de type. Par exemple : `auto x = myUnorderedMap->First();`.

## <a name="unorderedmapgetview-method"></a><a name="getview"></a> UnorderedMap :: GetView, méthode

Retourne une vue en lecture seule du UnorderedMap actif ; autrement dit, une [classe Platform :: Collections :: UnorderedMapView](../cppcx/platform-collections-unorderedmapview-class.md) qui implémente l’interface [Windows :: Foundation :: Collections :: IMapView :: IMapView](/uwp/api/windows.foundation.collections.imapview-2) .

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Valeur de retour

Objet `UnorderedMapView`.

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a> UnorderedMap :: Haskey,, méthode

Détermine si le UnorderedMap actif contient la clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé utilisée pour rechercher l'élément UnorderedMap. Le type de *clé* est TypeName *K*.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la clé est trouvée ; Sinon, **`false`** .

## <a name="unorderedmapinsert-method"></a><a name="insert"></a> UnorderedMap :: Insert, méthode

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
Partie de clé de la paire clé-valeur. Le type de *clé* est TypeName *K*.

*value*<br/>
Partie de valeur de la paire clé-valeur. Le type de *valeur* est TypeName *V*.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la clé d’un élément existant dans le mappage actuel correspond à la *clé* et que la partie valeur de cet élément est définie sur *valeur*. **`false`** Si aucun élément existant dans le mappage actuel ne correspond à la *clé* et que les paramètres de *clé* et de *valeur* sont définis dans une paire clé-valeur, puis ajoutés au UnorderedMap actuel.

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a> UnorderedMap :: Lookup, méthode

Récupère la valeur du type V associé à la clé spécifiée de type K.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé utilisée pour rechercher un élément dans l'objet UnorderedMap. Le type de *clé* est TypeName *K*.

### <a name="return-value"></a>Valeur renvoyée

Valeur associée à la *clé*. Le type de la valeur de retour est TypeName *V*.

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a> UnorderedMap :: MapChanged

Se déclenche lorsqu'un élément est inséré ou supprimé dans le mappage.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

[MapChangedEventHandler \<K,V> ](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) qui contient des informations sur l’objet qui a déclenché l’événement et le type de modification qui s’est produit. Voir aussi l' [énumération](/uwp/api/windows.foundation.collections.collectionchange) [IMapChangedEventArgs \<K> ](/uwp/api/windows.foundation.collections.imapchangedeventargs-1) et CollectionChange.

## <a name="net-framework-equivalent"></a>Équivalent .NET Framework

Windows Runtime les applications qui sont C# ou Visual Basic projet IMap \<K,V> en tant que IDictionary \<K,V> .

## <a name="unorderedmapremove-method"></a><a name="remove"></a> UnorderedMap :: Remove, méthode

Supprime la paire clé-valeur spécifiée de l'objet UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Partie de clé de la paire clé-valeur. Le type de *clé* est TypeName *K*.

## <a name="unorderedmapsize-method"></a><a name="size"></a> UnorderedMap :: Size, méthode

Retourne le nombre d’éléments [Windows :: Foundation :: Collections :: \<K,V> IKeyValuePair](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) dans le UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments contenus dans l'objet Unordered.

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a> UnorderedMap :: UnorderedMap, constructeur

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

*Rein*<br/>
Nom de type du UnorderedMap actif.

*P*<br/>
Objet de fonction qui peut comparer deux clés pour déterminer si elles sont égales. La valeur par défaut de ce paramètre est [STD \<K> :: equal_to](../standard-library/equal-to-struct.md).

*H*<br/>
Objet de fonction qui génère une valeur de hachage pour les clés. Par défaut, ce paramètre est la [classe de hachage 1](../standard-library/hash-class.md) pour les types de clés pris en charge par la classe.

*lecteur*<br/>
Une référence ou [lvalues et rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) à un [std :: unordered_map](../standard-library/unordered-map-class.md) qui est utilisé pour initialiser le UnorderedMap actuel.

*II*<br/>
[Std :: initializer_list](../standard-library/initializer-list-class.md) d’objets de l' [air std ::p](../standard-library/pair-structure.md) utilisé pour initialiser le mappage.

*first*<br/>
Itérateur d'entrée du premier élément d'une plage d'éléments utilisée pour initialiser le UnorderedMap actif.

*last*<br/>
Itérateur d'entrée du premier élément qui suit une plage d'éléments utilisée pour initialiser le UnorderedMap actif.

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](platform-namespace-c-cx.md)<br/>
[Espace de noms Platform :: Collections](../cppcx/platform-collections-namespace.md)<br/>
[Platform :: Collections :: Map, classe](../cppcx/platform-collections-map-class.md)<br/>
[Platform :: Collections :: UnorderedMapView, classe](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[Regroupements](../cppcx/collections-c-cx.md)<br/>
[Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
