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
ms.openlocfilehash: e2248c770c7eedde59d1cb592f7d5d7c1bfbde9a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126420"
---
# <a name="tiled_extent-class"></a>tiled_extent, classe

Un objet `tiled_extent` est un objet `extent` d’une à trois dimensions qui divise l’espace d’étendue en mosaïques unidimensionnelles, en deux ou trois dimensions.

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

|Name|Description|
|----------|-----------------|
|[Constructeur tiled_extent](#ctor)|Initialise une nouvelle instance de la classe `tiled_extent`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Retourne un objet `extent` qui capture les valeurs des arguments de modèle `tiled_extent` `_Dim0`, `_Dim1`et `_Dim2`.|
|[Tableau](#pad)|Retourne un nouvel objet `tiled_extent` avec des étendues ajustées pour être uniformément divisibles par les dimensions de la mosaïque.|
|[truncate](#truncate)|Retourne un nouvel objet `tiled_extent` avec des étendues ajustées de façon à ce qu’elles soient uniformément divisibles par les dimensions de la mosaïque.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator=](#operator_eq)|Copie le contenu de l’objet `tiled_index` spécifié dans celui-ci.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[Constante tile_dim0](#tile_dim0)|Stocke la longueur de la dimension la plus significative.|
|[Constante tile_dim1](#tile_dim1)|Stocke la longueur de la dimension la plus proche de la plus importante.|
|[Constante tile_dim2](#tile_dim2)|Stocke la longueur de la dimension la moins significative.|

### <a name="public-data-members"></a>Membres de données publiques

|Name|Description|
|----------|-----------------|
|[tile_extent](#tile_extent)|Obtient un objet `extent` qui capture les valeurs des arguments de modèle `tiled_extent` `_Dim0`, `_Dim1`et `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`extent`

`tiled_extent`

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="ctor"></a> constructeur tiled_extent

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
`extent` ou `tiled_extent` objet à copier.

## <a name="get_tile_extent"></a> get_tile_extent

Retourne un objet `extent` qui capture les valeurs des arguments de modèle `tiled_extent` `_Dim0`, `_Dim1`et `_Dim2`.

### <a name="syntax"></a>Syntaxe

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Valeur de retour

Objet `extent` qui capture les dimensions de cette `tiled_extent` instance.

## <a name="pad"></a> remplir

Retourne un nouvel objet `tiled_extent` avec des étendues ajustées pour être uniformément divisibles par les dimensions de la mosaïque.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>Valeur de retour

Nouvel objet `tiled_extent`, par valeur.
## <a name="truncate"></a> tronquer

Retourne un nouvel objet `tiled_extent` avec des étendues ajustées de façon à ce qu’elles soient uniformément divisibles par les dimensions de la mosaïque.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne un nouvel objet `tiled_extent` avec des étendues ajustées de façon à ce qu’elles soient uniformément divisibles par les dimensions de la mosaïque.

## <a name="operator_eq"></a> opérateur =

Copie le contenu de l’objet `tiled_index` spécifié dans celui-ci.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet `tiled_index` à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur de retour

Référence à cette instance de `tiled_index`.

## <a name="tile_dim0"></a> tile_dim0

Stocke la longueur de la dimension la plus significative.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a> tile_dim1

Stocke la longueur de la dimension la plus proche de la plus importante.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a> tile_dim2

Stocke la longueur de la dimension la moins significative.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a> tile_extent
  Obtient un objet `extent` qui capture les valeurs des arguments de modèle `tiled_extent` `_Dim0`, `_Dim1`et `_Dim2`.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
