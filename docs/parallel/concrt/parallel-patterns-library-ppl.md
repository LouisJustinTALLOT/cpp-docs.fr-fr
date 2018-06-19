---
title: Bibliothèque de modèles (parallèles PPL) en parallèle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Parallel Patterns Library (PPL)
ms.assetid: 40fd86b2-69fa-45e5-93d8-98a75636c242
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7263d764014fa3532c3234bd4c7a0d4f1ff8d3c3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691539"
---
# <a name="parallel-patterns-library-ppl"></a>Bibliothèque de modèles parallèles
La Bibliothèque de modèles parallèles (PPL) fournit un modèle de programmation essentiel qui favorise l’évolutivité et la facilité d’utilisation dans le cadre du développement d’applications simultanées. La bibliothèque PPL repose sur les composants de planification et de gestion des ressources du runtime d'accès concurrentiel. Elle élève le niveau d'abstraction entre le code de votre application et le mécanisme de threading sous-jacent en fournissant des algorithmes génériques de type sécurisé et des conteneurs qui agissent sur les données en parallèle. La bibliothèque PPL vous permet également de développer des applications qui évoluent en fournissant des alternatives à l'état partagé.  
  
 La bibliothèque PPL offre les fonctionnalités suivantes :  
  
- *Parallélisme des tâches*: mécanisme qui fonctionne par-dessus le pool de threads Windows pour exécuter plusieurs éléments de travail (tâches) en parallèle  
  
- *Algorithmes parallèles*: algorithmes génériques qui fonctionnent par-dessus le Runtime d’accès concurrentiel pour agir sur les collections de données en parallèle  
  
- *Conteneurs et objets parallèles*: types de conteneurs génériques qui fournissent un accès simultané sécurisé à leurs éléments  
  
## <a name="example"></a>Exemple  
 La bibliothèque PPL fournit un modèle de programmation qui ressemble à la bibliothèque C++ Standard. L’exemple suivant illustre de nombreuses fonctionnalités de la bibliothèque PPL. Il calcule plusieurs nombres de Fibonacci en série et en parallèle. Les deux calculs agissent sur un [std::array](../../standard-library/array-class-stl.md) objet. L'exemple affiche également sur la console le temps requis pour effectuer les deux calculs.  
  
 La version sérialisée utilise la bibliothèque C++ Standard [std::for_each](../../standard-library/algorithm-functions.md#for_each) algorithme pour parcourir le tableau et stocke les résultats dans un [std::vector](../../standard-library/vector-class.md) objet. La version parallèle effectue la même tâche, mais utilise la bibliothèque PPL [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorithme et stocke les résultats dans un [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) objet. La classe `concurrent_vector` permet à chaque itération de boucle d'ajouter simultanément des éléments sans avoir à synchroniser l'accès en écriture au conteneur.  
  
 Comme `parallel_for_each` agit simultanément, la version parallèle de cet exemple doit trier l'objet `concurrent_vector` pour produire les mêmes résultats que la version en série.  
  
 Notez que l'exemple utilise une méthode naïve pour calculer les nombres de Fibonacci ; toutefois, cette méthode illustre comment le runtime d'accès concurrentiel peut améliorer les performances de longs calculs.  
  
 [!code-cpp[concrt-parallel-fibonacci#1](../../parallel/concrt/codesnippet/cpp/parallel-patterns-library-ppl_1.cpp)]  
  
 L'exemple de sortie suivant concerne un ordinateur équipé de quatre processeurs.  
  
```Output  
serial time: 9250 ms  
parallel time: 5726 ms  
 
fib(24): 46368  
fib(26): 121393  
fib(41): 165580141  
fib(42): 267914296  
```  
  
 Chaque itération de la boucle nécessite une durée de temps différente pour s'exécuter. Les performances de `parallel_for_each` sont limitées par l'opération qui se termine en dernier. Par conséquent, vous ne devriez pas escompter des améliorations de performances linéaires entre les versions série et parallèle de l'exemple.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Décrit le rôle des tâches et des groupes de tâches dans la bibliothèque PPL.|  
|[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)|Décrit comment utiliser des algorithmes parallèles tels que `parallel_for` et `parallel_for_each`.|  
|[Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)|Décrit les différents objets et conteneurs parallèles fournis par la bibliothèque PPL.|  
|[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)|Explique comment annuler le travail effectué par un algorithme parallèle.|  
|[Le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)|Décrit le runtime d'accès concurrentiel, qui simplifie la programmation parallèle, et contient des liens vers les rubriques connexes.|

