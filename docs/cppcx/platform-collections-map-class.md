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
ms.openlocfilehash: 0ddb15507c97c0dfff48575e476b57fe91359239
ms.sourcegitcommit: 65fead53d56d531d71be42216056aca5f44def11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88610905"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map, classe

Représente *une carte*qui est une collection de paires clé-valeur. Implémente [Windows :: Foundation :: Collections :: IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) pour faciliter la [liaison de données](/windows/uwp/data-binding/data-binding-in-depth)XAML.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>Paramètres

*DK*<br/>
Type de la clé dans la paire clé-valeur.

*V*<br/>
Type de la valeur dans la paire clé-valeur.

*C*<br/>
Type qui fournit un objet de fonction qui peut comparer deux valeurs d'élément comme des clés de tri pour déterminer leur ordre relatif dans le Map. Par défaut, [std :: less \<K> ](../standard-library/less-struct.md).

*__is_valid_winrt_type ()* Fonction générée par le compilateur qui valide le type de *K* et de *V* et fournit un message d’erreur convivial si le type ne peut pas être stocké dans la classe Map.

### <a name="remarks"></a>Notes

Les types autorisés sont :

- entiers

- classe d’interface ^

- Classe ref publique ^

- value struct

- classe d'énumération publique

Map est essentiellement un wrapper pour [std::map](../standard-library/map-class.md). Il s’agit d’une implémentation concrète C++ des types [Windows :: Foundation :: Collections : \<Windows::Foundation::Collections::IKeyValuePair\<K,V> > : IMap](/uwp/api/windows.foundation.collections.imap-2) et [IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) qui sont passés sur des interfaces de Windows Runtime publiques. Si vous tentez d'utiliser un type `Platform::Collections::Map` dans une valeur de retour ou un paramètre public, l'erreur de compilateur C3986 est générée. Vous pouvez corriger l’erreur en remplaçant le type du paramètre ou de la valeur de retour par [Windows :: Foundation :: Collections : \<K,V> : IMap](/uwp/api/windows.foundation.collections.imap-2).

