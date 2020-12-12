---
description: 'En savoir plus sur les fonctions suivantes : &lt; Chrono &gt;'
title: '&lt;chrono&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
ms.openlocfilehash: 161edeccace243c10a6382d931f5f9387f35790d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234200"
---
# <a name="ltchronogt-functions"></a>&lt;chrono&gt;, fonctions

## <a name="duration_cast"></a><a name="duration_cast"></a> duration_cast

Caste un objet `duration` en un type spécifié.

```cpp
template <class To, class Rep, class Period>
constexpr To duration_cast(const duration<Rep, Period>& Dur);

template <class ToDuration, class Rep, class Period>
constexpr ToDuration floor(const duration<Rep, Period>& d);
template <class ToDuration, class Rep, class Period>
constexpr ToDuration ceil(const duration<Rep, Period>& d);
template <class ToDuration, class Rep, class Period>
constexpr ToDuration round(const duration<Rep, Period>& d);
```

### <a name="return-value"></a>Valeur renvoyée

Objet `duration` de type `To` qui représente l’intervalle de temps `Dur`, qui est tronqué s’il doit tenir dans le type cible.

### <a name="remarks"></a>Notes

Si `To` est une instanciation de `duration`, cette fonction ne participe pas à la résolution de surcharge.

## <a name="time_point_cast"></a><a name="time_point_cast"></a> time_point_cast

Caste un objet [time_point](../standard-library/time-point-class.md) en type spécifié.

```cpp
template <class To, class Clock, class Duration>
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);

template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
floor(const time_point<Clock, Duration>& tp);
template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
ceil(const time_point<Clock, Duration>& tp);
template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
round(const time_point<Clock, Duration>& tp);
```

### <a name="return-value"></a>Valeur renvoyée

Objet `time_point` qui a une durée de type `To`.

### <a name="remarks"></a>Notes

À moins que `To` soit une instanciation de [duration](../standard-library/duration-class.md), cette fonction ne participe pas à la résolution de surcharge.
