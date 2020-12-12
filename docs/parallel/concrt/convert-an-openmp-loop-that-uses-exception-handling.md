---
description: 'En savoir plus sur : Comment : convertir une boucle OpenMP qui utilise la gestion des exceptions pour utiliser le runtime d’accès concurrentiel'
title: "Comment : convertir une boucle OpenMP qui a recours à la gestion des exceptions pour utiliser le runtime d'accès concurrentiel"
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: 8258506cfce76361eea151fe6b7f934a04f3a0aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325730"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>Comment : convertir une boucle OpenMP qui a recours à la gestion des exceptions pour utiliser le runtime d'accès concurrentiel

Cet exemple montre comment convertir une boucle OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) qui effectue la gestion des exceptions pour utiliser le mécanisme de gestion des exceptions Runtime d’accès concurrentiel.

Dans OpenMP, une exception levée dans une région parallèle doit être interceptée et gérée dans la même région par le même thread. Une exception qui échappe la région parallèle est interceptée par le gestionnaire d’exceptions non gérées, qui met fin au processus par défaut.

Dans le runtime d’accès concurrentiel, quand vous levez une exception dans le corps d’une fonction de travail que vous transmettez à un groupe de tâches comme un objet [Concurrency :: task_group](reference/task-group-class.md) ou [Concurrency :: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) , ou à un algorithme parallèle tel que [Concurrency ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for), le runtime stocke cette exception et la marshale vers le contexte qui attend la fin du groupe de tâches Pour les groupes de tâches, le contexte d’attente est le contexte qui appelle [Concurrency :: task_group :: wait](reference/task-group-class.md#wait), [Concurrency :: structured_task_group :: wait](reference/structured-task-group-class.md#wait), [Concurrency :: task_group :: run_and_wait](reference/task-group-class.md#run_and_wait)ou [concurrency :: structured_task_group :: run_and_wait](reference/structured-task-group-class.md#run_and_wait). Pour un algorithme parallèle, le contexte d’attente est le contexte qui a appelé cet algorithme. Le runtime arrête également toutes les tâches actives qui se trouvent dans le groupe de tâches, y compris celles des groupes de tâches enfants, et ignore toutes les tâches qui n’ont pas encore démarré.

## <a name="example"></a>Exemple

Cet exemple montre comment gérer les exceptions dans une `parallel` région OpenMP et dans un appel à `parallel_for` . La `do_work` fonction effectue une demande d’allocation de mémoire qui ne fonctionne pas et, par conséquent, lève une exception de type [std :: bad_alloc](../../standard-library/bad-alloc-class.md). Dans la version qui utilise OpenMP, le thread qui lève l’exception doit également l’intercepter. En d’autres termes, chaque itération d’une boucle parallèle OpenMP doit gérer l’exception. Dans la version qui utilise le runtime d’accès concurrentiel, le thread principal intercepte une exception qui est levée par un autre thread.

[!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-exception-handling_1.cpp)]

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

Dans la version de cet exemple qui utilise OpenMP, l’exception se produit dans et est gérée par chaque itération de la boucle. Dans la version qui utilise le runtime d’accès concurrentiel, le runtime stocke l’exception, arrête toutes les tâches actives, ignore toutes les tâches qui n’ont pas encore démarré et marshale l’exception au contexte qui appelle `parallel_for` .

Si vous avez besoin que la version qui utilise OpenMP se termine après l’exception, vous pouvez utiliser un indicateur booléen pour signaler à d’autres itérations de boucle que l’erreur s’est produite. Comme dans l’exemple de la rubrique [Comment : convertir une boucle OpenMP qui utilise l’annulation pour utiliser l’Runtime d’accès concurrentiel](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md), les itérations de boucle suivantes ne font rien si l’indicateur est défini. À l’inverse, si vous avez besoin que la boucle qui utilise le runtime d’accès concurrentiel se poursuive après l’exception, gérez l’exception dans le corps de la boucle parallèle elle-même.

Les autres composants de la runtime d’accès concurrentiel, tels que les agents asynchrones et les tâches légères, ne transportent pas d’exceptions. Au lieu de cela, les exceptions non gérées sont interceptées par le gestionnaire d’exceptions non gérées, qui met fin au processus par défaut. Pour plus d’informations sur la gestion des exceptions, consultez [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Pour plus d’informations sur `parallel_for` et d’autres algorithmes parallèles, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `concrt-omp-exceptions.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc/OpenMP concrt-omp-exceptions. cpp**

## <a name="see-also"></a>Voir aussi

[Migration d'OpenMP au runtime d'accès concurrentiel](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)
