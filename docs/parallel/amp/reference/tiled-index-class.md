---
title: tiled_index, classe
ms.date: 03/27/2019
f1_keywords:
- tiled_index
- AMP/tiled_index
- AMP/Concurrency::tiled_index::tiled_index
- AMP/Concurrency::tiled_index::get_tile_extent
- AMP/Concurrency::tiled_index::barrier
- AMP/Concurrency::tiled_index::global
- AMP/Concurrency::tiled_index::local
- AMP/Concurrency::tiled_index::rank
- AMP/Concurrency::tiled_index::tile
- AMP/Concurrency::tiled_index::tile_dim0
- AMP/Concurrency::tiled_index::tile_dim1
- AMP/Concurrency::tiled_index::tile_dim2
- AMP/Concurrency::tiled_index::tile_origin
- AMP/Concurrency::tiled_index::tile_extent
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
ms.openlocfilehash: 9d295093031eaee0a2d4dd83aa931060e6eebc07
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832268"
---
# <a name="tiled_index-class"></a>tiled_index, classe

Fournit un index dans un objet [tiled_extent](tiled-extent-class.md) . Cette classe possède des propriétés permettant d’accéder aux éléments relatifs à l’origine de la vignette locale et par rapport à l’origine globale. Pour plus d’informations sur les espaces en mosaïques, consultez [utilisation de vignettes](../../../parallel/amp/using-tiles.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <
    int _Dim0,
    int _Dim1 = 0,
    int _Dim2 = 0
>
class tiled_index : public _Tiled_index_base<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_index<_Dim0, _Dim1, 0> : public _Tiled_index_base<2>;

template <
    int _Dim0
>
class tiled_index<_Dim0, 0, 0> : public _Tiled_index_base<1>;
```

### <a name="parameters"></a>Paramètres

*_Dim0*<br/>
Longueur de la dimension la plus significative.

*_Dim1*<br/>
Longueur de la dimension la plus proche de la plus importante.

*_Dim2*<br/>
Longueur de la dimension la moins significative.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur tiled_index](#ctor)|Initialise une nouvelle instance de la classe `tile_index`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|Retourne un objet [extent](extent-class.md) qui a les valeurs des `tiled_index` arguments template `_Dim0` , `_Dim1` et `_Dim2` .|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[barrière, constante](#tiled_index__barrier)|Stocke un objet [tile_barrier](tile-barrier-class.md) qui représente un cloisonnement dans la mosaïque actuelle de threads.|
|[Constante globale](#tiled_index__global)|Stocke un objet [index](index-class.md) de rang 1, 2 ou 3 qui représente l’index global dans un objet Grid.|
|[Constante locale](#tiled_index__local)|Stocke un `index` objet de rang 1, 2 ou 3 qui représente l’index relatif dans la mosaïque actuelle d’un objet [tiled_extent](tiled-extent-class.md) .|
|[Rank, constante](#tiled_index__rank)|Stocke le rang de l' `tiled_index` objet.|
|[mosaïque, constante](#tiled_index__tile)|Stocke un `index` objet de rang 1, 2 ou 3 qui représente les coordonnées de la mosaïque actuelle d’un `tiled_extent` objet.|
|[Constante tile_dim0](#tiled_index__tile_dim0)|Stocke la longueur de la dimension la plus significative.|
|[Constante tile_dim1](#tiled_index__tile_dim1)|Stocke la longueur de la dimension la plus proche de la plus importante.|
|[Constante tile_dim2](#tiled_index__tile_dim2)|Stocke la longueur de la dimension la moins significative.|
|[Constante tile_origin](#tiled_index__tile_origin)|Stocke un `index` objet de rang 1, 2 ou 3 qui représente les coordonnées globales de l’origine de la mosaïque actuelle dans un `tiled_extent` objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[tile_extent](#tile_extent)|Obtient un objet [extent](extent-class.md) qui a les valeurs des arguments de modèle des arguments `tiled_index` template `tiled_index` `_Dim0` , `_Dim1` et `_Dim2` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="tiled_index-constructor"></a><a name="ctor"></a> Constructeur tiled_index

Initialise une nouvelle instance de la classe `tiled_index`.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_index(
    const index<rank>& _Global,
    const index<rank>& _Local,
    const index<rank>& _Tile,
    const index<rank>& _Tile_origin,
    const tile_barrier& _Barrier ) restrict(amp,cpu);

tiled_index(
    const tiled_index& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Global*<br/>
[Index](index-class.md) global du construit `tiled_index` .

*_Local*<br/>
[Index](index-class.md) local du construit.`tiled_index`

*_Tile*<br/>
[Index](index-class.md) de mosaïques du construit`tiled_index`

*_Tile_origin*<br/>
[Index](index-class.md) d’origine de la mosaïque du construit`tiled_index`

*_Barrier*<br/>
Objet [tile_barrier](tile-barrier-class.md) du construit `tiled_index` .

*_Other*<br/>
`tile_index`Objet à copier dans le construit `tiled_index` .

### <a name="overloads"></a>Surcharges

|Nom|Description|
|-|-|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Initialise une nouvelle instance de la `tile_index` classe à partir de l’index de la mosaïque en coordonnées globales et de la position relative dans la mosaïque en coordonnées locales. Les `_Global` `_Tile_origin` paramètres et sont calculés.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Initialise une nouvelle instance de la `tile_index` classe en copiant l’objet spécifié `tiled_index` .|

## <a name="get_tile_extent"></a><a name="tiled_index__get_tile_extent"></a> get_tile_extent

Retourne un objet [extent](extent-class.md) qui a les valeurs des `tiled_index` arguments template `_Dim0` , `_Dim1` et `_Dim2` .

### <a name="syntax"></a>Syntaxe

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

`extent`Objet qui a les valeurs des `tiled_index` arguments template `_Dim0` , `_Dim1` et `_Dim2` .

## <a name="barrier"></a><a name="tiled_index__barrier"></a> bloqué

Stocke un objet [tile_barrier](tile-barrier-class.md) qui représente un cloisonnement dans la mosaïque actuelle de threads.

### <a name="syntax"></a>Syntaxe

```cpp
const tile_barrier barrier;
```

## <a name="global"></a><a name="tiled_index__global"></a> Généralités

Stocke un objet [index](index-class.md) de rang 1, 2 ou 3 qui représente l’index global d’un objet.

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> global;
```

## <a name="local"></a><a name="tiled_index__local"></a> localisé

Stocke un objet [index](index-class.md) de rang 1, 2 ou 3 qui représente l’index relatif dans la mosaïque actuelle d’un objet [tiled_extent](tiled-extent-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> local;
```

## <a name="rank"></a><a name="tiled_index__rank"></a> moteurs

Stocke le rang de l' `tiled_index` objet.

### <a name="syntax"></a>Syntaxe

```cpp
static const int rank = _Rank;
```

## <a name="tile"></a><a name="tiled_index__tile"></a> disposé

Stocke un objet [index](index-class.md) de rang 1, 2 ou 3 qui représente les coordonnées de la mosaïque actuelle d’un objet [tiled_extent](tiled-extent-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> tile;
```

## <a name="tile_dim0"></a><a name="tiled_index__tile_dim0"></a> tile_dim0

Stocke la longueur de la dimension la plus significative.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tiled_index__tile_dim1"></a> tile_dim1

Stocke la longueur de la dimension la plus proche de la plus importante.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tiled_index__tile_dim2"></a> tile_dim2

Stocke la longueur de la dimension la moins significative.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_origin"></a><a name="tiled_index__tile_origin"></a> tile_origin

Stocke un objet [index](index-class.md) de rang 1, 2 ou 3 qui représente les coordonnées globales de l’origine de la mosaïque actuelle dans un objet [tiled_extent](tiled-extent-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a><a name="tile_extent"></a> tile_extent

Obtient un objet [extent](extent-class.md) qui a les valeurs des arguments de modèle des arguments `tiled_index` template `tiled_index` `_Dim0` , `_Dim1` et `_Dim2` .

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
