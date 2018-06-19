---
title: '&lt;atomic&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- atomic/std::atomic_compare_exchange_strong
- atomic/std::atomic_compare_exchange_strong_explicit
- atomic/std::atomic_compare_exchange_weak
- atomic/std::atomic_compare_exchange_weak_explicit
- atomic/std::atomic_exchange
- atomic/std::atomic_exchange_explicit
- atomic/std::atomic_fetch_add
- atomic/std::atomic_fetch_add_explicit
- atomic/std::atomic_fetch_and
- atomic/std::atomic_fetch_and_explicit
- atomic/std::atomic_fetch_or
- atomic/std::atomic_fetch_or_explicit
- atomic/std::atomic_fetch_sub
- atomic/std::atomic_fetch_sub_explicit
- atomic/std::atomic_fetch_xor
- atomic/std::atomic_fetch_xor_explicit
- atomic/std::atomic_flag_clear
- atomic/std::atomic_flag_clear_explicit
- atomic/std::atomic_flag_test_and_set
- atomic/std::atomic_flag_test_and_set_explicit
- atomic/std::atomic_init
- atomic/std::atomic_is_lock_free
- atomic/std::atomic_load
- atomic/std::atomic_load_explicit
- atomic/std::atomic_signal_fence
- atomic/std::atomic_store
- atomic/std::atomic_store_explicit
- atomic/std::atomic_thread_fence
- atomic/std::kill_dependency
ms.assetid: 5c53b4f8-6ff5-47d7-beb2-2d6ee3c6ea89
author: mikeblome
ms.author: mblome
helpviewer_keywords:
- std::atomic_compare_exchange_strong [C++]
- std::atomic_compare_exchange_strong_explicit [C++]
- std::atomic_compare_exchange_weak [C++]
- std::atomic_compare_exchange_weak_explicit [C++]
- std::atomic_exchange [C++]
- std::atomic_exchange_explicit [C++]
- std::atomic_fetch_add [C++]
- std::atomic_fetch_add_explicit [C++]
- std::atomic_fetch_and [C++]
- std::atomic_fetch_and_explicit [C++]
- std::atomic_fetch_or [C++]
- std::atomic_fetch_or_explicit [C++]
- std::atomic_fetch_sub [C++]
- std::atomic_fetch_sub_explicit [C++]
- std::atomic_fetch_xor [C++]
- std::atomic_fetch_xor_explicit [C++]
- std::atomic_flag_clear [C++]
- std::atomic_flag_clear_explicit [C++]
- std::atomic_flag_test_and_set [C++]
- std::atomic_flag_test_and_set_explicit [C++]
- std::atomic_init [C++]
- std::atomic_is_lock_free [C++]
- std::atomic_load [C++]
- std::atomic_load_explicit [C++]
- std::atomic_signal_fence [C++]
- std::atomic_store [C++]
- std::atomic_store_explicit [C++]
- std::atomic_thread_fence [C++]
- std::kill_dependency [C++]
ms.workload:
- cplusplus
ms.openlocfilehash: 50e70230dd5b8d9aa61f4df8c1288569192048b0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848789"
---
# <a name="ltatomicgt-functions"></a>&lt;atomic&gt;, fonctions

