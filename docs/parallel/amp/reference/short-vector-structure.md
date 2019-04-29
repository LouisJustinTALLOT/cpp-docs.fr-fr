---
title: short_vector Structure
ms.date: 11/04/2016
f1_keywords:
- short_vector
- AMP_SHORT_VECTORS/short_vector
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector::short_vector Constructor
ms.assetid: e4f50b8f-1150-437d-b58c-79c5fb883708
ms.openlocfilehash: 012a70ae628a896c8202e46a5624f37f58b0781b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351545"
---
# <a name="shortvector-structure"></a>short_vector Structure

short_vector fournit les définitions de métaprogrammation qui sont utiles pour la programmation des vecteurs courts de manière générique.

## <a name="syntax"></a>Syntaxe

```
template<
    typename _Scalar_type,
    int _Size
>
struct short_vector;
template<>
struct short_vector<unsigned int, 1>;
template<>
struct short_vector<unsigned int, 2>;
template<>
struct short_vector<unsigned int, 3>;
template<>
struct short_vector<unsigned int, 4>;
template<>
struct short_vector<int, 1>;
template<>
struct short_vector<int, 2>;
template<>
struct short_vector<int, 3>;
template<>
struct short_vector<int, 4>;
template<>
struct short_vector<float, 1>;
template<>
struct short_vector<float, 2>;
template<>
struct short_vector<float, 3>;
template<>
struct short_vector<float, 4>;
template<>
struct short_vector<unorm, 1>;
template<>
struct short_vector<unorm, 2>;
template<>
struct short_vector<unorm, 3>;
template<>
struct short_vector<unorm, 4>;
template<>
struct short_vector<norm, 1>;
template<>
struct short_vector<norm, 2>;
template<>
struct short_vector<norm, 3>;
template<>
struct short_vector<norm, 4>;
template<>
struct short_vector<double, 1>;
template<>
struct short_vector<double, 2>;
template<>
struct short_vector<double, 3>;
template<>
struct short_vector<double, 4>;
```

#### <a name="parameters"></a>Paramètres

*_Scalar_type*<br/>

*_Size*<br/>

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`type`||

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[short_vector::short_vector, constructeur](#ctor)||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`short_vector`

## <a name="requirements"></a>Configuration requise

**En-tête :** amp_short_vectors.h

**Espace de noms :** Concurrency::graphics

##  <a name="ctor"></a>  short_vector::short_vector, constructeur

```
short_vector();
```

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
