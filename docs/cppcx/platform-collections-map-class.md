---
title: Platform::Collections::Map, classe
ms.date: 10/01/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Map::Map
- COLLECTION/Platform::Collections::Map::Clear
- COLLECTION/Platform::Collections::Map::First
- COLLECTION/Platform::Collections::Map::GetView
- COLLECTION/Platform::Collections::Map::HasKey
- COLLECTION/Platform::Collections::Map::Insert
- COLLECTION/Platform::Collections::Map::Lookup
- COLLECTION/Platform::Collections::Map::Remove
- COLLECTION/Platform::Collections::Map::Size
helpviewer_keywords:
- Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
ms.openlocfilehash: 7f41a924811be95160b06a2097db6103cde8fc11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354446"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map, classe

Représente *une carte*qui est une collection de paires clé-valeur. Implémente [Windows::Foundation:Collections::IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap_k_v_) pour aider avec XAML [liaison de données](/windows/uwp/data-binding/data-binding-in-depth).

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>Paramètres

*K*<br/>
Type de la clé dans la paire clé-valeur.

*V*<br/>
Type de la valeur dans la paire clé-valeur.

*C*<br/>
Type qui fournit un objet de fonction qui peut comparer deux valeurs d'élément comme des clés de tri pour déterminer leur ordre relatif dans le Map. Par défaut, [\<std::moins K>](../standard-library/less-struct.md).

*__is_valid_winrt_type()* Une fonction générée par compilateur qui valide le type de *K* et *V* et fournit un message d’erreur convivial si le type ne peut pas être stocké dans la carte.

### <a name="remarks"></a>Notes

Les types autorisés sont :

- Entiers

- classe d’interface

- Classe ref publique ^

- value struct

- classe d'énumération publique

