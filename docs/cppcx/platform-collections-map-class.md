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
ms.openlocfilehash: 81721d719a424250beed89f4a5656b3f2fc27922
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816297"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map, classe

Représente *une carte*qui est une collection de paires clé-valeur. Implémente [Windows :: Foundation :: Collections :: IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap_k_v_) pour faciliter la [liaison de données](/windows/uwp/data-binding/data-binding-in-depth)XAML.

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
Type qui fournit un objet de fonction qui peut comparer deux valeurs d'élément comme des clés de tri pour déterminer leur ordre relatif dans le Map. Par défaut, [std :: less @ no__t-1k >](../standard-library/less-struct.md).

*__is_valid_winrt_type ()* Fonction générée par le compilateur qui valide le type de *K* et de *V* et fournit un message d’erreur convivial si le type ne peut pas être stocké dans la classe Map.

### <a name="remarks"></a>Notes

Les types autorisés sont les suivants :

- Entiers

- classe d’interface ^

- Classe ref publique ^

- value struct

- classe d'énumération publique

Map est essentiellement un wrapper pour [std::map](../standard-library/map-class.md). Il s’agit C++ d’une implémentation concrète des types [Windows :: Foundation :: Collections :: IMap < Windows :: Foundation :: Collections :: IKeyValuePair @ no__t-2k, V > >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) et [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) qui sont passés dans les fenêtres publiques Interfaces d’exécution. Si vous tentez d'utiliser un type `Platform::Collections::Map` dans une valeur de retour ou un paramètre public, l'erreur de compilateur C3986 est générée. Vous pouvez corriger l’erreur en remplaçant le type du paramètre ou de la valeur de retour par [Windows :: Foundation :: Collections :: IMap @ no__t-1K, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Pour plus d’informations, consultez [Collections](../cppcx/collections-c-cx.md).

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Map::Map](#ctor)|Initialise une nouvelle instance de la classe Map.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Map::Clear](#clear)|Supprime toutes les paires clé-valeur de l'objet Map actuel.|
|[Map::First](#first)|Retourne un itérateur qui spécifie le premier élément de la carte.|
|[Map :: GetView](#getview)|Retourne une vue en lecture seule du Map actif ; autrement dit, [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md).|
|[Map::HasKey](#haskey)|Détermine si le Map actuel contient la clé spécifiée.|
|[Carte :: Insert](#insert)|Ajoute une paire clé-valeur spécifiée à l'objet Map actuel.|
|[Map::Lookup](#lookup)|Récupère l'élément à la clé spécifiée dans l'objet Map actuel.|
|[Map::Remove](#remove)|Supprime la paire clé-valeur spécifiée de l'objet Map actuel.|
|[Map :: Size](#size)|Retourne le nombre d'éléments dans l'objet Map actuel.|

### <a name="events"></a>Events

|||
|-|-|
|Name|Description|
|[Map :: MapChanged](#mapchanged) , événement|Se produit lorsque l'objet Map est modifié.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Map`

### <a name="requirements"></a>Configuration requise

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="clear"></a>Map :: Clear, méthode

Supprime toutes les paires clé-valeur de l'objet Map actuel.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Clear();
```

## <a name="first"></a>Map :: First, méthode

Retourne un itérateur qui spécifie le premier élément de la carte ou `nullptr` si la carte est vide.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui spécifie le premier élément de la carte.

### <a name="remarks"></a>Notes

Un moyen pratique de contenir l’itérateur retourné par First () consiste à affecter la valeur de retour à une variable déclarée avec le mot clé de déduction de type **auto** . Par exemple, `auto x = myMap->First();`.

## <a name="getview"></a>Map :: GetView, méthode

Retourne une vue en lecture seule du mappage en cours ; autrement dit, une [classe Platform :: Collections :: MapView](../cppcx/platform-collections-mapview-class.md), qui implémente l’interface [Windows :: Foundation :: Collections :: IMapView @ No__t-1K, V >]/UWP/API/Windows.Foundation.Collections.IMapView_K_V_).

### <a name="syntax"></a>Syntaxe

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Valeur de retour

Objet `MapView`.

## <a name="haskey"></a>Map :: Haskey,, méthode

Détermine si le Map actuel contient la clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé utilisée pour rechercher l’élément Map. Le type de *clé* est TypeName *K*.

### <a name="return-value"></a>Valeur de retour

**true** si la clé est trouvée ; Sinon, **false**.

## <a name="insert"></a>Map :: Insert, méthode

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

**true** si la clé d’un élément existant dans la classe Map actuelle correspond à la *clé* et que la partie valeur de cet élément est définie sur *value*. **false** si aucun élément existant dans le mappage actuel ne correspond à la *clé* et que les paramètres de *clé* et de *valeur* sont définis dans une paire clé-valeur, puis ajoutés au mappage en cours.

## <a name="lookup"></a>Map :: Lookup, méthode

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

## <a name="ctor"></a>Map :: Map, constructeur

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

*InIt*<br/>
Nom de type de l'objet Map actuel.

*comp*<br/>
Type qui fournit un objet de fonction qui peut comparer deux valeurs d'élément comme des clés de tri pour déterminer leur ordre relatif dans le Map.

*m*<br/>
Référence ou [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) à un `map Class` qui est utilisé pour initialiser le mappage actuel.

*first*<br/>
Itérateur d'entrée du premier élément d'une plage d'éléments utilisée pour initialiser le Map actuel.

*last*<br/>
Itérateur d'entrée du premier élément qui suit une plage d'éléments utilisée pour initialiser le Map actuel.

## <a name="mapchanged"></a>Map :: MapChanged, événement

Se déclenche lorsqu'un élément est inséré ou supprimé dans le mappage.

### <a name="syntax"></a>Syntaxe

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

[MapChangedEventHandler @ no__t-1K, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) qui contient des informations sur l’objet qui a déclenché l’événement et le type de modification qui s’est produit. Voir aussi [IMapChangedEventArgs @ no__t-1k >](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) et [énumération CollectionChange](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Équivalent .NET Framework

Windows Runtime les applications qui C# utilisent ou Visual Basic projet IMap @ No__t-1K, v > comme IDictionary @ No__t-2k, v >.

## <a name="remove"></a>Map :: Remove, méthode

Supprime la paire clé-valeur spécifiée de l'objet Map actuel.

### <a name="syntax"></a>Syntaxe

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Partie de clé de la paire clé-valeur. Le type de *clé* est TypeName *K*.

## <a name="size"></a>Map :: Size, méthode

Retourne le nombre d’éléments [Windows :: Foundation :: Collections :: IKeyValuePair @ no__t-1K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) dans le mappage.

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
