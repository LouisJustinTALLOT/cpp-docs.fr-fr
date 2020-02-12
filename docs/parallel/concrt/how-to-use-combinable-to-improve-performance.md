---
title: 'Comment : utiliser la classe combinable pour améliorer les performances'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
ms.openlocfilehash: db27a791b2b92102118606712db4cbd2920f9619
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142441"
---
# <a name="how-to-use-combinable-to-improve-performance"></a>Comment : utiliser la classe combinable pour améliorer les performances

Cet exemple montre comment utiliser la classe [Concurrency :: combinable](../../parallel/concrt/reference/combinable-class.md) pour calculer la somme des nombres d’un objet [std :: Array](../../standard-library/array-class-stl.md) qui sont premiers. La classe `combinable` améliore les performances en éliminant l’état partagé.

> [!TIP]
> Dans certains cas, le mappage parallèle ([concurrence ::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) et la réduction ([concurrence :: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) peuvent améliorer les performances par rapport à `combinable`. Pour obtenir un exemple qui utilise des opérations de mappage et de réduction pour produire les mêmes résultats que cet exemple, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

## <a name="example---accumulate"></a>Exemple-cumul

L’exemple suivant utilise la fonction [std :: Accumulate](../../standard-library/numeric-functions.md#accumulate) pour calculer la somme des éléments d’un tableau qui sont premiers. Dans cet exemple, `a` est un objet `array` et la fonction `is_prime` détermine si sa valeur d’entrée est premier.

[!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]

## <a name="example---parallel_for_each"></a>Exemple : parallel_for_each

L’exemple suivant montre un moyen naïve de paralléliser l’exemple précédent. Cet exemple utilise l’algorithme [Concurrency ::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) pour traiter le tableau en parallèle et un objet [Concurrency :: critical_section](../../parallel/concrt/reference/critical-section-class.md) pour synchroniser l’accès à la variable `prime_sum`. Cet exemple n’est pas mis à l’échelle, car chaque thread doit attendre que la ressource partagée devienne disponible.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]

## <a name="example---combinable"></a>Exemple : combinable

L’exemple suivant utilise un objet `combinable` pour améliorer les performances de l’exemple précédent. Cet exemple élimine le besoin d’objets de synchronisation. elle est mise à l’échelle parce que l’objet `combinable` permet à chaque thread d’exécuter sa tâche indépendamment.

Un objet `combinable` est généralement utilisé en deux étapes. Tout d’abord, produisez une série de calculs affinés en effectuant le travail en parallèle. Ensuite, combinez (ou réduisez) les calculs dans un résultat final. Cet exemple utilise la méthode [Concurrency :: combinable :: local](reference/combinable-class.md#local) pour obtenir une référence à la somme locale. Il utilise ensuite la méthode [Concurrency :: combinable :: combine](reference/combinable-class.md#combine) , et un objet [std ::p lu](../../standard-library/plus-struct.md) pour combiner les calculs locaux dans le résultat final.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]

## <a name="example---serial-and-parallel"></a>Exemple-série et parallèle

L’exemple complet suivant calcule la somme des nombres premiers à la fois en série et en parallèle. L’exemple imprime sur la console le temps nécessaire pour effectuer les deux calculs.

[!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]

L'exemple de sortie suivant concerne un ordinateur équipé de quatre processeurs.

```Output
1709600813
serial time: 6178 ms

1709600813
parallel time: 1638 ms
```

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le, puis collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `parallel-sum-of-primes.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc parallel-sum-of-primes. cpp**

## <a name="robust-programming"></a>Programmation fiable

Pour obtenir un exemple qui utilise des opérations de mappage et de réduction pour produire les mêmes résultats, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

## <a name="see-also"></a>Voir aussi

[Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable, classe](../../parallel/concrt/reference/combinable-class.md)<br/>
[critical_section, classe](../../parallel/concrt/reference/critical-section-class.md)
