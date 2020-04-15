---
title: packaged_task, classe
ms.date: 11/04/2016
f1_keywords:
- future/std::packaged_task
- future/std::packaged_task::packaged_task
- future/std::packaged_task::get_future
- future/std::packaged_task::make_ready_at_thread_exit
- future/std::packaged_task::reset
- future/std::packaged_task::swap
- future/std::packaged_task::valid
- future/std::packaged_task::operator()
- future/std::packaged_task::operator bool
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
helpviewer_keywords:
- std::packaged_task [C++]
- std::packaged_task [C++], packaged_task
- std::packaged_task [C++], get_future
- std::packaged_task [C++], make_ready_at_thread_exit
- std::packaged_task [C++], reset
- std::packaged_task [C++], swap
- std::packaged_task [C++], valid
ms.openlocfilehash: eb171e09451e16e89716dfdc44ed6c611e2d2280
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372124"
---
# <a name="packaged_task-class"></a>packaged_task, classe

Décrit un *fournisseur asynchrone* qui est un wrapper d’appel dont la signature d’appel est `Ty(ArgTypes...)`. Son *état asynchrone associé* contient une copie de l’objet pouvant être appelé, ainsi que le résultat potentiel.

## <a name="syntax"></a>Syntaxe

```cpp
template <class>
class packaged_task;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[packaged_task](#packaged_task)|Construit un objet `packaged_task`.|
|[packaged_task: Packaged_task Destructor](#dtorpackaged_task_destructor)|Détruit un objet `packaged_task` .|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_future](#get_future)|Retourne un objet [future](../standard-library/future-class.md) qui a le même état asynchrone associé.|
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|Appelle l’objet pouvant être appelé qui est stocké dans l’état asynchrone associé et stocke atomiquement la valeur retournée.|
|[Réinitialiser](#reset)|Remplace l’état asynchrone associé.|
|[swap](#swap)|Échange l’état asynchrone associé avec celui d’un objet spécifié.|
|[Valide](#valid)|Spécifie si l’objet a un état asynchrone associé.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[packaged_task::opérateur](#op_eq)|Transfère un état asynchrone associé d’un objet spécifié.|
|[packaged_task::opérateur()](#op_call)|Appelle l’objet pouvant être appelé qui est stocké dans l’état asynchrone associé, stocke atomiquement la valeur retournée et définit l’état sur *ready*.|
|[packaged_task::operator bool](#op_bool)|Spécifie si l’objet a un état asynchrone associé.|

## <a name="requirements"></a>Spécifications

**En-tête:** \<future>

**Espace de noms :** std

## <a name="packaged_taskget_future"></a><a name="get_future"></a>packaged_task::get_future

Retourne un objet de type `future<Ty>` qui a le même *état asynchrone associé*.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Notes

Si l’objet `packaged_task` n’a pas d’état asynchrone associé, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si cette méthode a déjà été appelée pour un objet `packaged_task` ayant le même état asynchrone associé, la méthode lève une exception `future_error` avec le code d’erreur `future_already_retrieved`.

## <a name="packaged_taskmake_ready_at_thread_exit"></a><a name="make_ready_at_thread_exit"></a>packaged_task::make_ready_at_thread_exit

Appelle l’objet pouvant être appelé qui est stocké dans l’*état asynchrone associé* et stocke atomiquement la valeur retournée.

```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

### <a name="remarks"></a>Notes

