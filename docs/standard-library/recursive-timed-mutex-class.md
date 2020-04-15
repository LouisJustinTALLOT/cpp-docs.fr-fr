---
title: recursive_timed_mutex, classe
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::lock
- mutex/std::recursive_timed_mutex::try_lock
- mutex/std::recursive_timed_mutex::try_lock_for
- mutex/std::recursive_timed_mutex::try_lock_until
- mutex/std::recursive_timed_mutex::unlock
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
helpviewer_keywords:
- std::recursive_timed_mutex [C++]
- std::recursive_timed_mutex [C++], recursive_timed_mutex
- std::recursive_timed_mutex [C++], lock
- std::recursive_timed_mutex [C++], try_lock
- std::recursive_timed_mutex [C++], try_lock_for
- std::recursive_timed_mutex [C++], try_lock_until
- std::recursive_timed_mutex [C++], unlock
ms.openlocfilehash: 93ce7b99728d1ce89c8124efd6c74aea7ff66d22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320147"
---
# <a name="recursive_timed_mutex-class"></a>recursive_timed_mutex, classe

Représente un *type de mutex chronométré*. Les objets de ce type permettent d’appliquer une exclusion mutuelle (mutex) en utilisant un blocage limité dans le temps dans un programme. Contrairement aux objets de type [timed_mutex](../standard-library/timed-mutex-class.md), l’effet des appels à des méthodes de verrouillage sur les objets `recursive_timed_mutex` est bien défini.

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|Construit un objet `recursive_timed_mutex` qui n’est pas verrouillé.|
|[Destructeur recursive_timed_mutex](#dtorrecursive_timed_mutex_destructor)|Libère les ressources utilisées par l’objet `recursive_timed_mutex`.|

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

## <a name="lock"></a><a name="lock"></a>Verrouillage

Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà le `mutex`, la méthode est retournée immédiatement, et le verrou précédent reste en vigueur.

## <a name="recursive_timed_mutex-constructor"></a><a name="recursive_timed_mutex"></a>recursive_timed_mutex Constructeur

Construit un objet `recursive_timed_mutex` qui n’est pas verrouillé.

```cpp
recursive_timed_mutex();
```

## <a name="recursive_timed_mutex-destructor"></a><a name="dtorrecursive_timed_mutex_destructor"></a>  ~recursive_timed_mutex, destructeur

Libère les ressources utilisées par l’objet `recursive_timed_mutex`.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Notes

Si l'objet est verrouillé lorsque le destructeur s'exécute, le comportement est indéfini.

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Valeur de retour

**vrai** si la méthode a `mutex` réussi à obtenir la `mutex`propriété du ou si le fil d’appel possède déjà le ; autrement, **faux**.

### <a name="remarks"></a>Notes

Si le fil d’appel possède déjà le `mutex`, la fonction retourne immédiatement **vrai**, et le verrou précédent reste en vigueur.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Paramètres

*Rel_time*\
Objet [chrono::duration](../standard-library/duration-class.md) qui spécifie la durée maximale pendant laquelle la méthode essaie d’obtenir la propriété du `mutex`.

### <a name="return-value"></a>Valeur de retour

**vrai** si la méthode obtient `mutex` avec succès la propriété `mutex`du ou si le fil d’appel possède déjà le ; autrement, **faux**.

### <a name="remarks"></a>Notes

Si le fil d’appel possède déjà le `mutex`, la méthode retourne immédiatement **vrai**, et le verrou précédent reste en vigueur.

## <a name="try_lock_until"></a><a name="try_lock_until"></a>try_lock_until

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

**vrai** si la méthode obtient `mutex` avec succès la propriété `mutex`du ou si le fil d’appel possède déjà le ; autrement, **faux**.

### <a name="remarks"></a>Notes

Si le fil d’appel possède déjà le `mutex`, la méthode retourne immédiatement **vrai**, et le verrou précédent reste en vigueur.

## <a name="unlock"></a><a name="unlock"></a>Déverrouiller

Libère la propriété du `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Notes

Cette méthode libère la propriété du `mutex` uniquement si elle a été appelée autant de fois que [lock](#lock), [try_lock](#try_lock), [try_lock_for](#try_lock_for) et [try_lock_until](#try_lock_until) ont été appelés avec succès sur l’objet `recursive_timed_mutex`.

Si le thread appelant ne possède pas `mutex`, le comportement est indéfini.

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
