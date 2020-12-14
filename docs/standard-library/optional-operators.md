---
description: 'En savoir plus sur &lt; : &gt; opérateurs facultatifs'
title: '&lt;opérateurs facultatifs &gt;'
ms.date: 11/04/2016
f1_keywords:
- optional/std::operator!=
- optional/std::operator==
- optional/std::operatoroperator&gt;
- optional/std::operatoroperator&gt=;
- optional/std::operatoroperator&lt;
- optional/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (optional)
- std::operator== (optional)
- std::operatoroperator&gt; (optional)
- std::operatoroperator&gt=; (optional)
- std::operatoroperator&lt; (optional)
- std::operatoroperator&lt;= (optional)
ms.openlocfilehash: 3c61f62ff87ab285dfeb5b26f1d22de86ef50fee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201857"
---
# <a name="ltoptionalgt-operators"></a>&lt;opérateurs facultatifs &gt;

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Teste si l'objet `optional` situé à gauche de l'opérateur est égal à l'objet `optional` situé à droite.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `optional` , `nullopt_t` ou `T` .

*Oui*\
Objet de type `optional` , `nullopt_t` ou `T` .

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Teste si l'objet `optional` situé à gauche de l'opérateur n'est pas égal à l'objet `optional` situé à droite.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `optional` , `nullopt_t` ou `T` .

*Oui*\
Objet de type `optional` , `nullopt_t` ou `T` .

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `!(left == right)`.

## <a name="operatorlt"></a><a name="op_lt"></a> and&lt;

Teste si l'objet `optional` situé à gauche de l'opérateur est inférieur à l'objet `optional` situé à droite.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `optional` , `nullopt_t` ou `T` .

*Oui*\
Objet de type `optional` , `nullopt_t` ou `T` .

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la liste située à gauche de l’opérateur est inférieure mais pas égale à la liste située à droite de l’opérateur ; Sinon, **`false`** .

## <a name="operatorlt"></a><a name="op_lt_eq"></a> and&lt;=

Teste si l'objet `optional` situé à gauche de l'opérateur est inférieur ou égal à l'objet `optional` situé à droite.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `optional` , `nullopt_t` ou `T` .

*Oui*\
Objet de type `optional` , `nullopt_t` ou `T` .

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la liste située à gauche de l’opérateur est inférieure ou égale à la liste située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `!(right < left)`.

## <a name="operatorgt"></a><a name="op_gt"></a> and&gt;

Teste si l'objet `optional` situé à gauche de l'opérateur est supérieur à l'objet `optional` situé à droite.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `optional` , `nullopt_t` ou `T` .

*Oui*\
Objet de type `optional` , `nullopt_t` ou `T` .

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la liste située à gauche de l’opérateur est supérieure à la liste située à droite de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `right < left`.

## <a name="operatorgt"></a><a name="op_gt_eq"></a> and&gt;=

Teste si l'objet `optional` situé à gauche de l'opérateur est supérieur ou égal à l'objet `optional` situé à droite.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `optional` , `nullopt_t` ou `T` .

*Oui*\
Objet de type `optional` , `nullopt_t` ou `T` .

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le `optional` à gauche de l’opérateur est supérieur ou égal à l’extrémité `optional` droite de l’opérateur ; sinon, **`false`** .

### <a name="remarks"></a>Notes

La fonction de modèle retourne `!(left < right)`.
