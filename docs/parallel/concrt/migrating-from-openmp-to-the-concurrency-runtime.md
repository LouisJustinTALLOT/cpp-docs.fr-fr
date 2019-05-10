---
title: Migration d'OpenMP au runtime d'accès concurrentiel
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
ms.openlocfilehash: ba2b413d40da601029f5c4e1d861576212c10494
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448425"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>Migration d'OpenMP au runtime d'accès concurrentiel

Le runtime d’accès concurrentiel accepte divers modèles de programmation. Ces modèles peuvent chevaucher ou compléter les modèles d’autres bibliothèques. Les documents dans cette section compare [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) au Runtime d’accès concurrentiel et fournissent des exemples sur la migration du code OpenMP existant pour utiliser le Runtime d’accès concurrentiel.

Le modèle de programmation OpenMP est défini par une norme ouverte et a des liaisons bien définies aux langages de programmation C/C++ et Fortran. Les versions OpenMP 2.0 et 2.5, qui sont prises en charge par Microsoft C++ compilateur, sont bien adapté pour les algorithmes parallèles itératifs ; Autrement dit, ils effectuent une itération parallèle sur un tableau de données. OpenMP 3.0 prend en charge les tâches non itératif en plus des tâches itératifs.

OpenMP montre une efficacité optimale quand le degré de parallélisme est prédéterminé et correspond aux ressources disponibles sur le système. Le modèle OpenMP est une excellente correspondance pour l’informatique hautes performances, où les problèmes de calcul très volumineux sont répartis sur les ressources de traitement d’un ordinateur. Dans ce scénario, l’environnement matériel est généralement fixe et le développeur peut raisonnablement s’attendre à avoir un accès exclusif à toutes les ressources de calculs lors de l’exécution de l’algorithme.

Toutefois, environnements informatique moins contraints peut-être pas une bonne correspondance pour OpenMP. Par exemple, les tâches récursives (par exemple, l’algorithme de tri rapide ou la recherche dans une arborescence de données) sont plus difficiles à implémenter à l’aide d’OpenMP 2.0 et 2.5. Le Runtime d’accès concurrentiel étend les fonctionnalités d’OpenMP en fournissant la [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) et [bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). La bibliothèque d’Agents asynchrones prend en charge le parallélisme des tâches de granularité grossière. la bibliothèque PPL prend en charge davantage de tâches parallèles affinées. Le Runtime d’accès concurrentiel fournit l’infrastructure qui est requis pour effectuer des opérations en parallèle afin que vous puissiez vous concentrer sur la logique de votre application. Toutefois, étant donné que le Runtime d’accès concurrentiel permet une variété de modèles de programmation, sa charge de planification peut être supérieure à d’autres bibliothèques d’accès concurrentiel tels que OpenMP. Par conséquent, nous vous recommandons de tester les performances incrémentielle lorsque vous convertissez votre code OpenMP existant pour utiliser le Runtime d’accès concurrentiel.

## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Quand migrer d’OpenMP au Runtime d’accès concurrentiel

Il peut être avantageux de migration du code OpenMP existant pour utiliser le Runtime d’accès concurrentiel dans les cas suivants.

