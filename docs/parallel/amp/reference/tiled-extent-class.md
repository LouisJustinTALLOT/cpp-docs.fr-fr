---
title: tiled_extent, classe
ms.date: 11/04/2016
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
ms.openlocfilehash: ce2710da1a745efedcd6e9e524355eda41e26de2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374711"
---
# <a name="tiled_extent-class"></a>tiled_extent, classe

Un `tiled_extent` objet `extent` est un objet d’une à trois dimensions qui subdivise l’étendue de l’espace en tuiles unidimensionnelles, bidimensionnelles ou tridimensionnelles.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    int _Dim0,
    int _Dim1,
    int _Dim2
>
class tiled_extent : public Concurrency::extent<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;

template <
    int _Dim0
>
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;
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
|[tiled_extent Constructeur](#ctor)|Initialise une nouvelle instance de la classe `tiled_extent`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Retourne `extent` un objet qui capture `tiled_extent` les `_Dim0`valeurs `_Dim1`des `_Dim2`arguments de modèle , , et .|
|[Pad](#pad)|Retourne un `tiled_extent` nouvel objet avec des étendues ajustées pour être uniformément divisibles par les dimensions de la tuile.|
|[Tronquer](#truncate)|Retourne un `tiled_extent` nouvel objet avec des étendues ajustées pour être uniformément divisible par les dimensions de la tuile.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur](#operator_eq)|Copie le contenu `tiled_index` de l’objet spécifié dans celui-ci.|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[tile_dim0 Constant](#tile_dim0)|Stocke la longueur de la dimension la plus importante.|
|[tile_dim1 Constant](#tile_dim1)|Stocke la longueur de la dimension la plus importante.|
|[tile_dim2 Constant](#tile_dim2)|Stocke la longueur de la dimension la moins importante.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[tile_extent](#tile_extent)|Obtient `extent` un objet qui capture `tiled_extent` les `_Dim0`valeurs `_Dim1`des `_Dim2`arguments de modèle , , et .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`extent`

`tiled_extent`

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="tiled_extent-constructor"></a><a name="ctor"> </a> tiled_extent Constructeur

Initialise une nouvelle instance de la classe `tiled_extent`.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
L’objet `extent` ou `tiled_extent` l’objet à copier.

## <a name="get_tile_extent"></a><a name="get_tile_extent"> </a> get_tile_extent

Retourne `extent` un objet qui capture `tiled_extent` les `_Dim0`valeurs `_Dim1`des `_Dim2`arguments de modèle , , et .

### <a name="syntax"></a>Syntaxe

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

Un `extent` objet qui capture les `tiled_extent` dimensions de cette instance.

## <a name="pad"></a><a name="pad"> </a> pad

Retourne un `tiled_extent` nouvel objet avec des étendues ajustées pour être uniformément divisibles par les dimensions de la tuile.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>Valeur de retour

Le `tiled_extent` nouvel objet, par valeur.

## <a name="truncate"></a><a name="truncate"> </a> tronquer

Retourne un `tiled_extent` nouvel objet avec des étendues ajustées pour être uniformément divisible par les dimensions de la tuile.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne un `tiled_extent` nouvel objet avec des étendues ajustées pour être uniformément divisible par les dimensions de la tuile.

## <a name="operator"></a><a name="operator_eq"> </a> opérateur

Copie le contenu `tiled_index` de l’objet spécifié dans celui-ci.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
L’objet `tiled_index` à copier.

### <a name="return-value"></a>Valeur de retour

Une référence `tiled_index` à cette instance.

## <a name="tile_dim0"></a><a name="tile_dim0"> </a> tile_dim0

Stocke la longueur de la dimension la plus importante.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tile_dim1"> </a> tile_dim1

Stocke la longueur de la dimension la plus importante.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tile_dim2"> </a> tile_dim2

Stocke la longueur de la dimension la moins importante.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a><a name="tile_extent"> </a> tile_extent

Obtient `extent` un objet qui capture `tiled_extent` les `_Dim0`valeurs `_Dim1`des `_Dim2`arguments de modèle , , et .

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Voir aussi

[Concurrency Namespace (AMP)](concurrency-namespace-cpp-amp.md)
