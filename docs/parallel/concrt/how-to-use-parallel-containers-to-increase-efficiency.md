---
title: 'Comment : utiliser des conteneurs parallèles pour une efficacité accrue | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0e0d79693bef358a582e878ec2d6d138387752c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696199"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>Comment : utiliser des conteneurs parallèles pour une efficacité accrue
Cette rubrique montre comment utiliser des conteneurs parallèles pour stocker efficacement et d’accéder aux données en parallèle.  
  
 L’exemple de code calcule le jeu de nombres premiers et Carmichael en parallèle. Ensuite, pour chaque nombre de Carmichael, le code calcule les facteurs premiers de ce nombre.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la `is_prime` (fonction), qui détermine si une valeur d’entrée est un nombre premier, et le `is_carmichael` (fonction), qui détermine si la valeur d’entrée est un nombre de Carmichael.  
  
 [!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `is_prime` et `is_carmichael` fonctions pour calculer les ensembles de nombres premiers et Carmichael. L’exemple utilise le [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) et [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithmes pour calculer chaque valeur en parallèle. Pour plus d’informations sur les algorithmes parallèles, consultez [des algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).  
  
 Cet exemple utilise un [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) objet pour stocker l’ensemble de Carmichael numéros, car il utilisera ultérieurement cet objet comme une file d’attente de travail. Il utilise un [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) objet pour stocker l’ensemble de nombres premiers, car il sera ultérieurement au sein de cet ensemble pour rechercher les facteurs premiers.  
  
 [!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre le `prime_factors_of` (fonction), qui utilise la division par évaluation pour rechercher tous les facteurs premiers de la valeur donnée.  
  
 Cette fonction utilise le [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorithme pour effectuer une itération au sein de la collection de nombres premiers. Le `concurrent_vector` objet permet d’ajouter simultanément des facteurs premiers au résultat de la boucle parallèle.  
  
 [!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]  
  
## <a name="example"></a>Exemple  
 Cet exemple traite chaque élément dans la file d’attente de nombres de Carmichael en appelant le `prime_factors_of` fonction pour calculer ses facteurs premiers. Il utilise un groupe de tâches pour exécuter ce travail en parallèle. Pour plus d’informations sur les groupes de tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Cet exemple imprime les facteurs premiers pour chaque nombre de Carmichael si ce nombre possède plus de quatre facteurs premiers.  
  
 [!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]  
  
## <a name="example"></a>Exemple  
 Le code suivant montre l’exemple complet, qui utilise des conteneurs parallèles pour calculer les facteurs premiers des nombres de Carmichael.  
  
 [!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]  
  
 Cet exemple génère la sortie suivante.  
  
```Output  
Prime factors of 9890881 are: 7 11 13 41 241.  
Prime factors of 825265 are: 5 7 17 19 73.  
Prime factors of 1050985 are: 5 13 19 23 37.  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `carmichael-primes.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 **CL.exe /EHsc carmichael-primes.cpp**  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)   
 [Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Classe concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)   
 [concurrent_queue, classe](../../parallel/concrt/reference/concurrent-queue-class.md)   
 [parallel_invoke, fonction](reference/concurrency-namespace-functions.md#parallel_invoke)   
 [parallel_for (fonction)](reference/concurrency-namespace-functions.md#parallel_for)   
 [task_group, classe](reference/task-group-class.md)