Si l’objet `packaged_task` n’a pas d’état asynchrone associé, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si cette méthode ou [make_ready_at_thread_exit](#make_ready_at_thread_exit) a déjà été appelée pour un objet `packaged_task` ayant le même état asynchrone associé, la méthode lève une exception `future_error` avec le code d’erreur `promise_already_satisfied`.

Sinon, cet opérateur appelle `INVOKE(fn, args..., Ty)`, où *fn* est l’objet pouvant être appelé qui est stocké dans l’état asynchrone associé. Chaque valeur retournée est stockée atomiquement comme résultat retourné de l’état asynchrone associé.

Contrairement à [packaged_task::operator()](#op_call), l’état asynchrone associé n’est pas défini à `ready` tant que les objets locaux de thread dans le thread appelant n’ont pas tous été détruits. En règle générale, les threads qui sont bloqués sur l’état asynchrone associé sont libérés seulement au moment de la sortie du thread appelant.

## <a name="packaged_taskoperator"></a><a name="op_eq"></a>packaged_task::opérateur

Transfère *l’état asynchrone associé* à partir d’un objet spécifié.

```cpp
packaged_task& operator=(packaged_task&& Right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet `packaged_task` .

### <a name="return-value"></a>Valeur de retour

`*this`

### <a name="remarks"></a>Notes

Après l’opération, *Right n’a* plus d’état asynchrone associé.

## <a name="packaged_taskoperator"></a><a name="op_call"></a>packaged_task::opérateur()

Appelle l’objet callable qui est stocké dans *l’état asynchrone associé*, stocke atomiquement la valeur retournée, et met l’état à *prêt*.

```cpp
void operator()(ArgTypes... args);
```

### <a name="remarks"></a>Notes

Si l’objet `packaged_task` n’a pas d’état asynchrone associé, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si cette méthode ou [make_ready_at_thread_exit](#make_ready_at_thread_exit) a déjà été appelée pour un objet `packaged_task` ayant le même état asynchrone associé, la méthode lève une exception `future_error` avec le code d’erreur `promise_already_satisfied`.

Sinon, cet opérateur appelle `INVOKE(fn, args..., Ty)`, où *fn* est l’objet pouvant être appelé qui est stocké dans l’état asynchrone associé. Chaque valeur retournée est stockée atomiquement comme résultat retourné de l’état asynchrone associé, et l’état est défini sur ready. Tous les threads qui sont bloqués sur l’état asynchrone associé sont alors libérés.

## <a name="packaged_taskoperator-bool"></a><a name="op_bool"></a>packaged_task::opérateur bool

Spécifie si l’objet a un `associated asynchronous state`.

```cpp
operator bool() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

**vrai** si l’objet a un état asynchrone associé; autrement, **faux**.

## <a name="packaged_taskpackaged_task-constructor"></a><a name="packaged_task"></a>packaged_task::p-constructeur de tâches

Construit un objet `packaged_task`.

```cpp
packaged_task() noexcept;
packaged_task(packaged_task&& Right) noexcept;
template <class Fn>
   explicit packaged_task(Fn&& fn);

template <class Fn, class Alloc>
   explicit packaged_task(
      allocator_arg_t, const Alloc& alloc, Fn&& fn);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet `packaged_task` .

*Alloc*\
Allocateur de mémoire. Pour plus d’informations, voir [ \<les allocataires>](../standard-library/allocators-header.md).

*Fn*\
Objet de fonction.

### <a name="remarks"></a>Notes

Le premier constructeur construit `packaged_task` un objet qui n’a pas *d’état asynchrone associé.*

Le deuxième constructeur construit `packaged_task` un objet et transfère l’état asynchrone associé de *droite*. Après l’opération, *Right n’a* plus d’état asynchrone associé.

Le troisième constructeur construit `packaged_task` un objet qui a une copie de *fn* stockée dans son état asynchrone associé.

Le quatrième constructeur construit `packaged_task` un objet qui a une copie de *fn* stockée dans `alloc` son état asynchrone associé, et utilise pour l’allocation de mémoire.

## <a name="packaged_taskpackaged_task-destructor"></a><a name="dtorpackaged_task_destructor"></a>packaged_task: Packaged_task Destructor

Détruit un objet `packaged_task` .

```cpp
~packaged_task();
```

### <a name="remarks"></a>Notes

Si l’*état asynchrone associé* n’est pas défini sur *ready*, le destructeur stocke une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `broken_promise` comme résultat dans l’état asynchrone associé, et les threads qui sont bloqués sur l’état asynchrone associé sont libérés.

## <a name="packaged_taskreset"></a><a name="reset"></a>packaged_task::reset

Remplace l’état asynchrone associé existant par un nouvel *état asynchrone associé*.

```cpp
void reset();
```

### <a name="remarks"></a>Notes

En effet, cette méthode exécute `*this = packaged_task(move(fn))`, où *fn* est l’objet de fonction qui est stocké dans l’état asynchrone associé pour cet objet. Par conséquent, l’état de l’objet est effacé, et les méthodes [get_future](#get_future), [operator()](#op_call) et [make_ready_at_thread_exit](#make_ready_at_thread_exit) peuvent être appelées de la même manière que pour un nouvel objet construit.

## <a name="packaged_taskswap"></a><a name="swap"></a>packaged_task::swap

Échange l’état asynchrone associé avec celui d’un objet spécifié.

```cpp
void swap(packaged_task& Right) noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet `packaged_task` .

## <a name="packaged_taskvalid"></a><a name="valid"></a>packaged_task::valide

Spécifie si l’objet a un `associated asynchronous state`.

```cpp
bool valid() const;
```

### <a name="return-value"></a>Valeur de retour

**vrai** si l’objet a un état asynchrone associé; autrement, **faux**.

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<>avenir](../standard-library/future.md)
