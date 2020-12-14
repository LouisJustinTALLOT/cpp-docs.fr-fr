---
description: 'En savoir plus sur : &lt; opérateurs de type Variant &gt;'
title: '&lt;&gt;opérateurs variant'
ms.date: 04/04/2019
f1_keywords:
- variant/std::operator!=
- variant/std::operator==
- variant/std::operatoroperator&gt;
- variant/std::operatoroperator&gt=;
- variant/std::operatoroperator&lt;
- variant/std::operatoroperator&lt;=
helpviewer_keywords:
- std::operator!= (variant)
- std::operator== (variant)
- std::operatoroperator&gt; (variant)
- std::operatoroperator&gt=; (variant)
- std::operatoroperator&lt; (variant)
- std::operatoroperator&lt;= (variant)
ms.openlocfilehash: 3315c73ea529ad7ade4f32be3784a43bda07ac26
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312824"
---
# <a name="ltvariantgt-operators"></a>&lt;&gt;opérateurs variant

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est égal à l’objet de liste forward_list situé à droite.

```cpp
template <class... Types>
    constexpr bool operator==(const variant<Types...>&, const variant<Types...>&);
```

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Vérifie si l’objet de liste forward_list à gauche de l’opérateur n’est pas égal à l’objet de liste forward_list situé à droite.

```cpp
template <class... Types>
    constexpr bool operator!=(const variant<Types...>&, const variant<Types...>&);
```

## <a name="operatorlt"></a><a name="op_lt"></a> and&lt;

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est inférieur à l’objet de liste forward_list situé à droite.

```cpp
template <class... Types>
    constexpr bool operator<(const variant<Types...>&, const variant<Types...>&);
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> and&lt;=

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est inférieur ou égal à l’objet de liste forward_list situé à droite.

```cpp
template <class... Types>
    constexpr bool operator<=(const variant<Types...>&, const variant<Types...>&);
```

## <a name="operatorgt"></a><a name="op_gt"></a> and&gt;

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est supérieur à l’objet de liste forward_list situé à droite.

```cpp
template <class... Types> constexpr
    bool operator>(const variant<Types...>&, const variant<Types...>&);
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> and&gt;=

Vérifie si l’objet de liste forward_list à gauche de l’opérateur est supérieur ou égal à l’objet de liste forward_list situé à droite.

```cpp
template <class... Types> constexpr
    bool operator>=(const variant<Types...>&, const variant<Types...>&);
```
