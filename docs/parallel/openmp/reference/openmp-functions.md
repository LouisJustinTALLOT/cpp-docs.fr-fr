---
title: OpenMP, fonctions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5daa7737f63df437f31f349a85811befe0c8f5b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425598"
---
# <a name="openmp-functions"></a>Fonctions OpenMP

Fournit des liens vers les fonctions utilisées dans l’API OpenMP.

L’implémentation Visual C++ de l’OpenMP standard inclut les fonctions suivantes.

|Fonction|Description|
|--------------|-----------------|
|[omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|Désinitialise un verrou.|
|[omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|Désinitialise un verrou pouvant être imbriqué.|
|[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|Retourne une valeur qui indique si le nombre de threads disponibles dans une région parallèle suivante peut être ajusté par la durée d’exécution.|
|[omp_get_max_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|Retourne un entier qui est égal à ou supérieur au nombre de threads qui serait disponible si une région parallèle sans [num_threads](../../../parallel/openmp/reference/num-threads.md) ont été définies à ce stade dans le code.|
|[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)|Retourne une valeur qui indique si le parallélisme imbriquée est activée.|
|[omp_get_num_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|Retourne le nombre de processeurs qui sont disponibles lorsque la fonction est appelée.|
|[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|Retourne le nombre de threads dans la région parallèle.|
|[omp_get_thread_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|Retourne le nombre de threads d’exécution du thread au sein de son équipe de thread.|
|[omp_get_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|Retourne le nombre de secondes entre les battements d’horloge de processeur.|
|[omp_get_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|Retourne qu'une valeur en secondes du temps écoulé à partir d’un moment donné.|
|[omp_in_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|Retourne une valeur différente de zéro si elle est appelée à partir de dans une région parallèle.|
|[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)|Initialise un verrou simple.|
|[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|Initialise un verrou.|
|[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|Indique que le nombre de threads disponibles dans une région parallèle suivante peut être ajusté en le temps d’exécution.|
|[omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)|Blocs d’exécution de thread jusqu'à ce qu’un verrou est disponible.|
|[omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|Blocs d’exécution de thread jusqu'à ce qu’un verrou est disponible.|
|[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)|Active le parallélisme imbriqué.|
|[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|Définit le nombre de threads dans des régions parallèles suivantes, sauf substitution par une [num_threads](../../../parallel/openmp/reference/num-threads.md) clause.|
|[omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)|Tente de définir un verrou, mais ne bloque pas l’exécution du thread.|
|[omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|Tente de définir un verrou pouvant être imbriqué, mais ne bloque pas l’exécution du thread.|
|[omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|Libère un verrou.|
|[omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|Libère un verrou pouvant être imbriqué.|

## <a name="see-also"></a>Voir aussi

[Référence de la bibliothèque](../../../parallel/openmp/reference/openmp-library-reference.md)