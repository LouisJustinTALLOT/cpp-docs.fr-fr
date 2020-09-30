---
title: 'Comment : convertir une boucle OpenMP parallèle pour utiliser le runtime d’accès concurrentiel'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: 4f523f9f6de7f1ffb4c3b578b60de587239dffb6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507875"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>Comment : convertir une boucle OpenMP parallèle pour utiliser le runtime d’accès concurrentiel

Cet exemple montre comment convertir une boucle de base qui utilise les directives [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) et [for pour](../openmp/reference/openmp-directives.md#for-openmp) utiliser la Runtime d’accès concurrentiel l’algorithme [Concurrency ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) .

## <a name="example---prime-count"></a>Exemple-nombre premier

Cet exemple utilise à la fois OpenMP et le runtime d’accès concurrentiel pour calculer le nombre de nombres premiers dans un tableau de valeurs aléatoires.

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

L' `parallel_for` algorithme et OpenMP 3,0 permettent au type d’index d’être un type intégral signé ou un type intégral non signé. L' `parallel_for` algorithme permet également de s’assurer que la plage spécifiée ne déborde pas un type signé. Les versions OpenMP 2,0 et 2,5 autorisent uniquement les types d’index intégral signés. OpenMP ne valide pas non plus la plage d’index.

La version de cet exemple qui utilise le runtime d’accès concurrentiel utilise également un objet [Concurrency :: combinable](../../parallel/concrt/reference/combinable-class.md) à la place de la directive [Atomic](../openmp/reference/openmp-directives.md#atomic) pour incrémenter la valeur de compteur sans nécessiter de synchronisation.

Pour plus d’informations sur `parallel_for` et d’autres algorithmes parallèles, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md). Pour plus d’informations sur la `combinable` classe, consultez [conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="example---use-stdarray"></a>Exemple : utilisation de std :: Array

Cet exemple modifie le précédent pour qu’il agisse sur un objet [std :: Array](../../standard-library/array-class-stl.md) plutôt que sur un tableau natif. Étant donné que les versions OpenMP 2,0 et 2,5 autorisent uniquement les types d’index intégraux signés dans une `parallel_for` construction, vous ne pouvez pas utiliser d’itérateurs pour accéder aux éléments d’un conteneur de bibliothèque standard C++ en parallèle. La bibliothèque de modèles parallèles (PPL) fournit l’algorithme d' [accès concurrentiel ::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) , qui effectue des tâches en parallèle sur un conteneur itératif comme ceux fournis par la bibliothèque standard C++. Elle utilise la même logique de partitionnement que celle utilisée par l' `parallel_for` algorithme. L' `parallel_for_each` algorithme ressemble à l’algorithme [std :: for_each](../../standard-library/algorithm-functions.md#for_each) de la bibliothèque standard C++, sauf que l' `parallel_for_each` algorithme exécute les tâches simultanément.

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `concrt-omp-count-primes.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc/OpenMP concrt-omp-count-primes. cpp**

## <a name="see-also"></a>Voir aussi

[Migration d'OpenMP au runtime d'accès concurrentiel](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)
