---
title: norm_2, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp_short_vectors/Concurrency::graphics::norm_2::set_x
- amp_short_vectors/Concurrency::graphics::norm_2::set_xy
- amp_short_vectors/Concurrency::graphics::norm_2::g
- amp_short_vectors/Concurrency::graphics::norm_2::get_yx
- amp_short_vectors/Concurrency::graphics::norm_2::set_yx
- amp_short_vectors/Concurrency::graphics::norm_2::operator-=
- amp_short_vectors/Concurrency::graphics::norm_2::operator/=
- amp_short_vectors/Concurrency::graphics::norm_2::operator*=
- amp_short_vectors/Concurrency::graphics::norm_2::yx
- amp_short_vectors/Concurrency::graphics::norm_2::y
- amp_short_vectors/Concurrency::graphics::norm_2::xy
- amp_short_vectors/Concurrency::graphics::norm_2::operator++
- amp_short_vectors/Concurrency::graphics::norm_2::operator-
- amp_short_vectors/Concurrency::graphics::norm_2::rg
- amp_short_vectors/Concurrency::graphics::norm_2::operator=
- amp_short_vectors/Concurrency::graphics::norm_2::get_y
- amp_short_vectors/Concurrency::graphics::norm_2::r
- amp_short_vectors/Concurrency::graphics::norm_2::get_x
- amp_short_vectors/Concurrency::graphics::norm_2::get_xy
- amp_short_vectors/Concurrency::graphics::norm_2::gr
- amp_short_vectors/Concurrency::graphics::norm_2::set_y
- amp_short_vectors/Concurrency::graphics::norm_2::x
- amp_short_vectors/Concurrency::graphics::norm_2::operator+=
- amp_short_vectors/Concurrency::graphics::norm_2
- amp_short_vectors/Concurrency::graphics::norm_2::operator--
dev_langs:
- C++
ms.assetid: 80703f9b-61f4-414a-93fd-bc774f7d3393
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 352e614b2b99f21b3eba0c03b59dcebb992abd90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431150"
---
# <a name="norm2-class"></a>norm_2, classe

Représente un vecteur court de deux nombres normaux.

## <a name="syntax"></a>Syntaxe

```
class norm_2;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[norm_2 constructeur](#ctor)|Surchargé. Par défaut constructeur initialise tous les éléments par 0.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|norm_2::get_x||
|norm_2::get_xy||
|norm_2::get_y||
|norm_2::get_yx||
|norm_2::ref_g||
|norm_2::ref_r||
|norm_2::ref_x||
|norm_2::ref_y||
|norm_2::set_x||
|norm_2::set_xy||
|norm_2::set_y||
|norm_2::set_yx||

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|norm_2::operator-||
|norm_2::operator--||
|norm_2::operator * =||
|/ = norm_2::operator||
|norm_2::operator ++||
|norm_2::operator +=||
|norm_2::operator=||
|norm_2::operator =||

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[taille (constante)](#norm_2__size)||

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|norm_2::g||
|norm_2::GR||
|norm_2::r||
|norm_2::RG||
|norm_2::x||
|norm_2::XY||
|norm_2::y||
|norm_2::YX||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`norm_2`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp_short_vectors.h

**Namespace :** Concurrency::graphics

##  <a name="ctor"></a> norm_2

Par défaut constructeur initialise tous les éléments par 0.

```
norm_2() restrict(amp,
    cpu);

norm_2(
    norm _V0,
    norm _V1) restrict(amp,
    cpu);

norm_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

norm_2(
    unorm _V0,
    unorm _V1) restrict(amp,
    cpu);

norm_2(
    norm _V) restrict(amp,
    cpu);

explicit norm_2(
    float _V) restrict(amp,
    cpu);

norm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
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

##  <a name="norm_2__size"></a> Taille

```
static const int size = 2;
```

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
