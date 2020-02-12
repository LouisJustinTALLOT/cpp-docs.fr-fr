---
title: short_vector Structure
ms.date: 11/04/2016
f1_keywords:
- short_vector
- AMP_SHORT_VECTORS/short_vector
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector::short_vector Constructor
ms.assetid: e4f50b8f-1150-437d-b58c-79c5fb883708
ms.openlocfilehash: 531b8d53eac8d997b7e8ca4d29aad7d34ef90e22
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126433"
---
# <a name="short_vector-structure"></a>short_vector Structure

short_vector fournit des définitions de la surprogrammation qui sont utiles pour la programmation de vecteurs courts de façon générique.

## <a name="syntax"></a>Syntaxe

```cpp
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

### <a name="parameters"></a>Paramètres

*_Scalar_type*<br/>

*_Size*<br/>

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`type`||

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[short_vector :: short_vector, constructeur](#ctor)||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`short_vector`

## <a name="requirements"></a>Spécifications

**En-tête :** amp_short_vectors. h

**Espace de noms :** Concurrency :: Graphics

## <a name="ctor"></a>short_vector :: short_vector, constructeur

```cpp
short_vector();
```

## <a name="see-also"></a>Voir aussi

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
