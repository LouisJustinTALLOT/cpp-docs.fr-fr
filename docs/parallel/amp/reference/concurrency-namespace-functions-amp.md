---
title: Concurrency, fonctions de l’espace de noms (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::all_memory_fence
- amp/Concurrency::atomic_compare_exchange
- amp/Concurrency::atomic_fetch_dec
- amp/Concurrency::atomic_fetch_max
- amp/Concurrency::atomic_fetch_min
- amp/Concurrency::copy
- amp/Concurrency::direct3d_abort
- amp/Concurrency::direct3d_printf
- amp/Concurrency::global_memory_fence
- amp/Concurrency::tile_static_memory_fence
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
ms.openlocfilehash: 1187b745a6d8c903c22958185be8d98a6e3d0204
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376348"
---
# <a name="concurrency-namespace-functions-amp"></a>Concurrency, fonctions de l’espace de noms (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[atomic_exchange, fonction (C++ AMP)](#atomic_exchange)|[atomic_fetch_add, fonction (C++ AMP)](#atomic_fetch_add)|[atomic_fetch_and, fonction (C++ AMP)](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or, fonction (C++ AMP)](#atomic_fetch_or)|[atomic_fetch_sub, fonction (C++ AMP)](#atomic_fetch_sub)|
|[atomic_fetch_xor, fonction (C++ AMP)](#atomic_fetch_xor)|[Copie](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[parallel_for_each, fonction (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

## <a name="all_memory_fence"></a><a name="all_memory_fence"></a>all_memory_fence

Bloque l’exécution de tous les fils dans une tuile jusqu’à ce que tous les accès à la mémoire aient été complétés. Cela garantit que tous les accès à la mémoire sont visibles à d’autres threads dans la tuile de fil, et sont exécutés dans l’ordre du programme.

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Barrier*<br/>
Objet `tile_barrier` .

## <a name="amp_uninitialize"></a><a name="amp_uninitialize"></a>amp_uninitialize

Uninitialise le temps d’exécution de l’AMP CMD. Il est légal d’appeler cette fonction plusieurs fois au cours d’une durée de vie des applications. L’appel de n’importe quel API AMP DE CMD après avoir appelé cette fonction réinitialisera le temps d’exécution de l’AMP de C. Notez qu’il est illégal d’utiliser des objets AMP CMD à travers les appels à cette fonction et ce faisant entraînera un comportement indéfini. En outre, en même temps appeler cette fonction et tout autre API AMP est illégal et entraînerait un comportement indéfini.

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a><a name="atomic_compare_exchange"></a>atomic_compare_exchange

Compare atomiquement la valeur stockée à un endroit de mémoire spécifié dans le premier argument pour l’égalité avec la valeur du deuxième argument spécifié, et si les valeurs sont les mêmes, la valeur à l’emplacement de mémoire est changée à celle du troisième argument spécifié.

```cpp
inline bool atomic_compare_exchange(
    _Inout_ int* _Dest,
    _Inout_ int* _Expected_value,
    int value
    ) restrict(amp)

inline bool atomic_compare_exchange(
    _Inout_ unsigned int* _Dest,
    _Inout_ unsigned int* _Expected_value,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
L’emplacement à partir duquel l’une des valeurs à comparer est lue et à laquelle la nouvelle valeur, le cas échéant, doit être stockée.

*_Expected_value*<br/>
L’emplacement à partir duquel la deuxième valeur à comparer est lu.

*value*<br/>
La valeur à stocker à l’emplacement `_Dest` de `_Expected_value`mémoire spécifié par `_Dest` si est égal à .

### <a name="return-value"></a>Valeur de retour

**vrai** si l’opération est réussie; autrement, **faux**.

## <a name="atomic_exchange-function-c-amp"></a><a name="atomic_exchange"></a>fonction atomic_exchange (AMP DE C)

Définit la valeur de l’emplacement de destination en tant qu’opération atomique.

```cpp
inline int atomic_exchange(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_exchange(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)

inline float atomic_exchange(
    _Inout_ float* _Dest,
    float value
    ) restrict(amp)
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Pointeur vers l’emplacement de destination.

*value*<br/>
Nouvelle valeur.

### <a name="return-value"></a>Valeur de retour

La valeur originale de l’emplacement de destination.

## <a name="atomic_fetch_add-function-c-amp"></a><a name="atomic_fetch_add"></a>fonction atomic_fetch_add (AMP DE C)

Atomically ajouter une valeur à la valeur d’un emplacement de mémoire.

```cpp
inline int atomic_fetch_add(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_add(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Pointeur à l’emplacement de la mémoire.

*value*<br/>
Valeur à ajouter.

### <a name="return-value"></a>Valeur de retour

La valeur originale de l’emplacement de la mémoire.

## <a name="atomic_fetch_and-function-c-amp"></a><a name="atomic_fetch_and"></a>fonction atomic_fetch_and (AMP DE C)

Atomically effectue un peuwise ET le fonctionnement d’une valeur et la valeur d’un emplacement de mémoire.

```cpp
inline int atomic_fetch_and(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_and(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Pointeur à l’emplacement de la mémoire.

*value*<br/>
La valeur à utiliser dans le bitwise ET le calcul.

### <a name="return-value"></a>Valeur de retour

La valeur originale de l’emplacement de la mémoire.

## <a name="atomic_fetch_dec"></a><a name="atomic_fetch_dec"></a>atomic_fetch_dec

L’atome décrète atomiquement la valeur stockée à l’emplacement de mémoire spécifié.

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
L’emplacement en mémoire de la valeur à déc recréer.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine stockée à l’emplacement de la mémoire.

## <a name="atomic_fetch_inc"></a><a name="atomic_fetch_inc"></a>atomic_fetch_inc

Incréments atomiques de la valeur stockée à l’emplacement de mémoire spécifié.

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
L’emplacement en mémoire de la valeur à incrémenter.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine stockée à l’emplacement de la mémoire.

## <a name="atomic_fetch_max"></a><a name="atomic_fetch_max"></a>atomic_fetch_max

Atomically calcule la valeur maximale entre la valeur stockée à l’emplacement de mémoire spécifié dans le premier argument et la valeur spécifiée dans le deuxième argument, et la stocke au même emplacement de mémoire.

```cpp
inline int atomic_fetch_max(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_max(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
L’emplacement à partir duquel l’une des valeurs à comparer est lue et à laquelle le maximum des deux valeurs doit être stocké.

*value*<br/>
La valeur à comparer à la valeur à l’emplacement spécifié.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine stockée à l’emplacement spécifié.

## <a name="atomic_fetch_min"></a><a name="atomic_fetch_min"></a>atomic_fetch_min

Atomically calcule la valeur minimale entre la valeur stockée à l’emplacement de mémoire spécifié dans le premier argument et la valeur spécifiée dans le deuxième argument, et la stocke au même emplacement de mémoire.

```cpp
inline int atomic_fetch_min(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_min(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
L’emplacement à partir duquel l’une des valeurs à comparer est lue, et à laquelle le minimum des deux valeurs doit être stocké.

*value*<br/>
La valeur à comparer à la valeur à l’emplacement spécifié.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine stockée à l’emplacement spécifié.

## <a name="atomic_fetch_or-function-c-amp"></a><a name="atomic_fetch_or"></a>fonction atomic_fetch_or (AMP DE C)

Atomically effectue une opération peu sage OU avec une valeur et la valeur d’un emplacement de mémoire.

```cpp
inline int atomic_fetch_or(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_or(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Pointeur à l’emplacement de la mémoire.

*value*<br/>
La valeur à utiliser dans le calcul bitwise OU.

### <a name="return-value"></a>Valeur de retour

La valeur originale de l’emplacement de la mémoire.

## <a name="atomic_fetch_sub-function-c-amp"></a><a name="atomic_fetch_sub"></a>fonction atomic_fetch_sub (AMP DE C)

Il soustrait atomiquement une valeur à partir d’un emplacement de mémoire.

```cpp
inline int atomic_fetch_sub(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_sub(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Pointeur vers l’emplacement de destination.

*value*<br/>
La valeur à soustraire.

### <a name="return-value"></a>Valeur de retour

La valeur originale de l’emplacement de la mémoire.

## <a name="atomic_fetch_xor-function-c-amp"></a><a name="atomic_fetch_xor"></a>fonction atomic_fetch_xor (AMP DE C)

Atomically effectue une opération XOR peu sage d’une valeur et un emplacement de mémoire.

```cpp
inline int atomic_fetch_xor(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_xor(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Pointeur à l’emplacement de la mémoire.

*value*<br/>
La valeur à utiliser dans le calcul XOR.

### <a name="return-value"></a>Valeur de retour

La valeur originale de l’emplacement de la mémoire.

## <a name="copy"></a><a name="copy"></a>Copie

Copie d’un objet AMP C. Toutes les exigences de transfert de données synchrones sont remplies. Vous ne pouvez pas copier les données lors de l’exécution du code sur un accélérateur. La forme générale de `copy(src, dest)`cette fonction est .

```cpp
template <typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    array<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
   OutputIterator _DestIter);

template <typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<const value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<const value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    array_view<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    OutputIterator _DestIter);
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Objet cible de la copie.

*_DestIter*<br/>
Un itérateur de sortie à la position de début à destination.

*InputIterator (en)*<br/>
Type de l'itérateur d'entrée.

*Iterator De sortie*<br/>
Le type de l’itérateur de sortie.

*_Rank*<br/>
Le rang de l’objet à copier ou l’objet à copier.

*_Src*<br/>
Pour s’opposer à copier.

*_SrcFirst*<br/>
Un itérateur de début dans le récipient source.

*_SrcLast*<br/>
Un itérateur de fin dans le récipient source.

*value_type*<br/>
Le type de données des éléments copiés.

## <a name="copy_async"></a><a name="copy_async"></a>copy_async

Copie d’un objet AMP et renvoie un [objet completion_future](completion-future-class.md) qui peut être attendu. Vous ne pouvez pas copier les données lors de l’exécution du code sur un accélérateur.  La forme générale de `copy(src, dest)`cette fonction est .

```cpp
template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst,
    array<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src, OutputIterator _DestIter);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst,
    array_view<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src, OutputIterator _DestIter);
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Objet cible de la copie.

*_DestIter*<br/>
Un itérateur de sortie à la position de début à destination.

*InputIterator (en)*<br/>
Type de l'itérateur d'entrée.

*Iterator De sortie*<br/>
Le type de l’itérateur de sortie.

*_Rank*<br/>
Le rang de l’objet à copier ou l’objet à copier.

*_Src*<br/>
Pour s’opposer à copier.

*_SrcFirst*<br/>
Un itérateur de début dans le récipient source.

*_SrcLast*<br/>
Un itérateur de fin dans le récipient source.

*value_type*<br/>
Le type de données des éléments copiés.

### <a name="return-value"></a>Valeur de retour

Un `future<void>` qui peut être attendu.

## <a name="direct3d_abort"></a><a name="direct3d_abort"></a>direct3d_abort

Interrompt l’exécution d’une fonction avec la clause de restriction `restrict(amp)` . Lorsque le runtime AMP détecte l’appel, il déclenche une exception [runtime_exception](runtime-exception-class.md) avec le message d’erreur « Reference Rasterizer: Shader abort instruction hit ».

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a><a name="direct3d_errorf"></a>direct3d_errorf

Imprime une chaîne formatée à la fenêtre de sortie Visual Studio. Il est appelé à `restrict(amp)` partir d’une fonction avec la clause de restriction. Lorsque l’arrêt AMP détecte l’appel, il soulève une [runtime_exception](runtime-exception-class.md) exception avec la même chaîne de formatage.

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a><a name="direct3d_printf"></a>direct3d_printf

Imprime une chaîne formatée à la fenêtre de sortie Visual Studio. Il est appelé à `restrict(amp)` partir d’une fonction avec la clause de restriction.

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a><a name="global_memory_fence"></a>global_memory_fence

Bloque l’exécution de tous les fils dans une tuile jusqu’à ce que tous les accès à la mémoire mondiale aient été complétés. Cela garantit que les accès à la mémoire globale sont visibles à d’autres threads dans la tuile de fil, et sont exécutés dans l’ordre du programme.

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Barrier*<br/>
Un objet tile_barrier

## <a name="parallel_for_each-function-c-amp"></a><a name="parallel_for_each"></a>fonction parallel_for_each (AMP DE C)

Exécute une fonction à travers le domaine de calcul. Pour plus d’informations, voir [aperçu de l’AMP](../../../parallel/amp/cpp-amp-overview.md).

```cpp
template <int _Rank, typename _Kernel_type>
void parallel_for_each(
    const extent<_Rank>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
   const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Rank, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const extent<_Rank>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0>& _Compute_domain,
    const _Kernel_type& _Kernel);
```

### <a name="parameters"></a>Paramètres

*_Accl_view*<br/>
L’objet `accelerator_view` pour exécuter le calcul parallèle dessus.

*_Compute_domain*<br/>
Un `extent` objet qui contient les données pour le calcul.

*_Dim0*<br/>
La dimension `tiled_extent` de l’objet.

*_Dim1*<br/>
La dimension `tiled_extent` de l’objet.

*_Dim2*<br/>
La dimension `tiled_extent` de l’objet.

*_Kernel*<br/>
Un lambda ou un objet de fonction\<qui prend un argument de type "index _Rank>" et effectue le calcul parallèle.

*_Kernel_type*<br/>
Un lambda ou functor.

*_Rank*<br/>
Le rang de l’étendue.

## <a name="tile_static_memory_fence"></a><a name="tile_static_memory_fence"></a>tile_static_memory_fence

Bloque l’exécution de tous les fils `tile_static` dans une tuile jusqu’à ce que tous les accès à la mémoire en suspens aient été complétés. Cela garantit `tile_static` que les accès à la mémoire sont visibles à d’autres threads dans la tuile de fil, et que les accès sont exécutés dans l’ordre du programme.

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Barrier*<br/>
Un objet tile_barrier.

## <a name="see-also"></a>Voir aussi

[Concurrency Namespace (AMP)](concurrency-namespace-cpp-amp.md)
