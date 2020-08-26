---
title: Concurrency, opérateurs de l’espace de noms (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: 1b6353e1edbe216dcb8aa5a342e139d826b82c6c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845339"
---
# <a name="concurrency-namespace-operators-amp"></a>Concurrency, opérateurs de l’espace de noms (AMP)

:::row:::
   :::column span="":::
      [`operator==`](#operator_eq_eq)\
      [`operator!=`](#operator_neq)
   :::column-end:::
   :::column span="":::
      [`operator+`](#operator_add)\
      [`operator-`](#operator-)
   :::column-end:::
   :::column span="":::
      [`operator*`](#operator_star)\
      [`operator/`](#operator_div)
   :::column-end:::
   :::column span="":::
      [`operator%`](#operator_mod)
   :::column-end:::
:::row-end:::

## <a name="operator"></a><a name="operator_eq_eq"></a> opérateur = =

Détermine si les arguments spécifiés sont égaux.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Rang des arguments de Tuple.

*_Lhs*<br/>
Un des tuples à comparer.

*_Rhs*<br/>
Un des tuples à comparer.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les tuples sont égaux ; Sinon, **`false`** .

## <a name="operator"></a><a name="operator_neq"></a> opérateur ! =

Détermine si les arguments spécifiés ne sont pas égaux.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Rang des arguments de Tuple.

*_Lhs*<br/>
Un des tuples à comparer.

*_Rhs*<br/>
Un des tuples à comparer.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les tuples ne sont pas égaux ; Sinon, **`false`** .

## <a name="operator"></a><a name="operator_add"></a> opérateur +

Calcule la somme au niveau du composant des arguments spécifiés.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Rang des arguments de Tuple.

*_Lhs*<br/>
Un des arguments à ajouter.

*_Rhs*<br/>
Un des arguments à ajouter.

### <a name="return-value"></a>Valeur renvoyée

Somme au niveau du composant des arguments spécifiés.

## <a name="operator-"></a><a name="operator-"></a> and

Calcule la différence au niveau du composant entre les arguments spécifiés.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Rang des arguments de Tuple.

*_Lhs*<br/>
Argument à soustraire de.

*_Rhs*<br/>
Argument à soustraire.

### <a name="return-value"></a>Valeur renvoyée

Différence au niveau du composant entre les arguments spécifiés.

## <a name="operator"></a><a name="operator_star"></a> and

Calcule le produit au niveau du composant des arguments spécifiés.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```

### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Rang des arguments de Tuple.

*_Lhs*<br/>
Un des tuples à multiplier.

*_Rhs*<br/>
Un des tuples à multiplier.

### <a name="return-value"></a>Valeur renvoyée

Produit au niveau du composant des arguments spécifiés.

## <a name="operator"></a><a name="operator_div"></a> and

Calcule le quotient au niveau du composant des arguments spécifiés.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Rang des arguments de Tuple.

*_Lhs*<br/>
Tuple à diviser.

*_Rhs*<br/>
Tuple par lequel diviser.

### <a name="return-value"></a>Valeur renvoyée

Quotient au niveau du composant des arguments spécifiés.

## <a name="operator"></a><a name="operator_mod"></a> and

Calcule le modulo du premier argument spécifié par le deuxième argument spécifié.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Rank*<br/>
Rang des arguments de Tuple.

*_Lhs*<br/>
Tuple à partir duquel le modulo est calculé.

*_Rhs*<br/>
Tuple par lequel modulo.

### <a name="return-value"></a>Valeur renvoyée

Le résultat du premier argument spécifié modulo le deuxième argument spécifié.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace-cpp-amp.md)
