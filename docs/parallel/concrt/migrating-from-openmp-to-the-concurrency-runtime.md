---
title: Migration d’OpenMP au Runtime d’accès concurrentiel | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16e10287526e6b815ba56183a8e3d590102507aa
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690486"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>Migration d'OpenMP au runtime d'accès concurrentiel
Le runtime d’accès concurrentiel accepte divers modèles de programmation. Ces modèles peuvent chevaucher ou compléter les modèles d’autres bibliothèques. Les documents dans cette section compare [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) le runtime d’accès concurrentiel et fournissent des exemples sur la migration du code OpenMP existant pour utiliser le Runtime d’accès concurrentiel.  
  
 Le modèle de programmation OpenMP est défini par une norme ouverte et a des liaisons bien définies aux langages de programmation C/C++ et Fortran. Les versions OpenMP 2.0 et 2.5, qui sont pris en charge par le compilateur Visual C++, sont adaptées aux algorithmes parallèles qui sont itératifs ; Autrement dit, ils effectuent itération parallèle sur un tableau de données. OpenMP 3.0 prend en charge les tâches non itératif en plus des tâches itératifs.  
  
 OpenMP montre une efficacité optimale quand le degré de parallélisme est prédéterminé et correspond aux ressources disponibles sur le système. Le modèle OpenMP correspond particulièrement à l’informatique hautes performances, où les problèmes de calcul très volumineux sont répartis sur les ressources de traitement d’un ordinateur. Dans ce scénario, l’environnement matériel est généralement fixe et le développeur peut raisonnablement s’attendre à avoir un accès exclusif à toutes les ressources de calcul lors de l’exécution de l’algorithme.  
  
 Toutefois, environnements informatique moins contraints peut-être pas une bonne correspondance pour OpenMP. Par exemple, les problèmes récursifs (par exemple, l’algorithme de tri rapide ou la recherche dans une arborescence de données) sont plus difficiles à implémenter à l’aide de OpenMP 2.0 et 2.5. Le Runtime d’accès concurrentiel complète les fonctions d’OpenMP en fournissant la [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) et [bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). La bibliothèque d’Agents asynchrones prend en charge le parallélisme des tâches à granularité grossière ; la bibliothèque PPL prend en charge davantage de tâches parallèles affinées. Le Runtime d’accès concurrentiel fournit l’infrastructure qui est requis pour effectuer des opérations en parallèle afin de pouvoir vous concentrer sur la logique de votre application. Toutefois, étant donné que le Runtime d’accès concurrentiel active divers modèles de programmation, sa charge de planification peut être supérieure à d’autres bibliothèques d’accès concurrentiel tels que OpenMP. Par conséquent, nous vous recommandons de tester les performances incrémentielle lorsque vous convertissez votre code OpenMP existant pour utiliser le Runtime d’accès concurrentiel.  
  
## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Lorsque la migration d’OpenMP au Runtime d’accès concurrentiel  
 Il peut être avantageux de migration du code OpenMP existant pour utiliser le Runtime d’accès concurrentiel dans les cas suivants.  
  
