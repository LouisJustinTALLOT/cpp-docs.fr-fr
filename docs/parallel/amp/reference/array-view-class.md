---
title: array_view, classe
ms.date: 11/04/2016
f1_keywords:
- array_view
- AMP/array_view
- AMP/Concurrency::array_view::array_view
- AMP/Concurrency::array_view::copy_to
- AMP/Concurrency::array_view::data
- AMP/Concurrency::array_view::discard_data
- AMP/Concurrency::array_view::get_extent
- AMP/Concurrency::array_view::get_ref
- AMP/Concurrency::array_view::get_source_accelerator_view
- AMP/Concurrency::array_view::refresh
- AMP/Concurrency::array_view::reinterpret_as
- AMP/Concurrency::array_view::section
- AMP/Concurrency::array_view::synchronize
- AMP/Concurrency::array_view::synchronize_async
- AMP/Concurrency::array_view::synchronize_to
- AMP/Concurrency::array_view::synchronize_to_async
- AMP/Concurrency::array_view::view_as
- AMP/Concurrency::array_view::rank
- AMP/Concurrency::array_view::extent
- AMP/Concurrency::array_view::source_accelerator_view
- AMP/Concurrency::array_view::value_type
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
ms.openlocfilehash: 2aef75eedcde2a2064fe12815d9afd21fee2c293
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127135"
---
# <a name="array_view-class"></a>array_view, classe

Représente une vue en N dimensions sur les données contenues dans un autre conteneur.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename value_type,
    int _Rank = 1
>
class array_view : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;

template <
    typename value_type,
    int _Rank
