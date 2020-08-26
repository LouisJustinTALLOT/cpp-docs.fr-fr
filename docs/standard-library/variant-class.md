---
title: Classe de variante
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
ms.openlocfilehash: aba121604636ebd253523acb9b630dd9ab762584
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840022"
---
# <a name="variant-class"></a>Classe de variante

Toute instance de variant à un moment donné contient une valeur de l’un de ses autres types, ou elle ne contient aucune valeur.

## <a name="syntax"></a>Syntaxe

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[variant](#variant)|Construit un objet de type `variant`.|

### <a name="functions"></a>Functions

|Nom|Description|
|-|-|
|[emplace](#emplace)|Crée une nouvelle valeur contenue.|
|[index](#index)|Retourne l’index d’une valeur contenue.|
|[swap](#swap)||
|[valueless_by_exception](#emplace)|Retourne **`false`** si le variant contient une valeur.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur =](#op_eq)|Remplace la variante par une copie d’une autre variante.|

## <a name="emplace"></a><a name="emplace"></a> emplace

Crée une nouvelle valeur contenue.

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

## <a name="index"></a><a name="index"></a> évaluer

Retourne l’index d’une valeur contenue.

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a><a name="variant"></a> différent

Construit un objet de type `variant`. Comprend également un destructeur.

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

*&*\
Classe allocator à utiliser avec cet objet.

## <a name="operator"></a><a name="op_eq"></a> opérateur =

Remplace la variante par une copie d’une autre variante.

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a><a name="swap"></a> échange

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless_by_exception"></a><a name="valueless"></a> valueless_by_exception

Retourne **`false`** si le variant contient une valeur.

```cpp
constexpr bool valueless_by_exception() const noexcept;
```
