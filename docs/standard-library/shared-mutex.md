---
title: '&lt;shared_mutex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <shared_mutex>
- shared_mutex/std::swap
- shared_mutex/std::shared_lock
- shared_mutex/std::shared_lock::shared_lock
- shared_mutex/std::shared_lock::operator=
- shared_mutex/std::shared_lock::operator =
- shared_mutex/std::shared_lock::lock
- shared_mutex/std::shared_lock::try_lock
- shared_mutex/std::shared_lock::try_lock_for
- shared_mutex/std::shared_lock::try_lock_until
- shared_mutex/std::shared_lock::unlock
- shared_mutex/std::shared_lock::swap
- shared_mutex/std::shared_lock::release
- shared_mutex/std::shared_lock::owns_lock
- shared_mutex/std::shared_lock::operator bool
- shared_mutex/std::shared_lock::mutex
- shared_mutex/std::shared_mutex
- shared_mutex/std::shared_mutex::native_handle_type
- shared_mutex/std::shared_mutex::shared_mutex
- shared_mutex/std::shared_mutex::operator=
- shared_mutex/std::shared_mutex::operator =
- shared_mutex/std::shared_mutex::lock
- shared_mutex/std::shared_mutex::try_lock
- shared_mutex/std::shared_mutex::unlock
- shared_mutex/std::shared_mutex::lock_shared
- shared_mutex/std::shared_mutex::try_lock_shared
- shared_mutex/std::shared_mutex::unlock_shared
- shared_mutex/std::shared_mutex::native_handle
- shared_mutex/std::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::operator=
- shared_mutex/std::shared_timed_mutex::operator =
- shared_mutex/std::shared_timed_mutex::lock
- shared_mutex/std::shared_timed_mutex::try_lock
- shared_mutex/std::shared_timed_mutex::try_lock_for
- shared_mutex/std::shared_timed_mutex::try_lock_until
- shared_mutex/std::shared_timed_mutex::unlock
- shared_mutex/std::shared_timed_mutex::lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared_for
- shared_mutex/std::shared_timed_mutex::try_lock_shared_until
- shared_mutex/std::shared_timed_mutex::unlock_shared
dev_langs:
- C++
ms.assetid: 0b37a97d-ee5d-4050-b29f-09db9f76beb3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6def4845356c542b0bdd5d0de14dc3402640dc05
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391330"
---
# <a name="ltsharedmutex"></a>&lt;shared_mutex>

Le &lt;shared_mutex > en-tête fournit des primitives de synchronisation pour la protection des données partagées qui sont accessibles par plusieurs threads. En plus du contrôle d’accès exclusif fourni par les classes mutex, les classes mutex partagé prennent en charge la propriété partagée par plusieurs threads pour permettre un accès non exclusif. Les mutex partagés s’utilisent pour contrôler les ressources qui peuvent être lues par plusieurs threads sans provoquer de condition critique, mais qui doivent être écrites en mode exclusif par un seul thread.

L’en-tête &lt;shared_mutex > définit les classes `shared_mutex` et `shared_timed_mutex`, la classe de modèle `shared_lock`et la fonction de modèle `swap` pour partagé prise en charge de mutex.

