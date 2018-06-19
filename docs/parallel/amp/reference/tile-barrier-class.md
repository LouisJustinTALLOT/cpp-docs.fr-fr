---
title: tile_barrier, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
dev_langs:
- C++
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62e81b7cab8d7e8774e6ac50c5de5f256d76b232
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686488"
---
# <a name="tilebarrier-class"></a>tile_barrier, classe
Synchronise l’exécution des threads qui s’exécutent dans le groupe de threads (la mosaïque) à l’aide de `wait` méthodes. Seulement le runtime peut instancier cette classe.  
  
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
|[attente](#wait)|Fait en sorte que tous les threads dans le groupe de threads (mosaïque) pour arrêter l’exécution jusqu'à la fin de tous les threads dans la vignette en attente.|  
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous les accès mémoire ont été effectuées et de tous les threads dans la vignette a été atteint cet appel.|  
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous les accès mémoire globale ont été effectuées et de tous les threads dans la vignette ont atteint cet appel.|  
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Bloque l’exécution de tous les threads dans une vignette tant que tous les `tile_static` accès mémoire ont été effectuées et de tous les threads dans la vignette ont atteint cet appel.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `tile_barrier`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** amp.h  
  
 **Espace de noms :** Concurrency  

## <a name="tile_barrier__ctor"></a>  tile_barrier, constructeur  
 Initialise une nouvelle instance de la classe en copiant un existant.  
  
### <a name="syntax"></a>Syntaxe 
  
```  
tile_barrier(  
    const tile_barrier& _Other ) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `tile_barrier` objet à copier.  

## <a name="wait"></a>  attente 
Fait en sorte que tous les threads dans le groupe de threads (mosaïque) pour arrêter l’exécution jusqu'à la fin de tous les threads dans la vignette en attente.  
  
### <a name="syntax"></a>Syntaxe 
  
```  
void wait() const restrict(amp);  
```    

## <a name="wait_with_all_memory_fence"></a>  wait_with_all_memory_fence   
Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous les threads dans une vignette ont atteint cet appel. Cela garantit que tous les accès mémoire sont visibles à d’autres threads dans la vignette de thread et ont été exécutées dans l’ordre du programme.  
  
### <a name="syntax"></a>Syntaxe 
  
```  
void wait_with_all_memory_fence() const restrict(amp);  
```  
  

## <a name="wait_with_global_memory_fence"></a>  wait_with_global_memory_fence   
Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous les threads dans une vignette ont atteint cet appel. Cela garantit que tous les accès mémoire globale sont visibles à d’autres threads dans la vignette de thread et ont été exécutées dans l’ordre du programme.  
  
### <a name="syntax"></a>Syntaxe 
  
```  
void wait_with_global_memory_fence() const  restrict(amp);  
```

## <a name="wait_with_tile_static_memory_fence"></a>  wait_with_tile_static_memory_fence   
Bloque l’exécution de tous les threads dans une mosaïque jusqu'à ce que tous les threads dans une vignette ont atteint cet appel. Cela garantit que `tile_static` mémoire accès sont visibles à d’autres threads dans la vignette de thread et ont été exécutées dans l’ordre du programme.  
  
### <a name="syntax"></a>Syntaxe 
  
```  
void wait_with_tile_static_memory_fence() const restrict(amp);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
