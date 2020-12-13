---
description: 'En savoir plus sur : classe tiled_extent'
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
ms.openlocfilehash: ca5b5c630152263ca49adf5c201ee0b892a192c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163871"
---
# <a name="tiled_extent-class"></a>tiled_extent, classe

Un `tiled_extent` objet est un `extent` objet d’une à trois dimensions qui subdivise l’espace d’étendue en mosaïques unidimensionnelles, en deux ou trois dimensions.

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
Longueur de la dimension la plus significative.

*_Dim1*<br/>
Longueur de la dimension la plus proche de la plus importante.

*_Dim2*<br/>
Longueur de la dimension la moins significative.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur tiled_extent](#ctor)|Initialise une nouvelle instance de la classe `tiled_extent`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Retourne un `extent` objet qui capture les valeurs des `tiled_extent` arguments template `_Dim0` , `_Dim1` et `_Dim2` .|
|[Tableau](#pad)|Retourne un nouvel `tiled_extent` objet dont les étendues sont ajustées de façon à ce qu’elles soient uniformément divisibles par les dimensions de la mosaïque.|
|[truncate](#truncate)|Retourne un nouvel `tiled_extent` objet avec des étendues ajustées de façon à ce qu’elles soient uniformément divisibles par les dimensions de la mosaïque.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur =](#operator_eq)|Copie le contenu de l’objet spécifié dans celui- `tiled_index` ci.|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[Constante tile_dim0](#tile_dim0)|Stocke la longueur de la dimension la plus significative.|
|[Constante tile_dim1](#tile_dim1)|Stocke la longueur de la dimension la plus proche de la plus importante.|
|[Constante tile_dim2](#tile_dim2)|Stocke la longueur de la dimension la moins significative.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[tile_extent](#tile_extent)|Obtient un `extent` objet qui capture les valeurs des `tiled_extent` arguments template `_Dim0` , `_Dim1` et `_Dim2` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`extent`

`tiled_extent`

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="tiled_extent-constructor"></a><a name="ctor"></a> constructeur tiled_extent

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
`extent`Objet ou `tiled_extent` à copier.

## <a name="get_tile_extent"></a><a name="get_tile_extent"></a> get_tile_extent

Retourne un `extent` objet qui capture les valeurs des `tiled_extent` arguments template `_Dim0` , `_Dim1` et `_Dim2` .

### <a name="syntax"></a>Syntaxe

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

`extent`Objet qui capture les dimensions de cette `tiled_extent` instance.

## <a name="pad"></a><a name="pad"></a> remplir

Retourne un nouvel `tiled_extent` objet dont les étendues sont ajustées de façon à ce qu’elles soient uniformément divisibles par les dimensions de la mosaïque.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>Valeur de retour

Nouvel `tiled_extent` objet, par valeur.

## <a name="truncate"></a><a name="truncate"></a> tronquer

Retourne un nouvel `tiled_extent` objet avec des étendues ajustées de façon à ce qu’elles soient uniformément divisibles par les dimensions de la mosaïque.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne un nouvel `tiled_extent` objet avec des étendues ajustées de façon à ce qu’elles soient uniformément divisibles par les dimensions de la mosaïque.

## <a name="operator"></a><a name="operator_eq"></a> opérateur =

Copie le contenu de l’objet spécifié dans celui- `tiled_index` ci.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
`tiled_index`Objet à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur renvoyée

Référence à cette `tiled_index` instance.

## <a name="tile_dim0"></a><a name="tile_dim0"></a> tile_dim0

Stocke la longueur de la dimension la plus significative.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tile_dim1"></a> tile_dim1

Stocke la longueur de la dimension la plus proche de la plus importante.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tile_dim2"></a> tile_dim2

Stocke la longueur de la dimension la moins significative.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a><a name="tile_extent"></a> tile_extent

Obtient un `extent` objet qui capture les valeurs des `tiled_extent` arguments template `_Dim0` , `_Dim1` et `_Dim2` .

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
