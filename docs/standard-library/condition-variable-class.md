---
description: 'En savoir plus sur : classe condition_variable'
title: condition_variable, classe
ms.date: 11/04/2016
f1_keywords:
- condition_variable/std::condition
- condition_variable/std::condition_variable::condition_variable
- condition_variable/std::condition_variable::native_handle
- condition_variable/std::condition_variable::notify_all
- condition_variable/std::condition_variable::notify_one
- condition_variable/std::condition_variable::wait
- condition_variable/std::condition_variable::wait_for
- condition_variable/std::condition_variable::wait_until
ms.assetid: 80b1295c-b73d-4d46-b664-6e183f2eec1b
helpviewer_keywords:
- std::condition
- std::condition_variable::condition_variable
- std::condition_variable::native_handle
- std::condition_variable::notify_all
- std::condition_variable::notify_one
- std::condition_variable::wait
- std::condition_variable::wait_for
- std::condition_variable::wait_until
ms.openlocfilehash: f5987c050dece8536aef0f91731a0848b56d3a4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233810"
---
# <a name="condition_variable-class"></a>condition_variable, classe

Utilisez la classe `condition_variable` pour attendre un événement quand vous avez un `mutex` de type `unique_lock<mutex>`. Les objets de ce type peuvent avoir de meilleures performances que les objets de type [condition_variable_any<unique_lock \<mutex> > ](../standard-library/condition-variable-any-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class condition_variable;
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[condition_variable](#condition_variable)|Construit un objet `condition_variable`.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|[native_handle](#native_handle)|Retourne le type spécifique de l’implémentation qui représente le descripteur condition_variable.|
|[notify_all](#notify_all)|Débloque tous les threads qui attendent l’objet `condition_variable`.|
|[notify_one](#notify_one)|Débloque un des threads qui attendent l’objet `condition_variable`.|
|[wait](#wait)|Bloque un thread.|
|[wait_for](#wait_for)|Bloque un thread et définit un intervalle de temps après lequel le thread est débloqué.|
|[wait_until](#wait_until)|Bloque un thread et définit un point dans le temps maximal auquel le thread est débloqué.|

## <a name="condition_variable"></a><a name="condition_variable"></a> condition_variable

Construit un objet `condition_variable`.

```cpp
condition_variable();
```

### <a name="remarks"></a>Notes

Si la mémoire disponible n’est pas suffisante, le constructeur lève un objet [system_error](../standard-library/system-error-class.md) avec le code d’erreur `not_enough_memory`. Si l’objet ne peut pas être construit, car une autre ressource n’est pas disponible, le constructeur lève un objet `system_error` avec le code d’erreur `resource_unavailable_try_again`.

## <a name="native_handle"></a><a name="native_handle"></a> native_handle

Retourne le type spécifique de l’implémentation qui représente le descripteur condition_variable.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Valeur renvoyée

`native_handle_type` est défini comme un pointeur vers les structures de données internes du runtime d’accès concurrentiel.

## <a name="notify_all"></a><a name="notify_all"></a> notify_all

Débloque tous les threads qui attendent l’objet `condition_variable`.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a><a name="notify_one"></a> notify_one

Débloque un des threads qui attendent l’objet `condition_variable`.

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a><a name="wait"></a> qu'

Bloque un thread.

```cpp
void wait(unique_lock<mutex>& Lck);

template <class Predicate>
void wait(unique_lock<mutex>& Lck, Predicate Pred);
```

### <a name="parameters"></a>Paramètres

*LCK*\
Objet [unique_lock \<mutex> ](../standard-library/unique-lock-class.md) .

*Prédit*\
Toute expression qui retourne **`true`** ou **`false`** .

### <a name="remarks"></a>Notes

La première méthode se bloque jusqu’à ce que l’objet `condition_variable` soit signalé par un appel à [notify_one](#notify_one) ou [notify_all](#notify_all). Elle peut également s’éveiller sans motif.

La deuxième méthode exécute le code suivant.

```cpp
while(!Pred())
    wait(Lck);
```

## <a name="wait_for"></a><a name="wait_for"></a> wait_for

Bloque un thread et définit un intervalle de temps après lequel le thread est débloqué.

```cpp
template <class Rep, class Period>
cv_status wait_for(
    unique_lock<mutex>& Lck,
    const chrono::duration<Rep, Period>& Rel_time);

template <class Rep, class Period, class Predicate>
bool wait_for(
    unique_lock<mutex>& Lck,
    const chrono::duration<Rep, Period>& Rel_time,
    Predicate Pred);
```

### <a name="parameters"></a>Paramètres

*LCK*\
Objet [unique_lock \<mutex> ](../standard-library/unique-lock-class.md) .

*Rel_time*\
Objet `chrono::duration` qui spécifie le délai avant l’éveil du thread.

*Prédit*\
Toute expression qui retourne **`true`** ou **`false`** .

### <a name="return-value"></a>Valeur renvoyée

La première méthode retourne `cv_status::timeout` si l’attente se termine quand *Rel_time* s’est écoulé. Dans le cas contraire, la méthode retourne `cv_status::no_timeout`.

La deuxième méthode retourne la valeur de *prédit*.

### <a name="remarks"></a>Notes

La première méthode se bloque jusqu’à ce que l' `condition_variable` objet soit signalé par un appel à [notify_one](#notify_one) ou [notify_all](#notify_all) ou jusqu’à ce que l’intervalle de temps *Rel_time* s’est écoulé. Elle peut également s’éveiller sans motif.

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
template <class Clock, class Duration>
cv_status wait_until(
    unique_lock<mutex>& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time);

template <class Clock, class Duration, class Predicate>
bool wait_until(
    unique_lock<mutex>& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time,
    Predicate Pred);

cv_status wait_until(
    unique_lock<mutex>& Lck,
    const xtime* Abs_time);

template <class Predicate>
bool wait_until(
    unique_lock<mutex>& Lck,
    const xtime* Abs_time,
    Predicate Pred);
```

### <a name="parameters"></a>Paramètres

*LCK*\
Objet [unique_lock \<mutex> ](../standard-library/unique-lock-class.md) .

*Abs_time*\
Objet [chrono::time_point](../standard-library/time-point-class.md).

*Prédit*\
Toute expression qui retourne **`true`** ou **`false`** .

### <a name="return-value"></a>Valeur renvoyée

Les méthodes qui retournent un `cv_status` type retournent `cv_status::timeout` si l’attente se termine lorsque *Abs_time* s’arrête. Sinon, les méthodes retournent `cv_status::no_timeout`.

Les méthodes qui retournent une **`bool`** valeur retournent la valeur de *prédit*.

### <a name="remarks"></a>Notes

La première méthode se bloque jusqu’à ce que l’objet `condition_variable` soit signalé par un appel à [notify_one](#notify_one) ou [notify_all](#notify_all), ou jusqu’à `Abs_time`. Elle peut également s’éveiller sans motif.

La deuxième méthode exécute le code suivant

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

Les troisième et quatrième méthodes utilisent un pointeur vers un objet de type `xtime` pour remplacer l’objet `chrono::time_point`. L’objet `xtime` spécifie le délai d’attente maximal d’un signal.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[<condition_variable>](../standard-library/condition-variable.md)