>
class array_view<const value_type, _Rank> : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;
```

### <a name="parameters"></a>Paramètres

*value_type*<br/>
Type de données des éléments de l’objet `array_view`.

*_Rank*<br/>
Rang de l’objet `array_view`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[Constructeur array_view](#ctor)|Initialise une nouvelle instance de la classe `array_view`. Il n’existe aucun constructeur par défaut pour `array<T,N>`. Tous les constructeurs sont limités à s’exécuter sur le processeur uniquement et ne peuvent pas être exécutés sur une cible Direct3D.|
|[Destructeur ~ array_view](#ctor)|Détruit l’objet `array_view`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[copy_to](#copy_to)|Copie le contenu de l’objet `array_view` vers la destination spécifiée en appelant `copy(*this, dest)`.|
|[data](#data)|Retourne un pointeur vers les données brutes du `array_view`.|
|[discard_data](#discard_data)|Ignore les données actuelles sous-jacentes à cette vue.|
|[get_extent](#get_extent)|Retourne l’objet extent de l’objet array_view.|
|[get_ref](#get_ref)|Retourne une référence à l’élément indexé.|
|[get_source_accelerator_view](#get_source_accelerator_view)|Retourne le [accelerator_view](accelerator-view-class.md) où se trouve la source de données du `array_view`.|
|[générer](#refresh)|Avertit l’objet `array_view` que sa mémoire liée a été modifiée en dehors de l’interface `array_view`. Un appel à cette méthode restitue toutes les informations mises en cache obsolètes.|
|[reinterpret_as](#reinterpret_as)|Retourne un tableau unidimensionnel qui contient tous les éléments de l’objet `array_view`.|
|[section](#section)|Retourne une sous-section de l’objet `array_view` qui est à l’origine spécifiée et, éventuellement, qui a l’étendue spécifiée.|
|[synchronize](#synchronize)|Synchronise toutes les modifications apportées à l’objet `array_view` à ses données sources.|
|[synchronize_async](#synchronize_async)|Synchronise de façon asynchrone toutes les modifications apportées à l’objet `array_view` à ses données sources.|
|[synchronize_to](#synchronize_to)|Synchronise toutes les modifications apportées à l’objet `array_view` dans le [accelerator_view](accelerator-view-class.md)spécifié.|
|[synchronize_to_async](#synchronize_to_async)|Synchronise de façon asynchrone toutes les modifications apportées à l’objet `array_view` sur le [accelerator_view](accelerator-view-class.md)spécifié.|
|[view_as](#view_as)|Produit un objet `array_view` d’un rang différent en utilisant les données de cet objet `array_view`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator()](#operator_call)|Retourne la valeur de l’élément spécifié par le paramètre ou les paramètres.|
|[operator\[\]](#operator_at)|Retourne l’élément spécifié par les paramètres.|
|[operator=](#operator_eq)|Copie le contenu de l’objet `array_view` spécifié dans celui-ci.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[Rank, constante](#rank)|Stocke le rang de l’objet `array_view`.|

### <a name="data-members"></a>Données membres

|Name|Description|
|----------|-----------------|
|[extent](#extent)|Obtient l'objet `extent` qui définit la forme de l'objet `array_view`.|
|[source_accelerator_view](#source_accelerator_view)|Obtient le [accelerator_view](accelerator-view-class.md) où se trouve la source de données du `array_view`|
|[value_type](#value_type)|Type de valeur de la `array_view` et du tableau lié.|

## <a name="remarks"></a>Notes

La classe `array_view` représente une vue dans les données contenues dans un objet [tableau](array-class.md) ou dans une sous-section d’un objet `array`.

Vous pouvez accéder à l’objet `array_view` dans lequel se trouvent les données sources (localement) ou sur un autre accélérateur ou un domaine de cohérence (à distance). Lorsque vous accédez à l’objet à distance, les vues sont copiées et mises en cache si nécessaire. À l’exception des effets de la mise en cache automatique, les objets `array_view` ont un profil de performances similaire à celui des objets `array`. Une faible baisse des performances se pose lorsque vous accédez aux données par le biais de vues.

Il existe trois scénarios d’utilisation à distance :

- Une vue d’un pointeur mémoire système est passée au moyen d’un [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each) appel à un accélérateur et accessible sur l’accélérateur.

- Une vue d’un tableau situé sur un accélérateur est passée au moyen d’un `parallel_for_each` appel à un autre accélérateur et y accède.

- Une vue d’un tableau situé sur un accélérateur est accessible sur le processeur.

Dans l’un de ces scénarios, les vues référencées sont copiées par le runtime vers l’emplacement distant et, si elles sont modifiées par les appels à l’objet `array_view`, sont recopiées dans l’emplacement local. Le runtime peut optimiser le processus de copie des modifications, ne copier que les éléments modifiés, ou peut également copier des parties inchangées. Il n’est pas garanti que le chevauchement des objets `array_view` sur une source de données conserve l’intégrité référentielle dans un emplacement distant.

Vous devez synchroniser tout accès multithread à la même source de données.

Le runtime apporte les garanties suivantes concernant la mise en cache des données dans les objets `array_view` :

- Tous les accès bien synchronisés à un objet `array` et un objet `array_view` sur celui-ci dans l’ordre du programme obéissent à une relation série-avant.

- Tous les accès bien synchronisés au chevauchement des objets `array_view` sur le même accélérateur sur un objet `array` unique sont associés à l’objet `array`. Ils induitnt un total de la relation qui obéit à la commande du programme. Il n’y a pas de mise en cache. Si les objets `array_view` s’exécutent sur différents accélérateurs, l’ordre d’accès n’est pas défini, ce qui crée une condition de concurrence.

Lorsque vous créez un objet `array_view` à l’aide d’un pointeur dans la mémoire système, vous devez modifier l’objet de vue `array_view` uniquement par le biais du pointeur `array_view`. Vous devez également appeler `refresh()` sur l’un des objets `array_view` attachés au pointeur système, si la mémoire Native sous-jacente est modifiée directement, et non par l’intermédiaire de l’objet `array_view`.

L’une ou l’autre action notifie l’objet `array_view` que la mémoire Native sous-jacente est modifiée et que toutes les copies situées sur un accélérateur sont obsolètes. Si vous suivez ces instructions, les vues basées sur des pointeurs sont identiques à celles fournies aux vues des tableaux parallèles de données.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_Array_view_shape`

`_Array_view_base`

`array_view`

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="dtor"></a>~ array_view

Détruit l’objet `array_view`.

```cpp
~array_view()restrict(amp,cpu);
```

## <a name="ctor"></a>array_view

Initialise une nouvelle instance de la classe `array_view`.

