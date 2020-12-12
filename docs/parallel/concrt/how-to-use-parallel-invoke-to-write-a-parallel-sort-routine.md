---
description: 'En savoir plus sur : Comment : utiliser parallel_invoke pour écrire une routine de tri parallèle'
title: 'Comment : utiliser parallel_invoke pour écrire une routine de tri parallèle'
ms.date: 11/04/2016
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
ms.openlocfilehash: 4146bed939e265f611d79c465681c10ef28a1ebe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205666"
---
# <a name="how-to-use-parallel_invoke-to-write-a-parallel-sort-routine"></a>Comment : utiliser parallel_invoke pour écrire une routine de tri parallèle

Ce document explique comment utiliser l’algorithme [parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke) pour améliorer les performances de l’algorithme de tri bitonique. L’algorithme de tri bitonique divise de manière récursive la séquence d’entrée en partitions triées plus petites. L’algorithme de tri bitonique peut s’exécuter en parallèle, car chaque opération de partition est indépendante de toutes les autres opérations.

Bien que le tri bitonique soit un exemple de *réseau de tri* qui trie toutes les combinaisons de séquences d’entrée, cet exemple trie les séquences dont les longueurs sont une puissance de deux.

> [!NOTE]
> Cet exemple utilise une routine de tri parallèle pour l’illustration. Vous pouvez également utiliser les algorithmes de tri intégrés fournis par la bibliothèque PPL : [concurrence ::p arallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [accès concurrentiel ::p arallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)et [accès concurrentiel ::p arallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Pour plus d’informations, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

## <a name="sections"></a><a name="top"></a> Sections

Ce document décrit les tâches suivantes :

- [Exécution d’un tri bitonique en série](#serial)

- [Utilisation de parallel_invoke pour effectuer un tri bitonique en parallèle](#parallel)

## <a name="performing-bitonic-sort-serially"></a><a name="serial"></a> Exécution d’un tri bitonique en série

L’exemple suivant illustre la version série de l’algorithme de tri bitonique. La `bitonic_sort` fonction divise la séquence en deux partitions, trie ces partitions dans des directions opposées, puis fusionne les résultats. Cette fonction s’appelle elle-même deux fois de manière récursive pour trier chaque partition.

[!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]

[[Haut](#top)]

## <a name="using-parallel_invoke-to-perform-bitonic-sort-in-parallel"></a><a name="parallel"></a> Utilisation de parallel_invoke pour effectuer un tri bitonique en parallèle

Cette section décrit comment utiliser l' `parallel_invoke` algorithme pour exécuter l’algorithme de tri bitonique en parallèle.

### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>Pour exécuter l’algorithme de tri bitonique en parallèle

1. Ajoutez une `#include` directive pour le fichier d’en-tête ppl. h.

[!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]

1. Ajoutez une **`using`** directive pour l' `concurrency` espace de noms.

[!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]

1. Créez une nouvelle fonction, appelée `parallel_bitonic_mege` , qui utilise l' `parallel_invoke` algorithme pour fusionner les séquences en parallèle s’il y a suffisamment de travail à effectuer. Sinon, appelez `bitonic_merge` pour fusionner les séquences en série.

[!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]

1. Exécutez un processus qui ressemble à celui de l’étape précédente, mais pour la `bitonic_sort` fonction.

[!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]

1. Créez une version surchargée de la `parallel_bitonic_sort` fonction qui trie le tableau dans l’ordre de plus en plus important.

[!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]

L' `parallel_invoke` algorithme réduit la charge en effectuant la dernière série de tâches sur le contexte d’appel. Par exemple, dans la `parallel_bitonic_sort` fonction, la première tâche s’exécute sur un contexte distinct, et la deuxième tâche s’exécute sur le contexte d’appel.

[!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]

L’exemple complet suivant effectue à la fois les versions en série et parallèles de l’algorithme de tri bitonique. L’exemple imprime également sur la console le temps nécessaire pour effectuer chaque calcul.

[!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]

L'exemple de sortie suivant concerne un ordinateur équipé de quatre processeurs.

```Output
serial time: 4353
parallel time: 1248
```

[[Haut](#top)]

### <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le, puis collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `parallel-bitonic-sort.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc Parallel-bitonic-sort. cpp**

## <a name="robust-programming"></a>Programmation fiable

Cet exemple utilise l' `parallel_invoke` algorithme au lieu de la classe [Concurrency :: task_group](reference/task-group-class.md) , car la durée de vie de chaque groupe de tâches ne s’étend pas au-delà d’une fonction. Nous vous recommandons d’utiliser `parallel_invoke` lorsque vous en avez la possibilité, car elle a moins de charge d’exécution que `task group` les objets, ce qui vous permet d’écrire du code plus performant.

Les versions parallèles de certains algorithmes fonctionnent mieux uniquement lorsque le travail est suffisant. Par exemple, la `parallel_bitonic_merge` fonction appelle la version série, `bitonic_merge` , s’il y a 500 ou moins d’éléments dans la séquence. Vous pouvez également planifier votre stratégie de tri globale en fonction de la quantité de travail. Par exemple, il peut être plus efficace d’utiliser la version série de l’algorithme de tri rapide si le tableau contient moins de 500 éléments, comme indiqué dans l’exemple suivant :

[!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]

Comme pour n’importe quel algorithme parallèle, nous vous recommandons de Profiler et de paramétrer votre code comme il convient.

## <a name="see-also"></a>Voir aussi

[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[parallel_invoke, fonction](reference/concurrency-namespace-functions.md#parallel_invoke)
