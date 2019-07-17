---
title: Classe de type Variant
ms.date: 04/04/2019
f1_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
helpviewer_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
ms.openlocfilehash: 9bfdf644374a0b825fd0ca02bf4164a766cb42a3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269301"
---
# <a name="variant-class"></a>Classe de type Variant

N’importe quelle instance de type variant à un moment donné conserve soit une valeur d’un de ses autres types, ou elle ne contient aucune valeur.

## <a name="syntax"></a>Syntaxe

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|||
|-|-|
|[Type Variant](#variant)|Construit un objet de type `variant`.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[emplace](#emplace)|Crée une nouvelle valeur de relation contenant-contenue.|
|[index](#index)|Retourne l’index d’une valeur de relation contenant-contenue.|
|[swap](#swap)||
|[valueless_by_exception](#emplace)|Retourne **false** si la variante conserve une valeur.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator=](#op_eq)|Remplace la variante avec une copie d’une autre variante.|

## <a name="emplace"></a> emplace

Crée une nouvelle valeur de relation contenant-contenue.

```cpp
template <class T, class... Args>
    T& emplace(Args&&...);
template <class T, class U, class... Args>
    T& emplace(initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(Args&&...);
template <size_t I, class U, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(initializer_list<U>, Args&&...);
```

## <a name="index"></a> Index

Retourne l’index d’une valeur de relation contenant-contenue.

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a> Type Variant

Construit un objet de type `variant`. Inclut également un destructeur.

```cpp
constexpr variant() noexcept(see below);
variant(const variant&);
variant(variant&&) noexcept(see below);
template <class T>
    constexpr variant(T&&) noexcept(see below);
template <class T, class... Args>
    constexpr explicit variant(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    constexpr explicit variant(in_place_type_t<T>, initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    constexpr explicit variant(in_place_index_t<I>, Args&&...);
template <size_t I, class U, class... Args>
    constexpr explicit variant(in_place_index_t<I>, initializer_list<U>, Args&&...);

template <class Alloc>
    variant(allocator_arg_t, const Al&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, const variant&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, variant&&);
template <class Alloc, class T>
    variant(allocator_arg_t, const Al&, T&&);
template <class Alloc, class T, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, Args&&...);
template <class Alloc, class T, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, initializer_list<U>, Args&&...);
template <class Alloc, size_t I, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, Args&&...);
template <class Alloc, size_t I, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, initializer_list<U>, Args&&...);

~variant();
```

### <a name="parameters"></a>Paramètres

*Al*\
Classe allocator à utiliser avec cet objet.

## <a name="op_eq"></a> opérateur =

Remplace la variante avec une copie d’une autre variante.

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a> échange

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless"></a> valueless_by_exception

Retourne **false** si la variante conserve une valeur.

```cpp
constexpr bool valueless_by_exception() const noexcept;
```
