---
description: 'En savoir plus sur : fonctions d’espace de noms d’accès concurrentiel (AMP)'
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
ms.openlocfilehash: 65255f14acdc402003be46de5f978da6d9a8f8ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211815"
---
# <a name="concurrency-namespace-functions-amp"></a>Concurrency, fonctions de l’espace de noms (AMP)

:::row:::
   :::column span="":::
      [`all_memory_fence`](#all_memory_fence)\
      [`amp_uninitialize`](#amp_uninitialize)\
      [`atomic_compare_exchange`](#atomic_compare_exchange)\
      [`atomic_exchange`](#atomic_exchange)\
      [`atomic_fetch_add`](#atomic_fetch_add)\
      [`atomic_fetch_and`](#atomic_fetch_and)
   :::column-end:::
   :::column span="":::
      [`atomic_fetch_dec`](#atomic_fetch_dec)\
      [`atomic_fetch_inc`](#atomic_fetch_inc)\
      [`atomic_fetch_max`](#atomic_fetch_max)\
      [`atomic_fetch_min`](#atomic_fetch_min)\
      [`atomic_fetch_or`](#atomic_fetch_or)
   :::column-end:::
   :::column span="":::
      [`atomic_fetch_sub`](#atomic_fetch_sub)\
      [`atomic_fetch_xor`](#atomic_fetch_xor)\
      [`copy`](#copy)\
      [`copy_async`](#copy_async)\
      [`direct3d_abort`](#direct3d_abort)
   :::column-end:::
   :::column span="":::
      [`direct3d_errorf`](#direct3d_errorf)\
      [`direct3d_printf`](#direct3d_printf)\
      [`global_memory_fence`](#global_memory_fence)\
      [`parallel_for_each`](#parallel_for_each)\
      [`tile_static_memory_fence`](#tile_static_memory_fence)
   :::column-end:::
:::row-end:::

## <a name="all_memory_fence"></a><a name="all_memory_fence"></a> all_memory_fence

Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les accès à la mémoire aient été effectués. Cela garantit que tous les accès mémoire sont visibles par d’autres threads dans la vignette de thread et sont exécutés dans l’ordre du programme.

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Barrier*<br/>
Objet `tile_barrier`.

## <a name="amp_uninitialize"></a><a name="amp_uninitialize"></a> amp_uninitialize

Réinitialise le runtime C++ AMP. Il est légal d’appeler cette fonction plusieurs fois pendant la durée de vie d’une application. L’appel de toute API C++ AMP après l’appel de cette fonction réinitialisera le runtime C++ AMP. Notez qu’il n’est pas conforme d’utiliser des objets C++ AMP entre les appels à cette fonction et cela entraînera un comportement indéfini. En outre, l’appel simultané de cette fonction et de toutes les autres API AMP est illégal et provoquerait un comportement indéfini.

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a><a name="atomic_compare_exchange"></a> atomic_compare_exchange

Compare atomiquement la valeur stockée à un emplacement de mémoire spécifié dans le premier argument pour l’égalité avec la valeur du deuxième argument spécifié, et si les valeurs sont identiques, la valeur à l’emplacement de la mémoire est remplacée par celle du troisième argument spécifié.

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
Emplacement à partir duquel l’une des valeurs à comparer est lue, et dans laquelle la nouvelle valeur, le cas échéant, doit être stockée.

*_Expected_value*<br/>
Emplacement à partir duquel la deuxième valeur à comparer est lue.

*value*<br/>
Valeur à stocker dans l’emplacement de mémoire spécifié dans par `_Dest` si `_Dest` est égal à `_Expected_value` .

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’opération réussit ; Sinon, **`false`** .

## <a name="atomic_exchange-function-c-amp"></a><a name="atomic_exchange"></a> Fonction atomic_exchange (C++ AMP)

Définit la valeur de l’emplacement de destination sous la forme d’une opération atomique.

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

### <a name="return-value"></a>Valeur renvoyée

Valeur d’origine de l’emplacement de destination.

## <a name="atomic_fetch_add-function-c-amp"></a><a name="atomic_fetch_add"></a> Fonction atomic_fetch_add (C++ AMP)

Ajoute atomiquement une valeur à la valeur d’un emplacement de mémoire.

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
Pointeur vers l’emplacement de mémoire.

*value*<br/>
Valeur à ajouter.

### <a name="return-value"></a>Valeur renvoyée

Valeur d’origine de l’emplacement de mémoire.

## <a name="atomic_fetch_and-function-c-amp"></a><a name="atomic_fetch_and"></a> Fonction atomic_fetch_and (C++ AMP)

Effectue atomiquement une opération and au niveau du bit d’une valeur et la valeur d’un emplacement de mémoire.

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
Pointeur vers l’emplacement de mémoire.

*value*<br/>
Valeur à utiliser dans le calcul and au niveau du bit.

### <a name="return-value"></a>Valeur renvoyée

Valeur d’origine de l’emplacement de mémoire.

## <a name="atomic_fetch_dec"></a><a name="atomic_fetch_dec"></a> atomic_fetch_dec

Décrémente atomiquement la valeur stockée à l’emplacement de mémoire spécifié.

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Emplacement en mémoire de la valeur à décrémenter.

### <a name="return-value"></a>Valeur renvoyée

Valeur d’origine stockée à l’emplacement de mémoire.

## <a name="atomic_fetch_inc"></a><a name="atomic_fetch_inc"></a> atomic_fetch_inc

Incrémente atomiquement la valeur stockée à l’emplacement de mémoire spécifié.

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Emplacement en mémoire de la valeur à incrémenter.

### <a name="return-value"></a>Valeur renvoyée

Valeur d’origine stockée à l’emplacement de mémoire.

## <a name="atomic_fetch_max"></a><a name="atomic_fetch_max"></a> atomic_fetch_max

Calcule atomiquement la valeur maximale entre la valeur stockée à l’emplacement de mémoire spécifié dans le premier argument et la valeur spécifiée dans le deuxième argument, et la stocke dans le même emplacement de mémoire.

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
L’emplacement à partir duquel l’une des valeurs à comparer est lue, et dans lequel le maximum des deux valeurs doit être stocké.

*value*<br/>
Valeur à comparer à la valeur à l’emplacement spécifié.

### <a name="return-value"></a>Valeur renvoyée

Valeur d’origine stockée à l’emplacement d’emplacement spécifié.

## <a name="atomic_fetch_min"></a><a name="atomic_fetch_min"></a> atomic_fetch_min

Calcule atomiquement la valeur minimale entre la valeur stockée à l’emplacement de mémoire spécifié dans le premier argument et la valeur spécifiée dans le deuxième argument, et la stocke dans le même emplacement de mémoire.

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
L’emplacement à partir duquel l’une des valeurs à comparer est lue, et dans lequel le minimum des deux valeurs doit être stocké.

*value*<br/>
Valeur à comparer à la valeur à l’emplacement spécifié.

### <a name="return-value"></a>Valeur renvoyée

Valeur d’origine stockée à l’emplacement d’emplacement spécifié.

## <a name="atomic_fetch_or-function-c-amp"></a><a name="atomic_fetch_or"></a> Fonction atomic_fetch_or (C++ AMP)

Effectue atomiquement une opération or au niveau du bit avec une valeur et la valeur d’un emplacement de mémoire.

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
Pointeur vers l’emplacement de mémoire.

*value*<br/>
Valeur à utiliser dans le calcul de bits or.

### <a name="return-value"></a>Valeur renvoyée

Valeur d’origine de l’emplacement de mémoire.

## <a name="atomic_fetch_sub-function-c-amp"></a><a name="atomic_fetch_sub"></a> Fonction atomic_fetch_sub (C++ AMP)

Soustrait de manière atomique une valeur d’un emplacement de mémoire.

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
Valeur à soustraire.

### <a name="return-value"></a>Valeur renvoyée

Valeur d’origine de l’emplacement de mémoire.

## <a name="atomic_fetch_xor-function-c-amp"></a><a name="atomic_fetch_xor"></a> Fonction atomic_fetch_xor (C++ AMP)

Effectue atomiquement une opération XOR au niveau du bit d’une valeur et d’un emplacement de mémoire.

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
Pointeur vers l’emplacement de mémoire.

*value*<br/>
Valeur à utiliser dans le calcul XOR.

### <a name="return-value"></a>Valeur renvoyée

Valeur d’origine de l’emplacement de mémoire.

## <a name="copy"></a><a name="copy"></a> reprographie

Copie un objet C++ AMP. Toutes les exigences de transfert de données synchrones sont respectées. Vous ne pouvez pas copier de données lors de l’exécution du code sur un accélérateur. La forme générale de cette fonction est `copy(src, dest)` .

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
Itérateur de sortie à la position de début à la destination.

*InputIterator*<br/>
Type de l'itérateur d'entrée.

*OutputIterator*<br/>
Type de l’itérateur de sortie.

*_Rank*<br/>
Rang de l’objet à partir duquel effectuer la copie ou de l’objet vers lequel effectuer la copie.

*_Src*<br/>
À l’objet à copier.

*_SrcFirst*<br/>
Itérateur de début dans le conteneur source.

*_SrcLast*<br/>
Itérateur de fin dans le conteneur source.

*value_type*<br/>
Type de données des éléments copiés.

## <a name="copy_async"></a><a name="copy_async"></a> copy_async

Copie un objet C++ AMP et retourne un objet [completion_future](completion-future-class.md) qui peut être attendu. Vous ne pouvez pas copier de données lors de l’exécution du code sur un accélérateur.  La forme générale de cette fonction est `copy(src, dest)` .

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
Itérateur de sortie à la position de début à la destination.

*InputIterator*<br/>
Type de l'itérateur d'entrée.

*OutputIterator*<br/>
Type de l’itérateur de sortie.

*_Rank*<br/>
Rang de l’objet à partir duquel effectuer la copie ou de l’objet vers lequel effectuer la copie.

*_Src*<br/>
À l’objet à copier.

*_SrcFirst*<br/>
Itérateur de début dans le conteneur source.

*_SrcLast*<br/>
Itérateur de fin dans le conteneur source.

*value_type*<br/>
Type de données des éléments copiés.

### <a name="return-value"></a>Valeur renvoyée

`future<void>`Qui peut être attendu.

## <a name="direct3d_abort"></a><a name="direct3d_abort"></a> direct3d_abort

Interrompt l’exécution d’une fonction avec la clause de restriction `restrict(amp)` . Lorsque le runtime AMP détecte l’appel, il déclenche une exception [runtime_exception](runtime-exception-class.md) avec le message d’erreur « Reference Rasterizer: Shader abort instruction hit ».

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a><a name="direct3d_errorf"></a> direct3d_errorf

Imprime une chaîne mise en forme dans la fenêtre sortie de Visual Studio. Elle est appelée à partir d’une fonction avec la `restrict(amp)` clause de restriction. Quand le runtime AMP détecte l’appel, il déclenche une exception [runtime_exception](runtime-exception-class.md) avec la même chaîne de mise en forme.

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a><a name="direct3d_printf"></a> direct3d_printf

Imprime une chaîne mise en forme dans la fenêtre sortie de Visual Studio. Elle est appelée à partir d’une fonction avec la `restrict(amp)` clause de restriction.

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a><a name="global_memory_fence"></a> global_memory_fence

Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les accès à la mémoire globale aient été effectués. Cela permet de s’assurer que les accès mémoire globaux sont visibles par d’autres threads dans la vignette de thread et sont exécutés dans l’ordre du programme.

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Barrier*<br/>
Objet tile_barrier

## <a name="parallel_for_each-function-c-amp"></a><a name="parallel_for_each"></a> Fonction parallel_for_each (C++ AMP)

Exécute une fonction sur le domaine de calcul. Pour plus d’informations, consultez [C++ amp vue d’ensemble](../../../parallel/amp/cpp-amp-overview.md).

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
`accelerator_view`Objet sur lequel exécuter le calcul parallèle.

*_Compute_domain*<br/>
`extent`Objet qui contient les données pour le calcul.

*_Dim0*<br/>
Dimension de l' `tiled_extent` objet.

*_Dim1*<br/>
Dimension de l' `tiled_extent` objet.

*_Dim2*<br/>
Dimension de l' `tiled_extent` objet.

*_Kernel*<br/>
Objet lambda ou de fonction qui prend un argument de type « index \<_Rank> » et effectue le calcul parallèle.

*_Kernel_type*<br/>
Lambda ou functor.

*_Rank*<br/>
Rang de l’étendue.

## <a name="tile_static_memory_fence"></a><a name="tile_static_memory_fence"></a> tile_static_memory_fence

Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les accès à la mémoire en suspens `tile_static` aient été effectués. Cela permet de s’assurer que `tile_static` les accès mémoire sont visibles par d’autres threads dans la vignette de thread, et que les accès sont exécutés dans l’ordre du programme.

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Barrier*<br/>
Objet tile_barrier.

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
