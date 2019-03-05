---
title: 'Procédure : Utiliser la classe combinable pour améliorer les performances'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
ms.openlocfilehash: c8f4c40be84b2204e5b5632fe6d3d5a5d22b8719
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258123"
---
# <a name="how-to-use-combinable-to-improve-performance"></a>Procédure : Utiliser la classe combinable pour améliorer les performances

Cet exemple montre comment utiliser le [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) classe pour calculer la somme des nombres dans un [std::array](../../standard-library/array-class-stl.md) objet premiers. Le `combinable` classe améliore les performances en éliminant l’état partagé.

> [!TIP]
>  Dans certains cas, parallèle map ([concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) et réduire ([concurrence :: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) peut améliorer les performances sur `combinable`. Pour obtenir un exemple qu’utilise mappe les opérations et de réduction pour produire les mêmes résultats que cet exemple, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

## <a name="example"></a>Exemple

L’exemple suivant utilise le [std::accumulate](../../standard-library/numeric-functions.md#accumulate) (fonction) pour calculer la somme des éléments dans un tableau qui sont les premiers. Dans cet exemple, `a` est un `array` objet et le `is_prime` fonction détermine si sa valeur d’entrée est un nombre premier.

[!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]

## <a name="example"></a>Exemple

L’exemple suivant montre une méthode naïve pour paralléliser l’exemple précédent. Cet exemple utilise le [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorithme pour traiter le tableau en parallèle et un [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) objet pour synchroniser l’accès à la `prime_sum` variable . Cet exemple n’évolue pas car chaque thread doit attendre la ressource partagée soit disponible.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]

## <a name="example"></a>Exemple

L’exemple suivant utilise un `combinable` objet pour améliorer les performances de l’exemple précédent. Cet exemple élimine la nécessité pour les objets de synchronisation ; Il met à l’échelle, car le `combinable` objet permet à chaque thread d’exécuter sa tâche indépendamment.

Un `combinable` objet est généralement utilisé dans deux étapes. Tout d’abord, générer une série de calculs affinés en effectuant le travail en parallèle. Ensuite, combinez (ou réduisez) les calculs dans un résultat final. Cet exemple utilise le [Concurrency::combinable :: local](reference/combinable-class.md#local) méthode pour obtenir une référence à la somme locale. Il utilise ensuite le [Concurrency::combinable :: combine](reference/combinable-class.md#combine) (méthode) et un [std::plus](../../standard-library/plus-struct.md) objet à combiner les calculs locaux dans le résultat final.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]

## <a name="example"></a>Exemple

L’exemple complet suivant calcule la somme des nombres premiers en série et en parallèle. L’exemple imprime sur la console le temps requis pour effectuer les deux calculs.

[!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]

L'exemple de sortie suivant concerne un ordinateur équipé de quatre processeurs.

```Output
1709600813
serial time: 6178 ms

1709600813
parallel time: 1638 ms
```

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `parallel-sum-of-primes.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**cl.exe /EHsc parallel-sum-of-primes.cpp**

## <a name="robust-programming"></a>Programmation fiable

Pour obtenir un exemple qu’utilise mappe les opérations et de réduction pour produire les mêmes résultats, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

## <a name="see-also"></a>Voir aussi

[Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable, classe](../../parallel/concrt/reference/combinable-class.md)<br/>
[critical_section, classe](../../parallel/concrt/reference/critical-section-class.md)