|Cases|Avantages du Runtime d’accès concurrentiel|  
|-----------|-------------------------------------------|  
|Vous avez besoin d’une infrastructure de programmation simultanée extensible.|La plupart des fonctionnalités du runtime d’accès concurrentiel peuvent être étendues. Vous pouvez également combiner des fonctionnalités existantes pour en composer de nouvelles. Étant donné que OpenMP repose sur les directives de compilateur, il ne peut pas facilement être étendu.|  
|Votre application va tirer parti de blocage coopératif.|Lorsqu’une tâche bloque, car elle nécessite une ressource qui n’est pas encore disponible, le Runtime d’accès concurrentiel peut effectuer d’autres tâches pendant que la première tâche attend la ressource.|  
|Votre application va tirer parti de l’équilibrage de charge dynamique.|Le Runtime d’accès concurrentiel utilise un algorithme de planification qui ajuste l’allocation des ressources de calcul que les charges de travail évoluent. OpenMP, lorsque le planificateur alloue des ressources informatiques nécessaires pour une région parallèle, ces allocations de ressources sont fixes dans le calcul.|  
|Vous avez besoin de prise en charge de la gestion des exceptions.|La bibliothèque PPL vous permet d’intercepter les exceptions à l’intérieur et en dehors d’une boucle ou une région parallèle. Dans OpenMP, vous devez gérer l’exception à l’intérieur de la boucle ou une région parallèle.|  
|Vous avez besoin d’un mécanisme d’annulation.|La bibliothèque PPL permet aux applications d’annuler les tâches individuelles et les arborescences de travail parallèle. OpenMP nécessite que l’application pour implémenter son propre mécanisme d’annulation.|  
|Vous avez besoin de code parallèle doit se terminer dans un contexte différent à partir de laquelle il démarre.|Le Runtime d’accès concurrentiel vous permet de démarrer une tâche dans un contexte et puis d’attendre ou annuler cette tâche dans un autre contexte. Dans OpenMP, tout le travail parallèle doit se terminer dans le contexte à partir duquel il démarre.|  
|Vous avez besoin de prise en charge du débogage améliorée.|Visual Studio fournit la **piles parallèles** et **tâches parallèles** windows afin que vous pouvez déboguer plus facilement des applications multithread.<br /><br /> Pour plus d’informations sur le débogage de prise en charge pour le Runtime d’accès concurrentiel, consultez [à l’aide de la fenêtre de tâches](/visualstudio/debugger/using-the-tasks-window), [à l’aide de la fenêtre Piles parallèles](/visualstudio/debugger/using-the-parallel-stacks-window), et [procédure pas à pas : débogage d’un parallèle Application](/visualstudio/debugger/walkthrough-debugging-a-parallel-application).|  
  
## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Quand ne pas migrer d’OpenMP au Runtime d’accès concurrentiel  
 Les exemples suivants décrivent lorsqu’il ne peut pas être approprié pour la migration du code OpenMP existant pour utiliser le Runtime d’accès concurrentiel.  
  
|Cases|Explication|  
|-----------|-----------------|  
|Votre application a déjà répond à vos besoins.|Si vous êtes satisfait des performances de l’application et la prise en charge du débogage actuelle, la migration ne peut pas être appropriée.|  
|Les corps des boucles parallèles peu de travail.|La surcharge du Planificateur de tâches du Runtime d’accès concurrentiel ne peut pas surmonter les avantages de l’exécution du corps de la boucle en parallèle, en particulier lorsque le corps de la boucle est relativement faible.|  
|Votre application est écrite en C.|Étant donné que le Runtime d’accès concurrentiel utilise de nombreuses fonctionnalités C++, il peut ne pas convenir lorsque vous ne peut pas écrire du code qui permet à l’application C à utiliser complètement.|  
  
## <a name="related-topics"></a>Rubriques connexes  
 [Guide pratique pour convertir une boucle OpenMP parallèle pour utiliser le runtime d’accès concurrentiel](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)  

 Étant donné une boucle de base qui utilise l’OpenMP [parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) et [pour](../../parallel/openmp/reference/for-openmp.md) directives, montre comment convertir pour utiliser le Runtime d’accès concurrentiel [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme.  

  
 [Guide pratique pour convertir une boucle OpenMP qui a recours à l’annulation pour utiliser le runtime d’accès concurrentiel](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)  
 Étant donné une OpenMP [parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pour](../../parallel/openmp/reference/for-openmp.md) boucle ne nécessitant pas de toutes les itérations à exécuter, montre comment convertir pour utiliser le mécanisme d’annulation de Runtime d’accès concurrentiel.  
  
 [Guide pratique pour convertir une boucle OpenMP qui a recours à la gestion des exceptions pour utiliser le runtime d’accès concurrentiel](../../parallel/concrt/convert-an-openmp-loop-that uses-exception-handling.md)  
 Étant donné une OpenMP [parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pour](../../parallel/openmp/reference/for-openmp.md) boucle qui effectue la gestion des exceptions, montre comment convertir pour utiliser le mécanisme de gestion des exceptions du Runtime d’accès concurrentiel.  
  
 [Guide pratique pour convertir une boucle OpenMP qui a recours à une variable de réduction pour utiliser le runtime d’accès concurrentiel](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)  
 Étant donné une OpenMP [parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pour](../../parallel/openmp/reference/for-openmp.md) boucle qui utilise le [réduction](../../parallel/openmp/reference/reduction.md) clause, montre comment convertir pour utiliser le Runtime d’accès concurrentiel.  
  
## <a name="see-also"></a>Voir aussi  
 [Runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)   
 [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)   
 [Bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)

