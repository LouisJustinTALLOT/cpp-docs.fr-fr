---
title: Concurrency Runtime
ms.date: 07/20/2018
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
ms.openlocfilehash: 6f7b70dcbee639bdd44a195709bddde9e06dee21
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278552"
---
# <a name="concurrency-runtime"></a>Concurrency Runtime

Le runtime d'accès concurrentiel pour C++ vous aide à écrire des applications parallèles fiables, évolutives et réactives. Il permet d'élever le niveau d'abstraction afin que vous n'ayez pas à gérer les détails de l'infrastructure liés à l'accès concurrentiel. Vous pouvez également l'utiliser pour spécifier les stratégies de planification qui répondent aux exigences de vos applications en matière de qualité de service. Utilisez ces ressources pour vous aider à vous familiariser avec le runtime d'accès concurrentiel.

Pour la documentation de référence, consultez [référence](../../parallel/concrt/reference/reference-concurrency-runtime.md).

> [!TIP]
>  Le runtime d’accès concurrentiel s’appuie fortement sur les caractéristiques de C++11 et adopte le style plus moderne de C++. Pour en savoir plus, [Bienvenue dans C++](../../cpp/welcome-back-to-cpp-modern-cpp.md).

## <a name="choosing-concurrency-runtime-features"></a>Choisir les fonctionnalités du runtime d’accès concurrentiel

