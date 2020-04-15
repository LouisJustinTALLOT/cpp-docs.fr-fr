---
title: '&lt;atomic&gt;, fonctions'
ms.date: 07/11/2018
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
ms.openlocfilehash: b6d03da446e4a3bae02f662e5b106bd5de534d0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376898"
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

## <a name="atomic_compare_exchange_strong"></a><a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

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

*Atome*\
Un pointeur *atomic* à un objet atomique `Ty`qui stocke une valeur de type .

*Exp*\
Pointeur vers une valeur de type `Ty`.

*Valeur*\
Valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

**vrai** si les valeurs sont égales, autrement **fausses**.

### <a name="remarks"></a>Notes

Cette méthode effectue une opération atomique de comparaison et d’échange à l’aide d’arguments implicites `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum). Pour plus d’informations, consultez [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

Effectue une opération *atomique de comparaison et d’échange.*

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

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `Ty`.

*Exp*\
Pointeur vers une valeur de type `Ty`.

*Valeur*\
Valeur de type `Ty`.

*Commande1*\
Premier argument [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

*Commande2*\
Deuxième argument `memory_order`. La valeur de *l’ordre2* ne peut pas être `memory_order_release` ou, `memory_order_acq_rel`il ne peut pas être plus fort que la valeur de *l’ordre1*.

### <a name="return-value"></a>Valeur de retour

**vrai** si les valeurs sont égales, autrement **fausses**.

### <a name="remarks"></a>Notes

Une *opération de comparaison et d’échange atomique* compare la valeur qui est stockée dans l’objet qui est pointé par *Atom* par rapport à la valeur qui est soulignée par *Exp*. Si les valeurs sont égales, la valeur qui est stockée dans l’objet `read-modify-write` pointé par *l’atome* est remplacée par la *valeur* par l’utilisation d’une opération et l’application des contraintes de commande de mémoire qui sont spécifiées par *Order1*. Si les valeurs ne sont pas égales, l’opération remplace la valeur pointée par *Exp* par la valeur qui est stockée dans l’objet qui est pointé par *Atom* et applique les contraintes de commande de mémoire qui sont spécifiées par *Order2*.

## <a name="atomic_compare_exchange_weak"></a><a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

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

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `Ty`.

*Exp*\
Pointeur vers une valeur de type `Ty`.

*Valeur*\
Valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

**vrai** si les valeurs sont égales, autrement **fausses**.

### <a name="remarks"></a>Notes

Cette méthode effectue une *opération atomique faible de comparaison et d’échange* qui a des arguments implicites `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum). Pour plus d’informations, consultez [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).

## <a name="atomic_compare_exchange_weak_explicit"></a><a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

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

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `Ty`.

*Exp*\
Pointeur vers une valeur de type `Ty`.

*Valeur*\
Valeur de type `Ty`.

