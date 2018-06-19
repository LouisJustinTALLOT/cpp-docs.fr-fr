---
title: thread, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- thread/std::thread
- thread/std::thread::id Class
- thread/std::thread::thread
- thread/std::thread::detach
- thread/std::thread::get_id
- thread/std::thread::hardware_concurrency
- thread/std::thread::join
- thread/std::thread::joinable
- thread/std::thread::native_handle
- thread/std::thread::swap
dev_langs:
- C++
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::thread [C++]
- std::thread [C++], thread
- std::thread [C++], detach
- std::thread [C++], get_id
- std::thread [C++], hardware_concurrency
- std::thread [C++], join
- std::thread [C++], joinable
- std::thread [C++], native_handle
- std::thread [C++], swap
ms.workload:
- cplusplus
ms.openlocfilehash: bfcb554b374d035e85d53d769d04317e52e4193b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861121"
---
# <a name="thread-class"></a>thread, classe

Définit un objet qui sert à observer et à gérer un thread d’exécution dans une application.

## <a name="syntax"></a>Syntaxe

```cpp
class thread;
```

## <a name="remarks"></a>Notes

Vous pouvez utiliser un objet `thread` pour observer et gérer un thread d’exécution dans une application. Un objet thread qui est créé à l’aide du constructeur par défaut n’est associé à aucun thread d’exécution. Un objet thread qui est construit à l’aide d’un objet joignable crée un nouveau thread d’exécution et appelle l’objet joignable dans ce thread. Les objets thread peuvent être déplacés mais pas copiés. Par conséquent, un thread d’exécution peut être associé à un seul objet thread.

Chaque thread d’exécution possède un identificateur unique de type `thread::id`. La fonction `this_thread::get_id` retourne l’identificateur du thread appelant. La fonction membre `thread::get_id` retourne l’identificateur du thread qui est géré par un objet thread. Pour un objet thread construit par défaut, la méthode `thread::get_id` retourne un objet qui a une valeur identique pour tous les objets thread construits par défaut et différente de la valeur retournée par `this_thread::get_id` pour n’importe quel thread d’exécution qui pouvait être joint au moment de l’appel.

## <a name="members"></a>Membres

### <a name="public-classes"></a>Classes publiques

