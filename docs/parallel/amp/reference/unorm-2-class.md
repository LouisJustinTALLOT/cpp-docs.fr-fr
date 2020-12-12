---
description: 'En savoir plus sur : classe unorm_2'
title: unorm_2, classe
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator+=
- amp_short_vectors/Concurrency::graphics::unnorm_2::y
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::x
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator--
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator*=
- amp_short_vectors/Concurrency::graphics::unnorm_2::xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator=
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::rg
- amp_short_vectors/Concurrency::graphics::unorm_2
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-=
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator/=
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::gr
- amp_short_vectors/Concurrency::graphics::unnorm_2::r
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::g
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator++
ms.assetid: 62e88ea7-e29f-4f62-95ce-61a1f39f5e34
ms.openlocfilehash: 1a91c1c203466f6ece535d45d5c2c828c8150dbd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326374"
---
# <a name="unorm_2-class"></a>unorm_2, classe

Représente un vecteur abrégé de deux nombres normaux non signés.

## <a name="syntax"></a>Syntaxe

```cpp
class unorm_2;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur unorm_2](#ctor)|Surchargé. Le constructeur par défaut initialise tous les éléments avec 0.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|unorm_2 :: get_x||
|unorm_2 :: get_xy||
|unorm_2 :: get_y||
|unorm_2 :: get_yx||
|unorm_2 :: ref_g||
|unorm_2 :: ref_r||
|unorm_2 :: ref_x||
|unorm_2 :: ref_y||
|unorm_2 :: set_x||
|unorm_2 :: set_xy||
|unorm_2 :: set_y||
|unorm_2 :: set_yx||

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|unorm_2 :: Operator--||
|unorm_2 :: Operator * =||
|unorm_2 :: Operator/=||
|unorm_2 :: Operator + +||
|unorm_2 :: Operator + =||
|unorm_2 :: Operator =||
|unorm_2 :: Operator-=||

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|unorm_2::size, constante||

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|unorm_2 :: g||
|unorm_2 :: gr||
|unorm_2 :: r||
|unorm_2 :: RG||
|unorm_2 :: x||
|unorm_2 :: XY||
|unorm_2 :: y||
|unorm_2 :: YX||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`unorm_2`

## <a name="requirements"></a>Spécifications

**En-tête :** amp_short_vectors. h

**Espace de noms :** Concurrency :: Graphics

## <a name="unorm_2"></a><a name="ctor"></a> unorm_2

Le constructeur par défaut initialise tous les éléments avec 0.

```cpp
unorm_2() restrict(amp,
    cpu);

unorm_2(
    unorm _V0,
    unorm _V1) restrict(amp,
    cpu);

unorm_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

unorm_2(
    unorm _V) restrict(amp,
    cpu);

explicit unorm_2(
    float _V) restrict(amp,
    cpu);

unorm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
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

## <a name="size"></a><a name="unorm_2__size"></a> corps

```cpp
static const int size = 2;
```

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
