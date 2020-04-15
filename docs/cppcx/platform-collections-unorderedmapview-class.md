---
title: Platform::Collections::UnorderedMapView, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: 8f8bc3490fba28232cdab3ea189dd9cfcc8d0650
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354394"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView, classe

Représente une vue en lecture seule dans une *carte*, qui est une collection de paires clé/valeur.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename K,
   typename V,
   typename C = ::std::equal_to<K>>
ref class UnorderedMapView sealed;
```

#### <a name="parameters"></a>Paramètres

*K*<br/>
Type de la clé dans la paire clé-valeur.

*V*<br/>
Type de la valeur dans la paire clé-valeur.

*C*<br/>
Type qui fournit un objet de fonction qui peut comparer l'égalité de deux valeurs de clés. Par défaut, [std::equal_to\<K>](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>Notes

UnorderedMapView est une implémentation concrète de [la Windows::Foundation::Collections::IMapView\<K,V>](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) interface qui est passée à travers l’interface binaire d’application (ABI). Pour plus d'informations, consultez [Collections (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[UnorderedMapView::UnorderedMapView](#ctor)|Initialise une nouvelle instance de la classe UnorderedMapView.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[UnorderedMapView::D’abord](#first)|Retourne un itérateur qui est initialisé au premier élément de la vue cartographique.|
|[UnorderedMapView::HasKey](#haskey)|Détermine si le UnorderedMapView actuel contient la clé spécifiée.|
|[UnorderedMapView::Lookup](#lookup)|Récupère l'élément à la clé spécifiée dans l'objet UnorderedMapView actuel.|
|[UnorderedMapView::Taille](#size)|Retourne le nombre d'éléments de l'objet UnorderedMapView actuel.|
|[UnorderedMapView::Split](#split)|Fractionne un objet UnorderedMapView d'origine en deux objets UnorderedMapView.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`UnorderedMapView`

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="unorderedmapviewfirst-method"></a><a name="first"></a>UnorderedMapView::Première méthode

Retourne un itérateur qui spécifie le premier [Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) élément dans la carte non ordonnée.

### <a name="syntax"></a>Syntaxe

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui spécifie le premier élément de la vue cartographique.

### <a name="remarks"></a>Notes

Une façon pratique de tenir l’itérateur retourné par First() est d’attribuer la valeur de retour à une variable qui est déclarée avec le mot clé de déduction de type **automatique.** Par exemple : `auto x = myMapView->First();`.

## <a name="unorderedmapviewhaskey-method"></a><a name="haskey"></a>UnorderedMapView::HasKey Méthode

Détermine si le UnorderedMap actif contient la clé spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé utilisée pour rechercher l'élément. Le type `key` de est nom de type *K*.

### <a name="return-value"></a>Valeur de retour

**vrai** si la clé est trouvée; autrement, **faux**.

## <a name="unorderedmapviewlookup-method"></a><a name="lookup"></a>UnorderedMapView::Méthode Lookup

Récupère la valeur du type V associé à la clé spécifiée de type K.

### <a name="syntax"></a>Syntaxe

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé utilisée pour rechercher un élément dans le UnorderedMapView. Le type `key` de est nom de type *K*.

### <a name="return-value"></a>Valeur de retour

Valeur associée à `key`. Le type de valeur de retour est typename *V*.

## <a name="unorderedmapviewsize-method"></a><a name="size"></a>UnorderedMapView::Méthode de taille

Retourne le nombre de [Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) éléments dans le UnorderedMapView.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments contenus dans l'objet UnorderedMapView actif.

## <a name="unorderedmapviewsplit-method"></a><a name="split"></a>UnorderedMapView::Méthode split

Divise l'objet UnorderedMapView actif en deux objets UnorderedMapView. Cette méthode n'est pas opérationnelle.

### <a name="syntax"></a>Syntaxe

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * secondPartition);
```

### <a name="parameters"></a>Paramètres

*firstPartition*<br/>
Première partie de l'objet UnorderedMapView d'origine.

*deuxièmePartition*<br/>
Deuxième partie de l'objet UnorderedMapView d'origine.

### <a name="remarks"></a>Notes

Cette méthode n'est pas opérationnelle. Elle ne fait rien.

## <a name="unorderedmapviewunorderedmapview-constructor"></a><a name="ctor"></a>UnorderedMapView::UnorderedMapView Constructor

Initialise une nouvelle instance de la classe UnorderedMapView.

### <a name="syntax"></a>Syntaxe

```cpp
UnorderedMapView();
explicit UnorderedMapView(size_t n);
UnorderedMapView(size_t n, const H& h);
UnorderedMapView(size_t n, const H& h, const P& p);

explicit UnorderedMapView(
    const std::unordered_map<K, V, H, P>& m);
explicit UnorderedMapView(
    std::unordered_map<K, V, H, P>&& m);

template <typename InIt> UnorderedMapView(InIt first, InIt last );
template <typename InIt> UnorderedMapView(InIt first, InIt last, size_t n );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p );

UnorderedMapView(std::initializer_list<std::pair<const K, V>);

UnorderedMapView(std::initializer_list< std::pair<const K, V>> il, size_t n

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h);

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p );
```

### <a name="parameters"></a>Paramètres

*n*<br/>
Nombre d'éléments pour lesquels préallouer de l'espace.

*Init*<br/>
Nom de type du UnorderedMapView.

*H (en)*<br/>
Objet de fonction qui peut avoir une valeur de hachage pour une clé. Défauts à [std::hash\<K>](../standard-library/hash-class.md) pour les types qui `std::hash` prend en charge.

*P*<br/>
Type qui fournit un objet de fonction qui peut comparer deux clés pour déterminer leur égalité. Défauts à [std::equal_to\<K>](../standard-library/equal-to-struct.md).

*M*<br/>
Une référence ou [Lvalues et Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) à un [std::unordered_map](../standard-library/unordered-map-class.md) qui est utilisé pour initialiser le UnorderedMapView.

*Première*<br/>
Itérateur d'entrée du premier élément d'une plage d'éléments utilisée pour initialiser le UnorderedMapView.

*Dernière*<br/>
Itérateur d'entrée du premier élément qui suit une plage d'éléments utilisée pour initialiser le UnorderedMapView.

## <a name="see-also"></a>Voir aussi

[Platform::Collections, espace de noms](../cppcx/platform-collections-namespace.md)<br/>
[Windows::Foundation::IMapView](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)