|Cases|Avantages du Runtime d’accès concurrentiel|
|-----------|-------------------------------------------|
|Vous avez besoin d’une infrastructure de programmation simultanée extensible.|La plupart des fonctionnalités du runtime d’accès concurrentiel peuvent être étendues. Vous pouvez également combiner des fonctionnalités existantes pour en composer de nouvelles. OpenMP repose sur les directives de compilateur, il ne peut pas être facilement étendue.|
|Votre application va tirer parti de blocage coopératif.|Lorsqu’une tâche bloque, car elle nécessite une ressource qui n’est pas encore disponible, le Runtime d’accès concurrentiel peut effectuer d’autres tâches pendant que la première tâche attend la ressource.|
|Votre application va tirer parti de l’équilibrage de charge dynamique.|Le Runtime d’accès concurrentiel utilise un algorithme de planification qui ajuste l’allocation des ressources de calcul comme charges de travail évoluent. OpenMP, lorsque le planificateur alloue des ressources informatiques nécessaires pour une région parallèle, ces allocations de ressources sont fixes dans le calcul.|
|Vous avez besoin de prise en charge de la gestion des exceptions.|La bibliothèque PPL vous permet d’intercepter les exceptions à l’intérieur et en dehors d’une boucle ou une région parallèle. OpenMP, vous devez gérer l’exception à l’intérieur de la boucle ou une région parallèle.|
|Vous avez besoin d’un mécanisme d’annulation.|La bibliothèque PPL permet aux applications d’annuler les tâches individuelles et les arborescences de travail parallèle. OpenMP, l’application doit implémenter son propre mécanisme d’annulation.|
|Vous avez besoin de code parallèle se termine dans un contexte différent à partir de laquelle il démarre.|Le Runtime d’accès concurrentiel vous permet de démarrer une tâche dans un contexte et puis d’attendre ou annuler cette tâche dans un autre contexte. OpenMP, tout le travail parallèle doit se terminer dans le contexte à partir de laquelle il démarre.|
|Vous avez besoin de prise en charge du débogage améliorée.|Visual Studio fournit le **piles parallèles** et **tâches parallèles** windows afin que vous pouvez déboguer plus facilement des applications multithread.<br /><br /> Pour plus d’informations sur le débogage de prise en charge pour le Runtime d’accès concurrentiel, consultez [à l’aide de la fenêtre tâches](/visualstudio/debugger/using-the-tasks-window), [à l’aide de la fenêtre Piles parallèles](/visualstudio/debugger/using-the-parallel-stacks-window), et [procédure pas à pas : Débogage d’une Application parallèle](/visualstudio/debugger/walkthrough-debugging-a-parallel-application).|

## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Quand ne pas migrer d’OpenMP au Runtime d’accès concurrentiel

Les cas suivants décrivent lorsqu’il n’est peut-être pas approprié pour la migration du code OpenMP existant pour utiliser le Runtime d’accès concurrentiel.

|Cases|Explication|
|-----------|-----------------|
|Votre application a déjà répond à vos besoins.|Si vous êtes satisfait des performances de l’application et la prise en charge du débogage en cours, migration n’est peut-être pas appropriée.|
|Votre corps des boucles parallèles peu de travail.|La surcharge, le Runtime d’accès concurrentiel du Planificateur de tâches ne peut pas surmonter les avantages de l’exécution du corps de la boucle en parallèle, en particulier lorsque le corps de boucle est relativement faible.|
|Votre application est écrite en C.|Le Runtime d’accès concurrentiel utilise de nombreuses fonctionnalités de C++, il peut ne pas être approprié lorsque vous ne pouvez pas écrire du code qui permet à l’application C à utiliser complètement.|

## <a name="related-topics"></a>Rubriques connexes

[Guide pratique pour convertir un parallèle OpenMP pour boucle pour utiliser le runtime d’accès concurrentiel](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)

Étant donné une boucle de base qui utilise le OpenMP [parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) et [pour](../../parallel/openmp/reference/for-openmp.md) directives, montre comment convertir pour utiliser le Runtime d’accès concurrentiel [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme.

[Guide pratique pour convertir une boucle OpenMP qui a recours à l’annulation pour utiliser le runtime d’accès concurrentiel](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)<br/>
Étant donné une OpenMP [parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pour](../../parallel/openmp/reference/for-openmp.md) boucle ne nécessitant pas de toutes les itérations à exécuter, montre comment convertir pour utiliser le mécanisme d’annulation de Runtime d’accès concurrentiel.

[Guide pratique pour convertir une boucle OpenMP qui a recours à la gestion des exceptions pour utiliser le runtime d'accès concurrentiel](../../parallel/concrt/convert-an-openmp-loop-that-uses-exception-handling.md)<br/>
Étant donné une OpenMP [parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pour](../../parallel/openmp/reference/for-openmp.md) boucle qui effectue la gestion des exceptions, montre comment convertir pour utiliser le mécanisme de gestion des exceptions de Runtime d’accès concurrentiel.

[Guide pratique pour Convertir une boucle OpenMP qui a recours à une variable de réduction pour utiliser le runtime d’accès concurrentiel](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)<br/>
Étant donné une OpenMP [parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pour](../../parallel/openmp/reference/for-openmp.md) boucle qui utilise le [réduction](../../parallel/openmp/reference/reduction.md) clause, montre comment convertir pour utiliser le Runtime d’accès concurrentiel.

## <a name="see-also"></a>Voir aussi

[Le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)<br/>
[Bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)
