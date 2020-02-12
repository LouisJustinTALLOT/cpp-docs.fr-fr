---
title: array, classe
ms.date: 11/04/2016
f1_keywords:
- array
- AMP/array
- AMP/Concurrency::array::array
- AMP/Concurrency::array::copy_to
- AMP/Concurrency::array::data
- AMP/Concurrency::array::get_accelerator_view
- AMP/Concurrency::array::get_associated_accelerator_view
- AMP/Concurrency::array::get_cpu_access_type
- AMP/Concurrency::array::get_extent
- AMP/Concurrency::array::reinterpret_as
- AMP/Concurrency::array::section
- AMP/Concurrency::array::view_as
- AMP/Concurrency::array::rank
- AMP/Concurrency::array::accelerator_view
- AMP/Concurrency::array::associated_accelerator_view
- AMP/Concurrency::array::cpu_access_type
- AMP/Concurrency::array::extent
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
ms.openlocfilehash: efea8dabb69a48e69d68a86110fdf9bc7664948b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127110"
---
# <a name="array-class"></a>array, classe

Représente un conteneur de données utilisé pour déplacer des données vers un accélérateur.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename value_type, int _Rank>
friend class array;
```

### <a name="parameters"></a>Paramètres

*value_type*<br/>
Type d’élément des données.

*_Rank*<br/>
Rang du tableau.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[Constructeur de tableau](#ctor)|Initialise une nouvelle instance de la classe `array`.|
|[Destructeur ~ Array](#dtor)|Détruit l’objet `array`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[copy_to](#copy_to)|Copie le contenu du tableau dans un autre tableau.|
|[data](#data)|Retourne un pointeur vers les données brutes du tableau.|
|[get_accelerator_view](#get_accelerator_view)|Retourne l’objet [accelerator_view](accelerator-view-class.md) qui représente l’emplacement où le tableau est alloué. Cette propriété est accessible uniquement sur le processeur.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Obtient le deuxième [accelerator_view](accelerator-view-class.md) objet passé en tant que paramètre lorsqu’un constructeur intermédiaire est appelé pour instancier l’objet `array`.|
|[get_cpu_access_type](#get_cpu_access_type)|Retourne le [access_type](concurrency-namespace-enums-amp.md#access_type) du tableau. Cette méthode est accessible uniquement sur le processeur.|
|[get_extent](#get_extent)|Retourne l’objet [extent](extent-class.md) du tableau.|
|[reinterpret_as](#reinterpret_as)|Retourne un tableau unidimensionnel qui contient tous les éléments de l’objet `array`.|
|[section](#section)|Retourne une sous-section de l’objet `array` qui est à l’origine spécifiée et, éventuellement, qui a l’étendue spécifiée.|
|[view_as](#view_as)|Retourne un objet [array_view](array-view-class.md) qui est construit à partir de l’objet `array`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[opérateur std :: Vector&lt;value_type&gt;](#operator_vec)|Utilise `copy(*this, vector)` pour convertir implicitement le tableau en objet std ::[Vector](../../../standard-library/vector-class.md) .|
|[operator()](#operator_call)|Retourne la valeur de l’élément qui est spécifiée par les paramètres.|
|[operator\[\]](#operator_at)|Retourne l’élément qui se trouve à l’index spécifié.|
|[operator=](#operator_eq)|Copie le contenu de l’objet `array` spécifié dans celui-ci.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[Rank, constante](#rank)|Stocke le rang du tableau.|

### <a name="public-data-members"></a>Membres de données publiques

|Name|Description|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|Obtient l’objet [accelerator_view](accelerator-view-class.md) qui représente l’emplacement où le tableau est alloué. Cette propriété est accessible uniquement sur le processeur.|
|[associated_accelerator_view](#associated_accelerator_view)|Obtient le deuxième [accelerator_view](accelerator-view-class.md) objet passé en tant que paramètre lorsqu’un constructeur intermédiaire est appelé pour instancier l’objet `array`.|
|[cpu_access_type](#cpu_access_type)|Obtient le [access_type](concurrency-namespace-enums-amp.md#access_type) qui représente la façon dont l’UC peut accéder au stockage du tableau.|
|[extent](#extent)|Obtient l’étendue qui définit la forme du tableau.|

## <a name="remarks"></a>Notes

Le `array<T,N>` de type représente un tableau à *N*dimensions dense et normal (non irrégulier) qui se trouve à un emplacement spécifique, tel qu’un accélérateur ou l’UC. Le type de données des éléments du tableau est `T`, qui doit être d’un type compatible avec l’accélérateur cible. Bien que le rang, `N`, (du tableau soit déterminé de manière statique et fait partie du type, l’étendue du tableau est déterminée par le runtime et est exprimée à l’aide de la classe `extent<N>`.

Un tableau peut avoir n’importe quel nombre de dimensions, bien que certaines fonctionnalités soient spécialisées pour `array` objets avec le rang un, deux et trois. Si vous omettez l’argument de dimension, la valeur par défaut est 1.

Les données du tableau sont disposées de façon contiguë en mémoire. Les éléments qui diffèrent par un dans la dimension la moins significative sont adjacents dans la mémoire.

Les tableaux sont logiquement considérés comme des types valeur, car lorsqu’un tableau est copié dans un autre tableau, une copie complète est effectuée. Deux tableaux ne pointent jamais vers les mêmes données.

Le type de `array<T,N>` est utilisé dans plusieurs scénarios :

- Comme un conteneur de données qui peut être utilisé dans les calculs sur un accélérateur.

- En tant que conteneur de données pour stocker la mémoire sur le processeur de l’ordinateur hôte (qui peut être utilisé pour copier vers et depuis d’autres tableaux).

- En tant qu’objet intermédiaire pour agir en tant qu’intermédiaire rapide dans les copies d’un hôte à l’appareil.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`array`

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="dtor"></a>~ Tableau

Détruit l’objet `array`.

```cpp
~array() restrict(cpu);
```

## <a name="accelerator_view"></a>accelerator_view

Obtient l’objet [accelerator_view](accelerator-view-class.md) qui représente l’emplacement où le tableau est alloué. Cette propriété est accessible uniquement sur le processeur.

```cpp
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