|Classes|Description|
|-------------|-----------------|
|[shared_mutex, classe](../standard-library/shared-mutex.md#class_shared_mutex)|Type de mutex partagé qui peut être verrouillé en mode exclusif par un seul agent ou être partagé en mode non exclusif par plusieurs agents.|
|[shared_timed_mutex, classe](../standard-library/shared-mutex.md#class_shared_timed_mutex)|Type de mutex temporisé partagé qui peut être verrouillé en mode exclusif par un seul agent ou être partagé en mode non exclusif par plusieurs agents.|
|[shared_lock, classe](../standard-library/shared-mutex.md#class_shared_lock)|Classe de modèle qui inclut un mutex partagé dans un wrapper pour prendre en charge les opérations de verrouillage temporisées et le partage non exclusif par plusieurs agents.|

|Fonctions|Description|
|---------------|-----------------|
|[swap](../standard-library/shared-mutex.md#function_swap)|Échange le contenu des objets mutex partagé qui sont référencés par les paramètres de la fonction.|

## <a name="syntax"></a>Syntaxe

```cpp
namespace std {
    class shared_mutex;
    class shared_timed_mutex;
    template <class Mutex>
class shared_lock;
    template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
}
```

## <a name="remarks"></a>Notes

Une instance de la classe `shared_mutex` est du *type mutex partagé*, qui est un type utilisé pour contrôler la propriété partagée d’un mutex dans une portée. Le type mutex partagé présente toutes les conditions du type mutex, ainsi que les membres pour prendre en charge la propriété non exclusive partagée.

Le type mutex partagé prend en charge les méthodes supplémentaires `lock_shared`, `unlock_shared` et `try_lock_shared` :

- La méthode `lock_shared` bloque le thread appelant jusqu’à ce que le thread obtienne la propriété partagée du mutex.

- La méthode `unlock_shared` libère la propriété partagée du mutex détenu par le thread appelant.

- La méthode `try_lock_shared` tente d’obtenir la propriété partagée du mutex sans bloquer le thread. Son type de retour est convertible en **bool** et est **true** si la méthode obtient la propriété, mais est sinon **false**.

La classe `shared_timed_mutex` est du *type mutex temporisé partagé*. Ce type remplit les conditions à la fois du type mutex partagé et du type mutex temporisé.

Le type mutex temporisé partagé prend en charge les méthodes supplémentaires `try_lock_shared_for` et `try_lock_shared_until` :

- La méthode `try_lock_shared_for` tente d’obtenir la propriété partagée du mutex jusqu’à ce que la durée spécifiée par le paramètre soit écoulée. Si la durée n’est pas positive, la méthode est équivalente à `try_lock_shared`. La méthode ne retourne pas de valeur dans la durée spécifiée, sauf si elle obtient la propriété partagée. Sa valeur de retour est **true** si la méthode obtient la propriété, mais est sinon **false**.

- La méthode `try_lock_shared_until` tente d’obtenir la propriété partagée du mutex jusqu’à ce que le temps absolu spécifié soit écoulé. Si le temps spécifié est écoulé, la méthode est équivalente à `try_lock_shared`. La méthode ne retourne pas de valeur avant le temps spécifié, sauf si elle obtient la propriété partagée. Sa valeur de retour est **true** si la méthode obtient la propriété, mais est sinon **false**.

La classe de modèle `shared_lock` étend la prise en charge du verrouillage temporisé et du transfert de propriété à un mutex partagé. La propriété du mutex peut être obtenue au moment ou après la construction, et être transférée à un autre objet `shared_lock`. Les objets de type `shared_lock` peuvent être déplacés, mais pas copiés.

> [!WARNING]
> À compter de Visual Studio 2015, les types de synchronisation de bibliothèque C++ Standard sont basés sur les primitives de synchronisation Windows et n’utilisent plus ConcRT (sauf si la plateforme cible est Windows XP). Les types définis dans &lt;shared_mutex > ne doit pas être utilisé avec des fonctions ou types ConcRT.

## <a name="classes"></a>Classes

###  <a name="class_shared_mutex"></a> shared_mutex, classe

La classe `shared_mutex` implémente un mutex non récursif avec une sémantique de propriété partagée.

```cpp
class shared_mutex {
public:
   shared_mutex();
   ~shared_mutex();
   shared_mutex(const shared_mutex&) = delete;
   shared_mutex& operator=(const shared_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   void unlock_shared();
   // Getters
   typedef void** native_handle_type; // implementation defined
   native_handle_type native_handle();
   };
```

###  <a name="class_shared_timed_mutex"></a> shared_timed_mutex, classe

La classe `shared_timed_mutex` implémente un mutex non récursif avec une sémantique de propriété partagée qui remplit les conditions du type mutex temporisé.

```cpp
class shared_timed_mutex {
public:
   shared_timed_mutex();
   ~shared_timed_mutex();
   shared_timed_mutex(const shared_timed_mutex&) = delete;
   shared_timed_mutex& operator=(const shared_timed_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   template <class Rep, class Period>
   bool try_lock_shared_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_shared_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock_shared();
   };
```

###  <a name="&lt;shared"></a> shared_lock, classe

La classe de modèle `shared_lock` contrôle la propriété partagée d’un objet mutex partagé dans une portée. Le paramètre de modèle doit être un type mutex partagé.

```cpp
class shared_lock {
public:
   typedef Mutex mutex_type;
   shared_lock() noexcept;
   explicit shared_lock(mutex_type& m);
   // blocking
   shared_lock(mutex_type& m, defer_lock_t) noexcept;
   shared_lock(mutex_type& m, try_to_lock_t);
   shared_lock(mutex_type& m, adopt_lock_t);
   template <class Clock, class Duration>
   shared_lock(mutex_type& m,
   const chrono::time_point<Clock, Duration>& abs_time);
   template <class Rep, class Period>
   shared_lock(mutex_type& m,
   const chrono::duration<Rep, Period>& rel_time);
   ~shared_lock();
   shared_lock(shared_lock const&) = delete;
   shared_lock& operator=(shared_lock const&) = delete;
   shared_lock(shared_lock&& u) noexcept;
   shared_lock& operator=(shared_lock&& u) noexcept;
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Setters
   void swap(shared_lock& u) noexcept;
   mutex_type* release() noexcept;
   // Getters
   bool owns_lock() const noexcept;
   explicit operator bool () const noexcept;
   mutex_type* mutex() const noexcept;
private:
   mutex_type* pm; // exposition only
   bool owns; // exposition only
   };
```

## <a name="functions"></a>Fonctions

###  <a name="function_swap"></a> échange

Échange les objets `shared_lock`.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

Échange le contenu de deux objets `shared_lock`. Fonctionne comme `x.swap(y)`.

## <a name="requirements"></a>Configuration requise

**En-tête :** &lt;shared_mutex>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[&lt;mutex>](../standard-library/mutex.md)