Pour plus d’informations, consultez [Collections](../cppcx/collections-c-cx.md).

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Mappage :: mapper](#ctor)|Initialise une nouvelle instance de la classe Map.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Mappage :: effacer](#clear)|Supprime toutes les paires clé-valeur de l'objet Map actuel.|
|[Map :: First](#first)|Retourne un itérateur qui spécifie le premier élément de la carte.|
|[Map :: GetView](#getview)|Retourne une vue en lecture seule du Map actif ; autrement dit, [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md).|
|[Map :: Haskey,](#haskey)|Détermine si le Map actuel contient la clé spécifiée.|
|[Carte :: Insert](#insert)|Ajoute une paire clé-valeur spécifiée à l'objet Map actuel.|
|[Mappage :: Lookup](#lookup)|Récupère l'élément à la clé spécifiée dans l'objet Map actuel.|
|[Map::Remove](#remove)|Supprime la paire clé-valeur spécifiée de l'objet Map actuel.|
|[Map :: Size](#size)|Retourne le nombre d'éléments dans l'objet Map actuel.|

### <a name="events"></a>Événements

|||
|-|-|
|Nom|Description|
|[Map :: MapChanged](#mapchanged) , événement|Se produit lorsque l'objet Map est modifié.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Map`

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="mapclear-method"></a><a name="clear"></a> Map :: Clear, méthode

Supprime toutes les paires clé-valeur de l'objet Map actuel.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="mapfirst-method"></a><a name="first"></a> Map :: First, méthode

Retourne un itérateur qui spécifie le premier élément de la classe Map, ou **`nullptr`** si le mappage est vide.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui spécifie le premier élément de la carte.

### <a name="remarks"></a>Notes

Un moyen pratique de contenir l’itérateur retourné par First () consiste à affecter la valeur de retour à une variable déclarée avec le **`auto`** mot clé de déduction de type. Par exemple : `auto x = myMap->First();`.

## <a name="mapgetview-method"></a><a name="getview"></a> Map :: GetView, méthode

Retourne une vue en lecture seule du mappage en cours ; autrement dit, une [classe Platform :: Collections :: MapView](../cppcx/platform-collections-mapview-class.md), qui implémente l’interface [Windows :: Foundation :: Collections :: \<K,V> IMapView](/uwp/api/windows.foundation.collections.imapview-2) .

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Valeur de retour

Objet `MapView`.

## <a name="maphaskey-method"></a><a name="haskey"></a> Map :: Haskey,, méthode

Détermine si le Map actuel contient la clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé utilisée pour rechercher l’élément Map. Le type de *clé* est TypeName *K*.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la clé est trouvée ; Sinon, **`false`** .

## <a name="mapinsert-method"></a><a name="insert"></a> Map :: Insert, méthode

Ajoute une paire clé-valeur spécifiée à l'objet Map actuel.

### <a name="syntax"></a>Syntaxe

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Partie de clé de la paire clé-valeur. Le type de *clé* est TypeName *K*.

*value*<br/>
Partie de valeur de la paire clé-valeur. Le type de *valeur* est TypeName *V*.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la clé d’un élément existant dans le mappage actuel correspond à la *clé* et que la partie valeur de cet élément est définie sur *valeur*. **`false`** Si aucun élément existant dans le mappage actuel ne correspond à la *clé* et que les paramètres de *clé* et de *valeur* sont définis dans une paire clé-valeur, puis ajoutés au mappage en cours.

## <a name="maplookup-method"></a><a name="lookup"></a> Map :: Lookup, méthode

Récupère la valeur de type V associée à la clé spécifiée de type K si la clé existe.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé utilisée pour trouver un élément dans le Map. Le type de *clé* est TypeName *K*.

### <a name="return-value"></a>Valeur de retour

Valeur associée à la *clé*. Le type de la valeur de retour est TypeName *V*.

### <a name="remarks"></a>Notes

Si la clé n’existe pas, une exception [Platform :: OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) est levée.

## <a name="mapmap-constructor"></a><a name="ctor"></a> Map :: Map, constructeur

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

*Rein*<br/>
Nom de type de l'objet Map actuel.

*comp*<br/>
Type qui fournit un objet de fonction qui peut comparer deux valeurs d'élément comme des clés de tri pour déterminer leur ordre relatif dans le Map.

*lecteur*<br/>
Référence ou [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) à un `map Class` utilisé pour initialiser le mappage actuel.

*first*<br/>
Itérateur d'entrée du premier élément d'une plage d'éléments utilisée pour initialiser le Map actuel.

*last*<br/>
Itérateur d'entrée du premier élément qui suit une plage d'éléments utilisée pour initialiser le Map actuel.

## <a name="mapmapchanged-event"></a><a name="mapchanged"></a> Map :: MapChanged, événement

Se déclenche lorsqu'un élément est inséré ou supprimé dans le mappage.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

[MapChangedEventHandler \<K,V> ](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) qui contient des informations sur l’objet qui a déclenché l’événement et le type de modification qui s’est produit. Voir aussi l' [énumération](/uwp/api/windows.foundation.collections.collectionchange) [IMapChangedEventArgs \<K> ](/uwp/api/windows.foundation.collections.imapchangedeventargs-1) et CollectionChange.

## <a name="net-framework-equivalent"></a>Équivalent .NET Framework

Windows Runtime les applications qui utilisent C# ou Visual Basic projet IMap \<K,V> comme IDictionary \<K,V> .

## <a name="mapremove-method"></a><a name="remove"></a> Map :: Remove, méthode

Supprime la paire clé-valeur spécifiée de l'objet Map actuel.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Partie de clé de la paire clé-valeur. Le type de *clé* est TypeName *K*.

## <a name="mapsize-method"></a><a name="size"></a> Map :: Size, méthode

Retourne le nombre d’éléments [Windows :: Foundation :: Collections :: \<K,V> IKeyValuePair](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) dans la classe Map.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments du Map.

## <a name="see-also"></a>Voir aussi

[Collections (C++/CX)](collections-c-cx.md)<br/>
[Espace de noms de plateforme](platform-namespace-c-cx.md)<br/>
[Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
