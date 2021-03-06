---
description: 'En savoir plus sur : Comment : utiliser des conteneurs parallèles pour améliorer l’efficacité'
title: 'Comment : utiliser des conteneurs parallèles pour une efficacité accrue'
ms.date: 11/04/2016
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
ms.openlocfilehash: 6e416da7b1cdcbe1a9b3073569cf4dda6434ceea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341553"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>Comment : utiliser des conteneurs parallèles pour une efficacité accrue

Cette rubrique montre comment utiliser des conteneurs parallèles pour stocker et accéder efficacement aux données en parallèle.

L’exemple de code calcule l’ensemble des nombres premiers et Carmichael en parallèle. Ensuite, pour chaque nombre de Carmichael, le code calcule les facteurs premiers de ce nombre.

## <a name="example-determine-if-an-input-value-is-a-prime-number"></a>Exemple : déterminer si une valeur d’entrée est un nombre premier

L’exemple suivant illustre la `is_prime` fonction, qui détermine si une valeur d’entrée est un nombre premier, et la `is_carmichael` fonction, qui détermine si la valeur d’entrée est un nombre Carmichael.

[!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]

## <a name="example-compute-prime-and-carmichael-numbers"></a>Exemple : calculer les nombres premiers et les nombres de Carmichael

L’exemple suivant utilise les `is_prime` `is_carmichael` fonctions et pour calculer les jeux de nombres premiers et de nombres de Carmichael. L’exemple utilise les algorithmes d' [accès concurrentiel ::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) et d' [accès concurrentiel ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) pour calculer chaque ensemble en parallèle. Pour plus d’informations sur les algorithmes parallèles, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

Cet exemple utilise un objet [Concurrency :: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) pour stocker le jeu de nombres de Carmichael, car il utilise ultérieurement cet objet comme file d’attente de travail. Elle utilise un objet [Concurrency :: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) pour contenir l’ensemble de nombres premiers, car elle itère ultérieurement ce jeu pour rechercher les facteurs premiers.

[!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]

## <a name="example-find-all-prime-factors-of-a-given-value"></a>Exemple : Rechercher tous les facteurs premiers d’une valeur donnée

L’exemple suivant illustre la `prime_factors_of` fonction, qui utilise la Division d’essai pour rechercher tous les facteurs premiers de la valeur donnée.

Cette fonction utilise l’algorithme [Concurrency ::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) pour itérer au sein de la collection de nombres premiers. L' `concurrent_vector` objet permet à la boucle parallèle d’ajouter simultanément des facteurs premiers au résultat.

[!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]

## <a name="example-processes-each-element-in-the-queue-of-carmichael-numbers"></a>Exemple : traite chaque élément dans la file d’attente de nombres de Carmichael

Cet exemple traite chaque élément de la file d’attente de nombres de Carmichael en appelant la `prime_factors_of` fonction pour calculer ses facteurs premiers. Il utilise un groupe de tâches pour effectuer ce travail en parallèle. Pour plus d’informations sur les groupes de tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Cet exemple imprime les facteurs premiers pour chaque nombre de Carmichael si ce nombre a plus de quatre facteurs premiers.

[!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]

## <a name="example-finished-parallel-container-code-sample"></a>Exemple : exemple de code de conteneur parallèle terminé

Le code suivant illustre l’exemple complet, qui utilise des conteneurs parallèles pour calculer les facteurs premiers des nombres de Carmichael.

[!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]

Cet exemple produit l’exemple de sortie suivant.

```Output
Prime factors of 9890881 are: 7 11 13 41 241.
Prime factors of 825265 are: 5 7 17 19 73.
Prime factors of 1050985 are: 5 13 19 23 37.
```

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `carmichael-primes.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc Carmichael-primes. cpp**

## <a name="see-also"></a>Voir aussi

[Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Classe concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)<br/>
[Classe concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)<br/>
[parallel_invoke, fonction](reference/concurrency-namespace-functions.md#parallel_invoke)<br/>
[parallel_for, fonction](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[Classe task_group](reference/task-group-class.md)
