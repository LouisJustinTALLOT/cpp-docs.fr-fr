---
title: Array, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9023f042cd2c39966adb6a5fb4c71b5e24c3e9d1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068045"
---
# <a name="array-class"></a>array, classe

Représente un conteneur de données utilisé pour déplacer des données vers un accélérateur.

## <a name="syntax"></a>Syntaxe

```
template <typename value_type, int _Rank>
friend class array;
```

#### <a name="parameters"></a>Paramètres

*value_type*<br/>
Le type d’élément de données.

*_Rank*<br/>
Le rang du tableau.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Array, constructeur](#ctor)|Initialise une nouvelle instance de la classe `array`.|
|[~ array, destructeur](#dtor)|Détruit le `array` objet.|
### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[copy_to](#copy_to)|Copie le contenu du tableau dans un autre tableau.|
|[data](#data)|Retourne un pointeur vers les données brutes du tableau.|
|[get_accelerator_view](#get_accelerator_view)|Retourne le [accelerator_view](accelerator-view-class.md) objet qui représente l’emplacement où le tableau est alloué. Cette propriété est accessible uniquement sur le CPU.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Obtient le deuxième [accelerator_view](accelerator-view-class.md) objet qui est passé en tant que paramètre quand un constructeur intermédiaire est appelé pour instancier le `array` objet.|
|[get_cpu_access_type](#get_cpu_access_type)|Retourne le [access_type](concurrency-namespace-enums-amp.md#access_type) du tableau. Cette méthode est accessible uniquement sur le CPU.|
|[get_extent](#get_extent)|Retourne le [étendue](extent-class.md) objet du tableau.|
|[reinterpret_as](#reinterpret_as)|Retourne un tableau unidimensionnel qui contient tous les éléments dans le `array` objet.|
|[section](#section)|Retourne une sous-section de le `array` objet qui est à l’origine spécifiée et, éventuellement, qui a l’étendue spécifiée.|
|[view_as](#view_as)|Retourne un [array_view](array-view-class.md) objet construit à partir de la `array` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur std::vector&lt;value_type&gt;](#operator_vec)|Utilise `copy(*this, vector)` convertir implicitement le tableau std ::[vecteur](../../../standard-library/vector-class.md) objet.|
|[operator()](#operator_call)|Retourne la valeur de l’élément qui est spécifiée par les paramètres.|
|[operator[]](#operator_at)|Retourne l’élément qui est à l’index spécifié.|
|[operator=](#operator_eq)|Copie le contenu de l’objet `array` objet dans celui-ci.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[rang (constante)](#rank)|Stocke le rang du tableau.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|Obtient le [accelerator_view](accelerator-view-class.md) objet qui représente l’emplacement où le tableau est alloué. Cette propriété est accessible uniquement sur le CPU.|
|[associated_accelerator_view](#associated_accelerator_view)|Obtient le deuxième [accelerator_view](accelerator-view-class.md) objet qui est passé en tant que paramètre quand un constructeur intermédiaire est appelé pour instancier le `array` objet.|
|[cpu_access_type](#cpu_access_type)|Obtient le [access_type](concurrency-namespace-enums-amp.md#access_type) qui représente la façon dont le processeur peut accéder le stockage du tableau.|
|[extent](#extent)|Obtient l’étendue qui définit la forme du tableau.|

## <a name="remarks"></a>Notes

Le type `array<T,N>` représente un dense et régulier (non-multidimensionnel) *N*-tableau unidimensionnel qui se trouve dans un emplacement spécifique, comme un accélérateur ou de l’UC. Le type de données des éléments dans le tableau est `T`, qui doit être d’un type qui est compatible avec l’accélérateur cible. Bien que le rang, `N`, (du tableau est déterminé statiquement et fait partie du type, l’étendue du tableau est déterminé par le runtime et est exprimée à l’aide de la classe `extent<N>`.

Un tableau peut avoir n’importe quel nombre de dimensions, bien que certaines fonctionnalités soient spécialisées pour `array` objets avec le rang un, deux et trois. Si vous omettez l’argument de dimension, la valeur par défaut est 1.

Données de tableau sont disposées de façon contiguë en mémoire. Éléments qui diffèrent d’une unité dans la dimension la moins significative sont adjacents dans la mémoire.

Tableaux sont logiquement considérés comme des types valeur, car lorsqu’un tableau est copié dans un autre tableau, une copie complète est effectuée. Deux tableaux ne désignent jamais les mêmes données.

Le `array<T,N>` type est utilisé dans plusieurs scénarios :

- Comme un conteneur de données qui peut être utilisé dans les calculs sur un accélérateur.

- En tant que conteneur de données pour stocker la mémoire sur l’ordinateur hôte du processeur (qui peut être utilisé pour copier vers et depuis d’autres tableaux).

- Comme un objet intermédiaire d’agir comme un intermédiaire rapide dans les copies de l’hôte-à-appareil.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`array`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp.h

**Espace de noms :** Concurrency

##  <a name="dtor"></a> ~ tableau

Détruit le `array` objet.

```
~array() restrict(cpu);
```

##  <a name="accelerator_view"></a> accelerator_view

Obtient le [accelerator_view](accelerator-view-class.md) objet qui représente l’emplacement où le tableau est alloué. Cette propriété est accessible uniquement sur le CPU.

```
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

##  <a name="ctor"></a> tableau

Initialise une nouvelle instance de la [array, classe](array-class.md). Il n’existe aucun constructeur par défaut pour `array<T,N>`. Tous les constructeurs sont exécutés sur le processeur seul. Ils ne peuvent pas être exécutées sur une cible Direct3D.

```
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
Un accelerator_view qui spécifie l’emplacement cible par défaut du tableau.

*_Av*<br/>
Un [accelerator_view](accelerator-view-class.md) objet qui spécifie l’emplacement du tableau.

*_Cpu_access_type*<br/>
Souhaité [access_type](concurrency-namespace-enums-amp.md#access_type) pour le groupe sur le processeur. Ce paramètre a la valeur par défaut `access_type_auto` en laissant de l’UC `access_type` détermination à l’exécution. Le processeur réel `access_type` pour le tableau peut être interrogé à l’aide de la `get_cpu_access_type` (méthode).

*_Extent*<br/>
Objet extent dans chaque dimension du tableau.

*_E0*<br/>
Le composant le plus significatif de l’étendue de cette section.

*_E1*<br/>
Le composant suivant-à-plus significatif de l’étendue de cette section.

*_E2*<br/>
Composant le moins significatif de l’étendue de cette section.

*_InputIterator*<br/>
Le type de l’itérateur d’entrée.

*_Src*<br/>
Objet à copier.

*_Src_first*<br/>
Un itérateur de départ dans le conteneur source.

*_Src_last*<br/>
Un itérateur de fin dans le conteneur source.

*_Autre*<br/>
Autre source de données.

*_Rank*<br/>
Le rang de la section.

*value_type*<br/>
Le type de données des éléments qui sont copiés.

##  <a name="associated_accelerator_view"></a> associated_accelerator_view

Obtient le deuxième [accelerator_view](accelerator-view-class.md) objet qui est passé en tant que paramètre quand un constructeur intermédiaire est appelé pour instancier le `array` objet.

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to

Copie le contenu de la `array` vers un autre `array`.

```
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Le [array_view](array-view-class.md) objet dans lequel copier.

##  <a name="cpu_access_type"></a> cpu_access_type sont

Obtient l’access_type d’UC autorisée pour ce tableau.

```
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

##  <a name="data"></a> Données

Retourne un pointeur vers les données brutes de la `array`.

```
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers les données brutes du tableau.

##  <a name="extent"></a> étendue

Obtient le [étendue](extent-class.md) objet qui définit la forme de la `array`.

```
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

##  <a name="get_accelerator_view"></a> get_accelerator_view

Retourne le [accelerator_view](accelerator-view-class.md) objet qui représente l’emplacement où le `array` objet est alloué. Cette propriété est accessible uniquement sur le CPU.

```
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>Valeur de retour

Le `accelerator_view` objet qui représente l’emplacement où le `array` objet est alloué.

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

Obtient le deuxième [accelerator_view](accelerator-view-class.md) objet qui est passé en tant que paramètre quand un constructeur intermédiaire est appelé pour instancier le `array` objet.

```
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>Valeur de retour

La seconde [accelerator_view](accelerator-view-class.md) objet passé au constructeur intermédiaire.

##  <a name="get_cpu_access_type"></a> get_cpu_access_type

Retourne l’access_type d’UC autorisée pour ce tableau.

```
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>Valeur de retour

##  <a name="get_extent"></a> get_extent

Retourne le [étendue](extent-class.md) objet de la `array`.

```
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

Le `extent` objet de la `array`.

##  <a name="operator_vec"></a> opérateur std::vector&lt;value_type&gt;

Utilise `copy(*this, vector)` pour convertir implicitement le tableau à un objet std::vector.

```
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>Paramètres

*value_type*<br/>
Le type de données des éléments du vecteur.

### <a name="return-value"></a>Valeur de retour

Un objet de type `vector<T>` qui contient une copie des données qui sont contenues dans le tableau.

##  <a name="operator_call"></a> operator()

Retourne la valeur de l’élément qui est spécifiée par les paramètres.

```
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
L’emplacement de l’élément.

*_I0*<br/>
Le composant le plus significatif de l’origine de cette section.

*_I1*<br/>
Le composant suivant-à-plus significatif de l’origine de cette section.

*_I2*<br/>
Composant le moins significatif de l’origine de cette section.

*_I*<br/>
L’emplacement de l’élément.

### <a name="return-value"></a>Valeur de retour

La valeur de l’élément spécifiée par les paramètres.

##  <a name="operator_at"></a> operator]

Retourne l’élément qui est à l’index spécifié.

```
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

L’élément qui est à l’index spécifié.

##  <a name="operator_eq"></a> opérateur =

Copie le contenu de l’objet `array` objet.

```
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>Paramètres

*_Autre*<br/>
Le `array` objet à copier.

*_Src*<br/>
Le `array` objet à copier.

### <a name="return-value"></a>Valeur de retour

Une référence à cet `array` objet.

##  <a name="rank"></a> rang

Stocke le rang de le `array`.

```
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a> reinterpret_as

Réinterprète le tableau via un array_view unidimensionnel, qui peut éventuellement avoir un type de valeur différent du tableau source.

### <a name="syntax"></a>Syntaxe

```
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Value_type2*<br/>
Le type de données des données retournées.

### <a name="return-value"></a>Valeur de retour

Un array_view ou un objet array_view const basé sur le tableau, avec le type d’élément réinterprété de T ElementType et le rang réduit de N à 1.

### <a name="remarks"></a>Notes

Il est parfois pratique d’afficher un tableau multidimensionnel comme s’il est un tableau unidimensionnel linéaire, éventuellement avec un type de valeur différent du tableau source. Vous pouvez utiliser cette méthode pour y parvenir.
**Attention** réinterprétation d’un objet tableau à l’aide d’un autre type de valeur est une opération potentiellement risquée. Nous vous recommandons d’utiliser cette fonctionnalité avec précaution.

Le code suivant fournit un exemple.

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

##  <a name="section"></a> Section

Retourne une sous-section de le `array` objet qui est à l’origine spécifiée et, éventuellement, qui a l’étendue spécifiée.

```
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
Le composant suivant-à-plus significatif de l’étendue de cette section.

*_E2*<br/>
Composant le moins significatif de l’étendue de cette section.

*_Ext*<br/>
Le [étendue](extent-class.md) objet qui spécifie l’étendue de la section. L’origine est 0.

*IDX*<br/>
Le [index](index-class.md) objet qui spécifie l’emplacement d’origine. La sous-section est le reste de l’étendue.

*_I0*<br/>
Le composant le plus significatif de l’origine de cette section.

*_I1*<br/>
Le composant suivant-à-plus significatif de l’origine de cette section.

*_I2*<br/>
Composant le moins significatif de l’origine de cette section.

*_Rank*<br/>
Le rang de la section.

*_Section_extent*<br/>
Le [étendue](extent-class.md) objet qui spécifie l’étendue de la section.

*_Section_origin*<br/>
Le [index](index-class.md) objet qui spécifie l’emplacement d’origine.

*value_type*<br/>
Le type de données des éléments qui sont copiés.

### <a name="return-value"></a>Valeur de retour

Retourne une sous-section de le `array` objet qui est à l’origine spécifiée et, éventuellement, qui a l’étendue spécifiée. Lorsque seul le `index` objet est spécifié, la sous-section contient tous les éléments dans la grille associée qui ont des index sont plus grands que les index des éléments dans le `index` objet.

##  <a name="view_as"></a> view_as

Réinterprète ce tableau comme un [array_view](array-view-class.md) d’un rang différent.

```
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_New_rank*<br/>
Le rang de le `extent` objet passé en tant que paramètre.

*_View_extent*<br/>
L’étendue qui est utilisé pour construire le nouvel [array_view](array-view-class.md) objet.

*value_type*<br/>
Le type de données des éléments dans les deux d’origine `array` objet et retourné `array_view` objet.

### <a name="return-value"></a>Valeur de retour

Le [array_view](array-view-class.md) objet construit.

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
