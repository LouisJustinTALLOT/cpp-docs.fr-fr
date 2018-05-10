---
title: 'Comment : utiliser la classe combinable pour améliorer les performances | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3185ee9f7546e6927197d2e3452ea4cf86f9ab5c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-combinable-to-improve-performance"></a>Comment : utiliser la classe combinable pour améliorer les performances
Cet exemple montre comment utiliser le [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) classe pour calculer la somme des nombres dans un [std::array](../../standard-library/array-class-stl.md) objet premiers. La `combinable` classe améliore les performances en éliminant l’état partagé.  
  
> [!TIP]
>  Dans certains cas, parallel plan ([concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) et réduire ([concurrency :: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) peut améliorer les performances sur `combinable`. Pour obtenir un exemple que mapper et réduire les opérations afin de produire les mêmes résultats que cet exemple, consultez [des algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le [std::accumulate](../../standard-library/numeric-functions.md#accumulate) fonction pour calculer la somme des éléments dans un tableau qui sont les premiers. Dans cet exemple, `a` est un `array` objet et le `is_prime` fonction détermine si sa valeur d’entrée est un nombre premier.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre une méthode naïve pour paralléliser l’exemple précédent. Cet exemple utilise le [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorithme pour traiter le tableau en parallèle et un [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) objet pour synchroniser l’accès à la `prime_sum` variable . Cet exemple n’évolue pas car chaque thread doit attendre la ressource partagée soit disponible.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un `combinable` objet pour améliorer les performances de l’exemple précédent. Cet exemple élimine la nécessité pour les objets de synchronisation ; Il met à l’échelle, car le `combinable` objet permet à chaque thread effectuer sa tâche indépendamment.  
  
 A `combinable` objet est généralement utilisé dans deux étapes. Tout d’abord, produisent une série de calculs affinés en effectuant le travail en parallèle. Ensuite, combinez (ou réduisez) les calculs dans un résultat final. Cet exemple utilise le [Concurrency::combinable :: local](reference/combinable-class.md#local) méthode pour obtenir une référence à la somme locale. Il utilise ensuite la [Concurrency::combinable :: combine](reference/combinable-class.md#combine) (méthode) et un [std::plus](../../standard-library/plus-struct.md) objet à combiner les calculs locaux dans le résultat final.  

  
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
  
 **CL.exe /EHsc parallel-sum-of-primes.cpp**  
  
## <a name="robust-programming"></a>Programmation fiable  
 Pour obtenir un exemple que mapper et réduire les opérations afin de produire les mêmes résultats, consultez [des algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable (classe)](../../parallel/concrt/reference/combinable-class.md)   
 [critical_section, classe](../../parallel/concrt/reference/critical-section-class.md)
