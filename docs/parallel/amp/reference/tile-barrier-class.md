---
title: tile_barrier, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 4336a4cc317344c881f60e5ed4c5bdf8328a34b8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301166"
---
# <a name="tilebarrier-class"></a>tile_barrier, classe

Synchronise l’exécution des threads qui s’exécutent dans le groupe de threads (la mosaïque) à l’aide de `wait` méthodes. Que le runtime peut instancier cette classe.

### <a name="syntax"></a>Syntaxe

```
class tile_barrier;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[tile_barrier, constructeur](#ctor)|Initialise une nouvelle instance de la classe `tile_barrier`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[wait](#wait)|Indique à tous les threads dans le groupe de threads (mosaïque) d’arrêter l’exécution jusqu'à ce que tous les threads dans la mosaïque aient terminé l’attente.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous les accès mémoire aient été effectués et tous les threads dans la mosaïque aient atteint cet appel.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous les accès mémoire globaux aient été effectués et que tous les threads dans la mosaïque aient atteint cet appel.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous `tile_static` accès mémoire aient été effectués et que tous les threads dans la mosaïque aient atteint cet appel.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tile_barrier`

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrence

## <a name="tile_barrier__ctor"></a>  tile_barrier, constructeur

Initialise une nouvelle instance de la classe en copiant une existante.

### <a name="syntax"></a>Syntaxe

```
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Le `tile_barrier` objet à copier.

## <a name="wait"></a>  wait

Indique à tous les threads dans le groupe de threads (mosaïque) pour arrêter l’exécution jusqu'à ce que tous les threads dans la mosaïque aient terminé l’attente.

### <a name="syntax"></a>Syntaxe

```
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a>  wait_with_all_memory_fence

Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous les threads dans une mosaïque aient atteint cet appel. Cela garantit que tous les accès mémoire sont visibles à d’autres threads dans la mosaïque de threads et ont été exécutés dans l’ordre du programme.

### <a name="syntax"></a>Syntaxe

```
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="wait_with_global_memory_fence"></a>  wait_with_global_memory_fence

Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous les threads dans une mosaïque aient atteint cet appel. Cela garantit que tous les accès mémoire globaux sont visibles à d’autres threads dans la mosaïque de threads et ont été exécutés dans l’ordre du programme.

### <a name="syntax"></a>Syntaxe

```
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="wait_with_tile_static_memory_fence"></a>  wait_with_tile_static_memory_fence

Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous les threads dans une mosaïque aient atteint cet appel. Cela garantit que `tile_static` mémoire les accès sont visibles à d’autres threads dans la mosaïque de threads et ont été exécutés dans l’ordre du programme.

### <a name="syntax"></a>Syntaxe

```
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
