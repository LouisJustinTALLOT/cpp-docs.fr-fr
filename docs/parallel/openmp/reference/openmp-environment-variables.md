---
title: Variables d’environnement OpenMP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b61535fd07066c4a1ee24658fdfe81047efc90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446567"
---
# <a name="openmp-environment-variables"></a>Variables d'environnement OpenMP

Fournit des liens vers les variables d’environnement utilisées dans l’API OpenMP.

L’implémentation Visual C++ de l’OpenMP standard inclut les variables d’environnement suivantes. Ces variables d’environnement sont lues au démarrage du programme et les modifications apportées à leurs valeurs sont ignorées lors de l’exécution (par exemple, à l’aide de [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Variable d’environnement|Description|
|--------------------------|-----------------|
|[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|Spécifie si la durée d’exécution de OpenMP peut ajuster le nombre de threads dans une région parallèle.|
|[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)|Spécifie si parallélisme imbriquée est activée, à moins que le parallélisme imbriquée est activée ou désactivée avec `omp_set_nested`.|
|[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|Définit le nombre maximal de threads dans la région parallèle, sauf substitution par [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) ou [num_threads](../../../parallel/openmp/reference/num-threads.md).|
|[OMP_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|Modifie le comportement de la [planification](../../../parallel/openmp/reference/schedule.md) clause lorsque `schedule(runtime)` est spécifié dans un `for` ou `parallel for` directive.|

## <a name="see-also"></a>Voir aussi

[Référence de la bibliothèque](../../../parallel/openmp/reference/openmp-library-reference.md)