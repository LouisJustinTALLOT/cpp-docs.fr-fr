---
title: 'Procédure : Utiliser parallel_invoke pour exécuter des opérations parallèles'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
ms.openlocfilehash: d618b5f202c6aaf454a60f4f37211d9000600562
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345654"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Procédure : Utiliser parallel_invoke pour exécuter des opérations parallèles

Cet exemple montre comment utiliser le [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorithme pour améliorer les performances d’un programme qui effectue plusieurs opérations sur une source de données partagée. Car aucune opération de modifie la source, elles peuvent être exécutées en parallèle d’une manière simple.

## <a name="example"></a>Exemple

Prenons l’exemple de code suivant qui crée une variable de type `MyDataType`, appelle une fonction pour initialiser cette variable, puis effectue plusieurs opérations de longue durée sur ces données.

[!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]

Si le `lengthy_operation1`, `lengthy_operation2`, et `lengthy_operation3` fonctions ne modifient pas le `MyDataType` variable, ces fonctions peuvent être exécutées en parallèle sans modification supplémentaire.

## <a name="example"></a>Exemple

L’exemple suivant modifie l’exemple précédent pour s’exécuter en parallèle. Le `parallel_invoke` algorithme exécute chaque tâche en parallèle et renvoie une fois que toutes les tâches sont terminées.

[!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]

## <a name="example"></a>Exemple

L’exemple suivant télécharge *l’Iliade* d’Homère à partir de gutenberg.org et exécute plusieurs opérations sur ce fichier. L’exemple effectue d’abord ces opérations en série, puis effectue les mêmes opérations en parallèle.

[!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]

Cet exemple produit la sortie suivante.

```Output
Downloading 'The Iliad'...

Running serial version... took 953 ms.
Running parallel version... took 656 ms.

The most common words that have five or more letters are:
    their (953)
    shall (444)
    which (431)
    great (398)
    Hector (349)
    Achilles (309)
    through (301)
    these (268)
    chief (259)
The longest sequence of words that have the same first letter is:
    through the tempest to the tented
The following palindromes appear in the text:
    spots stops
    speed deeps
    keels sleek
```

Cet exemple utilise le `parallel_invoke` algorithme pour appeler plusieurs fonctions qui agissent sur la même source de données. Vous pouvez utiliser le `parallel_invoke` algorithme pour appeler n’importe quel jeu de fonctions en parallèle, pas uniquement celles qui agissent sur les mêmes données.

Étant donné que le `parallel_invoke` algorithme appelle chaque fonction de travail en parallèle, ses performances sont limitées par la fonction qui prend le plus de temps (autrement dit, si le runtime traite chaque fonction sur un processeur distinct). Si cet exemple effectue plus de tâches en parallèle que le nombre de processeurs disponibles, plusieurs tâches peuvent s’exécuter sur chaque processeur. Dans ce cas, les performances sont limitées par le groupe de tâches qui prend le plus de temps pour terminer.

Étant donné que cet exemple effectue les trois tâches en parallèle, vous ne devriez pas les performances à l’échelle sur les ordinateurs dotés de processeurs plus de trois. Pour améliorer les performances de plus, vous pouvez diviser les tâches d’exécution la plus longue en tâches plus petites et exécuter ces tâches en parallèle.

Vous pouvez utiliser la `parallel_invoke` algorithme au lieu du [concurrency::task_group](reference/task-group-class.md) et [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) classes si vous n’avez pas besoin de prise en charge l’annulation. Pour obtenir un exemple qui compare l’utilisation de la `parallel_invoke` algorithme par rapport à des groupes de tâches, consultez [Comment : Utiliser parallel_invoke pour écrire une Routine de tri parallèle](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md).

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `parallel-word-mining.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**cl.exe /EHsc /MD /DUNICODE /D_AFXDLL parallel-word-mining.cpp**

## <a name="see-also"></a>Voir aussi

[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_invoke, fonction](reference/concurrency-namespace-functions.md#parallel_invoke)