|||
|-|-|
|[Vue d’ensemble](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|Explique pourquoi le runtime d’accès concurrentiel est important et décrit ses principales fonctionnalités.|
|[Comparaison aux autres modèles d’accès concurrentiel](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Montre la différence entre le runtime d’accès concurrentiel et d’autres modèles d’accès concurrentiel, tels que le pool de threads Windows et OpenMP, afin que vous puissiez utiliser le modèle d’accès concurrentiel le mieux adapté aux exigences de votre application.|
|[Migration d’OpenMP au runtime d’accès concurrentiel](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|Compare l'OpenMP au runtime d'accès concurrentiel et fournit des exemples sur la migration du code OpenMP existant pour utiliser le runtime d'accès concurrentiel.|
|[Bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Présente la bibliothèque de modèles parallèles, laquelle fournit des boucles parallèles, tâches et conteneurs parallèles.|
|[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)|Explique comment utiliser des agents asynchrones et le passage de messages pour intégrer facilement des tâches de flux de données et de traitement pipeline dans vos applications.|
|[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|Présente le Planificateur de tâches, lequel vous permet de réajuster le niveau de performance des applications de bureau utilisant le runtime d’accès concurrentiel.|

## <a name="task-parallelism-in-the-ppl"></a>Parallélisme des tâches dans la bibliothèque PPL

|||
|-|-|
|[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [Guide pratique pour utiliser parallel_invoke pour écrire une routine de tri parallèle](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [Guide pratique pour utiliser parallel_invoke pour exécuter des opérations parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [Guide pratique pour créer une tâche qui se termine après un certain délai](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Décrit les tâches et les groupes de tâches, qui peuvent vous aider à écrire du code asynchrone et à découper le travail parallèle en plus petits morceaux.|
|[Procédure pas à pas : implémentation de tâches futures](../../parallel/concrt/walkthrough-implementing-futures.md)|Montre comment combiner les fonctionnalités du runtime d’accès concurrentiel pour aller plus loin.|
|[Procédure pas à pas : suppression de travail d’un thread d’interface utilisateur](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|Montre comment déplacer le travail qui est effectué par l'IU thread dans une application MFC sur un thread de travail.|
|[Bonnes pratiques de la Bibliothèque de modèles parallèles](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Bonnes pratiques en général du runtime d’accès concurrentiel](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Donne les astuces et meilleures pratiques pour utiliser la bibliothèque de modèles parallèles.|

## <a name="data-parallelism-in-the-ppl"></a>Parallélisme des données dans la bibliothèque PPL

|||
|-|-|
|[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [Guide pratique pour écrire une boucle parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [Guide pratique pour écrire une boucle parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [Guide pratique pour exécuter des opérations de mappage et de réduction en parallèle](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Décrit `parallel_for`, `parallel_for_each`, `parallel_invoke`et d'autres algorithmes parallèles. Utilisez des algorithmes parallèles pour résoudre les problèmes de *données parallèles* qui impliquent des collections de données.|
|[Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [Guide pratique pour utiliser des conteneurs parallèles pour une efficacité accrue](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [Guide pratique pour utiliser la classe combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [Guide pratique pour utiliser la classe combinable pour combiner des ensembles](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|Décrit la classe `combinable` ainsi que `concurrent_vector`, `concurrent_queue`, `concurrent_unordered_map`et d'autres conteneurs parallèles. Utilisez des conteneurs et objets parallèles quand vous avez besoin de conteneurs qui fournissent un accès thread-safe à leurs éléments.|
|[Bonnes pratiques de la Bibliothèque de modèles parallèles](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Bonnes pratiques en général du runtime d’accès concurrentiel](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Donne les astuces et meilleures pratiques pour utiliser la bibliothèque de modèles parallèles.|

## <a name="canceling-tasks-and-parallel-algorithms"></a>Annulation des tâches et des algorithmes parallèles

|||
|-|-|
|[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)|Décrit le rôle de l'annulation dans la bibliothèque de modèles parallèles, en particulier comment initier des demandes d'annulation et y répondre.|
|[Guide pratique pour utiliser l’annulation pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [Guide pratique pour utiliser la gestion des exceptions pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Montre deux façons d'annuler du travail parallèle de données.|

## <a name="universal-windows-platform-apps"></a>Applications de la plateforme Windows universelle

|||
|-|-|
|[Création d’opérations asynchrones dans C++ pour les applications UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|Décrit certains des points clés à prendre en compte lorsque vous utilisez le Runtime d’accès concurrentiel pour effectuer des opérations asynchrones dans une application UWP.|
|[Procédure pas à pas : connexion à l’aide de tâches et de requêtes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|Montre comment combiner les tâches de la bibliothèque de modèles parallèles avec le `IXMLHTTPRequest2` et `IXMLHTTPRequest2Callback` interfaces pour envoyer des demandes HTTP GET et POST à un service web dans une application UWP.|
|[Exemples d’applications Windows Runtime](http://code.msdn.microsoft.com/windowsapps)|Contient des exemples de code téléchargeable et démonstration des applications pour Windows 8.x. Les exemples C++ utilisent les caractéristiques du runtime d'accès concurrentiel comme les tâches PPL pour traiter les données en arrière plan et garder l'UX réactive.|

## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>Programmation de flux de données dans la bibliothèque des agents asynchrones

|||
|-|-|
|[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)<br /><br /> [Guide pratique pour implémenter divers modèles de producteur-consommateur](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [Guide pratique pour fournir des fonctions de travail aux classes call et transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [Guide pratique pour utiliser la classe transformer dans un pipeline de données](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [Guide pratique pour effectuer une sélection parmi les tâches terminées](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [Guide pratique pour envoyer un message à intervalles réguliers](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [Guide pratique pour utiliser un filtre de bloc de message](../../parallel/concrt/how-to-use-a-message-block-filter.md)|Décrit les agents asynchrones, les blocs de messages et les fonctions de transmission de messages qui sont les blocs de base pour réaliser des opérations de flux de données dans le runtime d'accès concurrentiel.|
|[Procédure pas à pas : création d'une application basée sur des agents](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [Procédure pas à pas : création d’un agent de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|Indique comment créer des applications basées sur les agents de base.|
|[Procédure pas à pas : création d’un réseau de traitement d’image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|Montre comment créer un réseau de blocs de messages asynchrones qui effectuent le traitement d'image.|
|[Procédure pas à pas : Utilisation de jointures pour prévenir les interblocages](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|Utilisez le problème du dîner des philosophes pour illustrer comment utiliser le runtime d'accès concurrentiel pour empêcher tout interblocage dans votre application.|
|[Procédure pas à pas : création d’un bloc de message personnalisé](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|Décrit comment créer un type de bloc de message personnalisé qui classe les messages entrants par priorité.|
|[Bonnes pratiques pour la bibliothèque d’agents asynchrones](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [Bonnes pratiques en général du runtime d’accès concurrentiel](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Donne les astuces et meilleures pratiques pour travailler avec les agents.|

## <a name="exception-handling-and-debugging"></a>Gestion des exceptions et débogage

|||
|-|-|
|[Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Décrit comment travailler avec les exceptions du runtime d'accès concurrentiel.|
|[Outils de diagnostic parallèle](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Explique comment affiner vos applications et tirer le meilleur parti du runtime d'accès concurrentiel.|

## <a name="tuning-performance"></a>Réglage des performances

|||
|-|-|
|[Outils de diagnostic parallèle](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Explique comment affiner vos applications et tirer le meilleur parti du runtime d'accès concurrentiel.|
|[Instances de planificateur](../../parallel/concrt/scheduler-instances.md)<br /><br /> [Guide pratique pour gérer une instance de Scheduler](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [Stratégies de planificateur](../../parallel/concrt/scheduler-policies.md)<br /><br /> [Guide pratique pour spécifier des stratégies de Scheduler](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [Guide pratique pour créer des agents qui utilisent des stratégies spécifiques de Scheduler](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|Montre comment travailler avec la gestion d'instances et des politiques du planificateur. Pour les applications du bureau, les politiques du planificateur vous permettent d'associer des règles spécifiques à des types spécifiques de charge de travail. Par exemple, vous pouvez créer une instance du planificateur pour effectuer certaines tâches avec une priorité de thread élevée et utiliser le planificateur par défaut pour effectuer d’autres tâches avec une priorité de thread normale.|
|[Groupes de planification](../../parallel/concrt/schedule-groups.md)<br /><br /> [Guide pratique pour utiliser des groupes de planification pour influencer l’ordre d’exécution](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|Montre comment utiliser les groupes de planification pour grouper par affinités ou par tâches connexes. Par exemple, vous pourriez avoir besoin d’un niveau élevé de localité pour les tâches connexes lorsque ces tâches tirent profit d’une exécution sur le même nœud du processeur.|
|[Tâches légères](../../parallel/concrt/lightweight-tasks.md)|Explique comment les tâches légères sont utiles pour créer un travail qui ne requiert pas d’équilibrage de charge ni d’annulation, et à quel point elles sont aussi utiles pour adapter le code existant pour une utilisation avec le runtime d’accès concurrentiel.|
|[Contextes](../../parallel/concrt/contexts.md)<br /><br /> [Guide pratique pour utiliser la classe de contexte pour implémenter un sémaphore coopératif](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [Guide pratique pour utiliser le surabonnement afin de compenser la latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|Décrit comment contrôler le comportement des threads qui sont gérés par le runtime d'accès concurrentiel.|
|[Fonctions de gestion de la mémoire](../../parallel/concrt/memory-management-functions.md)<br /><br /> [Guide pratique pour utiliser Alloc et Free afin d’améliorer les performances de la mémoire](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|Décrit les fonctions de gestion de la mémoire que le runtime d'accès concurrentiel fournit pour vous aider à allouer et libérer de la mémoire de façon simultanée.|

## <a name="additional-resources"></a>Ressources supplémentaires

|||
|-|-|
|[Modèles de programmation asynchrones et conseils dans Hilo (applications du Windows Store utilisant C++ et XAML)](https://msdn.microsoft.com/library/windows/apps/jj160321.aspx)|Découvrez comment nous avons utilisé le Runtime d’accès concurrentiel pour implémenter des opérations asynchrones dans Hilo, une application Windows Runtime en C++ et XAML.|
|[Blog Programmation parallèle en code natif](http://go.microsoft.com/fwlink/p/?linkid=183873)|Fournit des articles de blog détaillés supplémentaires sur la programmation parallèle dans le runtime d'accès concurrentiel.|
|[Forum Informatique parallèle en C++ et en code natif](http://go.microsoft.com/fwlink/p/?linkid=183874)|Vous permet de participer à des discussions de la communauté sur le runtime d'accès concurrentiel.|
|[Programmation parallèle](/dotnet/standard/parallel-programming/index)|Vous enseigne sur le modèle de programmation parallèle qui est disponible dans le .NET Framework.|

## <a name="see-also"></a>Voir aussi

[Référence](../../parallel/concrt/reference/reference-concurrency-runtime.md)
