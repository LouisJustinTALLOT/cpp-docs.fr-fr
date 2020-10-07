---
title: Allocation de mémoire
ms.date: 11/04/2016
description: Répertorie les fonctions Microsoft C Runtime utilisées pour allouer, libérer et réallouer de la mémoire.
f1_keywords:
- c.memory
helpviewer_keywords:
- memory allocation, routines
- memory, managing
- memory, allocation
ms.assetid: b4470556-a128-4782-9943-2ccf7a7d9979
ms.openlocfilehash: 4e01d62fdfd24416f78254a849b3feea97883281
ms.sourcegitcommit: 8caaf5e00aeb727741a273aecafa15de293426cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91806498"
---
# <a name="memory-allocation"></a>Allocation de mémoire

Utilisez ces routines pour allouer, libérer et réallouer de la mémoire.

## <a name="memory-allocation-routines"></a>Routines d’allocation de mémoire

|Routine|Utilisation|
|-------------|---------|
|[_alloca](../c-runtime-library/reference/alloca.md), [_malloca](../c-runtime-library/reference/malloca.md)|Allouer de la mémoire à partir de la pile|
|[calloc](../c-runtime-library/reference/calloc.md)|Allouer le stockage pour le tableau, en initialisant chaque octet dans le bloc alloué à 0|
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|Version de débogage de **calloc** ; disponible uniquement dans les versions de débogage des bibliothèques Runtime|
|[Delete, opérateur&#91;&#93;](../c-runtime-library/delete-operator-crt.md)|Libérer le bloc alloué|
|[_expand](../c-runtime-library/reference/expand.md)|Développer ou réduire le bloc de mémoire sans le déplacer|
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|Version de débogage de **_expand** ; disponible uniquement dans les versions de débogage des bibliothèques Runtime|
|[free](../c-runtime-library/reference/free.md)|Libérer le bloc alloué|
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|Version de débogage de **free** ; disponible uniquement dans les versions de débogage des bibliothèques Runtime|
|[_freea](../c-runtime-library/reference/freea.md)|Bloc alloué gratuitement à partir de la pile|
|[_get_heap_handle](../c-runtime-library/reference/get-heap-handle.md)|Obtenir le HANDLE Win32 du tas CRT|
|[_heapadd](../c-runtime-library/heapadd.md)|Ajouter de la mémoire au tas|
|[_heapchk](../c-runtime-library/reference/heapchk.md)|Vérifier la cohérence du tas|
|[_heapmin](../c-runtime-library/reference/heapmin.md)|Libérer la mémoire inutilisée dans le tas|
|[_heapset](../c-runtime-library/heapset.md)|Renseigner les entrées du tas libres avec la valeur spécifiée|
|[_heapwalk](../c-runtime-library/reference/heapwalk.md)|Retourner des informations sur chaque entrée dans le tas|
|[malloc](../c-runtime-library/reference/malloc.md)|Allouer un bloc de mémoire à partir du tas|
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|Version de débogage de **malloc** ; disponible uniquement dans les versions de débogage des bibliothèques Runtime|
|[_msize](../c-runtime-library/reference/msize.md)|Retourner la taille du bloc alloué|
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|Version de débogage de **_msize** ; disponible uniquement dans les versions de débogage des bibliothèques Runtime|
|[nouveau&#91;&#93;](../c-runtime-library/new-operator-crt.md)|Allouer un bloc de mémoire à partir du tas|
|[_query_new_handler](../c-runtime-library/reference/query-new-handler.md)|Retourner l’adresse de la routine actuelle du nouveau gestionnaire telle qu’elle est définie par **_set_new_handler**|
|[_query_new_mode](../c-runtime-library/reference/query-new-mode.md)|Retourner l’entier indiquant le mode du nouveau gestionnaire défini par **_set_new_mode** pour **malloc**|
|[realloc](../c-runtime-library/reference/realloc.md)|Réallouer un bloc à une nouvelle taille|
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|Version de débogage de **realloc** ; disponible uniquement dans les versions de débogage des bibliothèques Runtime|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Activer le mécanisme de gestion des erreurs quand l' **`new`** opérateur échoue (pour allouer de la mémoire) et activer la compilation des bibliothèques C++ standard|
|[_set_new_mode](../c-runtime-library/reference/set-new-mode.md)|Définir le mode du nouveau gestionnaire pour **malloc**|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
