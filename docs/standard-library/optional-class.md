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
ms.openlocfilehash: f664df6493a7ee20361d49531a930aeb810d3d2a
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957151"
---
# <a name="optional-class"></a>Classe facultative

La classe `optional<T>` de modèle décrit un objet qui peut ou ne peut pas contenir une valeur `T`de type, appelée *valeur contenue*.

Lorsqu’une instance de `optional<T>` contient une valeur, la valeur contenue est allouée dans le `optional` stockage de l’objet, dans une région correctement `T`alignée pour le type. Lorsqu’un `optional<T>` est converti en `bool`, le résultat est `true` si l’objet contient une valeur; sinon, il s' `false`agit de.

Le type `T` de l’objet contenu ne doit pas être [in_place_t](in-place-t-struct.md) ou [nullopt_t](nullopt-t-structure.md). `T`doit être *destructible*, autrement dit, son destructeur doit récupérer toutes les ressources détenues et ne peut lever aucune exception.

La `optional` classe est nouvelle dans c++ 17.

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
| **Constructeurs et destructeur** | |
|[optional](#optional) | Construit un objet de type `optional`. |
|[~ facultatif](#optional-destructor) | Détruit un objet de type `optional`. |
| **Attribution** | |
| [operator=](#op_eq) | Remplace le `optional` par une copie d’un `optional`autre. |
| [emplace](#op_eq) | Initialise la valeur contenue avec les arguments spécifiés. |
| **Swap** | |
| [swap](#swap) | Permute la valeur contenue ou l’état vide avec un `optional`autre. |
| **Scientifiques** | |
| [has_value](#has_value) | Retourne une valeur `optional` indiquant si un objet contient une valeur. |
| [value](#value) | Retourne la valeur contenue. |
| [value_or](#value_or) | Retourne la valeur contenue, ou une alternative si aucune valeur n’est présente. |
| [operator->](#op_as) | Fait référence à la valeur contenue d’un `optional` objet. |
| [operator*](#op_mem) | Fait référence à la valeur contenue d’un `optional` objet. |
| [operator bool](#op_bool) | Retourne une valeur `optional` indiquant si un objet contient une valeur. |
| **Modificateurs** | |
| [reset](#reset) | Réinitialise le `optional` en détruisant toute valeur contenue. |

## <a name="has_value"></a>has_value

```cpp
constexpr bool has_value() const noexcept;
```

## <a name="optional"></a>constructeur facultatif

Construit un objet de type `optional`.

```cpp
constexpr optional() noexcept;
constexpr optional(nullopt_t nullopt) noexcept;
constexpr optional(const optional& rhs);
constexpr optional(optional&& rhs) noexcept;

template <class... Args>
constexpr explicit optional(in_place_t, Args&&... args);

template <class U, class... Args>
constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);

template <class U = T>
explicit constexpr optional(U&& rhs);

template <class U>
explicit optional(const optional<U>& rhs);

template <class U>
explicit optional(optional<U>&& rhs);
```

### <a name="parameters"></a>Paramètres

*RHS*\
`optional` À partir duquel la valeur contenue doit être copiée ou déplacée.

*i_list*\
Liste d’initialiseurs à partir de laquelle la valeur contenue doit être créée.

*attend*\
Liste d’arguments à partir de laquelle la valeur contenue doit être créée.

### <a name="remarks"></a>Notes

`constexpr optional() noexcept;`
`constexpr optional(nullopt_t nullopt) noexcept;`Ces constructeurs construisent un `optional` qui ne contient pas de valeur.

`constexpr optional(const optional& rhs);`Le constructeur de copie initialise la valeur contenue à partir de la valeur contenue de l’argument. Elle est définie comme Deleted `is_copy_constructible_v<T>` , sauf si a la valeur true, `is_trivially_copy_constructible_v<T>` et c’est trivial si a la valeur true.

`constexpr optional(optional&& rhs) noexcept;`Le constructeur de déplacement initialise la valeur contenue en se déplaçant de la valeur contenue de l’argument. Elle ne participe pas à la résolution `is_move_constructible_v<T>` de surcharge, sauf si a la valeur `is_trivially_move_constructible_v<T>` true, et c’est trivial si a la valeur true.

`template <class... Args> constexpr explicit optional(in_place_t, Args&&... args);`Direct initialise la valeur contenue comme si vous utilisiez `std::forward<Args>(args)`les arguments. Ce constructeur est `constexpr` si le `T` constructeur utilisé est `constexpr`. Elle ne participe pas à la résolution `is_constructible_v<T, Args...>` de surcharge, sauf si a la valeur true.

`template <class U, class... Args> constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);`Direct initialise la valeur contenue comme si vous utilisiez `i_list, std::forward<Args>(args)`les arguments. Ce constructeur est `constexpr` si le `T` constructeur utilisé est `constexpr`. Elle ne participe pas à la résolution `is_constructible_v<T, initializer_list<U>&, Args&&...>` de surcharge, sauf si a la valeur true.

`template <class U = T> explicit constexpr optional(U&& rhs);`Direct initialise la valeur contenue comme si vous `std::forward<U>(v)`utilisiez. Ce constructeur est `constexpr` si le `T` constructeur utilisé est `constexpr`. Elle ne participe pas à la résolution `is_constructible_v<T, U&&>` de surcharge, sauf `is_same_v<remove_cvref_t<U>, in_place_t>` si `is_same_v<remove_cvref_t<U>, optional>` a la valeur true et que et a la valeur false.

`template <class U> explicit optional(const optional<U>& rhs);`Si *RHS* contient une valeur, direct initialise la valeur contenue à partir de la valeur contenue de l’argument. Elle ne participe pas à la résolution `is_constructible_v<T, const U&>` de surcharge, sauf si `is_constructible_v<T, optional<U>&&>`a la valeur true `is_convertible_v<optional<U>&&, T>`, `is_convertible_v<const optional<U>&, T>`et `is_constructible_v<T, optional<U>&>`, `is_convertible_v<const optional<U>&&, T>` `is_constructible_v<T, const optional<U>&>` `is_constructible_v<T, const optional<U>&&>` `is_convertible_v<optional<U>&, T>`,,,,, et ont tous la valeur false.

`template <class U> explicit optional(optional<U>&& rhs);`Si *RHS* contient une valeur, direct initialise la valeur contenue comme si vous `std::move(*rhs)`utilisiez. Elle ne participe pas à la résolution `is_constructible_v<T, U&&>` de surcharge, sauf si `is_constructible_v<T, optional<U>&&>`a la valeur true `is_convertible_v<optional<U>&&, T>`, `is_convertible_v<const optional<U>&, T>`et `is_constructible_v<T, optional<U>&>`, `is_convertible_v<const optional<U>&&, T>` `is_constructible_v<T, const optional<U>&>` `is_constructible_v<T, const optional<U>&&>` `is_convertible_v<optional<U>&, T>`,,,,, et ont tous la valeur false.

## <a name="optional-destructor"></a>~ facultatif, destructeur

Détruit toute valeur contenue non destructible non triviale, si elle est présente, en appelant son destructeur.

```cpp
~optional();
```

### <a name="remarks"></a>Notes

Si `T` est destructible `optional<T>` de façon triviale, est également destructible de façon triviale.

## <a name="op_eq"></a>opérateur =

Remplace la valeur contenue d' `optional` un par une copie ou un déplacement `optional` à partir d’une autre valeur contenue.

```cpp
optional& operator=(nullopt_t) noexcept;
optional& operator=(const optional& rhs);
optional& operator=(optional&&) noexcept( /* see below */ );

template <class U = T>
    optional& operator=(U&&);

template <class U>
optional& operator=(const optional<U>&);

template <class U>
    optional& operator=(optional<U>&&);

template <class... Args>
T& emplace(Args&&...);

template <class U, class... Args>
T& emplace(initializer_list<U>, Args&&...);
```

## <a name="op_as"></a>> Operator

Déréférence la valeur contenue d’un `optional` objet.

```cpp
constexpr const T* operator->() const;
constexpr T* operator->();
```

## <a name="op_mem"></a>and

Déréférence la valeur contenue d’un `optional` objet.

```cpp
constexpr const T& operator*() const&;
constexpr T& operator*() &;
constexpr T&& operator*() &&;
constexpr const T&& operator*() const&&;
```

## <a name="op_bool"></a>bool, opérateur

Signale si `optional` l’objet a une valeur contenue.

```cpp
constexpr explicit operator bool() const noexcept;
```

## <a name="reset"></a>initialisation

En fait, appelle le destructeur de l’objet contenu, le cas échéant, et le définit sur un État non initialisé.

```cpp
void reset() noexcept;
```

## <a name="swap"></a>échange

```cpp
template<class T>
void swap(optional<T>&, optional<T>&) noexcept;
```

## <a name="value"></a>ajoutée

```cpp
constexpr const T& value() const&;
constexpr T& value() &;
constexpr T&& value() &&;
constexpr const T&& value() const&&;
```

## <a name="value_or"></a>value_or

```cpp
template <class U>
    constexpr T value_or(U&&) const&;
template <class U>
    constexpr T value_or(U&&) &&;
```

## <a name="see-also"></a>Voir aussi

[\<> facultative](optional.md)
