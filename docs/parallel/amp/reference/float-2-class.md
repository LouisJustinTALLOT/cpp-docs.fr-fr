---
description: 'En savoir plus sur : classe float_2'
title: float_2, classe
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::float_2::yx
- amp_short_vectors/Concurrency::graphics::float_2::operator-=
- amp_short_vectors/Concurrency::graphics::float_2::operator++
- amp_short_vectors/Concurrency::graphics::float_2::operator-
- amp_short_vectors/Concurrency::graphics::float_2::r
- amp_short_vectors/Concurrency::graphics::float_2::get_yx
- amp_short_vectors/Concurrency::graphics::float_2::get_xy
- amp_short_vectors/Concurrency::graphics::float_2::operator/=
- amp_short_vectors/Concurrency::graphics::float_2::set_yx
- amp_short_vectors/Concurrency::graphics::float_2::x
- amp_short_vectors/Concurrency::graphics::float_2::get_y
- amp_short_vectors/Concurrency::graphics::float_2::operator+=
- amp_short_vectors/Concurrency::graphics::float_2::gr
- amp_short_vectors/Concurrency::graphics::float_2::operator=
- amp_short_vectors/Concurrency::graphics::float_2::set_x
- amp_short_vectors/Concurrency::graphics::float_2::operator--
- amp_short_vectors/Concurrency::graphics::float_2::get_x
- amp_short_vectors/Concurrency::graphics::float_2::operator*=
- amp_short_vectors/Concurrency::graphics::float_2::rg
- amp_short_vectors/Concurrency::graphics::float_2::set_xy
- amp_short_vectors/Concurrency::graphics::float_2::xy
- amp_short_vectors/Concurrency::graphics::float_2
- amp_short_vectors/Concurrency::graphics::float_2::set_y
- amp_short_vectors/Concurrency::graphics::float_2::y
- amp_short_vectors/Concurrency::graphics::float_2::g
ms.assetid: b3ebd48e-f8c8-4f00-a640-357f702f0cae
ms.openlocfilehash: a0d350c9742da6c11a5bf982a1638a1fc0921eb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325848"
---
# <a name="float_2-class"></a>float_2, classe

Représente un vecteur abrégé de deux valeurs float.

## <a name="syntax"></a>Syntaxe

```cpp
class float_2;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur float_2](#ctor)|Surchargé. Le constructeur par défaut initialise tous les éléments avec 0.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|float_2 :: get_x||
|float_2 :: get_xy||
|float_2 :: get_y||
|float_2 :: get_yx||
|float_2 :: ref_g||
|float_2 :: ref_r||
|float_2 :: ref_x||
|float_2 :: ref_y||
|float_2 :: set_x||
|float_2 :: set_xy||
|float_2 :: set_y||
|float_2 :: set_yx||

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|float_2 :: Operator-||
|float_2 :: Operator--||
|float_2 :: Operator * =||
|float_2 :: Operator/=||
|float_2 :: Operator + +||
|float_2 :: Operator + =||
|float_2 :: Operator =||
|float_2 :: Operator-=||

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[taille, constante](#float_2__size)||

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|float_2 :: g||
|float_2 :: gr||
|float_2 :: r||
|float_2 :: RG||
|float_2 :: x||
|float_2 :: XY||
|float_2 :: y||
|float_2 :: YX||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`float_2`

## <a name="requirements"></a>Spécifications

**En-tête :** amp_short_vectors. h

**Espace de noms :** Concurrency :: Graphics

## <a name="float_2"></a><a name="ctor"></a> float_2

Le constructeur par défaut initialise tous les éléments avec 0.

```cpp
float_2() restrict(amp,
    cpu);

float_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

float_2(
    float _V) restrict(amp,
    cpu);

float_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
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

## <a name="size"></a><a name="float_2__size"></a> corps

```cpp
static const int size = 2;
```

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
