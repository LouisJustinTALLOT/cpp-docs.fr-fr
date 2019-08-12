---
title: Classe facultative
ms.date: 11/04/2016
f1_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
helpviewer_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
ms.openlocfilehash: 414b3e608e915ec06dbdf90726151a1c33ea4c60
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269201"
---
# <a name="optional-class"></a>Classe facultative

Décrit un objet qui peut ou ne peut pas contenir une valeur.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class optional
{
    using value_type = T;
};

template<class T> optional(T) -> optional<T>;
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|||
|-|-|
|[optional](#optional)|Construit un objet de type `optional`.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[has_value](#has_value)|Retourne **true** si `optional` contient la valeur.|
|[reset](#reset)|Réinitialise le `optional`.|
|[value](#value)|Évalue la `optional` valeur.|
|[value_or](#value_or)|Évalue la `optional` valeur.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator=](#op_eq)|Remplace le `optional` avec une copie d’un autre `optional`.|
|[operator->](#op_as)|Affectez la valeur à `optional`.|
|[operator*](#op_mem)|Référence de la mémoire de `optional`.|
|[operator bool](#op_bool)|Retourner la valeur booléenne de `optional` valeur.|

### <a name="has_value"></a> has_value

```cpp
constexpr bool has_value() const noexcept;
```

### <a name="optional"></a> Facultatif

Construit un objet de type `optional`. Inclut également un destructeur.

```cpp
constexpr optional() noexcept;
constexpr optional(nullopt_t) noexcept;
constexpr optional(const optional&);
constexpr optional(optional&&) noexcept(see below);

template <class... Args>
    constexpr explicit optional(in_place_t, Args&&...);
template <class U, class... Args>
    constexpr explicit optional(in_place_t, initializer_list<U>, Args&&...);
template <class U = T>
    explicit constexpr optional(U&&);
template <class U>
    explicit optional(const optional<U>&);
template <class U>
    explicit optional(optional<U>&&);

~optional();
```

### <a name="op_eq"></a> opérateur =

Remplace le `optional` avec une copie d’un autre `optional`.

```cpp
optional& operator=(nullopt_t) noexcept;
optional& operator=(const optional&);
optional& operator=(optional&&) noexcept(see below);

template <class U = T>
    optional& operator=(U&&); template <class U> optional& operator=(const optional<U>&);
template <class U>
    optional& operator=(optional<U>&&); template <class... Args> T& emplace(Args&&...);
template <class U, class... Args>
    T& emplace(initializer_list<U>, Args&&...);
```

### <a name="op_as"></a> operator ->

```cpp
constexpr const T* operator->() const;
constexpr T* operator->();
```

### <a name="op_mem"></a> opérateur *

```cpp
constexpr const T& operator*() const&;
constexpr T& operator*() &;
constexpr T&& operator*() &&;
constexpr const T&& operator*() const&&;
```

### <a name="op_bool"></a> opérateur bool

```cpp
constexpr explicit operator bool() const noexcept;
```

### <a name="reset"></a> Réinitialiser

```cpp
void reset() noexcept;
```

### <a name="value"></a> Valeur

```cpp
constexpr const T& value() const&;
constexpr T& value() &;
constexpr T&& value() &&;
constexpr const T&& value() const&&;
```

### <a name="value_or"></a> value_or

```cpp
template <class U>
    constexpr T value_or(U&&) const&;
template <class U>
    constexpr T value_or(U&&) &&;
```