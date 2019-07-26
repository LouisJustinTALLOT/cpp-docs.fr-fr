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
ms.openlocfilehash: 5bb04b84b723f239c338c02befa8cd3468cec3f2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450081"
---
# <a name="packagedtask-class"></a>packaged_task, classe

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
|[packaged_task::~packaged_task, destructeur](#dtorpackaged_task_destructor)|Détruit un objet `packaged_task`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_future](#get_future)|Retourne un objet [future](../standard-library/future-class.md) qui a le même état asynchrone associé.|
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|Appelle l’objet pouvant être appelé qui est stocké dans l’état asynchrone associé et stocke atomiquement la valeur retournée.|
|[reset](#reset)|Remplace l’état asynchrone associé.|
|[swap](#swap)|Échange l’état asynchrone associé avec celui d’un objet spécifié.|
|[valid](#valid)|Spécifie si l’objet a un état asynchrone associé.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[packaged_task::operator=](#op_eq)|Transfère un état asynchrone associé à partir d’un objet spécifié.|
|[packaged_task::operator()](#op_call)|Appelle l’objet pouvant être appelé qui est stocké dans l’état asynchrone associé, stocke atomiquement la valeur retournée et définit l’état sur *ready*.|
|[packaged_task::operator bool](#op_bool)|Spécifie si l’objet a un état asynchrone associé.|

## <a name="requirements"></a>Configuration requise

**En-tête:** \<> à venir

**Espace de noms :** std

## <a name="get_future"></a>  packaged_task::get_future

Retourne un objet de type `future<Ty>` qui a le même *état asynchrone associé*.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Notes

Si l’objet `packaged_task` n’a pas d’état asynchrone associé, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si cette méthode a déjà été appelée pour un objet `packaged_task` ayant le même état asynchrone associé, la méthode lève une exception `future_error` avec le code d’erreur `future_already_retrieved`.

## <a name="make_ready_at_thread_exit"></a>  packaged_task::make_ready_at_thread_exit

Appelle l’objet pouvant être appelé qui est stocké dans l’*état asynchrone associé* et stocke atomiquement la valeur retournée.

```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

### <a name="remarks"></a>Notes

Si l’objet `packaged_task` n’a pas d’état asynchrone associé, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si cette méthode ou [make_ready_at_thread_exit](#make_ready_at_thread_exit) a déjà été appelée pour un objet `packaged_task` ayant le même état asynchrone associé, la méthode lève une exception `future_error` avec le code d’erreur `promise_already_satisfied`.

Sinon, cet opérateur appelle `INVOKE(fn, args..., Ty)`, où *fn* est l’objet pouvant être appelé qui est stocké dans l’état asynchrone associé. Chaque valeur retournée est stockée atomiquement comme résultat retourné de l’état asynchrone associé.

Contrairement à [packaged_task::operator()](#op_call), l’état asynchrone associé n’est pas défini à `ready` tant que les objets locaux de thread dans le thread appelant n’ont pas tous été détruits. En règle générale, les threads qui sont bloqués sur l’état asynchrone associé sont libérés seulement au moment de la sortie du thread appelant.

## <a name="op_eq"></a>  packaged_task::operator=

Transfère l’*état asynchrone associé* à partir d’un objet spécifié.

```cpp
packaged_task& operator=(packaged_task&& Right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet `packaged_task`.

### <a name="return-value"></a>Valeur de retour

`*this`

### <a name="remarks"></a>Notes

Après l’opération, *le droit* n’est plus associé à un état asynchrone.

## <a name="op_call"></a>  packaged_task::operator()

Appelle l’objet pouvant être appelé qui est stocké dans l’*état asynchrone associé*, stocke atomiquement la valeur retournée et définit l’état sur *ready*.

```cpp
void operator()(ArgTypes... args);
```

### <a name="remarks"></a>Notes

Si l’objet `packaged_task` n’a pas d’état asynchrone associé, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si cette méthode ou [make_ready_at_thread_exit](#make_ready_at_thread_exit) a déjà été appelée pour un objet `packaged_task` ayant le même état asynchrone associé, la méthode lève une exception `future_error` avec le code d’erreur `promise_already_satisfied`.

Sinon, cet opérateur appelle `INVOKE(fn, args..., Ty)`, où *fn* est l’objet pouvant être appelé qui est stocké dans l’état asynchrone associé. Chaque valeur retournée est stockée atomiquement comme résultat retourné de l’état asynchrone associé, et l’état est défini sur ready. Tous les threads qui sont bloqués sur l’état asynchrone associé sont alors libérés.

## <a name="op_bool"></a>  packaged_task::operator bool

Spécifie si l’objet a un `associated asynchronous state`.

```cpp
operator bool() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

**true** si l’objet a un état asynchrone associé; Sinon, **false**.

## <a name="packaged_task"></a>  packaged_task::packaged_task, constructeur

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
Objet `packaged_task`.

*utilis*\
Allocateur de mémoire. Pour plus d’informations, consultez [\<allocators>](../standard-library/allocators-header.md).

*FN*\
Objet de fonction.

### <a name="remarks"></a>Notes

Le premier constructeur construit un objet `packaged_task` sans *état asynchrone associé*.

Le deuxième constructeur construit un `packaged_task` objet et transfère l’état asynchrone associé à partir de la *droite*. Après l’opération, *le droit* n’est plus associé à un état asynchrone.

Le troisième constructeur construit un `packaged_task` objet qui a une copie de *FN* stockée dans son état asynchrone associé.

Le quatrième constructeur construit un `packaged_task` objet qui a une copie de *FN* stockée dans son état asynchrone associé et utilise `alloc` pour l’allocation de mémoire.

## <a name="dtorpackaged_task_destructor"></a>  packaged_task::~packaged_task, destructeur

Détruit un objet `packaged_task`.

```cpp
~packaged_task();
```

### <a name="remarks"></a>Notes

Si l’*état asynchrone associé* n’est pas défini sur *ready*, le destructeur stocke une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `broken_promise` comme résultat dans l’état asynchrone associé, et les threads qui sont bloqués sur l’état asynchrone associé sont libérés.

## <a name="reset"></a>  packaged_task::reset

Remplace l’état asynchrone associé existant par un nouvel *état asynchrone associé*.

```cpp
void reset();
```

### <a name="remarks"></a>Notes

En effet, cette méthode exécute `*this = packaged_task(move(fn))`, où *fn* est l’objet de fonction qui est stocké dans l’état asynchrone associé pour cet objet. Par conséquent, l’état de l’objet est effacé, et les méthodes [get_future](#get_future), [operator()](#op_call) et [make_ready_at_thread_exit](#make_ready_at_thread_exit) peuvent être appelées de la même manière que pour un nouvel objet construit.

## <a name="swap"></a>  packaged_task::swap

Échange l’état asynchrone associé avec celui d’un objet spécifié.

```cpp
void swap(packaged_task& Right) noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet `packaged_task`.

## <a name="valid"></a>  packaged_task::valid

Spécifie si l’objet a un `associated asynchronous state`.

```cpp
bool valid() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si l’objet a un état asynchrone associé; Sinon, **false**.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
