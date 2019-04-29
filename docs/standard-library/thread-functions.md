---
title: '&lt;thread&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: c0a8e42cb7ee78c399459be82e50ef37ab203816
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279032"
---
# <a name="ltthreadgt-functions"></a>&lt;thread&gt;, fonctions

||||
|-|-|-|
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|
|[swap](#swap)|[yield](#yield)|

## <a name="get_id"></a>  get_id

Identifie de façon unique le thread d’exécution en cours.

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>Valeur de retour

Un objet de type [thread::id](../standard-library/thread-class.md) qui identifie de façon unique le thread d’exécution en cours.

## <a name="sleep_for"></a>  sleep_for

Bloque le thread appelant.

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Paramètres

*Rel_time*<br/>
Objet [duration](../standard-library/duration-class.md) qui spécifie un intervalle de temps.

### <a name="remarks"></a>Notes

La fonction bloque le thread appelant au moins l’heure spécifiée par *Rel_time*. Cette fonction ne lève aucune exception.

## <a name="sleep_until"></a>  sleep_until

Bloque le thread appelant au moins jusqu’à l’heure spécifiée.

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>Paramètres

*Abs_time*<br/>
Représente un point dans le temps.

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="swap"></a>  swap

Permute les États de deux **thread** objets.

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Gauche **thread** objet.

*Droite*<br/>
Droite **thread** objet.

### <a name="remarks"></a>Notes

La fonction appelle `Left.swap(Right)`.

## <a name="yield"></a>  yield

Indique au système d’exploitation d’exécuter d’autres threads, même si le thread actuel continuerait normalement à s’exécuter.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>Voir aussi

[\<thread>](../standard-library/thread.md)<br/>
