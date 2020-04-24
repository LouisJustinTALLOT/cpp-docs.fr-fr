---
title: Platform::Collections::UnorderedMap, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: 80b46cb95f2fdb83922ca22e8aa06a89aca4bfde
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031496"
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

*C*<br/>
Type de la valeur dans la paire clé-valeur.

*C*<br/>
Type qui fournit un objet de fonction qui peut comparer deux valeurs d'élément comme des clés de tri pour déterminer leur ordre relatif dans le Map. Par défaut, [std::equal_to\<K>](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Notes

Les types autorisés sont :

- Entiers

- classe d’interface

- Classe ref publique ^

- value struct

- classe d'énumération publique

**UnorderedMap** est essentiellement un emballage pour [std::unordered_map](../standard-library/unordered-map-class.md) qui prend en charge le stockage des types Windows Runtime. Il s’agit d’une implémentation concrète de [windows:::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2) et [IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) types qui sont passés à travers les interfaces publiques Windows Runtime. Si vous tentez d'utiliser un type `Platform::Collections::UnorderedMap` dans une valeur de retour ou un paramètre public, l'erreur de compilateur C3986 est générée. Vous pouvez corriger l’erreur en modifiant le type du paramètre ou la valeur de retour par [Windows::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2).

Pour plus d’informations, voir [Collections](../cppcx/collections-c-cx.md).

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[UnorderedMap::UnorderedMap](#ctor)|Initialise une nouvelle instance de la classe Map.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[UnorderedMap::Clear](#clear)|Supprime toutes les paires clé-valeur de l'objet Map actuel.|
|[UnorderedMap::Première](#first)|Retourne un itérateur qui spécifie le premier élément de la carte.|
|[UnorderedMap::GetView](#getview)|Retourne une vue en lecture seule de la carte active, soit une classe Platform::Collections::UnorderedMapView.|
|[UnorderedMap::HasKey](#haskey)|Détermine si le Map actuel contient la clé spécifiée.|
|[UnorderedMap::Insert](#insert)|Ajoute une paire clé-valeur spécifiée à l'objet Map actuel.|
|[UnorderedMap::Lookup](#lookup)|Récupère l'élément à la clé spécifiée dans l'objet Map actuel.|
|[UnorderedMap::Supprimer](#remove)|Supprime la paire clé-valeur spécifiée de l'objet Map actuel.|
|[UnorderedMap::Taille](#size)|Retourne le nombre d'éléments dans l'objet Map actuel.|

### <a name="events"></a>Événements

|||
|-|-|
|Nom|Description|
|[Carte::MapChanged](#mapchanged) event|Se produit lorsque l'objet Map est modifié.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`UnorderedMap`

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="unorderedmapclear-method"></a><a name="clear"></a>UnorderedMap::Méthode claire

Supprime toutes les paires clé-valeur de l'objet UnorderedMap actif.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a>UnorderedMap::Première méthode

Retourne un itérateur qui spécifie le premier [Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) élément dans la carte non ordonnée.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui spécifie le premier élément de la carte.

### <a name="remarks"></a>Notes

Une façon pratique de tenir l’itérateur retourné par First() est d’attribuer la valeur de retour à une variable qui est déclarée avec le mot clé de déduction de type **automatique.** Par exemple : `auto x = myUnorderedMap->First();`.

## <a name="unorderedmapgetview-method"></a><a name="getview"></a>UnorderedMap::GetView Méthode

Renvoie une vue de lecture uniquement de l’actuel UnorderedMap; [c’est-à-dire, une plate-forme::Collections::UnorderedMapView Class](../cppcx/platform-collections-unorderedmapview-class.md) qui implémente le [Windows::Foundation::Collections:IMapView::IMapView](/uwp/api/windows.foundation.collections.imapview-2) interface.

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Valeur de retour

Objet `UnorderedMapView`.

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a>UnorderedMap::HasKey Méthode

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

**vrai** si la clé est trouvée; autrement, **faux**.

## <a name="unorderedmapinsert-method"></a><a name="insert"></a>UnorderedMap::Insert Method

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

**vrai** si la clé d’un élément existant dans la carte actuelle correspond à la *clé* et que la partie valeur de cet élément est définie pour *la valeur*. **faux** si aucun élément existant dans la carte actuelle correspond à la *clé* et les paramètres *de clé* et de *valeur* sont transformés en une paire de valeur clé, puis ajouté à l’actuel UnorderedMap.

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a>UnorderedMap::Méthode lookup

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

La valeur qui est jumelée à la *clé*. Le type de valeur de retour est typename *V*.

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a>UnorderedMap::MapChanged

Se déclenche lorsqu'un élément est inséré ou supprimé dans le mappage.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Un [MapChangedEventHandler\<K,V>](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) qui contient des informations sur l’objet qui a soulevé l’événement, et le genre de changement qui s’est produit. Voir aussi [IMapChangedEventArgs\<K>](/uwp/api/windows.foundation.collections.imapchangedeventargs-1) et [CollectionChange Enumeration](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Équivalent .NET Framework

Applications Windows Runtime que nous C ou\<Visual Basic projet IMap K,V> comme IDictionary\<K,V>.

## <a name="unorderedmapremove-method"></a><a name="remove"></a>UnorderedMap::Supprimer la méthode

Supprime la paire clé-valeur spécifiée de l'objet UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Partie de clé de la paire clé-valeur. Le type de *clé* est typename *K*.

## <a name="unorderedmapsize-method"></a><a name="size"></a>UnorderedMap::Méthode de taille

Retourne le nombre de [Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) éléments dans le UnorderedMap.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments contenus dans l'objet Unordered.

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a>UnorderedMap::UnorderedMap Constructor

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

*Init*<br/>
Nom de type du UnorderedMap actif.

*P*<br/>
Objet de fonction qui peut comparer deux clés pour déterminer si elles sont égales. Ce paramètre par défaut à [std:equal_to\<K>](../standard-library/equal-to-struct.md).

*H (en)*<br/>
Objet de fonction qui génère une valeur de hachage pour les clés. Ce paramètre est par défaut pour [hachage classe 1](../standard-library/hash-class.md) pour les types clés que la classe prend en charge.

*M*<br/>
Une référence ou [Lvalues et Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) à un [std::unordered_map](../standard-library/unordered-map-class.md) qui est utilisé pour initialiser l’actuel UnorderedMap.

*il*<br/>
Une [std::initializer_list](../standard-library/initializer-list-class.md) [d’objets d’escalier :p](../standard-library/pair-structure.md) qui est utilisé pour initialiser la carte.

*first*<br/>
Itérateur d'entrée du premier élément d'une plage d'éléments utilisée pour initialiser le UnorderedMap actif.

*last*<br/>
Itérateur d'entrée du premier élément qui suit une plage d'éléments utilisée pour initialiser le UnorderedMap actif.

## <a name="see-also"></a>Voir aussi

[Espace nom de la plate-forme](platform-namespace-c-cx.md)<br/>
[Platform::Collections, espace de noms](../cppcx/platform-collections-namespace.md)<br/>
[classe Platform::Collections::Map](../cppcx/platform-collections-map-class.md)<br/>
[Platform::Collections::UnorderedMapView, classe](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[Regroupements](../cppcx/collections-c-cx.md)<br/>
[Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
