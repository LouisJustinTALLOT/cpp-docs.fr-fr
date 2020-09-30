---
title: Migration d'OpenMP au runtime d'accès concurrentiel
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
ms.openlocfilehash: 081d0ae8b312d827a0af98dd45c62f7563e81677
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507765"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>Migration d'OpenMP au runtime d'accès concurrentiel

Le runtime d’accès concurrentiel accepte divers modèles de programmation. Ces modèles peuvent chevaucher ou compléter les modèles d’autres bibliothèques. Les documents de cette section comparent [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) à la Runtime d’accès concurrentiel et fournissent des exemples sur la façon de migrer le code OpenMP existant pour utiliser le runtime d’accès concurrentiel.

Le modèle de programmation OpenMP est défini par une norme ouverte et a des liaisons bien définies aux langages de programmation C/C++ et Fortran. Les versions OpenMP 2,0 et 2,5, qui sont prises en charge par le compilateur Microsoft C++, conviennent parfaitement aux algorithmes parallèles qui sont itératifs. autrement dit, ils effectuent une itération parallèle sur un tableau de données. OpenMP 3,0 prend en charge les tâches non itératives en plus des tâches itératives.

OpenMP montre une efficacité optimale quand le degré de parallélisme est prédéterminé et correspond aux ressources disponibles sur le système. Le modèle OpenMP est particulièrement adapté au calcul hautes performances, où les problèmes de calcul très volumineux sont répartis entre les ressources de traitement d’un ordinateur. Dans ce scénario, l’environnement matériel est généralement fixe et le développeur peut raisonnablement s’attendre à avoir un accès exclusif à toutes les ressources de calcul lors de l’exécution de l’algorithme.

Toutefois, les environnements de calcul moins restreints peuvent ne pas être une bonne correspondance pour OpenMP. Par exemple, les problèmes récursifs (tels que l’algorithme tri rapide ou la recherche dans une arborescence de données) sont plus difficiles à implémenter à l’aide d’OpenMP 2,0 et 2,5. L’runtime d’accès concurrentiel complète les fonctionnalités d’OpenMP en fournissant la [bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) et la [bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). La bibliothèque d’agents asynchrones prend en charge le parallélisme des tâches à granularité grossière ; la bibliothèque de modèles parallèles prend en charge des tâches parallèles plus précises. L’runtime d’accès concurrentiel fournit l’infrastructure nécessaire pour effectuer des opérations en parallèle afin que vous puissiez vous concentrer sur la logique de votre application. Toutefois, étant donné que le runtime d’accès concurrentiel active un large éventail de modèles de programmation, sa surcharge de planification peut être supérieure à celle des autres bibliothèques de concurrence comme OpenMP. Par conséquent, nous vous recommandons de tester les performances de manière incrémentielle quand vous convertissez votre code OpenMP existant pour utiliser le runtime d’accès concurrentiel.

## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Quand migrer d’OpenMP vers le runtime d’accès concurrentiel

Il peut être avantageux de migrer le code OpenMP existant pour utiliser le runtime d’accès concurrentiel dans les cas suivants.

