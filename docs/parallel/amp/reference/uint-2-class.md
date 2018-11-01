---
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
ms.openlocfilehash: dc7b00d70a4f816845f5741bf605f1c1bb631ee2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589356"
---
# <a name="uint2-class"></a>uint_2, classe

Représente un vecteur court de deux entiers non signés.

## <a name="syntax"></a>Syntaxe

```
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
|[uint_2 constructeur](#ctor)|Surchargé. Par défaut constructeur initialise tous les éléments par 0.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|uint_2::get_x||
|uint_2::get_xy||
|uint_2::get_y||
|uint_2::get_yx||
|uint_2::ref_g_Method||
|uint_2::ref_r_Method||
|uint_2::ref_x_Method||
|uint_2::ref_y_Method||
|uint_2::set_x||
|uint_2::set_xy||
|uint_2::set_y||
|uint_2::set_yx||

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|uint_2::operator--||
|uint_2::operator % =||
|uint_2::operator & =||
|uint_2::operator * =||
|/ = uint_2::operator||
|uint_2::operator ^ =||
|uint_2::operator&#124;=||
|uint_2::operator ~||
|uint_2::operator ++||
|uint_2::operator +=||
|uint_2::operator <\<=||
|uint_2::operator =||
|uint_2::operator =||
|uint_2::operator >> =||

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[taille (constante)](#uint_2__size)||

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|uint_2::g||
|uint_2::GR||
|uint_2::r||
|uint_2::RG||
|uint_2::x||
|uint_2::XY||
|uint_2::y||
|uint_2::YX||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`uint_2`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp_short_vectors.h

**Namespace :** Concurrency::graphics

##  <a name="ctor"></a> uint_2

Par défaut constructeur initialise tous les éléments par 0.

```
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
La valeur pour initialiser l’élément 0.

*_V1*<br/>
La valeur pour initialiser l’élément 1.

*_V*<br/>
La valeur pour l’initialisation.

*_Autre*<br/>
L’objet utilisé pour initialiser.

##  <a name="uint_2__size"></a> Taille

```
static const int size = 2;
```

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