Map est essentiellement un wrapper pour [std::map](../standard-library/map-class.md). Il s’agit d’une implémentation concrète de [la Windows:::Foundation::Collections::IMap<Windows:::Foundation::Collections::IKeyValuePair\<K,V>>](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) et [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) types qui sont passés à travers les interfaces publiques Windows Runtime. Si vous tentez d'utiliser un type `Platform::Collections::Map` dans une valeur de retour ou un paramètre public, l'erreur de compilateur C3986 est générée. Vous pouvez corriger l’erreur en changeant le type du paramètre ou la valeur de retour à [Windows::Foundation::Collections::IMap\<K,V>](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Pour plus d’informations, voir [Collections](../cppcx/collections-c-cx.md).

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Carte::Carte](#ctor)|Initialise une nouvelle instance de la classe Map.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Carte::Clear](#clear)|Supprime toutes les paires clé-valeur de l'objet Map actuel.|
|[Carte::First](#first)|Retourne un itérateur qui spécifie le premier élément de la carte.|
|[Carte::GetView](#getview)|Retourne une vue en lecture seule du Map actif ; autrement dit, [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md).|
|[Carte::HasKey](#haskey)|Détermine si le Map actuel contient la clé spécifiée.|
|[Carte::Insert](#insert)|Ajoute une paire clé-valeur spécifiée à l'objet Map actuel.|
|[Carte::Lookup](#lookup)|Récupère l'élément à la clé spécifiée dans l'objet Map actuel.|
|[Map::Remove](#remove)|Supprime la paire clé-valeur spécifiée de l'objet Map actuel.|
|[Carte::Size](#size)|Retourne le nombre d'éléments dans l'objet Map actuel.|

### <a name="events"></a>Événements

|||
|-|-|
|Nom|Description|
|[Carte::MapChanged](#mapchanged) event|Se produit lorsque l'objet Map est modifié.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Map`

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="mapclear-method"></a><a name="clear"></a>Carte::Méthode claire

Supprime toutes les paires clé-valeur de l'objet Map actuel.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="mapfirst-method"></a><a name="first"></a>Carte::Première méthode

Retourne un itérateur qui spécifie le premier élément de la carte ou `nullptr` si la carte est vide.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui spécifie le premier élément de la carte.

### <a name="remarks"></a>Notes

Une façon pratique de tenir l’itérateur retourné par First() est d’attribuer la valeur de retour à une variable qui est déclarée avec le mot clé de déduction de type **automatique.** Par exemple : `auto x = myMap->First();`.

## <a name="mapgetview-method"></a><a name="getview"></a>Carte::GetView Méthode

Renvoie une vue de lecture uniquement de la carte actuelle; [c’est-à-dire, une plate-forme::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md), qui implémente\<l’interface [Windows::Foundation::Collections::IMapView K,V>]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) interface.

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Valeur de retour

Objet `MapView` .

## <a name="maphaskey-method"></a><a name="haskey"></a>Carte::HasKey Méthode

Détermine si le Map actuel contient la clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé utilisée pour rechercher l’élément Map. Le type de *clé* est typename *K*.

### <a name="return-value"></a>Valeur de retour

**vrai** si la clé est trouvée; autrement, **faux**.

## <a name="mapinsert-method"></a><a name="insert"></a>Carte::Insert Method

Ajoute une paire clé-valeur spécifiée à l'objet Map actuel.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Partie de clé de la paire clé-valeur. Le type de *clé* est typename *K*.

*value*<br/>
Partie de valeur de la paire clé-valeur. Le type de *valeur* est typename *V*.

### <a name="return-value"></a>Valeur de retour

**vrai** si la clé d’un élément existant dans la carte actuelle correspond à la *clé* et que la partie valeur de cet élément est définie pour *la valeur*. **faux** si aucun élément existant dans la carte actuelle correspond à la *clé* et les paramètres *de clé* et de *valeur* sont transformés en une paire de valeur clé, puis ajouté à la carte actuelle.

## <a name="maplookup-method"></a><a name="lookup"></a>Carte::Méthode Lookup

Récupère la valeur de type V associée à la clé spécifiée de type K si la clé existe.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé utilisée pour trouver un élément dans le Map. Le type de *clé* est typename *K*.

### <a name="return-value"></a>Valeur de retour

La valeur qui est jumelée à la *clé*. Le type de valeur de retour est typename *V*.

### <a name="remarks"></a>Notes

Si la clé n’existe pas, alors une [plate-forme::OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) est jeté.

## <a name="mapmap-constructor"></a><a name="ctor"></a>Carte::Map Constructor

Initialise une nouvelle instance de la classe Map.

### <a name="syntax"></a>Syntaxe

```cpp
explicit Map(const C& comp = C());
explicit Map(const StdMap& m);
explicit Map(StdMap&& m ;
template <typename InIt>
Map(
   InItfirst,
   InItlast,
   const C& comp = C());
```

### <a name="parameters"></a>Paramètres

*Init*<br/>
Nom de type de l'objet Map actuel.

*Comp*<br/>
Type qui fournit un objet de fonction qui peut comparer deux valeurs d'élément comme des clés de tri pour déterminer leur ordre relatif dans le Map.

*M*<br/>
Une référence ou [une](../cpp/lvalues-and-rvalues-visual-cpp.md) `map Class` évaluation à un qui est utilisé pour initialiser la carte actuelle.

*Première*<br/>
Itérateur d'entrée du premier élément d'une plage d'éléments utilisée pour initialiser le Map actuel.

*Dernière*<br/>
Itérateur d'entrée du premier élément qui suit une plage d'éléments utilisée pour initialiser le Map actuel.

## <a name="mapmapchanged-event"></a><a name="mapchanged"></a>Carte::MapChanged Event

Se déclenche lorsqu'un élément est inséré ou supprimé dans le mappage.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Un [MapChangedEventHandler\<K,V>](/uwp/api/windows.foundation.collections.mapchangedeventhandler) qui contient des informations sur l’objet qui a soulevé l’événement, et le genre de changement qui s’est produit. Voir aussi [IMapChangedEventArgs\<K>](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) et [CollectionChange Enumeration](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Équivalent .NET Framework

Les applications Windows Runtime qui utilisent le\<projet IMap K,V>\<comme IDictionary K,V>.

## <a name="mapremove-method"></a><a name="remove"></a>Carte::Supprimer la méthode

Supprime la paire clé-valeur spécifiée de l'objet Map actuel.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Partie de clé de la paire clé-valeur. Le type de *clé* est typename *K*.

## <a name="mapsize-method"></a><a name="size"></a>Carte::Méthode de taille

Retourne le nombre de [Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) éléments de la carte.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments du Map.

## <a name="see-also"></a>Voir aussi

[Collections (C/CX)](collections-c-cx.md)<br/>
[Espace nom de la plate-forme](platform-namespace-c-cx.md)<br/>
[Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