```cpp
array_view(
    array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view& _Other)restrict(amp,cpu);

explicit array_view(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    _Container& _Src) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    int _E0,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _Container& _Src);

explicit array_view(
    int _E0,
    _In_ value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    _In_ value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _In_ value_type* _Src)restrict(amp,cpu);

array_view(
    const array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<const value_type, _Rank>& _Src)restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const _Container& _Src) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    const _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    const _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    int _E0,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    int _E2,
    const _Container& _Src);

array_view(
    int _E0,
    const value_type* _Src)restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    const value_type* _Src) restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    int _E2,
    const value_type* _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Arr_type*<br/>
Type d’élément d’un tableau de style C à partir duquel les données sont fournies.

*_Container*<br/>
Argument de modèle qui doit spécifier un conteneur linéaire qui prend en charge les membres `data()` et `size()`.

*_E0*<br/>
Le composant le plus significatif de l’étendue de cette section.

*_E1*<br/>
Le composant suivant le plus significatif de l’étendue de cette section.

*_E2*<br/>
Composant le moins significatif de l’étendue de cette section.

*_Extent*<br/>
L’étendue de chaque dimension de cette `array_view`.

*_Other*<br/>
Objet de type `array_view<T,N>` à partir duquel initialiser la nouvelle `array_view`.

*_Size*<br/>
Taille d’un tableau de style C à partir duquel les données sont fournies.

*_Src*<br/>
Pointeur vers les données sources qui seront copiées dans le nouveau tableau.

## <a name="copy_to"></a>copy_to

Copie le contenu de l’objet `array_view` vers l’objet de destination spécifié en appelant `copy(*this, dest)`.

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Objet cible de la copie.

## <a name="data"></a>métadonnée

Retourne un pointeur vers les données brutes du `array_view`.

```cpp
value_type* data() const restrict(amp,
    cpu);

const value_type* data() const restrict(amp,
    cpu);
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers les données brutes du `array_view`.

## <a name="discard_data"></a>discard_data

Ignore les données actuelles sous-jacentes à cette vue. Il s’agit d’un indicateur d’optimisation pour le runtime utilisé pour éviter de copier le contenu actuel de la vue dans un `accelerator_view` cible sur lequel il est accessible, et son utilisation est recommandée si le contenu existant n’est pas nécessaire. Cette méthode est une absence d’opération lorsqu’elle est utilisée dans un contexte de restriction (amp).

```cpp
void discard_data() const restrict(cpu);
```

## <a name="extent"></a>étendue

Obtient l'objet `extent` qui définit la forme de l'objet `array_view`.

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_extent"></a>get_extent

Retourne l’objet [extent](extent-class.md) de l’objet `array_view`.

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```

### <a name="return-value"></a>Valeur de retour

Objet `extent` de l’objet `array_view`

## <a name="get_ref"></a>get_ref

Obtient une référence à l’élément indexé par _Index. Contrairement aux autres opérateurs d’indexation pour accéder à la array_view sur l’UC, cette méthode ne synchronise pas implicitement le contenu de ce array_view avec l’UC. Après avoir accès à la array_view sur un emplacement distant ou à effectuer une opération de copie impliquant cette array_view les utilisateurs sont chargés de synchroniser explicitement les array_view avec l’UC avant d’appeler cette méthode. Dans le cas contraire, le comportement n’est pas défini.

```cpp
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index.

### <a name="return-value"></a>Valeur de retour

Référence à l’élément indexé par _Index

## <a name="get_source_accelerator_view"></a>get_source_accelerator_view

Retourne le accelerator_view où se trouve la source de données du array_view. Si la array_view n’a pas de source de données, cette API lève une runtime_exception

```cpp
accelerator_view get_source_accelerator_view() const;
```

### <a name="return-value"></a>Valeur de retour

## <a name="operator_call"></a>, opérateur ()

Retourne la valeur de l’élément spécifié par le paramètre ou les paramètres.

```cpp
value_type& operator() (
    const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator() (
    int _I) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator() (
    int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Emplacement de l’élément.

*_I0*<br/>
Index dans la première dimension.

*_I1*<br/>
Index dans la deuxième dimension.

*_I2*<br/>
Index dans la troisième dimension.

*_I*<br/>
Emplacement de l’élément.

### <a name="return-value"></a>Valeur de retour

Valeur de l’élément spécifié par le paramètre ou les paramètres.

## <a name="operator_at"></a>[], opérateur

Retourne l’élément spécifié par les paramètres.

```cpp
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Index*<br/>
Index.

*_I*<br/>
Index.

### <a name="return-value"></a>Valeur de retour

Valeur de l’élément au niveau de l’index ou `array_view` projetée sur la dimension la plus significative.

## <a name="operator_eq"></a>opérateur =

Copie le contenu de l’objet `array_view` spécifié dans celui-ci.

```cpp
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet `array_view` à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur de retour

Référence à cet objet `array_view`.

## <a name="rank"></a>moteurs

Stocke le rang de l’objet `array_view`.

```cpp
static const int rank = _Rank;
```

## <a name="refresh"></a>générer

Avertit l’objet `array_view` que sa mémoire liée a été modifiée en dehors de l’interface `array_view`. Un appel à cette méthode restitue toutes les informations mises en cache obsolètes.

```cpp
void refresh() const restrict(cpu);
```

## <a name="reinterpret_as"></a>reinterpret_as

Réinterprète le array_view par le biais d’une array_view unidimensionnelle, qui, en tant qu’option, peut avoir un type de valeur différent de celui du array_view source.

### <a name="syntax"></a>Syntaxe

```cpp
template <
    typename _Value_type2
