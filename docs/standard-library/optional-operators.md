---
title: '&lt;opérateurs&gt; optionnels'
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
ms.openlocfilehash: 9bdef0669f90da7865f7652ff4528e51e584e1a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373631"
---
# <a name="ltoptionalgt-operators"></a>&lt;opérateurs&gt; optionnels

## <a name="operator"></a><a name="op_eq_eq"></a>opérateur

Teste si l'objet `optional` situé à gauche de l'opérateur est égal à l'objet `optional` situé à droite.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Un objet `optional`de `nullopt_t`type, , ou `T`.

*Oui*\
Un objet `optional`de `nullopt_t`type, , ou `T`.

## <a name="operator"></a><a name="op_neq"></a>opérateur!

Teste si l'objet `optional` situé à gauche de l'opérateur n'est pas égal à l'objet `optional` situé à droite.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Un objet `optional`de `nullopt_t`type, , ou `T`.

*Oui*\
Un objet `optional`de `nullopt_t`type, , ou `T`.

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `!(left == right)`.

## <a name="operatorlt"></a><a name="op_lt"></a>Opérateur&lt;

Teste si l'objet `optional` situé à gauche de l'opérateur est inférieur à l'objet `optional` situé à droite.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Un objet `optional`de `nullopt_t`type, , ou `T`.

*Oui*\
Un objet `optional`de `nullopt_t`type, , ou `T`.

### <a name="return-value"></a>Valeur de retour

**true** si la liste située à gauche de l’opérateur est inférieure mais pas égale à la liste située à droite de l’opérateur. Sinon, **false**.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>Opérateur&lt;=

Teste si l'objet `optional` situé à gauche de l'opérateur est inférieur ou égal à l'objet `optional` situé à droite.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Un objet `optional`de `nullopt_t`type, , ou `T`.

*Oui*\
Un objet `optional`de `nullopt_t`type, , ou `T`.

### <a name="return-value"></a>Valeur de retour

**true** si la liste située à gauche de l’opérateur est inférieure ou égale à la liste située à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `!(right < left)`.

## <a name="operatorgt"></a><a name="op_gt"></a>Opérateur&gt;

Teste si l'objet `optional` situé à gauche de l'opérateur est supérieur à l'objet `optional` situé à droite.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Un objet `optional`de `nullopt_t`type, , ou `T`.

*Oui*\
Un objet `optional`de `nullopt_t`type, , ou `T`.

### <a name="return-value"></a>Valeur de retour

**true** si la liste située à gauche de l’opérateur est supérieure à la liste située à droite de l’opérateur. Sinon, **false**.

### <a name="remarks"></a>Notes

Cette fonction de modèle retourne `right < left`.

## <a name="operatorgt"></a><a name="op_gt_eq"></a>Opérateur&gt;=

Teste si l'objet `optional` situé à gauche de l'opérateur est supérieur ou égal à l'objet `optional` situé à droite.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Un objet `optional`de `nullopt_t`type, , ou `T`.

*Oui*\
Un objet `optional`de `nullopt_t`type, , ou `T`.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet `optional` situé à gauche de l’opérateur est supérieur ou égal à l’objet `optional` situé à droite de l’opérateur ; sinon, **false**.

### <a name="remarks"></a>Notes

La fonction de modèle retourne `!(left < right)`.
