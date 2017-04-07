---
title: "Allocation de mémoire | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.memory
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, routines
- memory, managing
- memory, allocation
ms.assetid: b4470556-a128-4782-9943-2ccf7a7d9979
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: c8bbb5b6f634b401889c787977fde866ecd41eaa
ms.lasthandoff: 03/29/2017

---
# <a name="memory-allocation"></a>Allocation de mémoire
Utilisez ces routines pour allouer, libérer et réallouer de la mémoire.  
  
### <a name="memory-allocation-routines"></a>Routines d'allocation de mémoire  
  
|Routine|Utilisation|  
|-------------|---------|  
|[_alloca](../c-runtime-library/reference/alloca.md), [_malloca](../c-runtime-library/reference/malloca.md)|Allouer de la mémoire à partir de la pile|  
|[calloc](../c-runtime-library/reference/calloc.md)|Allouer le stockage pour le tableau, en initialisant chaque octet dans le bloc alloué à 0|  
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|Version de débogage de `calloc` ; disponible uniquement dans les versions de débogage des bibliothèques Runtime|  
|[operator delete](../c-runtime-library/operator-delete-crt.md)|Libérer le bloc alloué|  
|[operator delete&#91;&#93;](../c-runtime-library/delete-operator-crt.md)|Libérer le bloc alloué|  
|[_expand](../c-runtime-library/reference/expand.md)|Développer ou réduire le bloc de mémoire sans le déplacer|  
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|Version de débogage de `_expand` ; disponible uniquement dans les versions de débogage des bibliothèques Runtime|  
|[free](../c-runtime-library/reference/free.md)|Libérer le bloc alloué|  
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|Version de débogage de `free` ; disponible uniquement dans les versions de débogage des bibliothèques Runtime|  
|[_freea](../c-runtime-library/reference/freea.md)|Libérer le bloc alloué de la pile|  
|[_get_heap_handle](../c-runtime-library/reference/get-heap-handle.md)|Obtenir le HANDLE Win32 du tas CRT|  
|[_heapadd](../c-runtime-library/heapadd.md)|Ajouter de la mémoire au tas|  
|[_heapchk](../c-runtime-library/reference/heapchk.md)|Vérifier la cohérence du tas|  
|[_heapmin](../c-runtime-library/reference/heapmin.md)|Libérer la mémoire inutilisée dans le tas|  
|[_heapset](../c-runtime-library/heapset.md)|Renseigner les entrées du tas libres avec la valeur spécifiée|  
|[_heapwalk](../c-runtime-library/reference/heapwalk.md)|Retourner des informations sur chaque entrée dans le tas|  
|[malloc](../c-runtime-library/reference/malloc.md)|Allouer un bloc de mémoire à partir du tas|  
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|Version de débogage de `malloc` ; disponible uniquement dans les versions de débogage des bibliothèques Runtime|  
|[_msize](../c-runtime-library/reference/msize.md)|Retourner la taille du bloc alloué|  
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|Version de débogage de `_msize` ; disponible uniquement dans les versions de débogage des bibliothèques Runtime|  
|[new](../c-runtime-library/operator-new-crt.md)|Allouer un bloc de mémoire à partir du tas|  
|[new&#91;&#93;](../c-runtime-library/new-operator-crt.md)|Allouer un bloc de mémoire à partir du tas|  
|[_query_new_handler](../c-runtime-library/reference/query-new-handler.md)|Retourner l'adresse de la routine actuelle du nouveau gestionnaire telle qu'elle est définie par `_set_new_handler`|  
|[_query_new_mode](../c-runtime-library/reference/query-new-mode.md)|Retourner l’entier indiquant le mode du nouveau gestionnaire défini par `_set_new_mode` pour `malloc`|  
|[realloc](../c-runtime-library/reference/realloc.md)|Réallouer un bloc à une nouvelle taille|  
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|Version de débogage de `realloc` ; disponible uniquement dans les versions de débogage des bibliothèques Runtime|  
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Activer le mécanisme de gestion des erreurs quand l’opérateur `new` échoue (pour l’allocation de mémoire) et permettre la compilation des bibliothèques C++ Standard|  
|[_set_new_mode](../c-runtime-library/reference/set-new-mode.md)|Définir le mode du nouveau gestionnaire pour `malloc`|  
  
## <a name="see-also"></a>Voir aussi  
 [Routines runtime par catégorie](../c-runtime-library/run-time-routines-by-category.md)
