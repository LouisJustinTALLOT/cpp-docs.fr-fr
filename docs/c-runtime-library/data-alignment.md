---
title: Alignement des données
ms.date: 11/04/2016
f1_keywords:
- data.alignment
helpviewer_keywords:
- data alignment [C++]
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
ms.openlocfilehash: 7d835545bdc1f94de56846f35d510927c06c2560
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520283"
---
# <a name="data-alignment"></a>Alignement des données

Les fonctions Runtime C suivantes prennent en charge l’alignement des données.

## <a name="data-alignment-routines"></a>Routines d’alignement des données

|Routine|Utilisez|
|-------------|---------|
|[_aligned_free](../c-runtime-library/reference/aligned-free.md)|Libère un bloc de mémoire qui a été alloué avec [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) ou [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md).|
|[_aligned_free_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|Libère un bloc de mémoire qui a été alloué avec [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) ou [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) (version de débogage uniquement).|
|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)|Alloue de la mémoire sur une limite d'alignement spécifiée.|
|[_aligned_malloc_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|Alloue de la mémoire sur une limite d'alignement spécifiée avec de l'espace supplémentaire pour un en-tête de débogage et des mémoires tampons de remplacement (version de débogage uniquement).|
|[_aligned_msize](../c-runtime-library/reference/aligned-msize.md)|Retourne la taille d’un bloc de mémoire alloué dans le tas.|
|[_aligned_msize_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|Retourne la taille d’un bloc de mémoire alloué dans le tas (version de débogage uniquement).|
|[_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|Alloue de la mémoire sur une limite d'alignement spécifiée.|
|[_aligned_offset_malloc_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|Alloue de la mémoire sur une limite d’alignement spécifiée (version de débogage uniquement).|
|[_aligned_offset_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) ou [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md).|
|[_aligned_offset_realloc_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) ou [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) (version de débogage uniquement).|
|[_aligned_offset_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) ou [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) et initialise la mémoire à 0.|
|[_aligned_offset_recalloc_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) ou [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) et initialise la mémoire à 0 (version de débogage uniquement).|
|[_aligned_realloc](../c-runtime-library/reference/aligned-realloc.md)|Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) ou [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md).|
|[_aligned_realloc_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) ou [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) (version de débogage uniquement).|
|[_aligned_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) ou [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) et initialise la mémoire à 0.|
|[_aligned_recalloc_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|Modifie la taille d’un bloc de mémoire qui a été alloué avec [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) ou [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) et initialise la mémoire à 0 (version de débogage uniquement).|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>