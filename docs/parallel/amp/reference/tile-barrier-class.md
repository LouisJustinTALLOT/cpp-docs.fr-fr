---
title: tile_barrier, classe
ms.date: 03/27/2019
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
ms.openlocfilehash: 757309a10da3e6d1c9c053430cce2cf603380b1f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127762"
---
# <a name="tile_barrier-class"></a>tile_barrier, classe

Synchronise l’exécution des threads qui s’exécutent dans le groupe de threads (la vignette) à l’aide des méthodes `wait`. Seul le runtime peut instancier cette classe.

## <a name="syntax"></a>Syntaxe

```cpp
class tile_barrier;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[Constructeur tile_barrier](#ctor)|Initialise une nouvelle instance de la classe `tile_barrier`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[qu'](#wait)|Ordonne à tous les threads dans le groupe de threads (vignette) de cesser de s’exécuter jusqu’à ce que tous les threads de la mosaïque aient fini d’attendre.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les accès à la mémoire aient été effectués et que tous les threads de la mosaïque aient atteint cet appel.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les accès à la mémoire globale aient été effectués et que tous les threads de la mosaïque aient atteint cet appel.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les accès à la mémoire `tile_static` aient été effectués et que tous les threads de la mosaïque aient atteint cet appel.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tile_barrier`

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="ctor"></a>Constructeur tile_barrier

Initialise une nouvelle instance de la classe en copiant une instance existante.

### <a name="syntax"></a>Syntaxe

```cpp
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet `tile_barrier` à copier.

## <a name="wait"></a>wait

Indique à tous les threads dans le groupe de threads (vignette) d’arrêter l’exécution jusqu’à ce que tous les threads de la mosaïque aient fini de s’attendre.

### <a name="syntax"></a>Syntaxe

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les threads d’une vignette aient atteint cet appel. Cela garantit que tous les accès mémoire sont visibles par d’autres threads dans la vignette de thread et ont été exécutés dans l’ordre du programme.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence"> wait_with_global_memory_fence

Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les threads d’une vignette aient atteint cet appel. Cela garantit que tous les accès mémoire globaux sont visibles par d’autres threads dans la vignette de thread et ont été exécutés dans l’ordre du programme.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence"> wait_with_tile_static_memory_fence

Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les threads d’une vignette aient atteint cet appel. Cela garantit que les accès à la mémoire `tile_static` sont visibles par d’autres threads dans la vignette de thread et ont été exécutés dans l’ordre du programme.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
