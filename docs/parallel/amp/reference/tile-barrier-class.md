---
description: 'En savoir plus sur : classe tile_barrier'
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
ms.openlocfilehash: b4fd1758f9786f4cbb78556daadb0801795ca9c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321706"
---
# <a name="tile_barrier-class"></a>tile_barrier, classe

Synchronise l’exécution des threads qui s’exécutent dans le groupe de threads (la vignette) à l’aide de `wait` méthodes. Seul le runtime peut instancier cette classe.

## <a name="syntax"></a>Syntaxe

```cpp
class tile_barrier;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur tile_barrier](#ctor)|Initialise une nouvelle instance de la classe `tile_barrier`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[wait](#wait)|Ordonne à tous les threads dans le groupe de threads (vignette) de cesser de s’exécuter jusqu’à ce que tous les threads de la mosaïque aient fini d’attendre.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les accès à la mémoire aient été effectués et que tous les threads de la mosaïque aient atteint cet appel.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les accès à la mémoire globale aient été effectués et que tous les threads de la mosaïque aient atteint cet appel.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les `tile_static` accès à la mémoire aient été effectués et que tous les threads de la mosaïque aient atteint cet appel.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tile_barrier`

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="tile_barrier-constructor"></a><a name="ctor"></a> Constructeur tile_barrier

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

## <a name="wait_with_all_memory_fence"></a><a name="wait_with_all_memory_fence"></a> wait_with_all_memory_fence

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

Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les threads d’une vignette aient atteint cet appel. Cela permet de `tile_static` s’assurer que les accès mémoire sont visibles par d’autres threads dans la vignette de thread et ont été exécutés dans l’ordre du programme.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
