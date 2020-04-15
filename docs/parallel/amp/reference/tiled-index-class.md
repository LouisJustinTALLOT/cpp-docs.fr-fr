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
ms.openlocfilehash: 46a6b3548526f0917c4e022a12bf859242e70b20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375483"
---
# <a name="tiled_index-class"></a>tiled_index, classe

Fournit un index dans un [objet tiled_extent.](tiled-extent-class.md) Cette classe a des propriétés d’accès aux éléments relatifs à l’origine locale de tuiles et par rapport à l’origine mondiale. Pour plus d’informations sur les espaces carrelés, voir [Using Tiles](../../../parallel/amp/using-tiles.md).

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
La longueur de la dimension la plus significative.

*_Dim1*<br/>
La longueur de la dimension la plus significative.

*_Dim2*<br/>
La longueur de la dimension la moins significative.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[tiled_index Constructeur](#ctor)|Initialise une nouvelle instance de la classe `tile_index`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|Retourne un objet [d’étendue](extent-class.md) `tiled_index` qui `_Dim0`a `_Dim1`les `_Dim2`valeurs des arguments de modèle , , et .|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[barrière Constante](#tiled_index__barrier)|Stocke un [objet tile_barrier](tile-barrier-class.md) qui représente une barrière dans la tuile actuelle des fils.|
|||
|[Constant mondial](#tiled_index__global)|Stocke un [objet d’indice](index-class.md) de rang 1, 2 ou 3 qui représente l’indice mondial dans un objet de grille.|
|[Constante locale](#tiled_index__local)|Stocke `index` un objet de rang 1, 2 ou 3 qui représente l’indice relatif dans la tuile actuelle d’un objet [tiled_extent.](tiled-extent-class.md)|
|[rang Constant](#tiled_index__rank)|Stocke le `tiled_index` rang de l’objet.|
|[tuile Constant](#tiled_index__tile)|Stocke `index` un objet de rang 1, 2 ou 3 qui représente `tiled_extent` les coordonnées de la tuile actuelle d’un objet.|
|[tile_dim0 Constant](#tiled_index__tile_dim0)|Stocke la longueur de la dimension la plus importante.|
|[tile_dim1 Constant](#tiled_index__tile_dim1)|Stocke la longueur de la dimension la plus importante.|
|[tile_dim2 Constant](#tiled_index__tile_dim2)|Stocke la longueur de la dimension la moins importante.|
|[tile_origin Constant](#tiled_index__tile_origin)|Stocke `index` un objet de rang 1, 2 ou 3 qui représente les coordonnées `tiled_extent` globales de l’origine de la tuile actuelle dans un objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[tile_extent](#tile_extent)|Obtient un objet [d’étendue](extent-class.md) `tiled_index` qui `tiled_index` a `_Dim0`les `_Dim1`valeurs `_Dim2`des arguments de modèle arguments , , et .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="tiled_index-constructor"></a><a name="ctor"></a>tiled_index Constructeur

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
[L’indice](index-class.md) mondial `tiled_index`de la construction .

*_Local*<br/>
[L’indice](index-class.md) local des`tiled_index`

*_Tile*<br/>
[L’index](index-class.md) de tuiles de la construction`tiled_index`

*_Tile_origin*<br/>
[L’indice](index-class.md) d’origine des tuiles de la construction`tiled_index`

*_Barrier*<br/>
Le [tile_barrier](tile-barrier-class.md) objet de la `tiled_index`construction .

*_Other*<br/>
L’objet `tile_index` à copier à `tiled_index`la construction .

### <a name="overloads"></a>Overloads

|||
|-|-|
|Nom|Description|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Initialise une nouvelle instance `tile_index` de la classe à partir de l’index de la tuile dans les coordonnées globales et la position relative dans la tuile dans les coordonnées locales. Les `_Global` `_Tile_origin` paramètres et les paramètres sont calculés.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Initialise une nouvelle instance `tile_index` de la classe `tiled_index` en copiant l’objet spécifié.|

## <a name="get_tile_extent"></a><a name="tiled_index__get_tile_extent"></a>get_tile_extent

Retourne un objet [d’étendue](extent-class.md) `tiled_index` qui `_Dim0`a `_Dim1`les `_Dim2`valeurs des arguments de modèle , , et .

### <a name="syntax"></a>Syntaxe

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

Un `extent` objet qui a `tiled_index` les `_Dim0`valeurs `_Dim1`des `_Dim2`arguments de modèle , , et .

## <a name="barrier"></a><a name="tiled_index__barrier"></a>Barrière

Stocke un [objet tile_barrier](tile-barrier-class.md) qui représente une barrière dans la tuile actuelle des fils.

### <a name="syntax"></a>Syntaxe

```cpp
const tile_barrier barrier;
```

## <a name="global"></a><a name="tiled_index__global"></a>Mondiale

Stocke un [objet d’indice](index-class.md) de rang 1, 2 ou 3 qui représente l’indice mondial d’un objet.

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> global;
```

## <a name="local"></a><a name="tiled_index__local"></a>Local

Stocke un objet [d’index](index-class.md) de rang 1, 2 ou 3 qui représente l’indice relatif dans la tuile actuelle d’un objet [tiled_extent.](tiled-extent-class.md)

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> local;
```

## <a name="rank"></a><a name="tiled_index__rank"></a>Rang

Stocke le `tiled_index` rang de l’objet.

### <a name="syntax"></a>Syntaxe

```cpp
static const int rank = _Rank;
```

## <a name="tile"></a><a name="tiled_index__tile"></a>Tuile

Stocke un objet [d’index](index-class.md) de rang 1, 2 ou 3 qui représente les coordonnées de la tuile actuelle d’un objet [tiled_extent.](tiled-extent-class.md)

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> tile;
```

## <a name="tile_dim0"></a><a name="tiled_index__tile_dim0"></a>tile_dim0

Stocke la longueur de la dimension la plus importante.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tiled_index__tile_dim1"></a>tile_dim1

Stocke la longueur de la dimension la plus importante.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tiled_index__tile_dim2"></a>tile_dim2

Stocke la longueur de la dimension la moins importante.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_origin"></a><a name="tiled_index__tile_origin"></a>tile_origin

Stocke un objet [d’index](index-class.md) de rang 1, 2 ou 3 qui représente les coordonnées globales de l’origine de la tuile actuelle dans un [objet tiled_extent.](tiled-extent-class.md)

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a><a name="tile_extent"></a>tile_extent

Obtient un objet [d’étendue](extent-class.md) `tiled_index` qui `tiled_index` a `_Dim0`les `_Dim1`valeurs `_Dim2`des arguments de modèle arguments , , et .

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>Voir aussi

[Concurrency Namespace (AMP)](concurrency-namespace-cpp-amp.md)
