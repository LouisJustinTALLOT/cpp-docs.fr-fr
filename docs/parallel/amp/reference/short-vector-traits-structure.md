---
title: short_vector_traits Structure
ms.date: 11/04/2016
f1_keywords:
- short_vector_traits
- AMP_SHORT_VECTORS/short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::size Constant
ms.assetid: cd9492da-9e02-4a6e-9d50-b61252cdb460
ms.openlocfilehash: fd86228417234f705d3f765624cd942c982df875
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456184"
---
# <a name="shortvectortraits-structure"></a>short_vector_traits Structure

short_vector_traits permet la récupération de la longueur du vecteur = sous-jacent et type scalaire d’un type de vecteur court ou un type scalaire

## <a name="syntax"></a>Syntaxe

```
template<
    typename T
>
struct short_vector_traits;
template<>
struct short_vector_traits<unsigned int>;
template<>
struct short_vector_traits<uint_2>;
template<>
struct short_vector_traits<uint_3>;
template<>
struct short_vector_traits<uint_4>;
template<>
struct short_vector_traits<int>;
template<>
struct short_vector_traits<int_2>;
template<>
struct short_vector_traits<int_3>;
template<>
struct short_vector_traits<int_4>;
template<>
struct short_vector_traits<float>;
template<>
struct short_vector_traits<float_2>;
template<>
struct short_vector_traits<float_3>;
template<>
struct short_vector_traits<float_4>;
template<>
struct short_vector_traits<unorm>;
template<>
struct short_vector_traits<unorm_2>;
template<>
struct short_vector_traits<unorm_3>;
template<>
struct short_vector_traits<unorm_4>;
template<>
struct short_vector_traits<norm>;
template<>
struct short_vector_traits<norm_2>;
template<>
struct short_vector_traits<norm_3>;
template<>
struct short_vector_traits<norm_4>;
template<>
struct short_vector_traits<double>;
template<>
struct short_vector_traits<double_2>;
template<>
struct short_vector_traits<double_3>;
template<>
struct short_vector_traits<double_4>;
```

#### <a name="parameters"></a>Paramètres

`T`

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[short_vector_traits::short_vector_traits, constructeur](#ctor)||

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[short_vector_traits::Size, constante](#size)||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`short_vector_traits`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp_short_vectors.h

**Namespace :** Concurrency::graphics

##  <a name="ctor"></a>  short_vector_traits::short_vector_traits, constructeur

```
short_vector_traits();
```

##  <a name="size"></a>  short_vector_traits::Size, constante

```
static int const size = 1;
```

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
