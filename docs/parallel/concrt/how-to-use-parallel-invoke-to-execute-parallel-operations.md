---
description: 'En savoir plus sur : Comment : utiliser parallel_invoke pour exécuter des opérations parallèles'
title: 'Comment : utiliser parallel_invoke pour exécuter des opérations parallèles'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
ms.openlocfilehash: e31cc19a1670cf7ccf9d664ffbed33fea98134a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334662"
---
# <a name="how-to-use-parallel_invoke-to-execute-parallel-operations"></a>Comment : utiliser parallel_invoke pour exécuter des opérations parallèles

Cet exemple montre comment utiliser l’algorithme [Concurrency ::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) pour améliorer les performances d’un programme qui effectue plusieurs opérations sur une source de données partagée. Dans la mesure où aucune opération ne modifie la source, elle peut être exécutée en parallèle de manière simple.

## <a name="example-create-initialize-and-perform-operations-on-a-variable"></a>Exemple : créer, initialiser et effectuer des opérations sur une variable

Prenons l’exemple de code suivant qui crée une variable de type `MyDataType` , appelle une fonction pour initialiser cette variable, puis effectue plusieurs opérations de longue durée sur ces données.

[!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]

Si les `lengthy_operation1` `lengthy_operation2` fonctions, et `lengthy_operation3` ne modifient pas la `MyDataType` variable, ces fonctions peuvent être exécutées en parallèle sans modification supplémentaire.

## <a name="example-run-previous-example-in-parallel"></a>Exemple : exécuter l’exemple précédent en parallèle

L’exemple suivant modifie l’exemple précédent pour qu’il s’exécute en parallèle. L' `parallel_invoke` algorithme exécute chaque tâche en parallèle et retourne une fois toutes les tâches terminées.

[!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]

## <a name="example-perform-multiple-operations-on-a-downloaded-file"></a>Exemple : effectuer plusieurs opérations sur un fichier téléchargé

L’exemple suivant télécharge *le Iliade* à partir de Gutenberg.org et effectue plusieurs opérations sur ce fichier. L’exemple effectue d’abord ces opérations en série, puis effectue les mêmes opérations en parallèle.

[!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]

Cet exemple produit l’exemple de sortie suivant.

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

Cet exemple utilise l' `parallel_invoke` algorithme pour appeler plusieurs fonctions qui agissent sur la même source de données. Vous pouvez utiliser l' `parallel_invoke` algorithme pour appeler un ensemble de fonctions en parallèle, et non uniquement celles qui agissent sur les mêmes données.

Étant donné que l' `parallel_invoke` algorithme appelle chaque fonction de travail en parallèle, ses performances sont limitées par la fonction qui prend le plus de temps à se terminer (autrement dit, si le runtime traite chaque fonction sur un processeur distinct). Si cet exemple effectue plus de tâches en parallèle que le nombre de processeurs disponibles, plusieurs tâches peuvent s’exécuter sur chaque processeur. Dans ce cas, les performances sont limitées par le groupe de tâches qui prend le plus de temps à se terminer.

Étant donné que cet exemple effectue trois tâches en parallèle, vous ne devez pas vous attendre à ce que les performances soient mises à l’échelle sur les ordinateurs qui ont plus de trois processeurs. Pour améliorer les performances, vous pouvez décomposer les tâches les plus longues en tâches plus petites et exécuter ces tâches en parallèle.

Vous pouvez utiliser l' `parallel_invoke` algorithme à la place des classes [Concurrency :: task_group](reference/task-group-class.md) et [concurrency :: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) si vous n’avez pas besoin de la prise en charge de l’annulation. Pour obtenir un exemple qui compare l’utilisation de l' `parallel_invoke` algorithme et les groupes de tâches, consultez [Comment : utiliser Parallel_invoke pour écrire une routine de tri parallèle](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md).

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le, puis collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `parallel-word-mining.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc/MD/DUNICODE/D_AFXDLL Parallel-Word-Mining. cpp**

## <a name="see-also"></a>Voir aussi

[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_invoke, fonction](reference/concurrency-namespace-functions.md#parallel_invoke)
