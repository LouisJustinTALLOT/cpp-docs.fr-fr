---
title: Concurrency, opérateurs de l’espace de noms (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: c4086029b71d71091a12b9b6023cc6098faf2f85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376295"
---
# <a name="concurrency-namespace-operators-amp"></a>Concurrency, opérateurs de l’espace de noms (AMP)

||||
|-|-|-|
|[opérateur!](#operator_neq)|[opérateur %](#operator_mod)|[opérateur](#operator_star)|
|[opérateur](#operator_add)|[opérateur-](#operator-)|[opérateur/](#operator_div)|
|[opérateur](#operator_eq_eq)|

## <a name="operator"></a><a name="operator_eq_eq"></a>opérateur

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
Le rang des arguments de tuple.

*_Lhs*<br/>
Un des tuples à comparer.

*_Rhs*<br/>
Un des tuples à comparer.

### <a name="return-value"></a>Valeur de retour

**vrai** si les tuples sont égaux; autrement, **faux**.

## <a name="operator"></a><a name="operator_neq"></a>opérateur!

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
Le rang des arguments de tuple.

*_Lhs*<br/>
Un des tuples à comparer.

*_Rhs*<br/>
Un des tuples à comparer.

### <a name="return-value"></a>Valeur de retour

**vrai** si les tuples ne sont pas égaux; autrement, **faux**.

## <a name="operator"></a><a name="operator_add"></a>opérateur

Calcule la somme composante-sage des arguments spécifiés.

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
Le rang des arguments de tuple.

*_Lhs*<br/>
Un des arguments à ajouter.

*_Rhs*<br/>
Un des arguments à ajouter.

### <a name="return-value"></a>Valeur de retour

La somme de la composante-sage des arguments spécifiés.

## <a name="operator-"></a><a name="operator-"></a>opérateur-

Calcule la différence de composante-sage entre les arguments spécifiés.

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
Le rang des arguments de tuple.

*_Lhs*<br/>
L’argument à soustraire.

*_Rhs*<br/>
L’argument à soustraire.

### <a name="return-value"></a>Valeur de retour

La différence de composante-sage entre les arguments spécifiés.

## <a name="operator"></a><a name="operator_star"></a>opérateur

Calcule le produit de composants-sage des arguments spécifiés.

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
Le rang des arguments de tuple.

*_Lhs*<br/>
L’un des tuples à multiplier.

*_Rhs*<br/>
L’un des tuples à multiplier.

### <a name="return-value"></a>Valeur de retour

Le produit de la composante des arguments spécifiés.

## <a name="operator"></a><a name="operator_div"></a>opérateur/

Calcule le quotient composante-sage des arguments spécifiés.

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
Le rang des arguments de tuple.

*_Lhs*<br/>
Le tuple à diviser.

*_Rhs*<br/>
Le tuple à diviser par.

### <a name="return-value"></a>Valeur de retour

Le quotient de composante-sage des arguments spécifiés.

## <a name="operator"></a><a name="operator_mod"></a>opérateur %

Calcule le modulus du premier argument spécifié par le deuxième argument spécifié.

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
Le rang des arguments de tuple.

*_Lhs*<br/>
Le tuple à partir duquel le modulo est calculé.

*_Rhs*<br/>
Le tuple à modulo par.

### <a name="return-value"></a>Valeur de retour

Le résultat du premier argument spécifié modulus l’argument spécifié second.

## <a name="see-also"></a>Voir aussi

[Accordurrency Namespace](concurrency-namespace-cpp-amp.md)
