---
title: tiled_index, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f266efa2fb6de580bc1af04bdee6f80e2244fa23
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070047"
---
# <a name="tiledindex-class"></a>tiled_index, classe

Fournit un index dans un [tiled_extent](tiled-extent-class.md) objet. Cette classe possède des propriétés pour accéder aux éléments par rapport à l’origine de la vignette local et par rapport à l’origine globale. Pour plus d’informations sur les espaces en mosaïque, consultez [à l’aide de vignettes](../../../parallel/amp/using-tiles.md).

## <a name="syntax"></a>Syntaxe

```
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

#### <a name="parameters"></a>Paramètres

*_Dim0*<br/>
La longueur de la dimension la plus significative.

*_Dim1*<br/>
La longueur de la prochaine-à-dimension la plus significative.

*_Dim2*<br/>
La longueur de la dimension la moins significative.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[tiled_index, constructeur](#ctor)|Initialise une nouvelle instance de la classe `tile_index`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|Retourne un [étendue](extent-class.md) objet qui a les valeurs de la `tiled_index` arguments template `_Dim0`, `_Dim1`, et `_Dim2`.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[Barrier (constante)](#tiled_index__barrier)|Stocke un [tile_barrier](tile-barrier-class.md) objet qui représente une barrière de la mosaïque de threads actuelle.|
|||
|[global (constante)](#tiled_index__global)|Stocke un [index](index-class.md) objet de rang 1, 2 ou 3 qui représente l’index global dans un objet de grille.|
|[Constante locale](#tiled_index__local)|Stocke un `index` objet d’index de rang 1, 2 ou 3 qui représente le rapport dans la mosaïque actuelle d’un [tiled_extent](tiled-extent-class.md) objet.|
|[rang (constante)](#tiled_index__rank)|Stocke le rang de le `tiled_index` objet.|
|[Tile (constante)](#tiled_index__tile)|Stocke un `index` objet de rang 1, 2 ou 3 qui représente les coordonnées de la mosaïque actuelle d’un `tiled_extent` objet.|
|[tile_dim0 (constante)](#tiled_index__tile_dim0)|Stocke la longueur de la dimension la plus significative.|
|[tile_dim1 (constante)](#tiled_index__tile_dim1)|Stocke la longueur de la prochaine-à-dimension la plus significative.|
|[tile_dim2 (constante)](#tiled_index__tile_dim2)|Stocke la longueur de la dimension la moins significative.|
|[tile_origin (constante)](#tiled_index__tile_origin)|Stocke un `index` objet de coordonnées de rang 1, 2 ou 3 qui représente les paramètres globaux de l’origine de la mosaïque actuelle dans un `tiled_extent` objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[tile_extent](#tile_extent)|Obtient un [étendue](extent-class.md) objet qui a les valeurs de la `tiled_index` arguments template `tiled_index` arguments template `_Dim0`, `_Dim1`, et `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="tiled_index__ctor"></a>  tiled_index, constructeur

Initialise une nouvelle instance de la classe `tiled_index`.

## <a name="syntax"></a>Syntaxe

```
tiled_index(
    const index<rank>& _Global,
    const index<rank>& _Local,
    const index<rank>& _Tile,
    const index<rank>& _Tile_origin,
    const tile_barrier& _Barrier ) restrict(amp,cpu);

tiled_index(
    const tiled_index& _Other ) restrict(amp,cpu);
```

#### <a name="parameters"></a>Paramètres

*_Global*<br/>
Global [index](index-class.md) de construit `tiled_index`.

*_Locale*<br/>
Local [index](index-class.md) de construit `tiled_index`

*_Tile*<br/>
La vignette [index](index-class.md) de construit `tiled_index`

*_Tile_origin*<br/>
L’origine de la vignette [index](index-class.md) de construit `tiled_index`

*_Barrier*<br/>
Le [tile_barrier](tile-barrier-class.md) objet de construit `tiled_index`.

*_Autre*<br/>
Le `tile_index` objet doit être copié vers construit `tiled_index`.

## <a name="overloads"></a>Overloads

|||
|-|-|
|Name|Description|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Initialise une nouvelle instance de la `tile_index` classe à partir de l’index de la mosaïque en coordonnées globales et la position relative dans la mosaïque en coordonnées locales. Le `_Global` et `_Tile_origin` paramètres sont calculées.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Initialise une nouvelle instance de la `tile_index` classe en copiant le texte spécifié `tiled_index` objet.|

## <a name="tiled_index__get_tile_extent"></a>  get_tile_extent

Retourne un [étendue](extent-class.md) objet qui a les valeurs de la `tiled_index` arguments template `_Dim0`, `_Dim1`, et `_Dim2`.

## <a name="syntax"></a>Syntaxe

```
extent<rank> get_tile_extent()restrict(amp,cpu);
```

## <a name="return-value"></a>Valeur de retour

Un `extent` objet qui a les valeurs de la `tiled_index` arguments template `_Dim0`, `_Dim1`, et `_Dim2`.

## <a name="tiled_index__barrier"></a>  cloisonnement

Stocke un [tile_barrier](tile-barrier-class.md) objet qui représente une barrière de la mosaïque de threads actuelle.

## <a name="syntax"></a>Syntaxe

```
const tile_barrier barrier;
```

## <a name="tiled_index__global"></a>  global

Stocke un [index](index-class.md) objet de rang 1, 2 ou 3 qui représente l’index global d’un objet.

## <a name="syntax"></a>Syntaxe

```
const index<rank> global;
```

## <a name="tiled_index__local"></a>  local

Stocke un [index](index-class.md) objet d’index de rang 1, 2 ou 3 qui représente le rapport dans la mosaïque actuelle d’un [tiled_extent](tiled-extent-class.md) objet.

## <a name="syntax"></a>Syntaxe

```
const index<rank> local;
```

## <a name="tiled_index__rank"></a>  rang

Stocke le rang de le `tiled_index` objet.

## <a name="syntax"></a>Syntaxe

```
static const int rank = _Rank;
```

## <a name="tiled_index__tile"></a>  vignette

Stocke un [index](index-class.md) objet de rang 1, 2 ou 3 qui représente les coordonnées de la mosaïque actuelle d’un [tiled_extent](tiled-extent-class.md) objet.

## <a name="syntax"></a>Syntaxe

```
const index<rank> tile;
```

## <a name="tiled_index__tile_dim0"></a>  tile_dim0

Stocke la longueur de la dimension la plus significative.

## <a name="syntax"></a>Syntaxe

```
static const int tile_dim0 = _Dim0;
```

## <a name="tiled_index__tile_dim1"></a>  tile_dim1

Stocke la longueur de la prochaine-à-dimension la plus significative.

## <a name="syntax"></a>Syntaxe

```
static const int tile_dim1 = _Dim1;
```

## <a name="tiled_index__tile_dim2"></a>  tile_dim2

Stocke la longueur de la dimension la moins significative.

## <a name="syntax"></a>Syntaxe

```
static const int tile_dim2 = _Dim2;
```

## <a name="tiled_index__tile_origin"></a>  tile_origin

Stocke un [index](index-class.md) objet de coordonnées de rang 1, 2 ou 3 qui représente les paramètres globaux de l’origine de la mosaïque actuelle au sein d’un [tiled_extent](tiled-extent-class.md) objet.

## <a name="syntax"></a>Syntaxe

```
const index<rank> tile_origin
```

## <a name="tile_extent"></a>  tile_extent
  Obtient un [étendue](extent-class.md) objet qui a les valeurs de la `tiled_index` arguments template `tiled_index` arguments template `_Dim0`, `_Dim1`, et `_Dim2`.

## <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
