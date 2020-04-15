---
title: timed_mutex, classe
ms.date: 11/04/2016
f1_keywords:
- mutex/std::timed_mutex
- mutex/std::timed_mutex::timed_mutex
- mutex/std::timed_mutex::lock
- mutex/std::timed_mutex::try_lock
- mutex/std::timed_mutex::try_lock_for
- mutex/std::timed_mutex::try_lock_until
- mutex/std::timed_mutex::unlock
ms.assetid: cd198081-6f38-447a-9dba-e06dfbfafe59
helpviewer_keywords:
- std::timed_mutex [C++]
- std::timed_mutex [C++], timed_mutex
- std::timed_mutex [C++], lock
- std::timed_mutex [C++], try_lock
- std::timed_mutex [C++], try_lock_for
- std::timed_mutex [C++], try_lock_until
- std::timed_mutex [C++], unlock
ms.openlocfilehash: 6c9840d9b8c00d4b03e6ea329c7707a0edff9512
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368016"
---
# <a name="timed_mutex-class"></a>timed_mutex, classe

Représente un *type de mutex chronométré*. Les objets de ce type permettent d’appliquer une exclusion mutuelle (mutex) via un blocage limité dans le temps dans un programme.

## <a name="syntax"></a>Syntaxe

```cpp
class timed_mutex;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|Construit un objet `timed_mutex` qui n’est pas verrouillé.|
|[timed_mutex: Timed_mutex Destructor](#dtortimed_mutex_destructor)|Libère les ressources utilisées par l’objet `timed_mutex`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Verrouillage](#lock)|Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.|
|[try_lock](#try_lock)|Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.|
|[try_lock_for](#try_lock_for)|Tente d’obtenir la propriété du `mutex` pour un intervalle de temps spécifié.|
|[try_lock_until](#try_lock_until)|Tente d’obtenir la propriété du `mutex` jusqu’à une heure spécifiée.|
|[Déverrouiller](#unlock)|Libère la propriété du `mutex`.|

## <a name="requirements"></a>Spécifications

**En-tête:** \<mutex>

**Espace de noms :** std

## <a name="timed_mutexlock"></a><a name="lock"></a>timed_mutex::lock

Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà `mutex`, le comportement est indéfini.

## <a name="timed_mutextimed_mutex-constructor"></a><a name="timed_mutex"></a>timed_mutex::timed_mutex Constructeur

Construit un objet `timed_mutex` qui n’est pas verrouillé.

```cpp
timed_mutex();
```

## <a name="timed_mutextimed_mutex-destructor"></a><a name="dtortimed_mutex_destructor"></a>timed_mutex: Timed_mutex Destructor

Libère les ressources utilisées par l’objet `mutex`.

```cpp
~timed_mutex();
```

### <a name="remarks"></a>Notes

Si l'objet est verrouillé lorsque le destructeur s'exécute, le comportement est indéfini.

## <a name="timed_mutextry_lock"></a><a name="try_lock"></a>timed_mutex::try_lock

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valeur de retour

**vrai** si la méthode obtient `mutex`avec succès la propriété de la ; autrement, **faux**.

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà `mutex`, le comportement est indéfini.

## <a name="timed_mutextry_lock_for"></a><a name="try_lock_for"></a>timed_mutex::try_lock_for

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Paramètres

*Rel_time*\
Objet [chrono::duration](../standard-library/duration-class.md) qui spécifie la durée maximale pendant laquelle la méthode essaie d’obtenir la propriété du `mutex`.

### <a name="return-value"></a>Valeur de retour

**vrai** si la méthode obtient `mutex`avec succès la propriété de la ; autrement, **faux**.

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà `mutex`, le comportement est indéfini.

## <a name="timed_mutextry_lock_until"></a><a name="try_lock_until"></a>timed_mutex::try_lock_until

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Paramètres

*Abs_time*\
Point dans le temps qui spécifie le seuil au-delà duquel la méthode ne tente plus d'obtenir la propriété du `mutex`.

### <a name="return-value"></a>Valeur de retour

**vrai** si la méthode obtient `mutex`avec succès la propriété de la ; autrement, **faux**.

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà `mutex`, le comportement est indéfini.

## <a name="timed_mutexunlock"></a><a name="unlock"></a>timed_mutex::unlock

Libère la propriété du `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Notes

Si le thread appelant ne possède pas `mutex`, le comportement est indéfini.

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