## <a name="ctor"></a>ensemble

Initialise une nouvelle instance de la [classe Array](array-class.md). Il n’existe aucun constructeur par défaut pour `array<T,N>`. Tous les constructeurs sont exécutés uniquement sur le processeur. Ils ne peuvent pas être exécutés sur une cible Direct3D.

```cpp
explicit array(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

explicit array(
    int _E0) restrict(cpu);

explicit array(
    int _E0,
    int _E1) restrict(cpu);

explicit array(
    int _E0,
    int _E1,
    int _E2) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

explicit array(
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av,
    accelerator_view _Associated_Av) restrict(cpu);

array(const array& _Other) restrict(cpu);

array(array&& _Other) restrict(cpu);
```

### <a name="parameters"></a>Paramètres

*_Associated_Av*<br/>
Accelerator_view qui spécifie l’emplacement cible préféré du tableau.

*_Av*<br/>
Objet [accelerator_view](accelerator-view-class.md) qui spécifie l’emplacement du tableau.

*_Cpu_access_type*<br/>
[Access_type](concurrency-namespace-enums-amp.md#access_type) souhaité pour le tableau sur l’UC. Ce paramètre a une valeur par défaut de `access_type_auto` laissant le processeur `access_type` détermination au Runtime. Le `access_type` d’UC réel du tableau peut être interrogé à l’aide de la méthode `get_cpu_access_type`.

*_Extent*<br/>
L’étendue de chaque dimension du tableau.

*_E0*<br/>
Le composant le plus significatif de l’étendue de cette section.

*_E1*<br/>
Le composant suivant le plus significatif de l’étendue de cette section.

*_E2*<br/>
Composant le moins significatif de l’étendue de cette section.

*_InputIterator*<br/>
Type de l'itérateur d'entrée.

*_Src*<br/>
À l’objet à copier.

*_Src_first*<br/>
Itérateur de début dans le conteneur source.

*_Src_last*<br/>
Itérateur de fin dans le conteneur source.

*_Other*<br/>
Autre source de données.

*_Rank*<br/>
Rang de la section.

*value_type*<br/>
Type de données des éléments copiés.

## <a name="associated_accelerator_view"></a>associated_accelerator_view

Obtient le deuxième [accelerator_view](accelerator-view-class.md) objet passé en tant que paramètre lorsqu’un constructeur intermédiaire est appelé pour instancier l’objet `array`.

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a>copy_to

Copie le contenu du `array` dans un autre `array`.

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Objet [array_view](array-view-class.md) vers lequel effectuer la copie.

## <a name="cpu_access_type"></a>cpu_access_type

Obtient l’UC access_type autorisée pour ce tableau.

```cpp
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

## <a name="data"></a>métadonnée

Retourne un pointeur vers les données brutes du `array`.

```cpp
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers les données brutes du tableau.

## <a name="extent"></a>étendue

Obtient l’objet [extent](extent-class.md) qui définit la forme de la `array`.

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_accelerator_view"></a>get_accelerator_view

Retourne l’objet [accelerator_view](accelerator-view-class.md) qui représente l’emplacement où l’objet `array` est alloué. Cette propriété est accessible uniquement sur le processeur.

```cpp
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>Valeur de retour

Objet `accelerator_view` qui représente l’emplacement où l’objet `array` est alloué.

## <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

Obtient le deuxième [accelerator_view](accelerator-view-class.md) objet passé en tant que paramètre lorsqu’un constructeur intermédiaire est appelé pour instancier l’objet `array`.

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>Valeur de retour

Deuxième [accelerator_view](accelerator-view-class.md) objet passé au constructeur intermédiaire.

## <a name="get_cpu_access_type"></a>get_cpu_access_type

Retourne le access_type d’UC autorisé pour ce tableau.

```cpp
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>Valeur de retour

## <a name="get_extent"></a>get_extent

Retourne l’objet [extent](extent-class.md) de l' `array`.

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

Objet `extent` de l'objet `array`.

## <a name="operator_vec"></a>opérateur std :: Vector&lt;value_type&gt;

Utilise `copy(*this, vector)` pour convertir implicitement le tableau en objet std :: Vector.

```cpp
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>Paramètres

*value_type*<br/>
Type de données des éléments du vecteur.

### <a name="return-value"></a>Valeur de retour

Objet de type `vector<T>` qui contient une copie des données contenues dans le tableau.

## <a name="operator_call"></a>, opérateur ()

Retourne la valeur de l’élément qui est spécifiée par les paramètres.

```cpp
value_type& operator() (const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator() (const index<_Rank>& _Index) cons  t restrict(amp,cpu);

value_type& operator() (int _I0, int _I1) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1) const restrict(amp,cpu)  ;

value_type& operator() (int _I0, int _I1, int _I2) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1, int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator()(int _I) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator()(int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Emplacement de l’élément.

*_I0*<br/>
Composant le plus significatif de l’origine de cette section.

*_I1*<br/>
Composant suivant le plus significatif de l’origine de cette section.

*_I2*<br/>
Composant le moins significatif de l’origine de cette section.

*_I*<br/>
Emplacement de l’élément.

### <a name="return-value"></a>Valeur de retour

Valeur de l’élément spécifiée par les paramètres.

## <a name="operator_at"></a>[], opérateur

Retourne l’élément qui se trouve à l’index spécifié.

```cpp
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator[]
    (const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index.

*_I*<br/>
Index.

### <a name="return-value"></a>Valeur de retour

Élément qui se trouve à l’index spécifié.

## <a name="operator_eq"></a>opérateur =

Copie le contenu de l’objet `array` spécifié.

```cpp
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet `array` à partir duquel effectuer la copie.

*_Src*<br/>
Objet `array` à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur de retour

Référence à cet objet `array`.

## <a name="rank"></a>moteurs

Stocke le rang du `array`.

```cpp
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a>reinterpret_as

Réinterprète le tableau à l’aide d’un array_view unidimensionnel, qui peut éventuellement avoir un type de valeur différent du tableau source.

### <a name="syntax"></a>Syntaxe

```cpp
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Value_type2*<br/>
Type de données des données retournées.

### <a name="return-value"></a>Valeur de retour

Objet array_view ou const array_view basé sur le tableau, avec le type d’élément réinterprété de T en ElementType et le rang réduit de N à 1.

### <a name="remarks"></a>Notes

Il est parfois pratique d’afficher un tableau multidimensionnel comme s’il s’agissait d’un tableau linéaire à une dimension, éventuellement avec un type de valeur différent du tableau source. Vous pouvez utiliser cette méthode pour y parvenir.
**Attention** La réinterprétation d’un objet tableau à l’aide d’un type de valeur différent est une opération potentiellement risquée. Nous vous recommandons d’utiliser cette fonctionnalité avec précaution.

Le code suivant montre un exemple.

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a>section

Retourne une sous-section de l’objet `array` qui est à l’origine spécifiée et, éventuellement, qui a l’étendue spécifiée.

```cpp
array_view<value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const index<_Rank>& _Idx) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const index<_Rank>& _Idx) const restrict(amp,cpu);

array_view<value_type,1> section(
    int _I0,
    int _E0) restrict(amp,cpu);

array_view<const value_type,1> section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view<value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) restrict(amp,cpu);

array_view<const value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view<value_type,3> section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) restrict(amp,cpu);

array_view<const value_type,3> section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_E0*<br/>
Le composant le plus significatif de l’étendue de cette section.

*_E1*<br/>
Le composant suivant le plus significatif de l’étendue de cette section.

*_E2*<br/>
Composant le moins significatif de l’étendue de cette section.

*_Ext*<br/>
Objet [extent](extent-class.md) qui spécifie l’étendue de la section. L’origine est 0.

*_Idx*<br/>
Objet [index](index-class.md) qui spécifie l’emplacement de l’origine. La sous-section est le reste de l’étendue.

*_I0*<br/>
Composant le plus significatif de l’origine de cette section.

*_I1*<br/>
Composant suivant le plus significatif de l’origine de cette section.

*_I2*<br/>
Composant le moins significatif de l’origine de cette section.

*_Rank*<br/>
Rang de la section.

*_Section_extent*<br/>
Objet [extent](extent-class.md) qui spécifie l’étendue de la section.

*_Section_origin*<br/>
Objet [index](index-class.md) qui spécifie l’emplacement de l’origine.

*value_type*<br/>
Type de données des éléments copiés.

### <a name="return-value"></a>Valeur de retour

Retourne une sous-section de l’objet `array` qui est à l’origine spécifiée et, éventuellement, qui a l’étendue spécifiée. Lorsque seul l’objet `index` est spécifié, la sous-section contient tous les éléments de la grille associée dont les index sont plus grands que les index des éléments de l’objet `index`.

## <a name="view_as"></a>view_as

Réinterprète ce tableau comme un [array_view](array-view-class.md) d’un rang différent.

```cpp
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_New_rank*<br/>
Rang de l’objet `extent` passé en tant que paramètre.

*_View_extent*<br/>
Étendue utilisée pour construire le nouvel objet [array_view](array-view-class.md) .

*value_type*<br/>
Type de données des éléments de l’objet `array` d’origine et de l’objet `array_view` retourné.

### <a name="return-value"></a>Valeur de retour

Objet [array_view](array-view-class.md) qui est construit.

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
