---
title: recursive_timed_mutex, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::lock
- mutex/std::recursive_timed_mutex::try_lock
- mutex/std::recursive_timed_mutex::try_lock_for
- mutex/std::recursive_timed_mutex::try_lock_until
- mutex/std::recursive_timed_mutex::unlock
dev_langs:
- C++
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::recursive_timed_mutex [C++]
- std::recursive_timed_mutex [C++], recursive_timed_mutex
- std::recursive_timed_mutex [C++], lock
- std::recursive_timed_mutex [C++], try_lock
- std::recursive_timed_mutex [C++], try_lock_for
- std::recursive_timed_mutex [C++], try_lock_until
- std::recursive_timed_mutex [C++], unlock
ms.workload:
- cplusplus
ms.openlocfilehash: 9b4a87cadedb11368d7803231b96d0f7a5acfb99
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863710"
---
# <a name="recursivetimedmutex-class"></a>recursive_timed_mutex, classe

Représente un *type mutex limité dans le temps*. Les objets de ce type permettent d’appliquer une exclusion mutuelle (mutex) en utilisant un blocage limité dans le temps dans un programme. Contrairement aux objets de type [timed_mutex](../standard-library/timed-mutex-class.md), l’effet des appels à des méthodes de verrouillage sur les objets `recursive_timed_mutex` est bien défini.

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|Construit un objet `recursive_timed_mutex` qui n’est pas verrouillé.|
|[~recursive_timed_mutex, destructeur](#dtorrecursive_timed_mutex_destructor)|Libère les ressources utilisées par l’objet `recursive_timed_mutex`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[lock](#lock)|Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.|
|[try_lock](#try_lock)|Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.|
|[try_lock_for](#try_lock_for)|Tente d’obtenir la propriété du `mutex` pour un intervalle de temps spécifié.|
|[try_lock_until](#try_lock_until)|Tente d’obtenir la propriété du `mutex` jusqu’à une heure spécifiée.|
|[unlock](#unlock)|Libère la propriété du `mutex`.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<mutex >

**Espace de noms :** std

## <a name="lock"></a>  lock

Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà le `mutex`, la méthode est retournée immédiatement, et le verrou précédent reste en vigueur.

## <a name="recursive_timed_mutex"></a>  recursive_timed_mutex, constructeur

Construit un objet `recursive_timed_mutex` qui n’est pas verrouillé.

```cpp
recursive_timed_mutex();
```

## <a name="dtorrecursive_timed_mutex_destructor"></a>  ~recursive_timed_mutex, destructeur

Libère les ressources utilisées par l’objet `recursive_timed_mutex`.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Notes

Si l'objet est verrouillé lorsque le destructeur s'exécute, le comportement est indéfini.

## <a name="try_lock"></a>  try_lock

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Valeur de retour

`true` si la méthode a réussi à obtenir la propriété du `mutex` ou si le thread appelant possède déjà le `mutex`. Sinon, `false`.

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà le `mutex`, la fonction retourne immédiatement `true`, et le verrou précédent reste en vigueur.

## <a name="try_lock_for"></a>  try_lock_for

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Paramètres

`Rel_time` A [chrono::duration](../standard-library/duration-class.md) objet qui spécifie la durée maximale pendant laquelle la méthode essaie d’obtenir la propriété de la `mutex`.

### <a name="return-value"></a>Valeur de retour

`true` si la méthode réussit à obtenir la propriété du `mutex` ou si le thread appelant possède déjà le `mutex`. Sinon, `false`.

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà le `mutex`, la méthode retourne immédiatement `true`, et le verrou précédent reste en vigueur.

## <a name="try_lock_until"></a>  try_lock_until

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Paramètres

`Abs_time` Un point dans le temps qui spécifie le seuil au-delà duquel la méthode n’est plus tente d’obtenir la propriété de la `mutex`.

### <a name="return-value"></a>Valeur de retour

`true` si la méthode réussit à obtenir la propriété du `mutex` ou si le thread appelant possède déjà le `mutex`. Sinon, `false`.

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà le `mutex`, la méthode retourne immédiatement `true`, et le verrou précédent reste en vigueur.

## <a name="unlock"></a>  unlock

Libère la propriété du `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Notes

Cette méthode libère la propriété du `mutex` uniquement si elle a été appelée autant de fois que [lock](#lock), [try_lock](#try_lock), [try_lock_for](#try_lock_for) et [try_lock_until](#try_lock_until) ont été appelés avec succès sur l’objet `recursive_timed_mutex`.

Si le thread appelant ne possède pas `mutex`, le comportement est indéfini.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
