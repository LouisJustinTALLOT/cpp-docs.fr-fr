---
description: 'En savoir plus sur : classe uint_2'
title: uint_2, classe
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::uint_2::set_xy
- amp_short_vectors/Concurrency::graphics::uint_2::y
- amp_short_vectors/Concurrency::graphics::uint_2::gr
- amp_short_vectors/Concurrency::graphics::uint_2::operator-
- amp_short_vectors/Concurrency::graphics::uint_2::get_x
- amp_short_vectors/Concurrency::graphics::uint_2::operator-=
- amp_short_vectors/Concurrency::graphics::uint_2::r
- amp_short_vectors/Concurrency::graphics::uint_2::yx
- amp_short_vectors/Concurrency::graphics::uint_2::operator--
- amp_short_vectors/Concurrency::graphics::uint_2::set_yx
- amp_short_vectors/Concurrency::graphics::uint_2::operator=
- amp_short_vectors/Concurrency::graphics::uint_2::set_x
- amp_short_vectors/Concurrency::graphics::uint_2::operator+=
- amp_short_vectors/Concurrency::graphics::uint_2::get_y
- amp_short_vectors/Concurrency::graphics::uint_2::xy
- amp_short_vectors/Concurrency::graphics::uint_2::x
- amp_short_vectors/Concurrency::graphics::uint_2::get_xy
- amp_short_vectors/Concurrency::graphics::uint_2::set_y
- amp_short_vectors/Concurrency::graphics::uint_2
- amp_short_vectors/Concurrency::graphics::uint_2::operator*=
- amp_short_vectors/Concurrency::graphics::uint_2::get_yx
- amp_short_vectors/Concurrency::graphics::uint_2::operator/=
- amp_short_vectors/Concurrency::graphics::uint_2::g
- amp_short_vectors/Concurrency::graphics::uint_2::operator++
- amp_short_vectors/Concurrency::graphics::uint_2::rg
ms.assetid: 9fcc9129-72b1-4da7-9012-4d3be15f1c52
ms.openlocfilehash: 6cf10e10baad6cedb06cef4358feebb11e6ce076
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325808"
---
# <a name="uint_2-class"></a>uint_2, classe

Représente un vecteur abrégé de deux entiers non signés.

## <a name="syntax"></a>Syntaxe

```cpp
class uint_2;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur uint_2](#ctor)|Surchargé. Le constructeur par défaut initialise tous les éléments avec 0.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|uint_2 :: get_x||
|uint_2 :: get_xy||
|uint_2 :: get_y||
|uint_2 :: get_yx||
|uint_2 :: ref_g_Method||
|uint_2 :: ref_r_Method||
|uint_2 :: ref_x_Method||
|uint_2 :: ref_y_Method||
|uint_2 :: set_x||
|uint_2 :: set_xy||
|uint_2 :: set_y||
|uint_2 :: set_yx||

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|uint_2 :: Operator--||
|uint_2 :: Operator% =||
|uint_2 :: Operator&=||
|uint_2 :: Operator * =||
|uint_2 :: Operator/=||
|uint_2 :: Operator ^ =||
|uint_2 :: Operator&#124;=||
|uint_2 :: Operator ~||
|uint_2 :: Operator + +||
|uint_2 :: Operator + =||
|uint_2 :: Operator<\<=||
|uint_2 :: Operator =||
|uint_2 :: Operator-=||
|uint_2 :: Operator>>=||

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[taille, constante](#uint_2__size)||

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|uint_2 :: g||
|uint_2 :: gr||
|uint_2 :: r||
|uint_2 :: RG||
|uint_2 :: x||
|uint_2 :: XY||
|uint_2 :: y||
|uint_2 :: YX||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`uint_2`

## <a name="requirements"></a>Spécifications

**En-tête :** amp_short_vectors. h

**Espace de noms :** Concurrency :: Graphics

## <a name="uint_2"></a><a name="ctor"></a> uint_2

Le constructeur par défaut initialise tous les éléments avec 0.

```cpp
uint_2() restrict(amp,
    cpu);

uint_2(
    unsigned int _V0,
    unsigned int _V1) restrict(amp,
    cpu);

uint_2(
    unsigned int _V) restrict(amp,
    cpu);

uint_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const double_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Paramètres

*_V0*<br/>
Valeur pour initialiser l’élément 0.

*_V1*<br/>
Valeur pour initialiser l’élément 1.

*_V*<br/>
Valeur d’initialisation.

*_Other*<br/>
Objet utilisé pour initialiser.

## <a name="size"></a><a name="uint_2__size"></a> corps

```cpp
static const int size = 2;
```

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