*Commande1*\
Premier argument [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

*Commande2*\
Deuxième argument `memory_order`. La valeur de *l’ordre2* ne peut pas être `memory_order_release` ou, `memory_order_acq_rel`ni ne peut être plus forte que la valeur de *l’ordre1*.

### <a name="return-value"></a>Valeur de retour

**vrai** si les valeurs sont égales, autrement **fausses**.

### <a name="remarks"></a>Notes

Les saveurs fortes et faibles d’une opération atomique de *comparaison et d’échange* garantissent qu’elles ne stockent pas la nouvelle valeur si les valeurs attendues et actuelles ne sont pas égales. La saveur forte garantit qu’il stockera la nouvelle valeur si les valeurs attendues et actuelles sont égales. La saveur faible peut parfois revenir **faux** et ne pas stocker la nouvelle valeur, même si les valeurs actuelles et attendues sont égales. En d’autres termes, la fonction reviendra **fausse,** mais un examen ultérieur de la valeur attendue pourrait révéler qu’il n’a pas changé, et aurait donc dû comparer à égalité.

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a>atomic_exchange

Utilise *la valeur* pour remplacer la valeur stockée de *l’atome*.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `Ty`.

*Valeur*\
Valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

La valeur stockée *d’Atom* avant l’échange.

### <a name="remarks"></a>Notes

La `atomic_exchange` fonction effectue `read-modify-write` une opération pour échanger la valeur qui `memory_order_seq_cst`est stockée dans *Atom* with *Value*, en utilisant le [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

Remplace la valeur stockée de *l’atome* par *la valeur*.

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

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `Ty`.

*Valeur*\
Valeur de type `Ty`.

*commande*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

La valeur stockée *d’Atom* avant l’échange.

### <a name="remarks"></a>Notes

La `atomic_exchange_explicit` fonction effectue `read-modify-write` une opération pour échanger la valeur qui est stockée dans *Atom* with *Value*, dans les contraintes de mémoire qui sont spécifiées par *l’ordre*.

## <a name="atomic_fetch_add"></a><a name="atomic_fetch_add"></a>atomic_fetch_add

Ajoute une valeur à une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atome*\
Pointeur vers un objet `atomic` qui stocke un pointeur de type `T`.

*Valeur*\
Valeur de type `ptrdiff_t`.

### <a name="return-value"></a>Valeur de retour

Valeur du pointeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La `atomic_fetch_add` fonction effectue `read-modify-write` une opération pour ajouter atomiquement *la* valeur `memory_order_seq_cst`à la valeur stockée dans *l’atome*, en utilisant la contrainte [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

Lorsque le type `atomic_address`atomique est , *La valeur* a le type `ptrdiff_t` et l’opération traite le pointeur stocké comme un `char *`.

Cette opération est également surchargée pour les types intégraux :

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a><a name="atomic_fetch_add_explicit"></a>atomic_fetch_add_explicit

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

*Atome*\
Pointeur vers un objet `atomic` qui stocke un pointeur de type `T`.

*Valeur*\
Valeur de type `ptrdiff_t`.

### <a name="return-value"></a>Valeur de retour

Valeur du pointeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La `atomic_fetch_add_explicit` fonction effectue `read-modify-write` une opération pour ajouter atomiquement *la valeur* à la valeur stockée `Order`dans *l’atome*, dans les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) qui sont spécifiées par .

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

## <a name="atomic_fetch_and"></a><a name="atomic_fetch_and"></a>atomic_fetch_and

Effectue une opération `and` au niveau du bit sur une valeur et une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

*Valeur*\
Valeur de type `T`.

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La `atomic_fetch_and` fonction effectue `read-modify-write` une opération pour remplacer la valeur `and` stockée de *l’atome* par un peu plus de *valeur* et la valeur actuelle qui est stockée dans *Atom*, en utilisant la `memory_order_seq_cst`contrainte [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

## <a name="atomic_fetch_and_explicit"></a><a name="atomic_fetch_and_explicit"></a>atomic_fetch_and_explicit

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

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

*Valeur*\
Valeur de type `T`.

*commande*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La `atomic_fetch_and_explicit` fonction effectue `read-modify-write` une opération pour remplacer la valeur `and` stockée de *l’atome* par un peu plus de *valeur* et la valeur actuelle qui est stockée dans *l’atome*, dans les contraintes de mémoire qui sont spécifiées par *l’ordre*.

## <a name="atomic_fetch_or"></a><a name="atomic_fetch_or"></a>atomic_fetch_or

Effectue une opération `or` au niveau du bit sur une valeur et une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

*Valeur*\
Valeur de type `T`.

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La `atomic_fetch_or` fonction effectue `read-modify-write` une opération pour remplacer la valeur `or` stockée de *l’atome* par un peu plus de *valeur* et la valeur actuelle qui est stockée dans *Atom*, en utilisant le `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_or_explicit"></a><a name="atomic_fetch_or_explicit"></a>atomic_fetch_or_explicit

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

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

*Valeur*\
Valeur de type `T`.

*commande*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La `atomic_fetch_or_explicit` fonction effectue `read-modify-write` une opération pour remplacer la valeur `or` stockée de *l’atome* par un peu plus de *valeur* et la valeur actuelle qui est stockée dans *l’atome*, dans les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées par *l’ordre*.

## <a name="atomic_fetch_sub"></a><a name="atomic_fetch_sub"></a>atomic_fetch_sub

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

*Atome*\
Pointeur vers un objet `atomic` qui stocke un pointeur de type `T`.

*Valeur*\
Valeur de type `ptrdiff_t`.

### <a name="return-value"></a>Valeur de retour

Valeur du pointeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La `atomic_fetch_sub` fonction effectue `read-modify-write` une opération pour soustraire atomiquement la `memory_order_seq_cst` *valeur* de la valeur stockée dans *l’atome*, en utilisant la contrainte [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

Lorsque le type `atomic_address`atomique est , *La valeur* a le type `ptrdiff_t` et l’opération traite le pointeur stocké comme un `char *`.

Cette opération est également surchargée pour les types intégraux :

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a><a name="atomic_fetch_sub_explicit"></a>atomic_fetch_sub_explicit

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

*Atome*\
Pointeur vers un objet `atomic` qui stocke un pointeur de type `T`.

*Valeur*\
Valeur de type `ptrdiff_t`.

### <a name="return-value"></a>Valeur de retour

Valeur du pointeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La `atomic_fetch_sub_explicit` fonction effectue `read-modify-write` une opération pour soustraire atomiquement la *valeur* de la valeur `Order`stockée dans *l’atome*, dans les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) qui sont spécifiées par .

Lorsque le type `atomic_address`atomique est , *La valeur* a le type `ptrdiff_t` et l’opération traite le pointeur stocké comme un `char *`.

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

## <a name="atomic_fetch_xor"></a><a name="atomic_fetch_xor"></a>atomic_fetch_xor

Effectue une opération `exclusive or` au niveau du bit sur une valeur et une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

*Valeur*\
Valeur de type `T`.

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La `atomic_fetch_xor` fonction effectue `read-modify-write` une opération pour remplacer la valeur `exclusive or` stockée de *l’atome* par un peu plus de *valeur* et la valeur actuelle qui est stockée dans *Atom*, en utilisant le `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_xor_explicit"></a><a name="atomic_fetch_xor_explicit"></a>atomic_fetch_xor_explicit

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

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

*Valeur*\
Valeur de type `T`.

*commande*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

La `atomic_fetch_xor_explicit` fonction effectue `read-modify-write` une opération pour remplacer la valeur `exclusive or` stockée de *l’atome* par un peu plus de *valeur* et la valeur actuelle qui est stockée dans *l’atome*, dans les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) qui sont spécifiés par *l’ordre*.

## <a name="atomic_flag_clear"></a><a name="atomic_flag_clear"></a>atomic_flag_clear

Définit le drapeau **bool** dans un [atomic_flag](../standard-library/atomic-flag-structure.md) objet `memory_order_seq_cst`à **faux**, dans le [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Paramètres

*Drapeau*\
Pointeur vers un objet `atomic_flag` .

## <a name="atomic_flag_clear_explicit"></a><a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit

Définit le drapeau **bool** dans un [atomic_flag](../standard-library/atomic-flag-structure.md) objet à **faux**, dans les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

*Drapeau*\
Pointeur vers un objet `atomic_flag` .

*commande*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a><a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set

Définit le drapeau **bool** dans un [atomic_flag’objet](../standard-library/atomic-flag-structure.md) à `memory_order_seq_cst` **vrai**, dans les contraintes de la [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Paramètres

*Drapeau*\
Pointeur vers un objet `atomic_flag` .

### <a name="return-value"></a>Valeur de retour

La valeur initiale de *Flag*.

## <a name="atomic_flag_test_and_set_explicit"></a><a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit

Définit le drapeau **bool** dans un [atomic_flag’objet](../standard-library/atomic-flag-structure.md) à **vrai**, dans les contraintes [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifiées.

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

*Drapeau*\
Pointeur vers un objet `atomic_flag` .

*commande*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

La valeur initiale de *Flag*.

## <a name="atomic_init"></a><a name="atomic_init"></a>atomic_init

Définit la valeur stockée dans un objet `atomic`.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `Ty`.

*Valeur*\
Valeur de type `Ty`.

### <a name="remarks"></a>Notes

`atomic_init` n’est pas une opération atomique. Elle n’est pas thread‑safe.

## <a name="atomic_is_lock_free"></a><a name="atomic_is_lock_free"></a>atomic_is_lock_free

Spécifie si les opérations atomiques sur un objet `atomic` sont *sans verrou*.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atome*\
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

### <a name="return-value"></a>Valeur de retour

**vrai** si les opérations atomiques sur *Atom* sont sans verrou; autrement, **faux**.

### <a name="remarks"></a>Notes

Un type atomique est sans verrou si aucune opération atomique sur ce type utilise un verrou. Si cette fonction retourne la valeur true, le type peut être utilisé dans les gestionnaires de signal.

## <a name="atomic_load"></a><a name="atomic_load"></a>atomic_load

Récupère la valeur stockée dans un objet `atomic`.

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atome*\
Pointeur vers un objet `atomic` qui contient une valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

La valeur récupérée qui est stockée dans *Atom*.

### <a name="remarks"></a>Notes

`atomic_load` utilise implicitement `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_load_explicit"></a><a name="atomic_load_explicit"></a>atomic_load_explicit

Récupère la valeur stockée dans un objet `atomic`, en respectant un [memory_order](../standard-library/atomic-enums.md#memory_order_enum) spécifié.

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atome*\
Pointeur vers un objet `atomic` qui contient une valeur de type `Ty`.

*commande*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum). N’utilisez pas `memory_order_release` ou `memory_order_acq_rel`.

### <a name="return-value"></a>Valeur de retour

La valeur récupérée qui est stockée dans *Atom*.

## <a name="atomic_signal_fence"></a><a name="atomic_signal_fence"></a>atomic_signal_fence

Agit comme une *délimitation* (c’est-à-dire une primitive de synchronisation de mémoire qui applique un ordre entre les opérations de chargement/stockage) entre d’autres délimitations d’un thread d’appel qui ont des gestionnaires de signal exécutés dans le même thread.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

*commande*\
Contrainte d’ordre de mémoire qui détermine le type de délimitation.

### <a name="remarks"></a>Notes

*L’argument de l’Ordre* détermine le type de clôture.

|||
|-|-|
|`memory_order_relaxed`|La délimitation est sans effet.|
|`memory_order_consume`|La délimitation est une délimitation d’acquisition.|
|`memory_order_acquire`|La délimitation est une délimitation d’acquisition.|
|`memory_order_release`|La délimitation est une délimitation de libération.|
|`memory_order_acq_rel`|La délimitation est une délimitation d’acquisition et de libération.|
|`memory_order_seq_cst`|La délimitation est une délimitation d’acquisition et de libération, et est cohérente de manière séquentielle.|

## <a name="atomic_store"></a><a name="atomic_store"></a>atomic_store

Stocke de manière atomique une valeur dans un objet atomique.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atome*\
Pointeur vers un objet atomique qui contient une valeur de type `Ty`.

*Valeur*\
Valeur de type `Ty`.

### <a name="remarks"></a>Notes

`atomic_store`stocke *la valeur* dans l’objet qui `memory_order_seq_cst`est pointé vers *l’atome*, dans la contrainte [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

## <a name="atomic_store_explicit"></a><a name="atomic_store_explicit"></a>atomic_store_explicit

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

*Atome*\
Pointeur vers un objet `atomic` qui contient une valeur de type `Ty`.

*Valeur*\
Valeur de type `Ty`.

*commande*\
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum). N’utilisez pas `memory_order_consume`, `memory_order_acquire` ou `memory_order_acq_rel`.

### <a name="remarks"></a>Notes

`atomic_store`stocke *la valeur* dans l’objet qui `memory_order` est pointé par *Atom*, dans le qui est spécifié par *l’ordre*.

## <a name="atomic_thread_fence"></a><a name="atomic_thread_fence"></a>atomic_thread_fence

Agit comme une *délimitation* (c’est-à-dire, une primitive de synchronisation de mémoire qui applique un ordre entre les opérations de chargement/stockage) sans opération atomique associée.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

*commande*\
Contrainte d’ordre de mémoire qui détermine le type de délimitation.

### <a name="remarks"></a>Notes

*L’argument de l’Ordre* détermine le type de clôture.

|||
|-|-|
|`memory_order_relaxed`|La délimitation est sans effet.|
|`memory_order_consume`|La délimitation est une délimitation d’acquisition.|
|`memory_order_acquire`|La délimitation est une délimitation d’acquisition.|
|`memory_order_release`|La délimitation est une délimitation de libération.|
|`memory_order_acq_rel`|La délimitation est une délimitation d’acquisition et de libération.|
|`memory_order_seq_cst`|La délimitation est une délimitation d’acquisition et de libération, et est cohérente de manière séquentielle.|

## <a name="kill_dependency"></a><a name="kill_dependency"></a>kill_dependency

Supprime une dépendance.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>Paramètres

*Arg*\
Valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

La valeur de retour est *Arg*. L’évaluation *d’Arg* ne porte pas une dépendance à l’appel de fonction. En arrêtant une chaîne de dépendance possible, la fonction peut permettre au compilateur de générer du code plus efficace.

## <a name="see-also"></a>Voir aussi

[\<>atomique](../standard-library/atomic.md)
