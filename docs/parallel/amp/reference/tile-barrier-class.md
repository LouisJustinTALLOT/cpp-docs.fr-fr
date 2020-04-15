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
ms.openlocfilehash: c00f1e41e70e723be185959eeff176390def7647
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374724"
---
# <a name="tile_barrier-class"></a>tile_barrier, classe

Synchronise l’exécution des fils qui sont en cours d’exécution `wait` dans le groupe de thread (la tuile) en utilisant des méthodes. Seul le temps d’exécution peut instantanément cette classe.

## <a name="syntax"></a>Syntaxe

```cpp
class tile_barrier;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[tile_barrier Constructeur](#ctor)|Initialise une nouvelle instance de la classe `tile_barrier`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Attendre](#wait)|Demande à tous les fils du groupe de thread (tuile) d’arrêter d’exécuter jusqu’à ce que tous les fils de la tuile aient fini d’attendre.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Bloque l’exécution de tous les fils dans une tuile jusqu’à ce que tous les accès à la mémoire ont été complétés et tous les fils de la tuile ont atteint cet appel.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Bloque l’exécution de tous les fils dans une tuile jusqu’à ce que tous les accès à la mémoire globale ont été complétés et tous les fils dans la tuile ont atteint cet appel.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Bloque l’exécution de tous les `tile_static` fils dans une tuile jusqu’à ce que tous les accès à la mémoire ont été complétés et tous les fils de la tuile ont atteint cet appel.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tile_barrier`

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="tile_barrier-constructor"></a><a name="ctor"></a>tile_barrier Constructeur

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

Demande à tous les fils du groupe de thread (tuile) d’arrêter l’exécution jusqu’à ce que tous les fils de la tuile aient fini d’attendre.

### <a name="syntax"></a>Syntaxe

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a><a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

Bloque l’exécution de tous les fils dans une tuile jusqu’à ce que tous les fils d’une tuile aient atteint cet appel. Cela garantit que tous les accès à la mémoire sont visibles à d’autres threads dans la tuile de fil, et ont été exécutés dans l’ordre du programme.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence">wait_with_global_memory_fence

Bloque l’exécution de tous les fils dans une tuile jusqu’à ce que tous les fils d’une tuile aient atteint cet appel. Cela garantit que tous les accès à la mémoire globale sont visibles à d’autres threads dans la tuile de fil, et ont été exécutés dans l’ordre du programme.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence">wait_with_tile_static_memory_fence

Bloque l’exécution de tous les fils dans une tuile jusqu’à ce que tous les fils d’une tuile aient atteint cet appel. Cela garantit `tile_static` que les accès à la mémoire sont visibles à d’autres threads dans la tuile de fil, et ont été exécutés dans l’ordre du programme.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Voir aussi

[Concurrency Namespace (AMP)](concurrency-namespace-cpp-amp.md)
