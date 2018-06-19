---
title: 'Comment : convertir une boucle OpenMP qui utilise la gestion des exceptions pour utiliser le Runtime d’accès concurrentiel | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b96273589fb4e7d7e73e7bc72da03a92d5587de8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687801"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>Comment : convertir une boucle OpenMP qui a recours à la gestion des exceptions pour utiliser le runtime d'accès concurrentiel
Cet exemple montre comment convertir une OpenMP [parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pour](../../parallel/openmp/reference/for-openmp.md) boucle qui effectue la gestion des exceptions pour utiliser le mécanisme de gestion des exceptions du Runtime d’accès concurrentiel.  
  
 Dans OpenMP, une exception est levée dans une région parallèle doit être interceptée et gérée dans la même région, par le même thread. Une exception s’échappe de la région parallèle est interceptée par le Gestionnaire d’exception non gérée, qui met fin au processus par défaut.  
  

 Dans le Runtime d’accès concurrentiel, lorsque vous levez une exception dans le corps d’une fonction de travail que vous passez à un groupe de tâches comme un [concurrency::task_group](reference/task-group-class.md) ou [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objet, ou pour un algorithme parallèle comme [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), le runtime stocke cette exception et la marshale au contexte qui attend que le groupe de tâches ou l’algorithme à terminer. Pour les groupes de tâches, le contexte d’attente est le contexte qui appelle [Concurrency::task_group :: wait](reference/task-group-class.md#wait), [Concurrency::structured_task_group :: wait](reference/structured-task-group-class.md#wait), [concurrency::task_group::run_and _wait](reference/task-group-class.md#run_and_wait), ou [Concurrency::structured_task_group :: run_and_wait](reference/structured-task-group-class.md#run_and_wait). Pour un algorithme parallèle, le contexte d’attente est le contexte qui a appelé cet algorithme. Également, le runtime arrête toutes les tâches actives qui se trouvent dans le groupe de tâches, y compris celles figurant dans les groupes de tâches enfants, et ignore les tâches qui n’ont pas encore démarré.  


  
## <a name="example"></a>Exemple  
 Cet exemple montre comment gérer des exceptions dans une OpenMP `parallel` région et dans un appel à `parallel_for`. Le `do_work` fonction effectue une demande d’allocation de mémoire qui n’aboutit pas et par conséquent lève une exception de type [std::bad_alloc](../../standard-library/bad-alloc-class.md). Dans la version qui utilise OpenMP, le thread qui lève l’exception doit également l’intercepter. En d’autres termes, chaque itération d’une boucle OpenMP parallèle doit gérer l’exception. Dans la version qui utilise le Runtime d’accès concurrentiel, le thread principal intercepte une exception qui est levée par un autre thread.  
  
 [!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that uses-exception-handling_1.cpp)]  
  
 Cet exemple produit la sortie suivante.  
  
```Output  
Using OpenMP...  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
An error of type 'class std::bad_alloc' occurred.  
Using the Concurrency Runtime...  
An error of type 'class std::bad_alloc' occurred.  
```  
  
 Dans la version de cet exemple qui utilise OpenMP, l’exception se produit dans et est gérée par chaque itération de boucle. Dans la version qui utilise le Runtime d’accès concurrentiel, le runtime stocke l’exception, arrête toutes les tâches actives, ignore les tâches qui n’ont pas encore démarré et marshale l’exception au contexte qui appelle `parallel_for`.  
  
 Si vous avez besoin que la version qui utilise OpenMP se termine une fois que l’exception se produit, vous pouvez utiliser un indicateur booléen pour indiquer aux autres itérations de boucle que l’erreur s’est produite. Comme dans l’exemple dans la rubrique [Comment : convertir une boucle OpenMP qui l’utilise, annulation pour utiliser le Runtime d’accès concurrentiel](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md), itérations de boucle ultérieures n’auront aucun effet si l’indicateur est défini. À l’inverse, si vous avez besoin que la boucle qui utilise le Runtime d’accès concurrentiel se poursuit une fois que l’exception se produit, gérer l’exception dans le corps de la boucle parallèle.  
  
 Autres composants du Runtime d’accès concurrentiel, tels que les agents asynchrones et les tâches légères, ne transportent pas d’exceptions. Au lieu de cela, les exceptions non gérées sont interceptées par le Gestionnaire d’exception non gérée, qui met fin au processus par défaut. Pour plus d’informations sur la gestion des exceptions, consultez [la gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 Pour plus d’informations sur `parallel_for` et d’autres algorithmes parallèles, consultez [des algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `concrt-omp-exceptions.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 **CL.exe /EHsc /openmp concrt-omp-exceptions.cpp**  
  
## <a name="see-also"></a>Voir aussi  
 [Migration d’OpenMP au Runtime d’accès concurrentiel](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)