|Cas|Avantages de l’runtime d’accès concurrentiel|
|-----------|-------------------------------------------|
|Vous avez besoin d’une infrastructure de programmation simultanée extensible.|La plupart des fonctionnalités du runtime d’accès concurrentiel peuvent être étendues. Vous pouvez également combiner des fonctionnalités existantes pour en composer de nouvelles. Comme OpenMP repose sur des directives de compilateur, il ne peut pas être facilement étendu.|
|Votre application peut tirer parti d’un blocage coopératif.|Quand une tâche est bloquée parce qu’elle nécessite une ressource qui n’est pas encore disponible, le runtime d’accès concurrentiel peut effectuer d’autres tâches pendant que la première tâche attend la ressource.|
|Votre application peut tirer parti de l’équilibrage de charge dynamique.|L’runtime d’accès concurrentiel utilise un algorithme de planification qui ajuste l’allocation des ressources de calcul à mesure que les charges de travail changent. Dans OpenMP, lorsque le planificateur alloue des ressources de calcul à une région parallèle, ces allocations de ressources sont fixes tout au long du calcul.|
|Vous avez besoin de la prise en charge de la gestion des exceptions.|La bibliothèque PPL vous permet d’intercepter des exceptions à l’intérieur et à l’extérieur d’une région ou d’une boucle parallèle. Dans OpenMP, vous devez gérer l’exception à l’intérieur de la région ou de la boucle parallèle.|
|Vous avez besoin d’un mécanisme d’annulation.|La bibliothèque PPL permet aux applications d’annuler à la fois des tâches individuelles et des arborescences de travail parallèles. OpenMP exige que l’application implémente son propre mécanisme d’annulation.|
|Vous avez besoin d’un code parallèle pour terminer dans un contexte différent de celui à partir duquel il démarre.|La runtime d’accès concurrentiel vous permet de démarrer une tâche dans un contexte, puis d’attendre ou d’annuler cette tâche dans un autre contexte. Dans OpenMP, tout le travail parallèle doit se terminer dans le contexte à partir duquel il démarre.|
|Vous avez besoin d’une prise en charge améliorée du débogage.|Visual Studio fournit les fenêtres **Piles parallèles** et **tâches parallèles** pour vous permettre de déboguer plus facilement les applications multithread.<br /><br /> Pour plus d’informations sur la prise en charge du débogage pour le runtime d’accès concurrentiel, consultez [utilisation de la fenêtre tâches](/visualstudio/debugger/using-the-tasks-window), [utilisation de la fenêtre piles parallèles](/visualstudio/debugger/using-the-parallel-stacks-window)et [procédure pas à pas : débogage d’une application parallèle](/visualstudio/debugger/walkthrough-debugging-a-parallel-application).|

## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Quand ne pas migrer d’OpenMP vers le runtime d’accès concurrentiel

Les cas suivants décrivent le moment où il peut ne pas être approprié de migrer le code OpenMP existant pour utiliser le runtime d’accès concurrentiel.

|Cas|Explication|
|-----------|-----------------|
|Votre application répond déjà à vos besoins.|Si vous êtes satisfait des performances de l’application et de la prise en charge actuelle du débogage, la migration n’est peut-être pas appropriée.|
|Vos corps de boucles parallèles effectuent peu de travail.|La surcharge du planificateur de tâches runtime d’accès concurrentiel peut ne pas dépasser les avantages de l’exécution du corps de la boucle en parallèle, en particulier lorsque le corps de la boucle est relativement petit.|
|Votre application est écrite en C.|Étant donné que le runtime d’accès concurrentiel utilise de nombreuses fonctionnalités C++, il peut ne pas convenir lorsque vous ne pouvez pas écrire de code qui permet à l’application C de l’utiliser pleinement.|

## <a name="related-topics"></a>Rubriques connexes

[Comment : convertir une boucle OpenMP Parallel for pour utiliser le runtime d’accès concurrentiel](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)

Dans le cas d’une boucle de base qui utilise les directives OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) et [for](../openmp/reference/openmp-directives.md#for-openmp) , montre comment la convertir pour utiliser l’algorithme runtime d’accès concurrentiel [Concurrency ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) .

[Comment : convertir une boucle OpenMP qui utilise l’annulation pour utiliser l’runtime d’accès concurrentiel](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)<br/>
À partir d’une boucle OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) qui ne nécessite pas l’exécution de toutes les itérations, montre comment la convertir pour utiliser le mécanisme d’annulation Runtime d’accès concurrentiel.

[Comment : convertir une boucle OpenMP qui utilise la gestion des exceptions pour utiliser le runtime d’accès concurrentiel](../../parallel/concrt/convert-an-openmp-loop-that-uses-exception-handling.md)<br/>
À partir d’une boucle OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) qui effectue la gestion des exceptions, montre comment la convertir pour utiliser le mécanisme de gestion des exceptions Runtime d’accès concurrentiel.

[Comment : convertir une boucle OpenMP qui utilise une variable de réduction pour utiliser le runtime d’accès concurrentiel](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)<br/>
À partir d’une boucle OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) qui utilise la clause [Reduction](../openmp/reference/openmp-clauses.md#reduction) , montre comment la convertir pour utiliser le runtime d’accès concurrentiel.

## <a name="see-also"></a>Voir aussi

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)<br/>
[Bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)
