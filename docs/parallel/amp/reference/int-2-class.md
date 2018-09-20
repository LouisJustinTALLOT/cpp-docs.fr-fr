---
title: int_2, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp_short_vectors/Concurrency::graphics::int_2::y
- amp_short_vectors/Concurrency::graphics::int_2::set_x
- amp_short_vectors/Concurrency::graphics::int_2::set_y
- amp_short_vectors/Concurrency::graphics::int_2::get_yx
- amp_short_vectors/Concurrency::graphics::int_2::operator++
- amp_short_vectors/Concurrency::graphics::int_2::x
- amp_short_vectors/Concurrency::graphics::int_2::set_yx
- amp_short_vectors/Concurrency::graphics::int_2::operator/=
- amp_short_vectors/Concurrency::graphics::int_2::get_y
- amp_short_vectors/Concurrency::graphics::int_2::gr
- amp_short_vectors/Concurrency::graphics::int_2::operator*=
- amp_short_vectors/Concurrency::graphics::int_2::r
- amp_short_vectors/Concurrency::graphics::int_2::get_xy
- amp_short_vectors/Concurrency::graphics::int_2::operator=
- amp_short_vectors/Concurrency::graphics::int_2::g
- amp_short_vectors/Concurrency::graphics::int_2::rg
- amp_short_vectors/Concurrency::graphics::int_2::xy
- amp_short_vectors/Concurrency::graphics::int_2::operator-=
- amp_short_vectors/Concurrency::graphics::int_2::get_x
- amp_short_vectors/Concurrency::graphics::int_2::yx
- amp_short_vectors/Concurrency::graphics::int_2
- amp_short_vectors/Concurrency::graphics::int_2::operator-
- amp_short_vectors/Concurrency::graphics::int_2::set_xy
- amp_short_vectors/Concurrency::graphics::int_2::operator+=
- amp_short_vectors/Concurrency::graphics::int_2::operator--
dev_langs:
- C++
ms.assetid: 258b02e9-f1ee-46c2-8edd-dc9f69184846
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77d5738572164255494ad4a37b2bb0816fcb27a1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429204"
---
# <a name="int2-class"></a>int_2, classe

Représente un vecteur court de deux entiers.

## <a name="syntax"></a>Syntaxe

```
class int_2;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[int_2 constructeur](#ctor)|Surchargé. Par défaut constructeur initialise tous les éléments par 0.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|int_2::get_x||
|int_2::get_xy||
|int_2::get_y||
|int_2::get_yx||
|int_2::ref_g||
|int_2::ref_r||
|int_2::ref_x||
|int_2::ref_y||
|int_2::set_x||
|int_2::set_xy||
|int_2::set_y||
|int_2::set_yx||

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|int_2::operator-||
|int_2::operator--||
|int_2::operator%=||
|int_2::operator & =||
|int_2::operator * =||
|/ = int_2::operator||
|int_2::operator ^ =||
|int_2::operator&#124;=||
|int_2::operator ~||
|int_2::operator ++||
|int_2::operator +=||
|int_2::operator <\<=||
|int_2::operator=||
|int_2::operator =||
|int_2::operator >> =||

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[taille (constante)](#int_2__size)||

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|int_2::g||
|int_2::GR||
|int_2::r||
|int_2::rg||
|int_2::x||
|int_2::XY||
|int_2::y||
|int_2::yx||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`int_2`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp_short_vectors.h

**Namespace :** Concurrency::graphics

##  <a name="ctor"></a> int_2

Par défaut constructeur initialise tous les éléments par 0.

```
int_2() restrict(amp,
    cpu);

int_2(
    int _V0,
    int _V1) restrict(amp,
    cpu);

int_2(
    int _V) restrict(amp,
    cpu);

int_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
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

##  <a name="int_2__size"></a> Taille

```
static const int size = 2;
```

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
