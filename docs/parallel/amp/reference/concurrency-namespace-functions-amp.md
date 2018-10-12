---
title: Fonctions d’accès concurrentiel de l’espace de noms (AMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 211005f273500992440c0e95d2c3c4e3adcef581
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163411"
---
# <a name="concurrency-namespace-functions-amp"></a>Fonctions d’accès concurrentiel de l’espace de noms (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[atomic_exchange, fonction (C++ AMP)](#atomic_exchange)|[atomic_fetch_add, fonction (C++ AMP)](#atomic_fetch_add)|[atomic_fetch_and, fonction (C++ AMP)](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or, fonction (C++ AMP)](#atomic_fetch_or)|[atomic_fetch_sub, fonction (C++ AMP)](#atomic_fetch_sub)|
|[atomic_fetch_xor, fonction (C++ AMP)](#atomic_fetch_xor)|[copy](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[parallel_for_each, fonction (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

##  <a name="all_memory_fence"></a>  all_memory_fence

Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous les accès mémoire aient été effectués. Cela garantit que tous les accès mémoire sont visibles à d’autres threads dans la mosaïque de threads et sont exécutés dans l’ordre de programme.

```
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Barrier*<br/>
Objet `tile_barrier`.

##  <a name="amp_uninitialize"></a>  amp_uninitialize

N’initialise pas le runtime C++ AMP. Il est permis d’appeler cette fonction plusieurs fois pendant une durée de vie des applications. Appel de n’importe quel après API C++ AMP appeler cette fonction va se réinitialiser le runtime C++ AMP. Notez qu’il est interdit d’utiliser des objets de C++ AMP entre les appels à cette fonction et cela provoquera un comportement non défini. En outre, appel simultané de cette fonction et toute autre APIs AMP est non conforme et provoquerait un comportement non défini.

```
void __cdecl amp_uninitialize();
```

##  <a name="atomic_compare_exchange"></a>  atomic_compare_exchange

Compare atomiquement la valeur stockée dans un emplacement mémoire spécifié dans le premier argument pour l’égalité avec la valeur du deuxième argument spécifié, et si les valeurs sont identiques, la valeur à l’emplacement de mémoire est modifiée à ce que du troisième argument spécifié.

```
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
L’emplacement à partir duquel l’une des valeurs à comparer est lue, et à laquelle la nouvelle valeur, le cas échéant, doit être stocké.

*_Expected_value*<br/>
L’emplacement à partir duquel la deuxième valeur à comparer est lue.

*valeur*<br/>
La valeur à stocker à l’emplacement de mémoire spécifié dans par `_Dest` si `_Dest` est égal à `_Expected_value`.

### <a name="return-value"></a>Valeur de retour

**true** si l’opération a réussi ; sinon, **false**.

##  <a name="atomic_exchange"></a>  atomic_exchange, fonction (C++ AMP)

Définit la valeur de l’emplacement de destination comme une opération atomique.

```
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

*valeur*<br/>
Nouvelle valeur.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine de l’emplacement de destination.

##  <a name="atomic_fetch_add"></a>  atomic_fetch_add, fonction (C++ AMP)

Ajouter de manière atomique une valeur à la valeur d’un emplacement de mémoire.

```
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

*valeur*<br/>
Valeur à ajouter.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine de l’emplacement de mémoire.

##  <a name="atomic_fetch_and"></a>  atomic_fetch_and, fonction (C++ AMP)

Atomiquement effectue une opération AND au niveau du bit d’une valeur et la valeur d’un emplacement de mémoire.

```
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

*valeur*<br/>
La valeur à utiliser dans le calcul AND au niveau du bit.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine de l’emplacement de mémoire.

##  <a name="atomic_fetch_dec"></a>  atomic_fetch_dec

Atomiquement décrémente la valeur stockée à l’emplacement de mémoire spécifié.

```
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Emplacement dans la mémoire de la valeur à décrémenter.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine enregistrée à l’emplacement de mémoire.

##  <a name="atomic_fetch_inc"></a>  atomic_fetch_inc

Incrémente atomiquement la valeur stockée à l’emplacement de mémoire spécifié.

```
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Dest*<br/>
Emplacement dans la mémoire de la valeur à incrémenter.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine enregistrée à l’emplacement de mémoire.

##  <a name="atomic_fetch_max"></a>  atomic_fetch_max

Atomiquement calcule la valeur maximale entre la valeur stockée à l’emplacement de mémoire spécifié dans le premier argument et la valeur spécifiée dans le deuxième argument et le stocke dans le même emplacement de mémoire.

```
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
L’emplacement à partir duquel l’une des valeurs à comparer est lue, et à laquelle la valeur maximale de deux valeurs doit être stocké.

*valeur*<br/>
La valeur à comparer à la valeur à l’emplacement spécifié.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine enregistrée à l’emplacement spécifié.

##  <a name="atomic_fetch_min"></a>  atomic_fetch_min

Atomiquement calcule la valeur minimale entre la valeur stockée à l’emplacement de mémoire spécifié dans le premier argument et la valeur spécifiée dans le deuxième argument et le stocke dans le même emplacement de mémoire.

```
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
L’emplacement à partir duquel l’une des valeurs à comparer est lue, et dans lequel la valeur minimale de deux valeurs à stocker.

*valeur*<br/>
La valeur à comparer à la valeur à l’emplacement spécifié.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine enregistrée à l’emplacement spécifié.

##  <a name="atomic_fetch_or"></a>  atomic_fetch_or, fonction (C++ AMP)

Atomiquement effectue une opération OR au niveau du bit avec une valeur et la valeur d’un emplacement de mémoire.

```
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

*valeur*<br/>
La valeur à utiliser dans le calcul d’OR au niveau du bit.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine de l’emplacement de mémoire.

##  <a name="atomic_fetch_sub"></a>  atomic_fetch_sub, fonction (C++ AMP)

Atomiquement soustrait une valeur à partir d’un emplacement de mémoire.

```
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

*valeur*<br/>
La valeur à soustraire.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine de l’emplacement de mémoire.

##  <a name="atomic_fetch_xor"></a>  atomic_fetch_xor, fonction (C++ AMP)

Effectue une opération XOR au niveau du bit d’une valeur et un emplacement de mémoire de manière atomique.

```
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

*valeur*<br/>
La valeur à utiliser dans le calcul XOR.

### <a name="return-value"></a>Valeur de retour

La valeur d’origine de l’emplacement de mémoire.

##  <a name="copy"></a>  copy

Copie un objet C++ AMP. Toutes les exigences de transfert de données synchrone sont remplies. Vous ne pouvez pas copier des données lors de l’exécution de code sur un accélérateur. La forme générale de cette fonction est `copy(src, dest)`.

```
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
L’objet dans lequel copier.

*_DestIter*<br/>
Itérateur de sortie à la position de début à la destination.

*InputIterator*<br/>
Le type de l’itérateur d’entrée.

*OutputIterator*<br/>
Le type de l’itérateur de sortie.

*_Rank*<br/>
Le rang de l’objet à copier à partir d’ou de l’objet dans lequel copier.

*_Src*<br/>
Objet à copier.

*_SrcFirst*<br/>
Un itérateur de départ dans le conteneur source.

*_SrcLast*<br/>
Un itérateur de fin dans le conteneur source.

*value_type*<br/>
Le type de données des éléments qui sont copiés.

##  <a name="copy_async"></a>  copy_async

Copie un objet C++ AMP et renvoie un [completion_future](completion-future-class.md) objet qui peut être attendu. Vous ne pouvez pas copier des données lors de l’exécution de code sur un accélérateur.  La forme générale de cette fonction est `copy(src, dest)`.

```
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
L’objet dans lequel copier.

*_DestIter*<br/>
Itérateur de sortie à la position de début à la destination.

*InputIterator*<br/>
Le type de l’itérateur d’entrée.

*OutputIterator*<br/>
Le type de l’itérateur de sortie.

*_Rank*<br/>
Le rang de l’objet à copier à partir d’ou de l’objet dans lequel copier.

*_Src*<br/>
Objet à copier.

*_SrcFirst*<br/>
Un itérateur de départ dans le conteneur source.

*_SrcLast*<br/>
Un itérateur de fin dans le conteneur source.

*value_type*<br/>
Le type de données des éléments qui sont copiés.

### <a name="return-value"></a>Valeur de retour

Un `future<void>` qui peut être attendu.

##  <a name="direct3d_abort"></a>  direct3d_abort

Interrompt l’exécution d’une fonction avec la clause de restriction `restrict(amp)` . Lorsque le runtime AMP détecte l’appel, il déclenche une exception [runtime_exception](runtime-exception-class.md) avec le message d’erreur « Reference Rasterizer: Shader abort instruction hit ».

```
void direct3d_abort() restrict(amp);
```

##  <a name="direct3d_errorf"></a>  direct3d_errorf

Imprime une chaîne mise en forme dans la fenêtre de sortie de Visual Studio. Elle est appelée à partir d’une fonction avec la `restrict(amp)` clause de restriction. Lorsque le runtime AMP détecte l’appel, il déclenche une [runtime_exception](runtime-exception-class.md) exception avec la même chaîne de mise en forme.

```
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

##  <a name="direct3d_printf"></a>  direct3d_printf

Imprime une chaîne mise en forme dans la fenêtre de sortie de Visual Studio. Elle est appelée à partir d’une fonction avec la `restrict(amp)` clause de restriction.

```
void direct3d_printf(
    const char *,
...) restrict(amp);
```

##  <a name="global_memory_fence"></a>  global_memory_fence

Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que toute la mémoire globale accès ont été effectuées. Cela garantit que les accès mémoire globaux sont visibles à d’autres threads dans la mosaïque de threads et sont exécutés dans l’ordre de programme.

```
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Barrier*<br/>
Un objet tile_barrier

##  <a name="parallel_for_each"></a>  parallel_for_each, fonction (C++ AMP)

Exécute une fonction sur le domaine de calcul. Pour plus d’informations, consultez [présentation de C++ AMP](../../../parallel/amp/cpp-amp-overview.md).

```
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
Le `accelerator_view` objet pour exécuter le calcul parallèle sur.

*_Compute_domain*<br/>
Un `extent` objet qui contient les données pour le calcul.

*_Dim0*<br/>
La dimension de la `tiled_extent` objet.

*_Dim1*<br/>
La dimension de la `tiled_extent` objet.

*_Dim2*<br/>
La dimension de la `tiled_extent` objet.

*_Kernel*<br/>
Un objet lambda ou une fonction qui accepte un argument de type « index\<_Rank > » et effectue le calcul parallèle.

*_Kernel_type*<br/>
Une expression lambda ou un functor.

*_Rank*<br/>
Le rang de l’étendue.

##  <a name="tile_static_memory_fence"></a>  tile_static_memory_fence

Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous en suspens `tile_static` accès mémoire aient été effectués. Cela garantit que `tile_static` accès mémoire sont visibles à d’autres threads dans la mosaïque de threads et d’accès sont exécutés dans l’ordre du programme.

```
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Barrier*<br/>
Un objet tile_barrier.

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
