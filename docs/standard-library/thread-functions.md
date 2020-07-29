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
ms.openlocfilehash: 130328ca07de28e14eedd7fdc99fb8946f26c5cb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232857"
---
# <a name="ltthreadgt-functions"></a>&lt;thread&gt;, fonctions

||||
|-|-|-|
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|
|[swap](#swap)|[yield](#yield)|

## <a name="get_id"></a><a name="get_id"></a>get_id

Identifie de façon unique le thread d’exécution en cours.

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>Valeur de retour

Un objet de type [thread::id](../standard-library/thread-class.md) qui identifie de façon unique le thread d’exécution en cours.

## <a name="sleep_for"></a><a name="sleep_for"></a>sleep_for

Bloque le thread appelant.

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Paramètres

*Rel_time*\
Objet [duration](../standard-library/duration-class.md) qui spécifie un intervalle de temps.

### <a name="remarks"></a>Notes

La fonction bloque le thread appelant pendant au moins le temps spécifié par *Rel_time*. Cette fonction ne lève aucune exception.

## <a name="sleep_until"></a><a name="sleep_until"></a>sleep_until

Bloque le thread appelant au moins jusqu’à l’heure spécifiée.

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>Paramètres

*Abs_time*\
Représente un point dans le temps.

### <a name="remarks"></a>Notes

Cette fonction ne lève aucune exception.

## <a name="swap"></a><a name="swap"></a>échange

Permute les états de deux objets `thread`.

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Objet gauche `thread`.

*Oui*\
Objet droit `thread`.

### <a name="remarks"></a>Notes

La fonction appelle `Left.swap(Right)`.

## <a name="yield"></a><a name="yield"></a>génér

Indique au système d’exploitation d’exécuter d’autres threads, même si le thread actuel continuerait normalement à s’exécuter.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>Voir aussi

[\<thread>](../standard-library/thread.md)
