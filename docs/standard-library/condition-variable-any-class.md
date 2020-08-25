---
title: condition_variable_any, classe
ms.date: 11/04/2016
f1_keywords:
- condition_variable/std::condition_variable_any
- condition_variable/std::condition_variable_any::condition_variable_any
- condition_variable/std::condition_variable_any::notify_all
- condition_variable/std::condition_variable_any::notify_one
- condition_variable/std::condition_variable_any::wait
- condition_variable/std::condition_variable_any::wait_for
- condition_variable/std::condition_variable_any::wait_until
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
helpviewer_keywords:
- std::condition_variable_any
- std::condition_variable_any::condition_variable_any
- std::condition_variable_any::notify_all
- std::condition_variable_any::notify_one
- std::condition_variable_any::wait
- std::condition_variable_any::wait_for
- std::condition_variable_any::wait_until
ms.openlocfilehash: 9dc73de515aa8e321dbb28ca4a859b256613fbfe
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831475"
---
# <a name="condition_variable_any-class"></a>condition_variable_any, classe

Utilisez la classe `condition_variable_any` pour attendre un événement avec un type `mutex`.

## <a name="syntax"></a>Syntaxe

```cpp
class condition_variable_any;
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[condition_variable_any](#condition_variable_any)|Construit un objet `condition_variable_any`.|

### <a name="functions"></a>Functions

|Nom|Description|
|-|-|
|[notify_all](#notify_all)|Débloque tous les threads qui attendent l’objet `condition_variable_any`.|
|[notify_one](#notify_one)|Débloque un des threads qui attendent l’objet `condition_variable_any`.|
|[qu'](#wait)|Bloque un thread.|
|[wait_for](#wait_for)|Bloque un thread et définit un intervalle de temps après lequel le thread est débloqué.|
|[wait_until](#wait_until)|Bloque un thread et définit un point dans le temps maximal auquel le thread est débloqué.|

## <a name="condition_variable_any"></a><a name="condition_variable_any"></a> condition_variable_any

Construit un objet `condition_variable_any`.

```cpp
condition_variable_any();
```

### <a name="remarks"></a>Notes

Si la mémoire disponible n’est pas suffisante, le constructeur lève un objet [system_error](../standard-library/system-error-class.md) avec le code d’erreur `not_enough_memory`. Si l’objet ne peut pas être construit, car une autre ressource n’est pas disponible, le constructeur lève un objet `system_error` avec le code d’erreur `resource_unavailable_try_again`.

## <a name="notify_all"></a><a name="notify_all"></a> notify_all

Débloque tous les threads qui attendent l’objet `condition_variable_any`.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a><a name="notify_one"></a> notify_one

Débloque un des threads qui attendent l’objet `condition_variable_any`.

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a><a name="wait"></a> qu'

Bloque un thread.

```cpp
template <class Lock>
void wait(Lock& Lck);

template <class Lock, class Predicate>
void wait(Lock& Lck, Predicate Pred);
```

### <a name="parameters"></a>Paramètres

*LCK*\
Objet `mutex` de tout type.

*Prédit*\
Toute expression qui retourne **`true`** ou **`false`** .

### <a name="remarks"></a>Notes

La première méthode se bloque jusqu’à ce que l’objet `condition_variable_any` soit signalé par un appel à [notify_one](../standard-library/condition-variable-class.md#notify_one) ou [notify_all](../standard-library/condition-variable-class.md#notify_all). Elle peut également s’éveiller sans motif.

La deuxième méthode exécute le code suivant.

```cpp
while (!Pred())
    wait(Lck);
```

## <a name="wait_for"></a><a name="wait_for"></a> wait_for

Bloque un thread et définit un intervalle de temps après lequel le thread est débloqué.

```cpp
template <class Lock, class Rep, class Period>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time);

template <class Lock, class Rep, class Period, class Predicate>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time, Predicate Pred);
```

### <a name="parameters"></a>Paramètres

*LCK*\
Objet `mutex` de tout type.

*Rel_time*\
Objet `chrono::duration` qui spécifie le délai avant l’éveil du thread.

*Prédit*\
Toute expression qui retourne **`true`** ou **`false`** .

### <a name="return-value"></a>Valeur renvoyée

La première méthode retourne `cv_status::timeout` si l’attente se termine quand *Rel_time* s’est écoulé. Dans le cas contraire, la méthode retourne `cv_status::no_timeout`.

La deuxième méthode retourne la valeur de *prédit*.

### <a name="remarks"></a>Notes

La première méthode se bloque jusqu’à ce que l' `condition_variable_any` objet soit signalé par un appel à [notify_one](../standard-library/condition-variable-class.md#notify_one) ou [notify_all](../standard-library/condition-variable-class.md#notify_all), ou jusqu’à ce que l’intervalle de temps *Rel_time* s’est écoulé. Elle peut également s’éveiller sans motif.

La deuxième méthode exécute le code suivant.

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a><a name="wait_until"></a> wait_until

Bloque un thread et définit un point dans le temps maximal auquel le thread est débloqué.

```cpp
template <class Lock, class Clock, class Duration>
void wait_until(Lock& Lck, const chrono::time_point<Clock, Duration>& Abs_time);

template <class Lock, class Clock, class Duration, class Predicate>
void wait_until(
    Lock& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time,
    Predicate Pred);

template <class Lock>
void wait_until(Lock Lck, const xtime* Abs_time);

template <class Lock, class Predicate>
void wait_until(
    Lock Lck,
    const xtime* Abs_time,
    Predicate Pred);
```

### <a name="parameters"></a>Paramètres

*LCK*\
Objet mutex.

*Abs_time*\
Objet [chrono::time_point](../standard-library/time-point-class.md).

*Prédit*\
Toute expression qui retourne **`true`** ou **`false`** .

### <a name="return-value"></a>Valeur renvoyée

Les méthodes qui retournent un `cv_status` type retournent `cv_status::timeout` si l’attente se termine lorsque *Abs_time* s’arrête. Sinon, les méthodes retournent `cv_status::no_timeout`.

Les méthodes qui retournent une **`bool`** valeur retournent la valeur de *prédit*.

### <a name="remarks"></a>Notes

La première méthode se bloque jusqu’à ce que l' `condition_variable` objet soit signalé par un appel à [notify_one](../standard-library/condition-variable-class.md#notify_one) ou [notify_all](../standard-library/condition-variable-class.md#notify_all), ou jusqu’à *Abs_time*. Elle peut également s’éveiller sans motif.

La deuxième méthode exécute le code suivant.

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

Les troisième et quatrième méthodes utilisent un pointeur vers un objet de type `xtime` pour remplacer l’objet `chrono::time_point`. L’objet `xtime` spécifie le délai d’attente maximal d’un signal.
