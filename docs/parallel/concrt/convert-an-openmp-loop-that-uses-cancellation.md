---
description: 'En savoir plus sur : Comment : convertir une boucle OpenMP qui utilise l’annulation pour utiliser l’runtime d’accès concurrentiel'
title: 'Comment : convertir une boucle OpenMP qui a recours à l’annulation pour utiliser le runtime d’accès concurrentiel'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: d64ba8bc3910181f9ce9ddb3844f778cdfe464d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325743"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>Comment : convertir une boucle OpenMP qui a recours à l’annulation pour utiliser le runtime d’accès concurrentiel

Certaines boucles parallèles ne requièrent pas l’exécution de toutes les itérations. Par exemple, un algorithme qui recherche une valeur peut se terminer une fois la valeur trouvée. OpenMP ne fournit pas de mécanisme permettant d’annuler une boucle parallèle. Toutefois, vous pouvez utiliser une valeur booléenne, ou indicateur, pour permettre à une itération de la boucle d’indiquer que la solution a été trouvée. Le runtime d’accès concurrentiel fournit des fonctionnalités qui permettent à une tâche d’annuler d’autres tâches qui n’ont pas encore démarré.

Cet exemple montre comment convertir une boucle OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) qui ne nécessite pas l’exécution de toutes les itérations pour utiliser le mécanisme d’annulation Runtime d’accès concurrentiel.

## <a name="example"></a>Exemple

Cet exemple utilise à la fois OpenMP et le runtime d’accès concurrentiel pour implémenter une version parallèle de l’algorithme [std :: any_of](../../standard-library/algorithm-functions.md#any_of) . La version OpenMP de cet exemple utilise un indicateur pour coordonner toutes les itérations de boucle parallèle que la condition a été remplie. La version qui utilise l’runtime d’accès concurrentiel utilise la méthode [Concurrency :: structured_task_group :: Cancel](reference/structured-task-group-class.md#cancel) pour arrêter l’opération globale lorsque la condition est remplie.

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

Dans la version de qui utilise OpenMP, toutes les itérations de la boucle s’exécutent, même lorsque l’indicateur est défini. En outre, si une tâche doit avoir des tâches enfants, l’indicateur doit également être disponible pour que ces tâches enfants puissent communiquer l’annulation. Dans le runtime d’accès concurrentiel, lorsqu’un groupe de tâches est annulé, le runtime annule l’intégralité de l’arborescence du travail, y compris les tâches enfants. L’algorithme [Concurrency ::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) utilise des tâches pour effectuer le travail. Par conséquent, lorsqu’une itération de la boucle annule la tâche racine, l’arborescence entière du calcul est également annulée. Lorsqu’une arborescence de travail est annulée, le runtime ne démarre pas de nouvelles tâches. Toutefois, le runtime autorise l’achèvement des tâches qui ont déjà commencé. Par conséquent, dans le cas de l' `parallel_for_each` algorithme, les itérations de la boucle active peuvent nettoyer leurs ressources.

Dans les deux versions de cet exemple, si le tableau contient plus d’une copie de la valeur à rechercher, plusieurs itérations de boucle peuvent définir simultanément le résultat et annuler l’opération globale. Vous pouvez utiliser une primitive de synchronisation, telle qu’une section critique, si votre problème requiert qu’une seule tâche effectue un travail lorsqu’une condition est remplie.

Vous pouvez également utiliser la gestion des exceptions pour annuler les tâches qui utilisent la bibliothèque de modèles parallèles. Pour plus d’informations sur l’annulation, consultez [annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md).

Pour plus d’informations sur `parallel_for_each` et d’autres algorithmes parallèles, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `concrt-omp-parallel-any-of.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc/OpenMP concrt-omp-parallel-any-of. cpp**

## <a name="see-also"></a>Voir aussi

[Migration d'OpenMP au runtime d'accès concurrentiel](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)
