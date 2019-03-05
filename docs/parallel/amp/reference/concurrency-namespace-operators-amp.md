---
title: Opérateurs d’espace de noms d’accès concurrentiel (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: e2957aa84ffbf420dcf2672359a442b754866649
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283343"
---
# <a name="concurrency-namespace-operators-amp"></a>Opérateurs d’espace de noms d’accès concurrentiel (AMP)

||||
|-|-|-|
|[!=, opérateur](#operator_neq)|[operator%](#operator_mod)|[operator*](#operator_star)|
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|
|[operator==](#operator_eq_eq)|

##  <a name="operator_eq_eq"></a>  operator==

Détermine si les arguments spécifiés sont égaux.

```
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

**true** si les tuples sont égales ; sinon, **false**.

##  <a name="operator_neq"></a>  operator!=

Détermine si les arguments spécifiés ne sont pas égaux.

```
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

**true** si les tuples ne sont pas égales ; sinon, **false**.

##  <a name="operator_add"></a>  operator+

Calcule la somme des arguments spécifiés.

```
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

La somme des arguments spécifiés.

##  <a name="operator-"></a>  operator-

Calcule la différence entre les arguments spécifiés.

```
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

La différence entre les arguments spécifiés.

##  <a name="operator_star"></a>  operator*

Calcule le produit des arguments spécifiés.

```
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
Un des tuples à multiplier.

*_Rhs*<br/>
Un des tuples à multiplier.

### <a name="return-value"></a>Valeur de retour

Le produit des arguments spécifiés.

##  <a name="operator_div"></a>  operator/

Calcule le quotient des arguments spécifiés.

```
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

Le quotient des arguments spécifiés.

##  <a name="operator_mod"></a>  operator%

Calcule le modulo du premier argument spécifié par le deuxième argument spécifié.

```
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
Le tuple à partir de laquelle le modulo est calculé.

*_Rhs*<br/>
Le tuple à modulo par.

### <a name="return-value"></a>Valeur de retour

Le résultat premier argument spécifié du modulo de la deuxième argument spécifié.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace ](concurrency-namespace-cpp-amp.md)
