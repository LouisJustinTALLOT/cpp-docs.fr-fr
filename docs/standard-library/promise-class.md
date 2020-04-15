---
title: promise, classe
ms.date: 10/18/2018
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.openlocfilehash: a6541fefb2423853f8e59a662e1c8a37777dc14c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323039"
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
|[Promesse](#promise)|Construit un objet `promise`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get_future](#get_future)|Retourne un objet [future](../standard-library/future-class.md) associé à cet objet promise.|
|[set_exception](#set_exception)|Définit atomiquement le résultat de cet objet promise pour indiquer une exception.|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|Définit atomiquement le résultat de cet objet promise pour indiquer une exception, et remet la notification uniquement quand tous les objets locaux de thread dans le thread actuel ont été détruits (généralement à la sortie du thread).|
|[set_value](#set_value)|Définit atomiquement le résultat de cet objet promise pour indiquer une valeur.|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|Définit atomiquement le résultat de cet objet promise pour indiquer une valeur, et remet la notification uniquement quand tous les objets locaux de thread dans le thread actuel ont été détruits (généralement à la sortie du thread).|
|[swap](#swap)|Échange l’*état asynchrone associé* de cet objet promise avec celui d’un objet promise spécifié.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[promesse::opérateur](#op_eq)|Assignation de l’état partagé de cet objet promise.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

*Promesse*

## <a name="requirements"></a>Spécifications

**En-tête:** \<future>

**Espace de noms :** std

## <a name="promiseget_future"></a><a name="get_future"></a>promesse::get_future

Retourne un objet [future](../standard-library/future-class.md) qui a le même *état asynchrone associé* que cet objet promise.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Notes

Si l’objet promise est vide, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code [error_code](../standard-library/error-code-class.md)`no_state`.

Si cette méthode a déjà été appelée pour un objet promise ayant le même état asynchrone associé, la méthode lève une exception `future_error` avec le code `error_code``future_already_retrieved`.

## <a name="promiseoperator"></a><a name="op_eq"></a>promesse::opérateur

Transfère l’*état asynchrone associé* à partir d’un objet `promise` spécifié.

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

*Autres*\
Objet `promise` .

### <a name="return-value"></a>Valeur de retour

`*this`

### <a name="remarks"></a>Notes

Cet opérateur transfère l’état asynchrone associé *d’Autres*. Après le transfert, *l’autre* est *vide*.

## <a name="promisepromise-constructor"></a><a name="promise"></a>promesse::promise Constructor

Construit un objet `promise`.

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

*Al*\
Allocateur de mémoire. Voir [ \<les allocataires>](../standard-library/allocators-header.md) pour plus d’informations.

*Autres*\
Objet `promise` .

### <a name="remarks"></a>Notes

Le premier constructeur construit un objet *vide.* `promise`

Le deuxième constructeur construit `promise` un objet vide et utilise *Al* pour l’allocation de mémoire.

Le troisième constructeur construit `promise` un objet et transfère l’état asynchrone associé *d’autres,* et laisse *l’autre* vide.

## <a name="promiseset_exception"></a><a name="set_exception"></a>promesse::set_exception

Stocke atomiquement une exception comme résultat de cet objet `promise` et définit l’*état asynchrone associé* sur *ready*.

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>Paramètres

*Exc (en anglais)*\
[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) qui est stocké par cette méthode comme résultat de l’exception.

### <a name="remarks"></a>Notes

Si l’objet `promise` n’a pas d’état asynchrone associé, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si la méthode `set_exception`, [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) ou [set_value_at_thread_exit](#set_value_at_thread_exit) a déjà été appelée pour un objet `promise` ayant le même état asynchrone associé, cette méthode lève une exception `future_error` avec le code d’erreur `promise_already_satisfied`.

Cette méthode libère tous les threads qui sont bloqués sur l’état asynchrone associé.

## <a name="promiseset_exception_at_thread_exit"></a><a name="set_exception_at_thread_exit"></a>promesse::set_exception_at_thread_exit

Définit atomiquement le résultat de cet objet `promise` pour indiquer une exception, et remet la notification uniquement quand tous les objets locaux de thread dans le thread actuel ont été détruits (généralement à la sortie du thread).

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>Paramètres

*Exc (en anglais)*\
[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) qui est stocké par cette méthode comme résultat de l’exception.

### <a name="remarks"></a>Notes

Si l’objet promise n’a pas d’*état asynchrone associé*, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si [set_exception](#set_exception), `set_exception_at_thread_exit`, [set_value](#set_value), ou [set_value_at_thread_exit](#set_value_at_thread_exit) a déjà été `promise` appelé pour un objet qui a le même état `future_error` asynchrone associé, cette méthode jette un qui a un code d’erreur de `promise_already_satisfied`.

Contrairement à [set_exception](#set_exception), cette méthode ne définit pas l’état asynchrone associé sur ready tant que les objets locaux de thread dans le thread actuel n’ont pas tous été détruits. En règle générale, les threads qui sont bloqués sur l’état asynchrone associé sont libérés seulement au moment de la sortie du thread actuel.

## <a name="promiseset_value"></a><a name="set_value"></a>promesse::set_value

Stocke atomiquement une valeur comme résultat de cet objet `promise` et définit l’*état asynchrone associé* sur *ready*.

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>Paramètres

*Val*\
Valeur à stocker comme résultat.

### <a name="remarks"></a>Notes

Si l’objet `promise` n’a pas d’état asynchrone associé, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si la méthode [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), `set_value` ou [set_value_at_thread_exit](#set_value_at_thread_exit) a déjà été appelée pour un objet `promise` ayant le même état asynchrone associé, cette méthode lève une exception `future_error` avec le code d’erreur `promise_already_satisfied`.

Cette méthode libère tous les threads qui sont bloqués sur l’état asynchrone associé.

La première méthode jette également toute exception qui est jetée lorsque *Val* est copié dans l’état asynchrone associé. Dans ce cas, l’état asynchrone associé n’est pas défini sur ready.

La deuxième méthode jette également toute exception qui est jetée lorsque *Val* est déplacé dans l’état asynchrone associé. Dans ce cas, l’état asynchrone associé n’est pas défini sur ready.

Pour la spécialisation `promise<Ty&>`partielle, la valeur stockée est en fait une référence à *Val*.

Pour la spécialisation `promise<void>`, aucune valeur stockée n’existe.

## <a name="promiseset_value_at_thread_exit"></a><a name="set_value_at_thread_exit"></a>promesse::set_value_at_thread_exit

Stocke atomiquement une valeur comme résultat de cet objet `promise`.

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>Paramètres

*Val*\
Valeur à stocker comme résultat.

### <a name="remarks"></a>Notes

Si l’objet promise n’a pas d’*état asynchrone associé*, cette méthode lève une exception [future_error](../standard-library/future-error-class.md) avec le code d’erreur `no_state`.

Si la méthode [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) ou `set_value_at_thread_exit` a déjà été appelée pour un objet `promise` ayant le même état asynchrone associé, cette méthode lève une exception `future_error` avec le code d’erreur `promise_already_satisfied`.

Contrairement à `set_value`, l’état asynchrone associé n’est pas défini sur ready tant que les objets locaux de thread dans le thread actuel n’ont pas tous été détruits. En règle générale, les threads qui sont bloqués sur l’état asynchrone associé sont libérés seulement au moment de la sortie du thread actuel.

La première méthode jette également toute exception qui est jetée lorsque *Val* est copié dans l’état asynchrone associé.

La deuxième méthode jette également toute exception qui est jetée lorsque *Val* est déplacé dans l’état asynchrone associé.

Pour la spécialisation `promise<Ty&>`partielle, la valeur stockée est effectivement une référence à *Val*.

Pour la spécialisation `promise<void>`, aucune valeur stockée n’existe.

## <a name="promiseswap"></a><a name="swap"></a>promesse::swap

Échange l’*état asynchrone associé* de cet objet promise avec celui d’un objet spécifié.

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

*Autres*\
Objet `promise` .

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
