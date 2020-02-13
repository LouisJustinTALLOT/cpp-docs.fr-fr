---
title: 'Comment : utiliser la gestion des exceptions pour rompre une boucle parallèle'
ms.date: 11/04/2016
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
ms.openlocfilehash: a5576e8f2416804cac89f5ec34005f4e08b99c47
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142111"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>Comment : utiliser la gestion des exceptions pour rompre une boucle parallèle

Cette rubrique montre comment écrire un algorithme de recherche pour une arborescence de base.

L' [annulation](cancellation-in-the-ppl.md) de rubrique explique le rôle de l’annulation dans la bibliothèque de modèles parallèles. L’utilisation de la gestion des exceptions est un moyen moins efficace d’annuler un travail parallèle que l’utilisation des méthodes [Concurrency :: task_group :: Cancel](reference/task-group-class.md#cancel) et [Concurrency :: structured_task_group :: Cancel](reference/structured-task-group-class.md#cancel) . Toutefois, un scénario dans lequel l’utilisation de la gestion des exceptions pour annuler le travail est le cas lorsque vous appelez une bibliothèque tierce qui utilise des tâches ou des algorithmes parallèles, mais ne fournit pas d’objet `task_group` ou `structured_task_group` à annuler.

## <a name="example"></a>Exemple

L’exemple suivant montre un type de `tree` de base qui contient un élément de données et une liste de nœuds enfants. La section suivante montre le corps de la méthode `for_all`, qui exécute de manière récursive une fonction de travail sur chaque nœud enfant.

[!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]

## <a name="example"></a>Exemple

L’exemple suivant illustre la méthode `for_all`. Elle utilise l’algorithme [Concurrency ::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) pour exécuter une fonction de travail sur chaque nœud de l’arborescence en parallèle.

[!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]

## <a name="example"></a>Exemple

L'exemple suivant illustre la fonction `search_for_value`, qui recherche une valeur dans l'objet `tree` fourni. Cette fonction passe à la méthode `for_all` une fonction de travail qui lève lorsqu’elle trouve un nœud d’arbre qui contient la valeur fournie.

Supposons que la classe `tree` est fournie par une bibliothèque tierce et que vous ne pouvez pas la modifier. Dans ce cas, l’utilisation de la gestion des exceptions est appropriée, car la méthode `for_all` ne fournit pas d’objet `task_group` ou `structured_task_group` à l’appelant. Par conséquent, la fonction de travail ne peut pas annuler directement son groupe de tâches parent.

Lorsque la fonction de travail que vous fournissez à un groupe de tâches lève une exception, le runtime arrête toutes les tâches qui se trouvent dans le groupe de tâches (y compris les groupes de tâches enfants) et ignore toutes les tâches qui n’ont pas encore démarré. La fonction `search_for_value` utilise un bloc `try`-`catch` pour capturer l’exception et imprimer le résultat dans la console.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]

## <a name="example"></a>Exemple

L’exemple suivant crée un objet `tree` et le recherche pour plusieurs valeurs en parallèle. La fonction `build_tree` est présentée plus loin dans cette rubrique.

[!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]

Cet exemple utilise l’algorithme [Concurrency ::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) pour rechercher des valeurs en parallèle. Pour plus d’informations sur cet algorithme, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

## <a name="example"></a>Exemple

L’exemple complet suivant utilise la gestion des exceptions pour rechercher des valeurs dans une arborescence de base.

[!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]

Cet exemple produit l’exemple de sortie suivant.

```Output
Found a node with value 32614.
Found a node with value 86131.
Did not find node with value 17522.
```

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `task-tree-search.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc Task-Tree-Search. cpp**

## <a name="see-also"></a>Voir aussi

[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[Classe task_group](reference/task-group-class.md)<br/>
[structured_task_group, classe](../../parallel/concrt/reference/structured-task-group-class.md)<br/>
[parallel_for_each fonction)](reference/concurrency-namespace-functions.md#parallel_for_each)
