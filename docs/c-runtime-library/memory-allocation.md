---
title: Allocation de mémoire
ms.date: 11/18/2020
description: Liste des fonctions Microsoft C Runtime utilisées pour allouer, libérer et réallouer de la mémoire.
f1_keywords:
- c.memory
helpviewer_keywords:
- memory allocation, routines
- memory, managing
- memory, allocation
ms.openlocfilehash: 39be48a4ebdf8ee917395d7b743846196200878d
ms.sourcegitcommit: e82e13b80150fcb27a1387018aafb00d99a3827a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94920740"
---
# <a name="memory-allocation"></a>Allocation de mémoire

Ces routines allouent, libèrent et réallouent de la mémoire.

## <a name="memory-allocation-routines"></a>Routines d’allocation de mémoire

|Routine|Utilisation|
|-------------|---------|
|[`_alloca`](../c-runtime-library/reference/alloca.md), [`_malloca`](../c-runtime-library/reference/malloca.md)|Allouer de la mémoire à partir de la pile|
|[`calloc`](../c-runtime-library/reference/calloc.md)|Allouer un tableau et initialiser ses éléments à 0 (zéro)|
|[`_calloc_dbg`](../c-runtime-library/reference/calloc-dbg.md)|Version de débogage de **`calloc`** . Disponible uniquement dans les versions Debug des bibliothèques Runtime|
|[`operator delete`, `operator delete[]`](../c-runtime-library/delete-operator-crt.md)|Mémoire libre allouée sur le tas |
|[`_expand`](../c-runtime-library/reference/expand.md)|Développer ou réduire un bloc de mémoire sans le déplacer|
|[`_expand_dbg`](../c-runtime-library/reference/expand-dbg.md)|Version de débogage de **`_expand`** . Disponible uniquement dans les versions Debug des bibliothèques Runtime|
|[`free`](../c-runtime-library/reference/free.md)|Mémoire libre allouée sur le tas|
|[`_free_dbg`](../c-runtime-library/reference/free-dbg.md)|Version de débogage de **`free`** . Disponible uniquement dans les versions Debug des bibliothèques Runtime|
|[`_freea`](../c-runtime-library/reference/freea.md)|Mémoire libre allouée sur la pile|
|[`_get_heap_handle`](../c-runtime-library/reference/get-heap-handle.md)|Obtenir un Win32 `HANDLE` sur le tas du runtime C (CRT).|
|[`_heapadd`](../c-runtime-library/heapadd.md)|Ajouter de la mémoire au tas|
|[`_heapchk`](../c-runtime-library/reference/heapchk.md)|Vérifier la cohérence du tas|
|[`_heapmin`](../c-runtime-library/reference/heapmin.md)|Libérer de la mémoire inutilisée dans le tas|
|[`_heapset`](../c-runtime-library/heapset.md)|Remplir les entrées de tas libres avec une valeur|
|[`_heapwalk`](../c-runtime-library/reference/heapwalk.md)|Obtenir des informations sur chaque entrée du tas|
|[`malloc`](../c-runtime-library/reference/malloc.md)|Allouer de la mémoire à partir du tas|
|[`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md)|Version de débogage de **`malloc`** ; disponible uniquement dans les versions Debug des bibliothèques Runtime|
|[`_msize`](../c-runtime-library/reference/msize.md)|Retourne la taille d’un bloc de mémoire alloué|
|[`_msize_dbg`](../c-runtime-library/reference/msize-dbg.md)|Version de débogage de **`_msize`** ; disponible uniquement dans les versions Debug des bibliothèques Runtime|
|[`new`, `new[]`](../c-runtime-library/new-operator-crt.md)|Allouer un bloc de mémoire à partir du tas|
|[`_query_new_handler`](../c-runtime-library/reference/query-new-handler.md)|Obtient l’adresse de la routine de nouveau gestionnaire actuelle définie par **`_set_new_handler`**|
|[`_query_new_mode`](../c-runtime-library/reference/query-new-mode.md)|Obtenir le nouveau mode de gestionnaire défini par **`_set_new_mode`** pour **`malloc`**|
|[`realloc`](../c-runtime-library/reference/realloc.md)|Réallouer un bloc à une nouvelle taille|
|[`_realloc_dbg`](../c-runtime-library/reference/realloc-dbg.md)|Version de débogage de **`realloc`** ; disponible uniquement dans les versions Debug des bibliothèques Runtime|
|[`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md)|Activer le mécanisme de gestion des erreurs quand l' **`new`** opérateur ne parvient pas à allouer de la mémoire et activer la compilation des bibliothèques C++ standard|
|[`_set_new_mode`](../c-runtime-library/reference/set-new-mode.md)|Définir le nouveau mode de gestionnaire pour **`malloc`**|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)