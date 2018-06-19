---
title: '&lt;chrono&gt;, opérateurs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 1ac1051ddaa67dc1970119586ecb9e937583c58a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847398"
---
# <a name="ltchronogt-operators"></a>&lt;chrono&gt;, opérateurs

||||
|-|-|-|
|[opérateur modulo](#op_modulo)|[operator!=](#op_neq)|[operator&gt;](#op_gt)|
|[operator&gt;=](#op_gt_eq)|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|
|[operator*](#op_star)|[operator+](#op_add)|[operator-](#operator-)|
|[operator/](#op_div)|[operator==](#op_eq_eq)|

## <a name="operator-"></a>  operator-

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

`Left` Gauche `duration` ou `time_point` objet.

`Right` Droite `duration` ou `time_point` objet.

`Time` A `time_point` objet.

`Dur` A `duration` objet.

### <a name="return-value"></a>Valeur de retour

La première fonction retourne un objet `duration` dont la longueur de l'intervalle est la différence entre les intervalles de temps des deux arguments.

La deuxième fonction retourne un objet `time_point` qui représente un point dans le temps qui est déplacé, selon la négation de l'intervalle de temps représenté par `Dur`, à partir du point dans le temps spécifié par `Time`.

La troisième fonction retourne un objet `duration` qui représente l'intervalle de temps entre `Left` et `Right`.

## <a name="op_neq"></a>  operator!=

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

`Left` Gauche `duration` ou `time_point` objet.

`Right` Droite `duration` ou `time_point` objet.

### <a name="return-value"></a>Valeur de retour

Chaque fonction retourne `!(Left == Right)`.

## <a name="op_star"></a>  operator*

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

`Dur` A `duration` objet.

`Mult` Une valeur intégrale.

### <a name="return-value"></a>Valeur de retour

Chaque fonction retourne un objet `duration` dont la longueur de l'intervalle est égale à `Mult` multiplié par la longueur de `Dur`.

À moins que `is_convertible<Rep2, common_type<Rep1, Rep2>>`*ne contienne la valeur true*, la première fonction ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

À moins que `is_convertible<Rep1, common_type<Rep1, Rep2>>`*ne contienne la valeur true*, la deuxième fonction ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

## <a name="op_div"></a>  operator/

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

`Dur` A `duration` objet.

`Div` Une valeur intégrale.

`Left` Gauche `duration` objet.

`Right` Droite `duration` objet.

### <a name="return-value"></a>Valeur de retour

Le premier opérateur retourne un objet de durée dont l'intervalle de longueur est la longueur de `Dur` divisée par la valeur `Div`.

Le deuxième opérateur retourne le rapport des longueurs d'intervalle de `Left` et de `Right`.

À moins que `is_convertible<Rep2, common_type<Rep1, Rep2>>`*ne contienne la valeur true* et que `Rep2` ne soit pas une instanciation de `duration`, le premier opérateur ne participe pas à la résolution de surcharge. Pour plus d’informations, consultez [<type_traits>](../standard-library/type-traits.md).

## <a name="op_add"></a>  operator+

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

`Left` Gauche `duration` ou `time_point` objet.

`Right` Droite `duration` ou `time_point` objet.

`Time` A `time_point` objet.

`Dur` A `duration` objet.

### <a name="return-value"></a>Valeur de retour

La première fonction retourne un objet `duration` dont l'intervalle de temps est égal à la somme des intervalles de `Left` et de `Right`.

Les deuxième et troisième fonctions retournent un objet `time_point` qui représente un point dans le temps qui est déplacé, selon l'intervalle `Dur`, à partir du point dans le temps `Time`.

## <a name="op_lt"></a>  operator&lt;

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

`Left` Gauche `duration` ou `time_point` objet.

`Right` Droite `duration` ou `time_point` objet.

### <a name="return-value"></a>Valeur de retour

La première fonction retourne `true` si la longueur de l'intervalle de `Left` est inférieure à la longueur de l'intervalle de `Right`. Sinon, la fonction retourne `false`.

La deuxième fonction retourne `true` si `Left` précède `Right`. Sinon, la fonction retourne `false`.

## <a name="op_lt_eq"></a>  operator&lt;=

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

`Left` Gauche `duration` ou `time_point` objet.

`Right` Droite `duration` ou `time_point` objet.

### <a name="return-value"></a>Valeur de retour

Chaque fonction retourne `!(Right < Left)`.

## <a name="op_eq_eq"></a>  operator==

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

`Left` Gauche `duration` ou `time_point` objet.

`Right` Droite `duration` ou `time_point` objet.

### <a name="return-value"></a>Valeur de retour

La première fonction retourne `true` si `Left` et `Right` représentent des intervalles de temps de même longueur. Sinon, la fonction retourne `false`.

La deuxième fonction retourne `true` si `Left` et `Right` représentent le même point dans le temps. Sinon, la fonction retourne `false`.

## <a name="op_gt"></a>  operator&gt;

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

`Left` Gauche `duration` ou `time_point` objet.

`Right` Droite `duration` ou `time_point` objet.

### <a name="return-value"></a>Valeur de retour

Chaque fonction retourne `Right < Left`.

## <a name="op_gt_eq"></a>  operator&gt;=

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

`Left` Gauche `duration` ou `time_point` objet.

`Right` Droite `duration` ou `time_point` objet.

### <a name="return-value"></a>Valeur de retour

Chaque fonction retourne `!(Left < Right)`.

## <a name="op_modulo"></a>  opérateur modulo

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

`Dur` A `duration` objet.

`Div` Une valeur intégrale.

`Left` Gauche `duration` objet.

`Right` Droite `duration` objet.

### <a name="return-value"></a>Valeur de retour

La première fonction retourne un objet `duration` dont la longueur d'intervalle est `Dur` modulo `Div`.

La deuxième fonction retourne une valeur qui représente `Left` modulo `Right`.

## <a name="see-also"></a>Voir aussi

[\<chrono>](../standard-library/chrono.md)<br/>
