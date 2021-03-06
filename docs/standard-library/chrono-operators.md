---
description: 'En savoir plus sur &lt; : &gt; opérateurs Chrono'
title: '&lt;chrono&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 0e84f0c09188d8c69cd71094788fdbd0497dca4d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234174"
---
# <a name="ltchronogt-operators"></a>&lt;chrono&gt;, opérateurs

## <a name="operator-"></a><a name="operator-"></a> and

Opérateur de soustraction ou de négation des objets [duration](../standard-library/duration-class.md) et [time_point](../standard-library/time-point-class.md).

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator-(
       const duration<Rep1, Period1>& Left,
       cconst duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type
   operator-(
       const time_point<Clock, Duration1>& Time,
       const duration<Rep2, Period2>& Dur);

template <class Clock, class Duration1, class Duration2>
constexpr typename common_type<Duration1, Duration2>::type
   operator-(
       const time_point<Clock, Duration1>& Left,
       const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet `duration` ou `time_point` gauche.

*Oui*\
Objet `duration` ou `time_point` droit.

*Simultanément*\
Objet `time_point`.

*Dur*\
Objet `duration`.

### <a name="return-value"></a>Valeur renvoyée

La première fonction retourne un objet `duration` dont la longueur de l'intervalle est la différence entre les intervalles de temps des deux arguments.

La deuxième fonction retourne un `time_point` objet qui représente un point dans le temps qui est déplacé, par la négation de l’intervalle de temps représenté par l’intervalle de temps, à partir du point dans le temps spécifié par l' *heure*.

La troisième fonction retourne un `duration` objet qui représente l’intervalle de temps entre la *gauche* et la *droite*.

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Opérateur d’inégalité des objets [duration](../standard-library/duration-class.md) ou [time_point](../standard-library/time-point-class.md).

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator!=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator!=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet `duration` ou `time_point` gauche.

*Oui*\
Objet `duration` ou `time_point` droit.

### <a name="return-value"></a>Valeur renvoyée

Chaque fonction retourne `!(Left == Right)`.

## <a name="operator"></a><a name="op_star"></a> and

Opérateur de multiplication des objets [duration](../standard-library/chrono-operators.md#op_star).

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator*(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Mult);

template <class Rep1, class Rep2, class Period2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period2>
   operator*(
       const Rep1& Mult,
       const duration<Rep2,
       Period2>& Dur);
```

### <a name="parameters"></a>Paramètres

*Dur*\
Objet `duration`.

*Mult*\
Valeur intégrale.

### <a name="return-value"></a>Valeur renvoyée

Chaque fonction retourne un `duration` objet dont la longueur de l’intervalle est de *mult* multiplié par la longueur de l’intervalle de temps.

À moins que `is_convertible<Rep2, common_type<Rep1, Rep2>>`*ne contienne la valeur true*, la première fonction ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

À moins que `is_convertible<Rep1, common_type<Rep1, Rep2>>`*ne contienne la valeur true*, la deuxième fonction ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

## <a name="operator"></a><a name="op_div"></a> and

Opérateur de division des objets [duration](../standard-library/chrono-operators.md#op_star).

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator/(
     const duration<Rep1, Period1>& Dur,
     const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<Rep1, Rep2>::type
   operator/(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>Paramètres

*Dur*\
Objet `duration`.

*Div*\
Valeur intégrale.

*Gauche*\
Objet gauche `duration`.

*Oui*\
Objet droit `duration`.

### <a name="return-value"></a>Valeur renvoyée

Le premier opérateur retourne un objet Duration dont la *longueur de l’intervalle est égale à* la longueur de la valeur de l’élément *div*.

Le deuxième opérateur retourne le rapport des longueurs d’intervalle de *gauche* et de *droite*.

À moins que `is_convertible<Rep2, common_type<Rep1, Rep2>>`*ne contienne la valeur true* et que `Rep2` ne soit pas une instanciation de `duration`, le premier opérateur ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

## <a name="operator"></a><a name="op_add"></a> opérateur +

Ajoute des objets [duration](../standard-library/duration-class.md) et [time_point](../standard-library/time-point-class.md).

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator+(
      const duration<Rep1, Period1>& Left,
      const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type>
   operator+(
      const time_point<Clock, Duration1>& Time,
      const duration<Rep2, Period2>& Dur);

template <class Rep1, class Period1, class Clock, class Duration2>
time_point<Clock, constexpr typename common_type<duration<Rep1, Period1>, Duration2>::type>
   operator+(
      const duration<Rep1, Period1>& Dur,
      const time_point<Clock, Duration2>& Time);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet `duration` ou `time_point` gauche.

*Oui*\
Objet `duration` ou `time_point` droit.

*Simultanément*\
Objet `time_point`.

*Dur*\
Objet `duration`.

### <a name="return-value"></a>Valeur renvoyée

La première fonction retourne un `duration` objet dont l’intervalle de temps est égal à la somme des intervalles de *gauche* et de *droite*.

Les deuxième et troisième fonctions retournent un `time_point` objet qui représente un point dans le temps qui est déplacé, par intervalle, à partir du point dans le temps.

## <a name="operatorlt"></a><a name="op_lt"></a> and&lt;

Détermine si un objet [duration](../standard-library/duration-class.md) ou [time_point](../standard-library/time-point-class.md) est inférieur à un autre objet `duration` ou `time_point`.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet `duration` ou `time_point` gauche.

*Oui*\
Objet `duration` ou `time_point` droit.

### <a name="return-value"></a>Valeur renvoyée

La première fonction retourne **`true`** si la longueur de l’intervalle de *gauche* est inférieure à la longueur de l’intervalle de *droite*. Sinon, la fonction retourne **`false`** .

La deuxième fonction retourne **`true`** si *Left* précède *Right*. Sinon, la fonction retourne **`false`** .

## <a name="operatorlt"></a><a name="op_lt_eq"></a> and&lt;=

Détermine si un objet [duration](../standard-library/duration-class.md) ou [time_point](../standard-library/time-point-class.md) est inférieur ou égal à un autre objet `duration` ou `time_point`.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet `duration` ou `time_point` gauche.

*Oui*\
Objet `duration` ou `time_point` droit.

### <a name="return-value"></a>Valeur renvoyée

Chaque fonction retourne `!(Right < Left)`.

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Détermine si deux objets `duration` représentent des intervalles de temps de même longueur ou si deux objets `time_point` représentent le même point dans le temps.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator==(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator==(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet `duration` ou `time_point` gauche.

*Oui*\
Objet `duration` ou `time_point` droit.

### <a name="return-value"></a>Valeur renvoyée

La première fonction retourne **`true`** si les intervalles de temps de *gauche* et de *droite* représentent la même longueur. Sinon, la fonction retourne **`false`** .

La deuxième fonction retourne **`true`** si *Left* et *Right* représentent le même point dans le temps. Sinon, la fonction retourne **`false`** .

## <a name="operatorgt"></a><a name="op_gt"></a> and&gt;

Détermine si un objet [duration](../standard-library/duration-class.md) ou [time_point](../standard-library/time-point-class.md) est supérieur à un autre objet `duration` ou `time_point`.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet `duration` ou `time_point` gauche.

*Oui*\
Objet `duration` ou `time_point` droit.

### <a name="return-value"></a>Valeur renvoyée

Chaque fonction retourne `Right < Left`.

## <a name="operatorgt"></a><a name="op_gt_eq"></a> and&gt;=

Détermine si un objet [duration](../standard-library/duration-class.md) ou [time_point](../standard-library/time-point-class.md) est supérieur ou égal à un autre objet `duration` ou `time_point`.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet `duration` ou `time_point` gauche.

*Oui*\
Objet `duration` ou `time_point` droit.

### <a name="return-value"></a>Valeur renvoyée

Chaque fonction retourne `!(Left < Right)`.

## <a name="operator-modulo"></a><a name="op_modulo"></a> modulo, opérateur

Opérateur pour les opérations modulo sur des objets [duration](../standard-library/duration-class.md).

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<Rep1, Period1, Rep2>::type
   operator%(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, _Period1>, duration<Rep2, Period2>>::type
   operator%(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>Paramètres

*Dur*\
Objet `duration`.

*Div*\
Valeur intégrale.

*Gauche*\
Objet gauche `duration`.

*Oui*\
Objet droit `duration`.

### <a name="return-value"></a>Valeur renvoyée

La première fonction retourne un `duration` objet dont la longueur de  l’intervalle est la valeur de modulo *div*.

La deuxième fonction retourne une valeur qui représente *le* modulo de *gauche* .
