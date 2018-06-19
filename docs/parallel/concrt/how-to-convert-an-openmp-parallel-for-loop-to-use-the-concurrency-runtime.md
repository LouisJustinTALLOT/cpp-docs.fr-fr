---
title: 'Comment : convertir une boucle utiliser le Runtime d’accès concurrentiel OpenMP parallèle | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93538e3188f0086039ecc0b681f936954d82ae97
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687021"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>Comment : convertir une boucle OpenMP parallèle pour utiliser le runtime d’accès concurrentiel

Cet exemple montre comment convertir une boucle de base qui utilise l’OpenMP [parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) et [pour](../../parallel/openmp/reference/for-openmp.md) directives pour utiliser le Runtime d’accès concurrentiel [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise OpenMP et le Runtime d’accès concurrentiel pour calculer le nombre de nombres premiers dans un tableau de valeurs aléatoires.  
  
 [!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]  
  
 Cet exemple produit la sortie suivante.  
  
```Output  
Using OpenMP...  
found 107254 prime numbers.  
Using the Concurrency Runtime...  
found 107254 prime numbers.  
```  
  
 Le `parallel_for` algorithme et OpenMP 3.0 autorisent pour le type d’index doit être un type intégral signé ou un type intégral non signé. Le `parallel_for` algorithme également permet de s’assurer que la plage spécifiée ne dépasse pas un type signé. Les versions OpenMP 2.0 et 2.5 autorisent uniquement les types d’index intégraux signés. OpenMP ne valide pas la plage d’index.  
  
 La version de cet exemple qui utilise le Runtime d’accès concurrentiel utilise également un [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) de l’objet à la place de la [atomique](../../parallel/openmp/reference/atomic.md) directive pour incrémenter la valeur de compteur sans nécessiter de synchronisation.  
  
 Pour plus d’informations sur `parallel_for` et d’autres algorithmes parallèles, consultez [des algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md). Pour plus d’informations sur la `combinable` de classe, consultez [conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="example"></a>Exemple  

 Cet exemple modifie le précédent pour agir sur une [std::array](../../standard-library/array-class-stl.md) au lieu de l’objet sur un tableau natif. Étant donné que les versions OpenMP 2.0 et 2.5 autorisent pour signés uniquement dans les types d’index intégraux un `parallel_for` construction, vous ne pouvez pas utiliser d’itérateurs pour accéder aux éléments d’un conteneur de bibliothèque C++ Standard en parallèle. La bibliothèque de modèles parallèles (PPL) fournit le [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorithme, qui effectue des tâches, en parallèle, sur un conteneur itératif, tels que ceux fournis par la bibliothèque C++ Standard. Il utilise la même logique de partitionnement que la `parallel_for` algorithme utilise. Le `parallel_for_each` algorithme ressemble à la bibliothèque Standard C++ [std::for_each](../../standard-library/algorithm-functions.md#for_each) algorithme, à ceci près que le `parallel_for_each` algorithme exécute les tâches simultanément.  
  
 [!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `concrt-omp-count-primes.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 **CL.exe /EHsc /openmp concrt-omp-count-primes.cpp**  
  
## <a name="see-also"></a>Voir aussi  
 [Migration d’OpenMP au Runtime d’accès concurrentiel](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)   
 [Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)