||||
|-|-|-|
|[atomic_compare_exchange_strong](#atomic_compare_exchange_strong)|[atomic_compare_exchange_strong_explicit](#atomic_compare_exchange_strong_explicit)|[atomic_compare_exchange_weak](#atomic_compare_exchange_weak)|
|[atomic_compare_exchange_weak_explicit](#atomic_compare_exchange_weak_explicit)|[atomic_exchange](#atomic_exchange)|[atomic_exchange_explicit](#atomic_exchange_explicit)|
|[atomic_fetch_add](#atomic_fetch_add)|[atomic_fetch_add_explicit](#atomic_fetch_add_explicit)|[atomic_fetch_and](#atomic_fetch_and)|
|[atomic_fetch_and_explicit](#atomic_fetch_and_explicit)|[atomic_fetch_or](#atomic_fetch_or)|[atomic_fetch_or_explicit](#atomic_fetch_or_explicit)|
|[atomic_fetch_sub](#atomic_fetch_sub)|[atomic_fetch_sub_explicit](#atomic_fetch_sub_explicit)|[atomic_fetch_xor](#atomic_fetch_xor)|
|[atomic_fetch_xor_explicit](#atomic_fetch_xor_explicit)|[atomic_flag_clear](#atomic_flag_clear)|[atomic_flag_clear_explicit](#atomic_flag_clear_explicit)|
|[atomic_flag_test_and_set](#atomic_flag_test_and_set)|[atomic_flag_test_and_set_explicit](#atomic_flag_test_and_set_explicit)|[atomic_init](#atomic_init)|
|[atomic_is_lock_free](#atomic_is_lock_free)|[atomic_load](#atomic_load)|[atomic_load_explicit](#atomic_load_explicit)|
|[atomic_signal_fence](#atomic_signal_fence)|[atomic_store](#atomic_store)|[atomic_store_explicit](#atomic_store_explicit)|
|[atomic_thread_fence](#atomic_thread_fence)|[kill_dependency](#kill_dependency)|

## <a name="atomic_compare_exchange_strong"></a>  atomic_compare_exchange_strong

Effectue une opération atomique de comparaison et d’échange.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `Ty`.

`Exp` Un pointeur vers une valeur de type `Ty`.

`Value` Une valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

`bool` qui indique le résultat de la comparaison de valeurs.

### <a name="remarks"></a>Notes

Cette méthode effectue une opération atomique de comparaison et d’échange à l’aide d’arguments implicites `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum). Pour plus d’informations, consultez [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a>  atomic_compare_exchange_strong_explicit

Effectue une opération *atomique de comparaison et d’échange*.

```cpp
template <class T>
inline bool atomic_compare_exchange_strong_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `Ty`.

`Exp` Un pointeur vers une valeur de type `Ty`.

`Value` Une valeur de type `Ty`.

`Order1` Première [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argument.

`Order2` Deuxième `memory_order` argument. La valeur de `Order2` ne peut pas être `memory_order_release` ou `memory_order_acq_rel`, elle ne peut pas être supérieure à la valeur de `Order1`.

### <a name="return-value"></a>Valeur de retour

`bool` qui indique le résultat de la comparaison de valeurs.

### <a name="remarks"></a>Notes

Une *opération atomique de comparaison et d’échange* compare la valeur stockée dans l’objet désignée par `Atom` à la valeur désignée par `Exp`. Si les valeurs sont égales, la valeur stockée dans l’objet désignée par `atom` est remplacée par `Val` à l’aide d’une opération `read-modify-write` et en appliquant les contraintes d’ordre de mémoire spécifiées par `Order1`. Si les valeurs ne sont pas égales, l’opération remplace la valeur désignée par `Exp` par la valeur stockée dans l’objet désignée par `Atom` et applique les contraintes d’ordre de mémoire spécifiées par `Order2`.

## <a name="atomic_compare_exchange_weak"></a>  atomic_compare_exchange_weak

Effectue une opération *atomique faible de comparaison et d’échange*.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `Ty`.

`Exp` Un pointeur vers une valeur de type `Ty`.

`Value` Une valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

`bool` qui indique le résultat de la comparaison de valeurs.

### <a name="remarks"></a>Notes

Cette méthode effectue une *opération atomique faible de comparaison et d’échange* qui a des arguments implicites `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum). Pour plus d’informations, consultez [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).

## <a name="atomic_compare_exchange_weak_explicit"></a>  atomic_compare_exchange_weak_explicit

Effectue une opération *atomique faible de comparaison et d’échange*.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `Ty`.

`Exp` Un pointeur vers une valeur de type `Ty`.

`Value` Une valeur de type `Ty`.

`Order1` Première [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argument.

`Order2` Deuxième `memory_order` argument. La valeur de `Order2` ne peut pas être `memory_order_release` ou `memory_order_acq_rel`, elle ne peut pas être non plus supérieure à la valeur de `Order1`.

### <a name="return-value"></a>Valeur de retour

`bool` qui indique le résultat de la comparaison de valeurs.

### <a name="remarks"></a>Notes

Une *opération atomique de comparaison et d’échange* compare la valeur stockée dans l’objet désignée par `Atom` à la valeur désignée par `Exp`. Si les valeurs sont égales, l’opération remplace la valeur stockée dans l’objet désignée par `Atom` par `Val` à l’aide d’une opération `read-modify-write` et en appliquant les contraintes d’ordre de mémoire spécifiées par `Order1`. Si les valeurs ne sont pas égales, l’opération remplace la valeur désignée par `Exp` par la valeur stockée dans l’objet désignée par `Atom` et applique les contraintes d’ordre de mémoire spécifiées par `Order2`.

Une opération atomique *faible* de comparaison et d’échange effectue un échange si les valeurs comparées sont égales. Toutefois, si les valeurs ne sont pas égales, l’opération d’échange n’est pas garantie.

## <a name="atomic_exchange"></a>  atomic_exchange

Utilise `Value` pour remplacer la valeur stockée de `Atom`.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `Ty`.

`Value` Une valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

Valeur stockée de `Atom` avant l’échange.

### <a name="remarks"></a>Notes

La fonction `atomic_exchange` effectue une opération `read-modify-write` pour échanger la valeur stockée dans `Atom` avec `Value`, à l’aide de `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a>  atomic_exchange_explicit

Remplace la valeur stockée de `Atom` par `Value`.

```cpp
template <class Ty>
inline Ty atomic_exchange_explicit(
    volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_exchange_explicit(
    atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `Ty`.

`Value` Une valeur de type `Ty`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

Valeur stockée de `Atom` avant l’échange.

### <a name="remarks"></a>Notes

La fonction `atomic_exchange_explicit` effectue une opération `read-modify-write` pour échanger la valeur stockée dans `Atom` avec `Value`, en respectant les contraintes d’ordre de mémoire spécifiées par `Order`.

## <a name="atomic_fetch_add"></a>  atomic_fetch_add

Ajoute une valeur à une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke un pointeur vers le type `T`.

`Value` Une valeur de type `ptrdiff_t`.

### <a name="return-value"></a>Valeur de retour

Valeur du pointeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La fonction `atomic_fetch_add` effectue une opération `read-modify-write` pour ajouter de manière atomique `Value` à la valeur stockée dans `Atom`, à l’aide de la contrainte `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

Quand le type atomique est `atomic_address`, `Value` a le type `ptrdiff_t` et l’opération traite le pointeur stocké comme un `char *`.

Cette opération est également surchargée pour les types intégraux :

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a>  atomic_fetch_add_explicit

Ajoute une valeur à une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
T* atomic_fetch_add_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_add_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke un pointeur vers le type `T`.

`Value` Une valeur de type `ptrdiff_t`.

### <a name="return-value"></a>Valeur de retour

Valeur du pointeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La fonction `atomic_fetch_add_explicit` effectue une opération `read-modify-write` pour ajouter de manière atomique `Value` à la valeur stockée dans `Atom`, en respectant les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées par `Order`.

Quand le type atomique est `atomic_address`, `Value` a le type `ptrdiff_t` et l’opération traite le pointeur stocké comme un `char *`.

Cette opération est également surchargée pour les types intégraux :

```cpp
integral atomic_fetch_add_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_add_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_and"></a>  atomic_fetch_and

Effectue une opération `and` au niveau du bit sur une valeur et une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `T`.

`Value` Une valeur de type `T`.

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La fonction `atomic_fetch_and` effectue une opération `read-modify-write` pour remplacer la valeur stockée de `Atom` par une opération `and` au niveau du bit de `Value` et la valeur actuelle stockée dans `Atom`, à l’aide de la contrainte `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_and_explicit"></a>  atomic_fetch_and_explicit

Effectue une opération `and` au niveau du bit sur une valeur et une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `T`.

`Value` Une valeur de type `T`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La fonction `atomic_fetch_and_explicit` effectue une opération `read-modify-write` pour remplacer la valeur stockée de `Atom` par une opération `and` au niveau du bit de `Value` et la valeur actuelle stockée dans `Atom`, en respectant les contraintes de mémoire spécifiées par `Order`.

## <a name="atomic_fetch_or"></a>  atomic_fetch_or

Effectue une opération `or` au niveau du bit sur une valeur et une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `T`.

`Value` Une valeur de type `T`.

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La fonction `atomic_fetch_or` effectue une opération `read-modify-write` pour remplacer la valeur stockée de `Atom` par une opération `or` au niveau du bit de `Value` et la valeur actuelle stockée dans `Atom`, à l’aide de `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_or_explicit"></a>  atomic_fetch_or_explicit

Effectue une opération `or` au niveau du bit sur une valeur et une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `T`.

`Value` Une valeur de type `T`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La fonction `atomic_fetch_or_explicit` effectue une opération `read-modify-write` pour remplacer la valeur stockée de `Atom` par une opération `or` au niveau du bit de `Value` et la valeur actuelle stockée dans `Atom`, en respectant les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées par `Order`.

## <a name="atomic_fetch_sub"></a>  atomic_fetch_sub

Soustrait une valeur d’une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
T* atomic_fetch_sub(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;

template <class T>
T* atomic_fetch_sub(
    atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke un pointeur vers le type `T`.

`Value` Une valeur de type `ptrdiff_t`.

### <a name="return-value"></a>Valeur de retour

Valeur du pointeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La fonction `atomic_fetch_sub` effectue une opération `read-modify-write` pour soustraire de manière atomique `Value` de la valeur stockée dans `Atom`, à l’aide de la contrainte `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

Quand le type atomique est `atomic_address`, `Value` a le type `ptrdiff_t` et l’opération traite le pointeur stocké comme un `char *`.

Cette opération est également surchargée pour les types intégraux :

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a>  atomic_fetch_sub_explicit

Soustrait une valeur d’une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
T* atomic_fetch_sub_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_sub_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value, memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke un pointeur vers le type `T`.

`Value` Une valeur de type `ptrdiff_t`.

### <a name="return-value"></a>Valeur de retour

Valeur du pointeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La fonction `atomic_fetch_sub_explicit` effectue une opération `read-modify-write` pour soustraire de manière atomique `Value` de la valeur stockée dans `Atom`, en respectant les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées par `Order`.

Quand le type atomique est `atomic_address`, `Value` a le type `ptrdiff_t` et l’opération traite le pointeur stocké comme un `char *`.

Cette opération est également surchargée pour les types intégraux :

```cpp
integral atomic_fetch_sub_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_sub_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_xor"></a>  atomic_fetch_xor

Effectue une opération `exclusive or` au niveau du bit sur une valeur et une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `T`.

`Value` Une valeur de type `T`.

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La fonction `atomic_fetch_xor` effectue une opération `read-modify-write` pour remplacer la valeur stockée de `Atom` par une opération `exclusive or` au niveau du bit de `Value` et la valeur actuelle stockée dans `Atom`, à l’aide de `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_xor_explicit"></a>  atomic_fetch_xor_explicit

Effectue une opération `exclusive or` au niveau du bit sur une valeur et une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `T`.

`Value` Une valeur de type `T`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La fonction `atomic_fetch_xor_explicit` effectue une opération `read-modify-write` pour remplacer la valeur stockée de `Atom` par une opération `exclusive or` au niveau du bit de `Value` et la valeur actuelle stockée dans `Atom`, en respectant les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées par `Order`.

## <a name="atomic_flag_clear"></a>  atomic_flag_clear

Définit l’indicateur `bool` dans un objet [atomic_flag](../standard-library/atomic-flag-structure.md) avec la valeur `false`, en respectant `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Paramètres

`Flag` Un pointeur vers un `atomic_flag` objet.

## <a name="atomic_flag_clear_explicit"></a>  atomic_flag_clear_explicit

Définit l’indicateur `bool` dans un objet [atomic_flag](../standard-library/atomic-flag-structure.md) avec la valeur `false`, en respectant les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

`Flag` Un pointeur vers un `atomic_flag` objet.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a>  atomic_flag_test_and_set

Définit l’indicateur `bool` dans un objet [atomic_flag](../standard-library/atomic-flag-structure.md) avec la valeur `true`, en respectant les contraintes de `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Paramètres

`Flag` Un pointeur vers un `atomic_flag` objet.

### <a name="return-value"></a>Valeur de retour

Valeur initiale de `Flag`.

## <a name="atomic_flag_test_and_set_explicit"></a>  atomic_flag_test_and_set_explicit

Définit l’indicateur `bool` dans un objet [atomic_flag](../standard-library/atomic-flag-structure.md) avec la valeur `true`, en respectant les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées.

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

`Flag` Un pointeur vers un `atomic_flag` objet.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

Valeur initiale de `Flag`.

## <a name="atomic_init"></a>  atomic_init

Définit la valeur stockée dans un objet `atomic`.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `Ty`.

`Value` Une valeur de type `Ty`.

### <a name="remarks"></a>Notes

`atomic_init` n’est pas une opération atomique. Elle n’est pas thread‑safe.

## <a name="atomic_is_lock_free"></a>  atomic_is_lock_free

Spécifie si les opérations atomiques sur un objet `atomic` sont *sans verrou*.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui stocke une valeur de type `T`.

### <a name="return-value"></a>Valeur de retour

`true` si des opérations atomiques sur `Atom` sont sans verrou ; sinon, `false`.

### <a name="remarks"></a>Notes

Un type atomique est sans verrou si aucune opération atomique sur ce type utilise un verrou. Si cette fonction retourne la valeur true, le type peut être utilisé dans les gestionnaires de signal.

## <a name="atomic_load"></a>  atomic_load

Récupère la valeur stockée dans un objet `atomic`.

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui contient une valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

Valeur récupérée stockée dans `Atom`.

### <a name="remarks"></a>Notes

`atomic_load` utilise implicitement `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_load_explicit"></a>  atomic_load_explicit

Récupère la valeur stockée dans un objet `atomic`, en respectant un [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifié.

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui contient une valeur de type `Ty`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum). N’utilisez pas `memory_order_release` ou `memory_order_acq_rel`.

### <a name="return-value"></a>Valeur de retour

Valeur récupérée stockée dans `Atom`.

## <a name="atomic_signal_fence"></a>  atomic_signal_fence

Agit comme une *délimitation* (c’est-à-dire une primitive de synchronisation de mémoire qui applique un ordre entre les opérations de chargement/stockage) entre d’autres délimitations d’un thread d’appel qui ont des gestionnaires de signal exécutés dans le même thread.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

`Order` Une contrainte qui détermine le type de limite de classement de la mémoire.

### <a name="remarks"></a>Notes

L’argument `Order` détermine le type de délimitation.

|||
|-|-|
|`memory_order_relaxed`|La délimitation est sans effet.|
|`memory_order_consume`|La délimitation est une délimitation d’acquisition.|
|`memory_order_acquire`|La délimitation est une délimitation d’acquisition.|
|`memory_order_release`|La délimitation est une délimitation de libération.|
|`memory_order_acq_rel`|La délimitation est une délimitation d’acquisition et de libération.|
|`memory_order_seq_cst`|La délimitation est une délimitation d’acquisition et de libération, et est cohérente de manière séquentielle.|

## <a name="atomic_store"></a>  atomic_store

Stocke de manière atomique une valeur dans un objet atomique.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un objet atomique qui contient une valeur de type `Ty`.

`Value` Une valeur de type `Ty`.

### <a name="remarks"></a>Notes

`atomic_store` stocke `Value` dans l’objet désigné par `Atom`, en respectant la contrainte `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_store_explicit"></a>  atomic_store_explicit

Stocke de manière atomique une valeur dans un objet atomique.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(
    const volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_store_explicit(
    const atomic<Ty>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

`Atom` Un pointeur vers un `atomic` objet qui contient une valeur de type `Ty`.

`Value` Une valeur de type `Ty`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum). N’utilisez pas `memory_order_consume`, `memory_order_acquire` ou `memory_order_acq_rel`.

### <a name="remarks"></a>Notes

`atomic_store` stocke `Value` dans l’objet désigné par `Atom`, en respectant le `memory_order` spécifié par `Order`.

## <a name="atomic_thread_fence"></a>  atomic_thread_fence

Agit comme une *délimitation* (c’est-à-dire, une primitive de synchronisation de mémoire qui applique un ordre entre les opérations de chargement/stockage) sans opération atomique associée.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

`Order` Une contrainte qui détermine le type de limite de classement de la mémoire.

### <a name="remarks"></a>Notes

L’argument `Order` détermine le type de délimitation.

|||
|-|-|
|`memory_order_relaxed`|La délimitation est sans effet.|
|`memory_order_consume`|La délimitation est une délimitation d’acquisition.|
|`memory_order_acquire`|La délimitation est une délimitation d’acquisition.|
|`memory_order_release`|La délimitation est une délimitation de libération.|
|`memory_order_acq_rel`|La délimitation est une délimitation d’acquisition et de libération.|
|`memory_order_seq_cst`|La délimitation est une délimitation d’acquisition et de libération, et est cohérente de manière séquentielle.|

## <a name="kill_dependency"></a>  kill_dependency

Supprime une dépendance.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>Paramètres

`Arg` Une valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

La valeur de retour est `Arg`. L’évaluation de `Arg` ne comprend pas de dépendance à l’appel de fonction. En arrêtant une chaîne de dépendance possible, la fonction peut permettre au compilateur de générer du code plus efficace.

## <a name="see-also"></a>Voir aussi

[\<atomic>](../standard-library/atomic.md)<br/>
