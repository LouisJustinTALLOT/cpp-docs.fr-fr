---
title: 'Procédure : Convertir une boucle OpenMP qui a recours à l’annulation pour utiliser le Runtime d’accès concurrentiel'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: 618e93c18173bfe3e5f5b5f3058a8bb3d61e98ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413942"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>Procédure : Convertir une boucle OpenMP qui a recours à l’annulation pour utiliser le Runtime d’accès concurrentiel

Certains des boucles parallèles ne nécessitent pas que toutes les itérations être exécuté. Par exemple, un algorithme qui recherche une valeur peut s’arrêter après que la valeur est trouvée. OpenMP ne fournit pas un mécanisme permettant de quitter une boucle parallèle. Toutefois, vous pouvez utiliser une valeur booléenne, ou indicateur, pour permettre à une itération de la boucle pour indiquer que la solution a été trouvée. Le Runtime d’accès concurrentiel fournit des fonctionnalités qui activent une tâche pour annuler d’autres tâches qui n’ont pas encore démarré.

Cet exemple montre comment convertir une OpenMP [parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pour](../../parallel/openmp/reference/for-openmp.md) boucle qui ne nécessite pas d’utiliser le mécanisme d’annulation de Runtime d’accès concurrentiel pour toutes les itérations à exécuter.

## <a name="example"></a>Exemple

Cet exemple utilise OpenMP et le Runtime d’accès concurrentiel pour implémenter une version parallèle de la [std::any_of](../../standard-library/algorithm-functions.md#any_of) algorithme. La version OpenMP de cet exemple utilise un indicateur pour coordonner toutes les itérations de boucle parallèle que la condition a été remplie. La version qui utilise le Runtime d’accès concurrentiel utilise le [Concurrency::structured_task_group :: Cancel](reference/structured-task-group-class.md#cancel) méthode pour arrêter l’opération globale lorsque la condition est remplie.

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

Dans la version qui utilise OpenMP, toutes les itérations de la boucle s’exécutent, même lorsque l’indicateur est défini. En outre, si une tâche pour que toutes les tâches enfants, l’indicateur serait également doivent être disponibles pour ces tâches enfants pour communiquer l’annulation. Dans le Runtime d’accès concurrentiel, quand un groupe de tâches est annulé, le runtime annule l’ensemble de l’arborescence de travail, y compris les tâches enfants. Le [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorithme utilise des tâches pour effectuer le travail. Par conséquent, lorsqu’une itération de la boucle annule la tâche racine, l’arborescence entière de calcul est également annulé. Quand une arborescence de travail est annulée, le runtime ne démarre pas de nouvelles tâches. Toutefois, le runtime autorise les tâches que vous ont déjà commencé à terminer. Par conséquent, dans le cas de la `parallel_for_each` algorithme, itérations de boucle active peuvent nettoyer leurs ressources.

Dans les deux versions de cet exemple, si le tableau contient plusieurs copies de la valeur à rechercher, plusieurs itérations de boucle peuvent définir simultanément le résultat et annuler l’opération globale. Vous pouvez utiliser une primitive de synchronisation, par exemple une section critique, si votre problème nécessite que seule une tâche effectue un travail lorsqu’une condition est remplie.

Vous pouvez également utiliser la gestion des exceptions pour annuler des tâches qui utilisent la bibliothèque PPL. Pour plus d’informations sur l’annulation, consultez [l’annulation dans la bibliothèque PPL](cancellation-in-the-ppl.md).

Pour plus d’informations sur `parallel_for_each` et d’autres algorithmes parallèles, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `concrt-omp-parallel-any-of.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**cl.exe /EHsc /openmp concrt-omp-parallel-any-of.cpp**

## <a name="see-also"></a>Voir aussi

[Migration d’OpenMP au runtime d’accès concurrentiel](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)