|Nom|Description|
|----------|-----------------|
|[thread::id, classe](#id_class)|Identifie de façon unique le thread associé.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[thread](#thread)|Construit un objet `thread`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[detach](#detach)|Détache le thread associé de l’objet `thread`.|
|[get_id](#get_id)|Retourne l’identificateur unique du thread associé.|
|[hardware_concurrency](#hardware_concurrency)|Static. Retourne une estimation du nombre de contextes de thread matériel.|
|[join](#join)|Bloque jusqu’à ce que le thread associé soit terminé.|
|[joignable](#joinable)|Spécifie si le thread associé est joignable.|
|[native_handle](#native_handle)|Retourne le type propre à l’implémentation qui représente le descripteur de thread.|
|[swap](#swap)|Permute l’état de l’objet avec un objet `thread` spécifié.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[thread::operator=](#op_eq)|Associe un thread avec l’objet `thread` en cours.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<thread >

**Espace de noms :** std

## <a name="detach"></a>  thread::detach

Détache le thread associé. Le système d’exploitation devient responsable de la libération des ressources de thread lors d’un arrêt.

```cpp
void detach();
```

### <a name="remarks"></a>Notes

Après un appel à `detach`, les appels suivants à [get_id](#get_id) retournent [id](#id_class).

Si le thread qui est associé à l’objet appelant n’est pas joignable, la fonction lève un objet [system_error](../standard-library/system-error-class.md) doté du code d’erreur `invalid_argument`.

Si le thread qui est associé à l’objet appelant est non valide, la fonction lève un objet `system_error` dotée du code d’erreur `no_such_process`.

## <a name="get_id"></a>  thread::get_id

Retourne un identificateur unique du thread associé.

```cpp
id get_id() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

Un objet [thread::id](#id_class) qui identifie de façon unique le thread associé, ou `thread::id()` si aucun thread n’est associé à l’objet.

## <a name="hardware_concurrency"></a>  thread::hardware_concurrency

Méthode statique qui retourne une estimation du nombre de contextes de thread matériel.

```cpp
static unsigned int hardware_concurrency() noexcept;
```

### <a name="return-value"></a>Valeur de retour

Une estimation du nombre de contextes de thread matériel. Si la valeur ne peut pas être calculée ou n’est pas bien définie, cette méthode retourne 0.

## <a name="id_class"></a>  thread::id, classe

Fournit un identificateur unique pour chaque thread d’exécution dans le processus.

```cpp
class thread::id {
    id() noexcept;
};
```

### <a name="remarks"></a>Notes

Le constructeur par défaut crée un objet qui n’est pas considéré comme égal à l’objet `thread::id` pour n’importe quel thread existant.

Tous les objets `thread::id` construits par défaut sont considérés comme égaux.

## <a name="join"></a>  thread::Join

Bloque jusqu’à ce que le thread d’exécution associé à l’objet appelant soit terminé.

```cpp
void join();
```

### <a name="remarks"></a>Notes

Si l’appel réussit, les appels suivants à [get_id](#get_id) pour l’objet appelant retournent un [thread::id](#id_class) par défaut qui n’est pas considéré comme égal au `thread::id` de n’importe quel thread existant ; si l’appel n’aboutit pas, la valeur retournée par `get_id` est inchangée.

## <a name="joinable"></a>  thread::joinable

Spécifie si le thread associé est *joignable*.

```cpp
bool joinable() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

`true` si le thread associé est *joignable* ; sinon, `false`.

### <a name="remarks"></a>Notes

Un objet thread est *joignable* si `get_id() != id()`.

## <a name="native_handle"></a>  thread::native_handle

Retourne le type propre à l’implémentation qui représente le descripteur de thread. Vous pouvez utiliser le descripteur de thread de plusieurs manières propres à l’implémentation.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Valeur de retour

`native_handle_type` est défini comme un `HANDLE` Win32 converti en `void *`.

## <a name="op_eq"></a>  thread::operator=

Associe le thread d’un objet spécifié à l’objet en cours.

```cpp
thread& operator=(thread&& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

`Other` A `thread` objet.

### <a name="return-value"></a>Valeur de retour

`*this`

### <a name="remarks"></a>Notes

La méthode appelle detach si l’objet appelant est joignable.

Une fois l’association établie, `Other` est défini à un état construit par défaut.

## <a name="swap"></a>  thread::swap

Permute l’état de l’objet avec celui d’un objet `thread` spécifié.

```cpp
void swap(thread& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

`Other` A `thread` objet.

## <a name="thread"></a>  thread::thread, constructeur

Construit un objet `thread`.

```cpp
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

`F` Une fonction définie par l’application doit être exécutée par le thread.

`A` Une liste d’arguments à passer au `F`.

`Other` Existant `thread` objet.

### <a name="remarks"></a>Notes

Le premier constructeur construit un objet qui n’est pas associé à un thread d’exécution. La valeur retournée par un appel à `get_id` pour l’objet construit est `thread::id()`.

Le deuxième constructeur construit un objet qui est associé à un nouveau thread d’exécution et exécute la pseudo-fonction `INVOKE` qui est définie dans [\<functional>](../standard-library/functional.md). Si des ressources insuffisantes sont disponibles pour démarrer un nouveau thread, la fonction lève un objet [system_error](../standard-library/system-error-class.md) doté du code d’erreur `resource_unavailable_try_again`. Si l’appel à `F` se termine avec une exception non interceptée, la fonction [terminate](../standard-library/exception-functions.md#terminate) est appelée.

Le troisième constructeur construit un objet associé au thread qui est associé à `Other`. `Other` est ensuite défini à un état construit par défaut.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<thread>](../standard-library/thread.md)<br/>
