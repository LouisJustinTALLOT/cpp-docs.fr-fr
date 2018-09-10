---
title: condition_variable_any, classe │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- condition_variable/std::condition_variable_any
- condition_variable/std::condition_variable_any::condition_variable_any
- condition_variable/std::condition_variable_any::notify_all
- condition_variable/std::condition_variable_any::notify_one
- condition_variable/std::condition_variable_any::wait
- condition_variable/std::condition_variable_any::wait_for
- condition_variable/std::condition_variable_any::wait_until
dev_langs:
- C++
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::condition_variable_any
- std::condition_variable_any::condition_variable_any
- std::condition_variable_any::notify_all
- std::condition_variable_any::notify_one
- std::condition_variable_any::wait
- std::condition_variable_any::wait_for
- std::condition_variable_any::wait_until
ms.workload:
- cplusplus
ms.openlocfilehash: 9acd5abc941c3cc3ab2f1c22486298d7cc7da16c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106962"
---
# <a name="conditionvariableany-class"></a>condition_variable_any, classe

Utilisez la classe `condition_variable_any` pour attendre un événement avec un type `mutex`.

## <a name="syntax"></a>Syntaxe

```cpp
class condition_variable_any;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[condition_variable_any](#condition_variable_any)|Construit un objet `condition_variable_any`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[notify_all](#notify_all)|Débloque tous les threads qui attendent l’objet `condition_variable_any`.|
|[notify_one](#notify_one)|Débloque un des threads qui attendent l’objet `condition_variable_any`.|
|[attente](#wait)|Bloque un thread.|
|[wait_for](#wait_for)|Bloque un thread et définit un intervalle de temps après lequel le thread est débloqué.|
|[wait_until](#wait_until)|Bloque un thread et définit un point dans le temps maximal auquel le thread est débloqué.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<condition_variable >

**Espace de noms :** std

## <a name="condition_variable_any"></a>  condition_variable_any::condition_variable_any, constructeur

Construit un objet `condition_variable_any`.

```cpp
condition_variable_any();
```

### <a name="remarks"></a>Notes

Si la mémoire disponible n’est pas suffisante, le constructeur lève un objet [system_error](../standard-library/system-error-class.md) avec le code d’erreur `not_enough_memory`. Si l’objet ne peut pas être construit, car une autre ressource n’est pas disponible, le constructeur lève un objet `system_error` avec le code d’erreur `resource_unavailable_try_again`.

## <a name="notify_all"></a>  condition_variable_any::notify_all

Débloque tous les threads qui attendent l’objet `condition_variable_any`.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a>  condition_variable_any::notify_one

Débloque un des threads qui attendent l’objet `condition_variable_any`.

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a>  condition_variable_any::wait

Bloque un thread.

```cpp
template <class Lock>
void wait(Lock& Lck);

template <class Lock, class Predicate>
void wait(Lock& Lck, Predicate Pred);
```

### <a name="parameters"></a>Paramètres

*Lck*<br/>
Objet `mutex` de tout type.

*Pred*<br/>
Toute expression qui retourne **true** ou **false**.

### <a name="remarks"></a>Notes

La première méthode se bloque jusqu’à ce que l’objet `condition_variable_any` soit signalé par un appel à [notify_one](../standard-library/condition-variable-class.md#notify_one) ou [notify_all](../standard-library/condition-variable-class.md#notify_all). Elle peut également s’éveiller sans motif.

La deuxième méthode exécute le code suivant.

```cpp
while (!Pred())
    wait(Lck);
```

## <a name="wait_for"></a>  condition_variable_any::wait_for

Bloque un thread et définit un intervalle de temps après lequel le thread est débloqué.

```cpp
template <class Lock, class Rep, class Period>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time);

template <class Lock, class Rep, class Period, class Predicate>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time, Predicate Pred);
```

### <a name="parameters"></a>Paramètres

*Lck*<br/>
Objet `mutex` de tout type.

*Rel_time*<br/>
Objet `chrono::duration` qui spécifie le délai avant l’éveil du thread.

*Pred*<br/>
Toute expression qui retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

La première méthode retourne `cv_status::timeout` si l’attente termine quand *Rel_time* s’est écoulé. Dans le cas contraire, la méthode retourne `cv_status::no_timeout`.

La deuxième méthode retourne la valeur de *Pred*.

### <a name="remarks"></a>Notes

La première méthode se bloque jusqu'à ce que le `condition_variable_any` objet est signalé par un appel à [notify_one](../standard-library/condition-variable-class.md#notify_one) ou [notify_all](../standard-library/condition-variable-class.md#notify_all), ou jusqu'à ce que l’intervalle de temps *Rel_time* s’est écoulé. Elle peut également s’éveiller sans motif.

La deuxième méthode exécute le code suivant.

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a>  condition_variable_any::wait_until

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

*Lck*<br/>
Objet mutex.

*Abs_time*<br/>
Objet [chrono::time_point](../standard-library/time-point-class.md).

*Pred*<br/>
Toute expression qui retourne **true** ou **false**.

### <a name="return-value"></a>Valeur de retour

Les méthodes qui retournent un `cv_status` tapez retour `cv_status::timeout` si l’attente termine quand *Abs_time* s’écoule. Sinon, les méthodes retournent `cv_status::no_timeout`.

Les méthodes qui retournent un `bool` retournent la valeur de *Pred*.

### <a name="remarks"></a>Notes

La première méthode se bloque jusqu'à ce que le `condition_variable` objet est signalé par un appel à [notify_one](../standard-library/condition-variable-class.md#notify_one) ou [notify_all](../standard-library/condition-variable-class.md#notify_all), ou jusqu'à ce que *Abs_time*. Elle peut également s’éveiller sans motif.

La deuxième méthode exécute le code suivant.

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

Les troisième et quatrième méthodes utilisent un pointeur vers un objet de type `xtime` pour remplacer l’objet `chrono::time_point`. L’objet `xtime` spécifie le délai d’attente maximal d’un signal.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[<condition_variable>](../standard-library/condition-variable.md)<br/>
