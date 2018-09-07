---
title: '&lt;atomic&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 07/11/2018
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
ms.openlocfilehash: c00f66eef11d2d26bbcaa07110e9d9e738fc7c2f
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110160"
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

*Atom*<br/>
Un pointeur vers un *atomique* objet qui stocke une valeur de type `Ty`.

*Exp*<br/>
Pointeur vers une valeur de type `Ty`.

*Valeur*<br/>
Valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

**true** si les valeurs sont égales, sinon **false**.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `Ty`.

*Exp*<br/>
Pointeur vers une valeur de type `Ty`.

*Valeur*<br/>
Valeur de type `Ty`.

*Order1*<br/>
Premier argument [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

*Order2*<br/>
Deuxième argument `memory_order`. La valeur de *Order2* ne peut pas être `memory_order_release` ou `memory_order_acq_rel`, il ne peut pas être supérieure à la valeur de *Order1*.

### <a name="return-value"></a>Valeur de retour

**true** si les valeurs sont égales, sinon **false**.

### <a name="remarks"></a>Notes

Un *opération atomique de comparaison et d’échange* compare la valeur est stockée dans l’objet qui est indiqué par *Atom* par rapport à la valeur désignée par *Exp*. Si les valeurs sont égales, la valeur est stockée dans l’objet qui est indiqué par *atom* est remplacé par *valeur* en utilisant un `read-modify-write` opération et en appliquant les contraintes d’ordre de mémoire qui sont spécifié par *Order1*. Si les valeurs ne sont pas égales, l’opération remplace la valeur désignée par *Exp* avec la valeur est stockée dans l’objet qui est indiqué par *Atom* et applique les contraintes d’ordre de mémoire qui sont spécifié par *Order2*.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `Ty`.

*Exp*<br/>
Pointeur vers une valeur de type `Ty`.

*Valeur*<br/>
Valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

**true** si les valeurs sont égales, sinon **false**.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `Ty`.

*Exp*<br/>
Pointeur vers une valeur de type `Ty`.

*Valeur*<br/>
Valeur de type `Ty`.

*Order1*<br/>
Premier argument [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

*Order2*<br/>
Deuxième argument `memory_order`. La valeur de *Order2* ne peut pas être `memory_order_release` ou `memory_order_acq_rel`, ni à quel point est supérieure à la valeur de *Order1*.

### <a name="return-value"></a>Valeur de retour

**true** si les valeurs sont égales, sinon **false**.

### <a name="remarks"></a>Notes

Les versions forts et faibles d’un *opération atomique de comparaison et d’échange* garantie qu’elles ne stockent pas la nouvelle valeur si les valeurs attendues et en cours ne sont pas égales. La version forte garantit qu’il stocke la nouvelle valeur si les valeurs attendues et actuels sont égaux. La version faible peut parfois retourner **false** et pas stocker la nouvelle valeur même si l’actuel et les valeurs attendues sont égaux. En d’autres termes, la fonction retournera **false**, mais un examen ultérieur de la valeur attendue peut révéler qu’il n’a pas changé et par conséquent doit avoir comparé comme égales.

## <a name="atomic_exchange"></a>  atomic_exchange

Utilise *valeur* pour remplacer la valeur stockée de *Atom*.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `Ty`.

*Valeur*<br/>
Valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

La valeur stockée de *Atom* avant l’échange.

### <a name="remarks"></a>Notes

Le `atomic_exchange` fonction effectue une `read-modify-write` opération pour échanger la valeur est stockée dans *Atom* avec *valeur*, en utilisant le `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a>  atomic_exchange_explicit

Remplace la valeur stockée de *Atom* avec *valeur*.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `Ty`.

*Valeur*<br/>
Valeur de type `Ty`.

*Commande*<br/>
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

La valeur stockée de *Atom* avant l’échange.

### <a name="remarks"></a>Notes

Le `atomic_exchange_explicit` fonction effectue une `read-modify-write` opération pour échanger la valeur est stockée dans *Atom* avec *valeur*, respectant les contraintes de mémoire qui sont spécifiées par  *Commande*.

## <a name="atomic_fetch_add"></a>  atomic_fetch_add

Ajoute une valeur à une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke un pointeur de type `T`.

*Valeur*<br/>
Valeur de type `ptrdiff_t`.

### <a name="return-value"></a>Valeur de retour

Valeur du pointeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

Le `atomic_fetch_add` fonction effectue une `read-modify-write` opération pour ajouter de manière atomique *valeur* à la valeur stockée dans *Atom*, en utilisant le `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)contrainte.

Lorsque le type atomique est `atomic_address`, *valeur* a type `ptrdiff_t` et l’opération traite le pointeur stocké comme un `char *`.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke un pointeur de type `T`.

*Valeur*<br/>
Valeur de type `ptrdiff_t`.

### <a name="return-value"></a>Valeur de retour

Valeur du pointeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

Le `atomic_fetch_add_explicit` fonction effectue une `read-modify-write` opération pour ajouter de manière atomique *valeur* à la valeur stockée dans *Atom*, en respectant le [memory_order](../standard-library/atomic-enums.md#memory_order_enum) contraintes qui sont spécifiées par `Order`.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

*Valeur*<br/>
Valeur de type `T`.

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

Le `atomic_fetch_and` fonction effectue une `read-modify-write` opération remplace la valeur stockée de *Atom* avec un opérateur de bits `and` de *valeur* et la valeur actuelle qui est stockée dans *Atom*, en utilisant le `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) contrainte.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

*Valeur*<br/>
Valeur de type `T`.

*Commande*<br/>
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

Le `atomic_fetch_and_explicit` fonction effectue une `read-modify-write` opération remplace la valeur stockée de *Atom* avec un opérateur de bits `and` de *valeur* et la valeur actuelle qui est stockée dans *Atom*, respectant les contraintes de mémoire qui sont spécifiées par *ordre*.

## <a name="atomic_fetch_or"></a>  atomic_fetch_or

Effectue une opération `or` au niveau du bit sur une valeur et une valeur existante stockée dans un objet `atomic`.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

*Valeur*<br/>
Valeur de type `T`.

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

Le `atomic_fetch_or` fonction effectue une `read-modify-write` opération remplace la valeur stockée de *Atom* avec un opérateur de bits `or` de *valeur* et la valeur actuelle qui est stockée dans *Atom*, en utilisant le `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

*Valeur*<br/>
Valeur de type `T`.

*Commande*<br/>
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

Le `atomic_fetch_or_explicit` fonction effectue une `read-modify-write` opération remplace la valeur stockée de *Atom* avec un opérateur de bits `or` de *valeur* et la valeur actuelle qui est stockée dans *Atom*, en respectant le [memory_order](../standard-library/atomic-enums.md#memory_order_enum) contraintes spécifiées par *ordre*.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke un pointeur de type `T`.

*Valeur*<br/>
Valeur de type `ptrdiff_t`.

### <a name="return-value"></a>Valeur de retour

Valeur du pointeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

Le `atomic_fetch_sub` fonction effectue une `read-modify-write` opération à soustraire de manière atomique *valeur* à partir de la valeur stockée dans *Atom*, en utilisant le `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) contrainte.

Lorsque le type atomique est `atomic_address`, *valeur* a type `ptrdiff_t` et l’opération traite le pointeur stocké comme un `char *`.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke un pointeur de type `T`.

*Valeur*<br/>
Valeur de type `ptrdiff_t`.

### <a name="return-value"></a>Valeur de retour

Valeur du pointeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

Le `atomic_fetch_sub_explicit` fonction effectue une `read-modify-write` opération à soustraire de manière atomique *valeur* à partir de la valeur stockée dans *Atom*, en respectant le [memory_order](../standard-library/atomic-enums.md#memory_order_enum) les contraintes sont spécifiées par `Order`.

Lorsque le type atomique est `atomic_address`, *valeur* a type `ptrdiff_t` et l’opération traite le pointeur stocké comme un `char *`.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

*Valeur*<br/>
Valeur de type `T`.

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

Le `atomic_fetch_xor` fonction effectue une `read-modify-write` opération remplace la valeur stockée de *Atom* avec un opérateur de bits `exclusive or` de *valeur* et la valeur actuelle qui est stockée dans *Atom*, en utilisant le `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

*Valeur*<br/>
Valeur de type `T`.

*Commande*<br/>
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

Valeur contenue dans l’objet atomique immédiatement avant l’opération.

### <a name="remarks"></a>Notes

Le `atomic_fetch_xor_explicit` fonction effectue une `read-modify-write` opération remplace la valeur stockée de *Atom* avec un opérateur de bits `exclusive or` de *valeur* et la valeur actuelle qui est stockée dans *Atom*, en respectant le [memory_order](../standard-library/atomic-enums.md#memory_order_enum) contraintes sont spécifiées par *ordre*.

## <a name="atomic_flag_clear"></a>  atomic_flag_clear

Définit le **bool** indicateur dans un [atomic_flag](../standard-library/atomic-flag-structure.md) objet **false**, en respectant le `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Paramètres

*Indicateur*<br/>
Pointeur vers un objet `atomic_flag` .

## <a name="atomic_flag_clear_explicit"></a>  atomic_flag_clear_explicit

Définit le **bool** indicateur dans un [atomic_flag](../standard-library/atomic-flag-structure.md) objet **false**, dans le texte spécifié [memory_order](../standard-library/atomic-enums.md#memory_order_enum) contraintes.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

*Indicateur*<br/>
Pointeur vers un objet `atomic_flag` .

*Commande*<br/>
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a>  atomic_flag_test_and_set

Définit le **bool** indicateur dans un [atomic_flag](../standard-library/atomic-flag-structure.md) objet **true**, aux contraintes de la `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Paramètres

*Indicateur*<br/>
Pointeur vers un objet `atomic_flag` .

### <a name="return-value"></a>Valeur de retour

La valeur initiale de *indicateur*.

## <a name="atomic_flag_test_and_set_explicit"></a>  atomic_flag_test_and_set_explicit

Définit le **bool** indicateur dans un [atomic_flag](../standard-library/atomic-flag-structure.md) objet **true**, dans le texte spécifié [memory_order](../standard-library/atomic-enums.md#memory_order_enum) contraintes.

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

*Indicateur*<br/>
Pointeur vers un objet `atomic_flag` .

*Commande*<br/>
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valeur de retour

La valeur initiale de *indicateur*.

## <a name="atomic_init"></a>  atomic_init

Définit la valeur stockée dans un objet `atomic`.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Paramètres

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `Ty`.

*Valeur*<br/>
Valeur de type `Ty`.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui stocke une valeur de type `T`.

### <a name="return-value"></a>Valeur de retour

**true** si des opérations atomiques sur *Atom* sont sans verrou ; sinon, **false**.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui contient une valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

La valeur récupérée qui est stockée dans *Atom*.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui contient une valeur de type `Ty`.

*Commande*<br/>
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum). N’utilisez pas `memory_order_release` ou `memory_order_acq_rel`.

### <a name="return-value"></a>Valeur de retour

La valeur récupérée qui est stockée dans *Atom*.

## <a name="atomic_signal_fence"></a>  atomic_signal_fence

Agit comme une *délimitation* (c’est-à-dire une primitive de synchronisation de mémoire qui applique un ordre entre les opérations de chargement/stockage) entre d’autres délimitations d’un thread d’appel qui ont des gestionnaires de signal exécutés dans le même thread.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

*Commande*<br/>
Contrainte d’ordre de mémoire qui détermine le type de délimitation.

### <a name="remarks"></a>Notes

Le *ordre* argument détermine le type de délimitation.

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

*Atom*<br/>
Pointeur vers un objet atomique qui contient une valeur de type `Ty`.

*Valeur*<br/>
Valeur de type `Ty`.

### <a name="remarks"></a>Notes

`atomic_store` stocke *valeur* dans l’objet qui est indiqué par *Atom*, en respectant le `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) contrainte.

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

*Atom*<br/>
Pointeur vers un objet `atomic` qui contient une valeur de type `Ty`.

*Valeur*<br/>
Valeur de type `Ty`.

*Commande*<br/>
Une énumération [memory_order](../standard-library/atomic-enums.md#memory_order_enum). N’utilisez pas `memory_order_consume`, `memory_order_acquire` ou `memory_order_acq_rel`.

### <a name="remarks"></a>Notes

`atomic_store` stocke *valeur* dans l’objet qui est indiqué par *Atom*, en respectant le `memory_order` qui est spécifié par *ordre*.

## <a name="atomic_thread_fence"></a>  atomic_thread_fence

Agit comme une *délimitation* (c’est-à-dire, une primitive de synchronisation de mémoire qui applique un ordre entre les opérations de chargement/stockage) sans opération atomique associée.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Paramètres

*Commande*<br/>
Contrainte d’ordre de mémoire qui détermine le type de délimitation.

### <a name="remarks"></a>Notes

Le *ordre* argument détermine le type de délimitation.

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

*arg*<br/>
Valeur de type `Ty`.

### <a name="return-value"></a>Valeur de retour

La valeur de retour est *Arg*. L’évaluation de *Arg* ne comprend pas de dépendance à l’appel de fonction. En arrêtant une chaîne de dépendance possible, la fonction peut permettre au compilateur de générer du code plus efficace.

## <a name="see-also"></a>Voir aussi

[\<atomic>](../standard-library/atomic.md)<br/>
