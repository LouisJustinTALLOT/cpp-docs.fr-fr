---
title: promise, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
dev_langs:
- C++
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.workload:
- cplusplus
ms.openlocfilehash: 8a1ddfd30a1e061426f0a19ac1118aa5ade1de17
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958551"
---
# <a name="promise-class"></a>promise, classe

Décrit un *fournisseur asynchrone*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class promise;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[promesse](#promise)|Construit un objet `promise`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_future](#get_future)|Retourne un objet [future](../standard-library/future-class.md) associé à cet objet promise.|
|[set_exception](#set_exception)|Définit atomiquement le résultat de cet objet promise pour indiquer une exception.|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|Définit atomiquement le résultat de cet objet promise pour indiquer une exception, et remet la notification uniquement quand tous les objets locaux de thread dans le thread actuel ont été détruits (généralement à la sortie du thread).|
|[set_value](#set_value)|Définit atomiquement le résultat de cet objet promise pour indiquer une valeur.|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|Définit atomiquement le résultat de cet objet promise pour indiquer une valeur, et remet la notification uniquement quand tous les objets locaux de thread dans le thread actuel ont été détruits (généralement à la sortie du thread).|
|[swap](#swap)|Échange l’*état asynchrone associé* de cet objet promise avec celui d’un objet promise spécifié.|

### <a name="public-operators"></a>Opérateurs publics

|Nom|Description|
|----------|-----------------|
|[promise::operator=](#op_eq)|Assignation de l’état partagé de cet objet promise.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`promise`

## <a name="requirements"></a>Configuration requise

**En-tête :** \<future >

**Espace de noms :** std

## <a name="get_future"></a>  promise::get_future

Retourne un objet [future](../standard-library/future-class.md) qui a le même *état asynchrone associé* que cet objet promise.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Notes

Si l’objet promise est vide, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code [error_code](../standard-library/error-code-class.md) `no_state`.

Si cette méthode a déjà été appelée pour un objet promise ayant le même état asynchrone associé, la méthode lève une exception `future_error` avec le code `error_code` `future_already_retrieved`.

## <a name="op_eq"></a>  promise::operator=

Transfère l’*état asynchrone associé* à partir d’un objet `promise` spécifié.

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

*Autres* A `promise` objet.

### <a name="return-value"></a>Valeur de retour

`*this`

### <a name="remarks"></a>Notes

Cet opérateur transfère l’état asynchrone associé à partir de *autres*. Après le transfert, *autres* est *vide*.

## <a name="promise"></a>  promise::promise, constructeur

Construit un objet `promise`.

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

*Al* un allocateur de mémoire. Pour plus d’informations, consultez [\<allocators>](../standard-library/allocators-header.md).

*Autres* A `promise` objet.

### <a name="remarks"></a>Notes

Le premier constructeur construit un objet `promise` *vide*.

Le deuxième constructeur construit un vide `promise` objet et utilise *Al* pour l’allocation de mémoire.

Le troisième constructeur construit un `promise` de l’objet et transfère l’état asynchrone associé à partir de *autres*et laisse *autres* vide.

## <a name="set_exception"></a>  promise::set_exception

Stocke atomiquement une exception comme résultat de cet objet `promise` et définit l’*état asynchrone associé* sur *ready*.

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>Paramètres

*Exc* un [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) qui est stocké par cette méthode en tant que résultat de l’exception.

### <a name="remarks"></a>Notes

Si l’objet `promise` n’a pas d’état asynchrone associé, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si la méthode `set_exception`, [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) ou [set_value_at_thread_exit](#set_value_at_thread_exit) a déjà été appelée pour un objet `promise` ayant le même état asynchrone associé, cette méthode lève une exception `future_error` avec le code d’erreur `promise_already_satisfied`.

Cette méthode libère tous les threads qui sont bloqués sur l’état asynchrone associé.

## <a name="set_exception_at_thread_exit"></a>  promise::set_exception_at_thread_exit

Définit atomiquement le résultat de cet objet `promise` pour indiquer une exception, et remet la notification uniquement quand tous les objets locaux de thread dans le thread actuel ont été détruits (généralement à la sortie du thread).

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>Paramètres

*Exc* un [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) qui est stocké par cette méthode en tant que résultat de l’exception.

### <a name="remarks"></a>Notes

Si l’objet promise n’a pas d’*état asynchrone associé*, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si la méthode [set_exception](#set_exception), `set_exception_at_thread_exit`, [set_value](#set_value) ou [set_value_at_thread_exit](#set_value_at_thread_exit) a déjà été appelée pour un objet `promise` ayant le même état asynchrone associé, cette méthode lève une exception `future_error` avec le code d’erreur `promise_already_satisfied`.

Contrairement à [set_exception](#set_exception), cette méthode ne définit pas l’état asynchrone associé sur ready tant que les objets locaux de thread dans le thread actuel n’ont pas tous été détruits. En règle générale, les threads qui sont bloqués sur l’état asynchrone associé sont libérés seulement au moment de la sortie du thread actuel.

## <a name="set_value"></a>  promise::set_value

Stocke atomiquement une valeur comme résultat de cet objet `promise` et définit l’*état asynchrone associé* sur *ready*.

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>Paramètres

*Val* la valeur à stocker comme résultat.

### <a name="remarks"></a>Notes

Si l’objet `promise` n’a pas d’état asynchrone associé, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si la méthode [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), `set_value` ou [set_value_at_thread_exit](#set_value_at_thread_exit) a déjà été appelée pour un objet `promise` ayant le même état asynchrone associé, cette méthode lève une exception `future_error` avec le code d’erreur `promise_already_satisfied`.

Cette méthode libère tous les threads qui sont bloqués sur l’état asynchrone associé.

La première méthode lève également toute exception qui est levée lorsque *Val* est copié dans l’état asynchrone associé. Dans ce cas, l’état asynchrone associé n’est pas défini sur ready.

La deuxième méthode lève également toute exception qui est levée lorsque *Val* est déplacé vers l’état asynchrone associé. Dans ce cas, l’état asynchrone associé n’est pas défini sur ready.

Pour la spécialisation partielle `promise<Ty&>`, la valeur stockée est en vigueur une référence à *Val*.

Pour la spécialisation `promise<void>`, aucune valeur stockée n’existe.

## <a name="set_value_at_thread_exit"></a>  promise::set_value_at_thread_exit

Stocke atomiquement une valeur comme résultat de cet objet `promise`.

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>Paramètres

*Val* la valeur à stocker comme résultat.

### <a name="remarks"></a>Notes

Si l’objet promise n’a pas d’*état asynchrone associé*, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si la méthode [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) ou `set_value_at_thread_exit` a déjà été appelée pour un objet `promise` ayant le même état asynchrone associé, cette méthode lève une exception `future_error` avec le code d’erreur `promise_already_satisfied`.

Contrairement à `set_value`, l’état asynchrone associé n’est pas défini sur ready tant que les objets locaux de thread dans le thread actuel n’ont pas tous été détruits. En règle générale, les threads qui sont bloqués sur l’état asynchrone associé sont libérés seulement au moment de la sortie du thread actuel.

La première méthode lève également toute exception qui est levée lorsque *Val* est copié dans l’état asynchrone associé.

La deuxième méthode lève également toute exception qui est levée lorsque *Val* est déplacé vers l’état asynchrone associé.

Pour la spécialisation partielle `promise<Ty&>`, la valeur stockée est une référence à *Val*.

Pour la spécialisation `promise<void>`, aucune valeur stockée n’existe.

## <a name="swap"></a>  promise::swap

Échange l’*état asynchrone associé* de cet objet promise avec celui d’un objet spécifié.

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

*Autres* A `promise` objet.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