>
array_view< _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);

template <
    typename _Value_type2
>
array_view<const _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Value_type2*<br/>
Type de données du nouvel objet `array_view`.

### <a name="return-value"></a>Valeur de retour

Objet `array_view` ou objet const `array_view` basé sur ce `array_view`, avec le type d’élément converti de `T` en `_Value_type2`et le rang réduit de *N* à 1.

### <a name="remarks"></a>Notes

Il est parfois pratique d’afficher un tableau multidimensionnel sous la forme d’un tableau unidimensionnel linéaire, qui peut avoir un type de valeur différent du tableau source. Pour ce faire, vous pouvez utiliser une `array_view` à l’aide de cette méthode.

**Avertissement** La réinterprétation d’un objet array_view à l’aide d’un type de valeur différent est une opération potentiellement risquée. Cette fonctionnalité doit être utilisée avec précaution.

Voici un exemple :

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a>section

Retourne une sous-section de l’objet `array_view` qui est à l’origine spécifiée et, éventuellement, qui a l’étendue spécifiée.

```cpp
array_view section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view section(
    const Concurrency::index<_Rank>& _Idx) const restrict(amp,cpu);

array_view section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view section(
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

### <a name="return-value"></a>Valeur de retour

Sous-section de l’objet `array_view` qui est à l’origine spécifiée et, éventuellement, qui a l’étendue spécifiée. Lorsque seul l’objet `index` est spécifié, la sous-section contient tous les éléments de l’étendue associée qui ont des index plus grands que les index des éléments dans l’objet `index`.

## <a name="source_accelerator_view"></a>source_accelerator_view

Obtient le accelerator_view source auquel ce array_view est associé.

```cpp
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;
```

## <a name="synchronize"></a>non

Synchronise toutes les modifications apportées à l’objet `array_view` à ses données sources.

```cpp
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize() const restrict(cpu);
```

### <a name="parameters"></a>Paramètres

*_Access_type*<br/>
[Access_type](concurrency-namespace-enums-amp.md#access_type) prévu sur le [accelerator_view](accelerator-view-class.md)cible. La valeur par défaut de ce paramètre est `access_type_read`.

## <a name="synchronize_async"></a>synchronize_async

Synchronise de façon asynchrone toutes les modifications apportées à l’objet `array_view` à ses données sources.

```cpp
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_async() const restrict(cpu);
```

### <a name="parameters"></a>Paramètres

*_Access_type*<br/>
[Access_type](concurrency-namespace-enums-amp.md#access_type) prévu sur le [accelerator_view](accelerator-view-class.md)cible. La valeur par défaut de ce paramètre est `access_type_read`.

### <a name="return-value"></a>Valeur de retour

Un futur sur lequel attendre la fin de l’opération.

## <a name="synchronize_to"></a>synchronize_to

Synchronise toutes les modifications apportées à cette array_view dans le accelerator_view spécifié.

```cpp
void synchronize_to(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>Paramètres

*_Accl_view*<br/>
Accelerator_view cible vers lequel effectuer la synchronisation.

*_Access_type*<br/>
Access_type souhaité sur le accelerator_view cible. La valeur par défaut de ce paramètre est access_type_read.

## <a name="synchronize_to_async"></a>synchronize_to_async

Synchronise de façon asynchrone toutes les modifications apportées à cette array_view dans le accelerator_view spécifié.

```cpp
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>Paramètres

*_Accl_view*<br/>
Accelerator_view cible vers lequel effectuer la synchronisation.

*_Access_type*<br/>
Access_type souhaité sur le accelerator_view cible. La valeur par défaut de ce paramètre est access_type_read.

### <a name="return-value"></a>Valeur de retour

Un futur sur lequel attendre la fin de l’opération.

## <a name="value_type"></a>value_type

Type de valeur de la array_view et du tableau lié.

```cpp
typedef typenamevalue_type value_type;
```

## <a name="view_as"></a>view_as

Réinterprète ce `array_view` comme `array_view` d’un rang différent.

```cpp
template <
    int _New_rank
>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);

template <
    int _New_rank
>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank> _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_New_rank*<br/>
Rang du nouvel objet `array_view`.

*_View_extent*<br/>
`extent`de remodelage.

*value_type*<br/>
Type de données des éléments dans l’objet de [tableau](array-class.md) d’origine et l’objet de `array_view` retourné.

### <a name="return-value"></a>Valeur de retour

Objet `array_view` qui est construit.

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
