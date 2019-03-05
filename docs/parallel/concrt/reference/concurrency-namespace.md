---
title: concurrency, espace de noms
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue/concurrency
- agents/concurrency
- concurrent_vector/concurrency
- concrt/concurrency
- internal_split_ordered_list/concurrency
- concurrent_queue/concurrency
- pplcancellation_token/concurrency
- pplinterface/concurrency
- ppltasks/concurrency
- ppl/concurrency
- concurrent_unordered_map/concurrency
- concrtrm/concurrency
- concurrent_unordered_set/concurrency
- pplconcrt/concurrency
- internal_concurrent_hash/concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: f1d33ca2-679b-4442-b140-22a9d9df61d1
ms.openlocfilehash: aa2fe7dedd1c7e1a8b5a72e01508b4201bd72a7d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303389"
---
# <a name="concurrency-namespace"></a>concurrency, espace de noms

L'espace de noms `Concurrency` fournit des classes et des fonctions qui vous donnent accès au runtime d'accès concurrentiel, infrastructure de programmation simultanée pour C++. Pour plus d’informations, consultez [Runtime d’accès concurrentiel](../../../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Syntaxe

```
namespace concurrency;
```

## <a name="members"></a>Membres

### <a name="typedefs"></a>Typedef

|Nom|Description|
|----------|-----------------|
|`runtime_object_identity`|Chaque instance de message a une identité qui la suit quand elle est clonée et passée entre des composants de messagerie. Il ne peut pas s'agir de l'adresse de l'objet message.|
|`task_status`|Type représentant l'état terminal d'une tâche. Les valeurs valides sont `completed` et `canceled`.|
|`TaskProc`|Abstraction élémentaire d’une tâche, définie comme `void (__cdecl * TaskProc)(void *)`. Un `TaskProc` est appelé pour appeler le corps d’une tâche.|
|`TaskProc_t`|Abstraction élémentaire d’une tâche, définie comme `void (__cdecl * TaskProc_t)(void *)`. Un `TaskProc` est appelé pour appeler le corps d’une tâche.|

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[affinity_partitioner, classe](affinity-partitioner-class.md)|La classe `affinity_partitioner` est similaire à la classe `static_partitioner`, mais elle améliore l'affinité du cache par son choix de mapper les sous-plages aux threads de travail. Elle peut améliorer considérablement les performances quand une boucle est réexécutée sur le même jeu de données et que les données tiennent dans le cache. Notez que le même objet `affinity_partitioner` doit être utilisé avec les itérations suivantes d'une boucle parallèle exécutée sur un jeu de données particulier, pour bénéficier de la localité des données.|
|[agent, classe](agent-class.md)|Classe destinée à être utilisée comme classe de base pour tous les agents indépendants. Elle est utilisée pour masquer l'état des autres agents et interagir par transmission de messages.|
|[auto_partitioner, classe](auto-partitioner-class.md)|La classe `auto_partitioner` représente la méthode par défaut que `parallel_for`, `parallel_for_each` et `parallel_transform` utilisent pour partitionner la plage au sein de laquelle ils itèrent. Cette méthode de partitionnement utilise un vol de plage pour équilibrer la charge et annuler par itération.|
|[bad_target, classe](bad-target-class.md)|Cette classe décrit une exception levée quand un bloc de messagerie reçoit un pointeur vers une cible qui n'est pas valide pour l'opération en cours.|
|[call, classe](call-class.md)|Un bloc de messagerie `call` est un `target_block` ordonné à plusieurs sources qui appelle une fonction spécifiée lors de la réception d'un message.|
|[cancellation_token, classe](cancellation-token-class.md)|La classe `cancellation_token` représente la capacité à déterminer si l'annulation d'une opération a été demandée. Un jeton donné peut être associé à un objet `task_group`, `structured_task_group` ou `task` pour entraîner une annulation implicite. Il peut également être sondé à la recherche d'une annulation ou comporter un rappel enregistré en cas d'annulation de la classe `cancellation_token_source` associée.|
|[cancellation_token_registration, classe](cancellation-token-registration-class.md)|La classe `cancellation_token_registration` représente une notification de rappel de `cancellation_token`. Quand la méthode `register` sur une classe `cancellation_token` est utilisée pour recevoir une notification relative à la date d'annulation, un objet `cancellation_token_registration` est retourné comme handle au rappel afin que l'appelant puisse demander qu'un rappel spécifique ne soit plus effectué via l'utilisation de la méthode `deregister`.|
|[cancellation_token_source, classe](cancellation-token-source-class.md)|La classe `cancellation_token_source` représente la capacité d'annulation d'une opération annulable.|
|[choice, classe](choice-class.md)|Un bloc de messagerie `choice` est un bloc à plusieurs sources et à cible unique qui représente une interaction de flux de contrôle avec un jeu de sources. Le bloc choice attend que l'une des multiples sources produise un message et propage l'index de la source qui a généré le message.|
|[combinable, classe](combinable-class.md)|L'objet `combinable<T>` est destiné à fournir des copies privées de thread des données pour exécuter des sous-calculs locaux de thread sans verrou pendant des algorithmes parallèles. À la fin de l'opération parallèle, les sous-calculs privés de thread peuvent être fusionnées dans un résultat final. Cette classe peut être utilisée à la place d'une variable partagée et peut entraîner une amélioration des performances au cas où il y aurait beaucoup de conflit sur cette variable partagée.|
|[concurrent_priority_queue, classe](concurrent-priority-queue-class.md)|La classe `concurrent_priority_queue` est un conteneur qui permet à plusieurs threads d'appeler simultanément des méthodes Push et Pop sur des éléments. Les éléments sont dépilés dans l'ordre de priorité dans lequel la priorité est déterminée par un functor fourni comme argument de modèle.|
|[concurrent_queue, classe](concurrent-queue-class.md)|La classe `concurrent_queue` est une classe de conteneur de séquence qui autorise un accès Premier entré, premier sorti à ses éléments. Elle permet un ensemble limité d'opérations d'accès concurrentiel sécurisé, comme `push` et `try_pop`.|
|[concurrent_unordered_map, classe](concurrent-unordered-map-class.md)|La classe `concurrent_unordered_map` est un conteneur d'accès concurrentiel sécurisé qui contrôle une séquence à longueur variable d'éléments de type `std::pair<const K, _Element_type>`. La séquence est représentée d'une manière à permettre les opérations d'ajout d'accès concurrentiel sécurisé, d'accès à un élément, d'accès à un itérateur et de traversée d'itérateur.|
|[concurrent_unordered_multimap, classe](concurrent-unordered-multimap-class.md)|La classe `concurrent_unordered_multimap` est un conteneur d'accès concurrentiel sécurisé qui contrôle une séquence à longueur variable d'éléments de type `std::pair<const K, _Element_type>`. La séquence est représentée d'une manière à permettre les opérations d'ajout d'accès concurrentiel sécurisé, d'accès à un élément, d'accès à un itérateur et de traversée d'itérateur.|
|[concurrent_unordered_multiset, classe](concurrent-unordered-multiset-class.md)|Le `concurrent_unordered_multiset` classe est un conteneur d’accès concurrentiel sécurisé qui contrôle une séquence de longueur variable constituée d’éléments de type K. La séquence est représentée d’une façon qui permet l’accès concurrentiel sécurisé Ajout, l’accès à un élément, itérateurs et opérations de traversée d’itérateur.|
|[concurrent_unordered_set, classe](concurrent-unordered-set-class.md)|Le `concurrent_unordered_set` classe est un conteneur d’accès concurrentiel sécurisé qui contrôle une séquence de longueur variable constituée d’éléments de type K. La séquence est représentée d’une façon qui permet l’accès concurrentiel sécurisé Ajout, l’accès à un élément, itérateurs et opérations de traversée d’itérateur.|
|[concurrent_vector, classe](concurrent-vector-class.md)|La classe `concurrent_vector` est une classe de conteneur de séquence qui autorise un accès aléatoire à tout élément. Elle permet les opérations d'ajout d'accès concurrentiel sécurisé, d'accès à un élément, d'accès à un itérateur et de traversée d'itérateur.|
|[Context, classe](context-class.md)|Représente une abstraction pour un contexte d'exécution.|
|[context_self_unblock, classe](context-self-unblock-class.md)|Cette classe décrit une exception levée quand la méthode `Unblock` d'un objet `Context` est appelée à partir du même contexte. Elle indique une tentative par un contexte donné de se débloquer.|
|[context_unblock_unbalanced, classe](context-unblock-unbalanced-class.md)|Cette classe décrit une exception levée quand des appels aux méthodes `Block` et `Unblock` d'un objet `Context` ne sont pas correctement associés.|
|[critical_section, classe](critical-section-class.md)|Mutex non réentrant qui a explicitement connaissance du runtime d'accès concurrentiel.|
|[CurrentScheduler, classe](currentscheduler-class.md)|Représente une abstraction pour le planificateur actuel associé au contexte d'appel.|
|[default_scheduler_exists, classe](default-scheduler-exists-class.md)|Cette classe décrit une exception levée quand la méthode `Scheduler::SetDefaultSchedulerPolicy` est appelée alors qu'un planificateur par défaut existe déjà au sein du processus.|
|[event, classe](event-class.md)|Événement de réinitialisation manuelle qui a explicitement connaissance du runtime d'accès concurrentiel.|
|[improper_lock, classe](improper-lock-class.md)|Cette classe décrit une exception levée quand un verrou est incorrectement acquis.|
|[improper_scheduler_attach, classe](improper-scheduler-attach-class.md)|Cette classe décrit une exception levée quand la méthode `Attach` est appelée sur un objet `Scheduler` qui est déjà attaché au contexte actuel.|
|[improper_scheduler_detach, classe](improper-scheduler-detach-class.md)|Cette classe décrit une exception levée quand la méthode `CurrentScheduler::Detach` est appelée sur un contexte qui n'a pas été attaché à un planificateur à l'aide de la méthode `Attach` d'un objet `Scheduler`.|
|[improper_scheduler_reference, classe](improper-scheduler-reference-class.md)|Cette classe décrit une exception levée quand la méthode `Reference` est appelée sur un objet `Scheduler` en cours d'arrêt, à partir d'un contexte qui ne fait pas partie de ce planificateur.|
|[invalid_link_target, classe](invalid-link-target-class.md)|Cette classe décrit une exception levée quand la méthode `link_target` d'un bloc de messagerie est appelée et que le bloc de messagerie ne parvient pas à établir un lien avec la cible. Cette situation peut être due à un dépassement du nombre de liens autorisé pour le bloc de messagerie ou à une tentative à deux reprises de liaison d'une cible spécifique à la même source.|
|[invalid_multiple_scheduling, classe](invalid-multiple-scheduling-class.md)|Cette classe décrit une exception levée quand un objet `task_handle` est planifié à plusieurs reprises à l'aide de la méthode `run` d'un objet `task_group` ou `structured_task_group` sans appel intermédiaire aux méthodes `wait` ou `run_and_wait`.|
|[invalid_operation, classe](invalid-operation-class.md)|Cette classe décrit une exception qui est levée quand une opération non valide qui n'est pas décrite de façon plus précise par un autre type d'exception levé par le runtime d'accès concurrentiel est exécutée.|
|[invalid_oversubscribe_operation, classe](invalid-oversubscribe-operation-class.md)|Cette classe décrit une exception levée quand la méthode `Context::Oversubscribe` est appelée avec le paramètre `_BeginOversubscription` défini sur `false` sans appel préalable à la méthode `Context::Oversubscribe` avec le paramètre `_BeginOversubscription` défini sur `true`.|
|[invalid_scheduler_policy_key, classe](invalid-scheduler-policy-key-class.md)|Cette classe décrit une exception levée quand une clé non valide ou inconnue est passée à un constructeur d'objet `SchedulerPolicy`, ou quand la méthode `SetPolicyValue` d'un objet `SchedulerPolicy` est passée à une clé qui doit être modifiée à l'aide d'autres moyens que la méthode `SetConcurrencyLimits`.|
|[invalid_scheduler_policy_thread_specification, classe](invalid-scheduler-policy-thread-specification-class.md)|Cette classe décrit une exception levée quand est effectuée une tentative de définir les limites d'accès concurrentiel d'un objet `SchedulerPolicy` de telle sorte que la valeur de la clé `MinConcurrency` est inférieure à celle de la clé `MaxConcurrency`.|
|[invalid_scheduler_policy_value, classe](invalid-scheduler-policy-value-class.md)|Cette classe décrit une exception levée quand une clé de stratégie d'un objet `SchedulerPolicy` est défini sur une valeur non valide pour cette clé.|
|[ISource, classe](isource-class.md)|La classe `ISource` est l'interface de tous les blocs sources. Les blocs sources propagent les messages aux blocs `ITarget`.|
|[ITarget, classe](itarget-class.md)|La classe `ITarget` est l'interface de tous les blocs cibles. Les blocs cibles consomment les messages qui leur sont offerts par les blocs `ISource`.|
|[join, classe](join-class.md)|Un bloc de messagerie `join` est un `propagator_block` à cible unique, à sources multiples et ordonné qui combine des messages de type `T` en provenance de chacune de ses sources.|
|[location, classe](location-class.md)|Abstraction d'un emplacement physique sur du matériel.|
|[message, classe](message-class.md)|Enveloppe de message de base contenant la charge utile de données transmise entre les blocs de messagerie.|
|[message_not_found, classe](message-not-found-class.md)|Cette classe décrit une exception levée quand un bloc de messagerie ne parvient pas à trouver un message demandé.|
|[message_processor, classe](message-processor-class.md)|La classe `message_processor` est la classe de base abstraite pour le traitement des objets `message`. Aucune garantie n'existe sur l'ordre des messages.|
|[missing_wait, classe](missing-wait-class.md)|Cette classe décrit une exception levée quand il existe des tâches encore planifiées sur un objet `task_group` ou `structured_task_group` au moment où le destructeur d’objet s’exécute. Cette exception n'est jamais levée si le destructeur est atteint en raison d'un déroulement de pile consécutif à une exception.|
|[multi_link_registry, classe](multi-link-registry-class.md)|L'objet `multi_link_registry` est un `network_link_registry` qui gère plusieurs blocs sources ou plusieurs blocs cibles.|
|[multitype_join, classe](multitype-join-class.md)|Un bloc de messagerie `multitype_join` est un bloc de messagerie à sources multiples et à cible unique qui combine des messages de types différents en provenance de chacune de ses sources et qui offre un tuple des messages combinés à ses cibles.|
|[nested_scheduler_missing_detach, classe](nested-scheduler-missing-detach-class.md)|Cette classe décrit une exception levée quand le runtime d'accès concurrentiel détecte que vous avez omis d'appeler la méthode `CurrentScheduler::Detach` sur un contexte joint à un deuxième planificateur à l'aide de la méthode `Attach` de l'objet `Scheduler`.|
|[network_link_registry, classe](network-link-registry-class.md)|La classe de base abstraite `network_link_registry` gère les liens entre les blocs sources et cibles.|
|[operation_timed_out, classe](operation-timed-out-class.md)|Cette classe décrit une exception levée quand une opération a expiré.|
|[ordered_message_processor, classe](ordered-message-processor-class.md)|Un `ordered_message_processor` est un `message_processor` qui permet aux blocs de messages de traiter les messages dans l'ordre de leur réception.|
|[overwrite_buffer, classe](overwrite-buffer-class.md)|Un bloc de messagerie `overwrite_buffer` est un `propagator_block` à cibles multiples, à sources multiples et ordonné, capable de stocker un seul message à la fois. Les nouveaux messages remplacent ceux précédemment conservés.|
|[progress_reporter, classe](progress-reporter-class.md)|La classe d'indication de la progression permet de signaler des notifications de progression d'un type spécifique. Chaque objet progress_reporter est lié à une opération ou à une action asynchrone particulière.|
|[propagator_block, classe](propagator-block-class.md)|La classe `propagator_block` est une classe de base abstraite pour les blocs de messages qui sont à la fois une source et une cible. Elle combine les fonctionnalités des classes `source_block` et `target_block`.|
|[reader_writer_lock, classe](reader-writer-lock-class.md)|Verrou de lecteur-writer basé sur une file d'attente à préférence de writer avec rotation uniquement locale. Le verrou accorde un accès Premier entré, premier sorti aux writers et prive les lecteurs sous une charge continue de writers.|
|[ScheduleGroup, classe](schedulegroup-class.md)|Représente une abstraction d'un groupe de planification. Les groupes de planification organisent un ensemble de travaux connexes qui ont l’avantage d’être planifiés de façon rapprochée soit dans le temps, en exécutant une autre tâche dans le même groupe avant de passer à un autre groupe, soit dans l’espace, en exécutant plusieurs éléments au sein du même groupe sur le même nœud NUMA ou socket physique.|
|[Scheduler, classe](scheduler-class.md)|Représente une abstraction pour un planificateur de runtime d'accès concurrentiel.|
|[scheduler_not_attached, classe](scheduler-not-attached-class.md)|Cette classe décrit une exception levée quand une opération qui requiert l'attachement d'un planificateur au contexte actuel est effectuée alors qu'aucun planificateur n'est attaché.|
|[scheduler_resource_allocation_error, classe](scheduler-resource-allocation-error-class.md)|Cette classe décrit une exception levée en raison d'un échec d'acquisition d'une ressource critique dans le runtime d'accès concurrentiel.|
|[scheduler_worker_creation_error, classe](scheduler-worker-creation-error-class.md)|Cette classe décrit une exception levée en raison d'un échec de création d'un contexte d'exécution de travail dans le runtime d'accès concurrentiel.|
|[SchedulerPolicy, classe](schedulerpolicy-class.md)|La classe `SchedulerPolicy` contient un jeu de paires clé/valeur, un pour chaque élément de stratégie, qui contrôlent le comportement d'une instance du planificateur.|
|[simple_partitioner, classe](simple-partitioner-class.md)|La classe `simple_partitioner` représente un partitionnement statique de la plage itérée par `parallel_for`. Le partitionneur divise la plage en segments de sorte que chaque segment comporte au moins le nombre d'itérations spécifié par la taille du segment.|
|[single_assignment, classe](single-assignment-class.md)|Un bloc de messagerie `single_assignment` est un `propagator_block` à cibles multiples, à sources multiples et ordonné, capable de stocker un `message` unique écrit une seule fois.|
|[single_link_registry, classe](single-link-registry-class.md)|L'objet `single_link_registry` est un `network_link_registry` qui gère uniquement un seul bloc source ou cible.|
|[source_block, classe](source-block-class.md)|La classe `source_block` est une classe de base abstraite pour les blocs sources uniquement. La classe fournit une fonctionnalité de gestion des liens de base ainsi que des vérifications d'erreurs courantes.|
|[source_link_manager, classe](source-link-manager-class.md)|L'objet `source_link_manager` gère les liens réseau des blocs de messagerie avec les blocs `ISource`.|
|[static_partitioner, classe](static-partitioner-class.md)|La classe `static_partitioner` représente un partitionnement statique de la plage itérée par `parallel_for`. Le partitionneur divise la plage en autant de segments que de travaux disponibles pour le planificateur sous-jacent.|
|[structured_task_group, classe](structured-task-group-class.md)|La classe `structured_task_group` représente une collection très structurée de travail parallèle. Vous pouvez mettre en file d'attente des tâches parallèles individuelles dans un `structured_task_group` à l'aide d'objets `task_handle`, attendre qu'elles se terminent ou annuler le groupe de tâches avant la fin de leur exécution, ce qui annule toutes les tâches dont l'exécution n'a pas commencé.|
|[target_block, classe](target-block-class.md)|La classe `target_block` est une classe de base abstraite qui fournit une fonctionnalité de gestion des liens de base et une vérification des erreurs pour les blocs cibles uniquement.|
|[task (Concurrency Runtime), classe](task-class.md)|Classe `task` de la bibliothèque de modèles parallèles (PPL, Parallel Patterns Library). Un objet `task` représente le travail qui peut être exécuté de manière asynchrone et simultanément avec d'autres tâches et le travail parallèle produit par des algorithmes parallèles dans le runtime d'accès concurrentiel. Il génère un résultat de type `_ResultType` quand il s'exécute correctement. Les tâches de type `task<void>` ne génèrent aucun résultat. Une tâche peut être mise en attente et annulée indépendamment des autres tâches. Elle peut également être composée avec d'autres tâches à l'aide de continuations (`then`) et de modèles de jointure (`when_all`) et de choix (`when_any`).|
|[task_canceled, classe](task-canceled-class.md)|Cette classe décrit une exception levée par la couche de tâches PPL pour forcer l’annulation de la tâche actuelle. Elle est également levée par le `get()` méthode sur [tâche](task-class.md), pour une tâche annulée.|
|[task_completion_event, classe](task-completion-event-class.md)|La classe `task_completion_event` vous permet de retarder l'exécution d'une tâche jusqu'à ce qu'une condition soit satisfaite, ou de démarrer une tâche en réponse à un événement externe.|
|[task_continuation_context, classe](task-continuation-context-class.md)|La classe `task_continuation_context` vous permet de spécifier où vous souhaitez qu'une continuation soit exécutée. Il est uniquement utile d’utiliser cette classe à partir d’une application UWP. Pour les applications non - Windows Runtime, le contexte d’exécution de la continuation tâche est déterminé par le runtime et non configurables.|
|[Classe task_group](task-group-class.md)|La classe `task_group` représente une collection de travail parallèle qui peut être attendue ou annulée.|
|[task_handle, classe](task-handle-class.md)|La classe `task_handle` représente un élément de travail parallèle individuel. Elle encapsule les instructions et les données requises pour exécuter un élément de travail.|
|[task_options, classe (Concurrency Runtime)](task-options-class-concurrency-runtime.md)|Représente les options autorisées pour la création d’une tâche.|
|[timer, classe](timer-class.md)|Un bloc de messagerie `timer` est un `source_block` à cible unique, capable d'envoyer un message à sa cible après un délai spécifié ou à intervalles spécifiques.|
|[transformer, classe](transformer-class.md)|Un bloc de messagerie `transformer` est un `propagator_block` à cible unique, à sources multiples et classé qui peut accepter des messages d'un type et est capable de stocker un nombre illimité de messages d'un type différent.|
|[Classe unbounded_buffer](unbounded-buffer-class.md)|Un bloc de messagerie `unbounded_buffer` est un `propagator_block` à cibles multiples, à sources multiples et ordonné, capable de stocker un nombre illimité de messages.|
|[unsupported_os, classe](unsupported-os-class.md)|Cette classe décrit une exception levée quand un système d'exploitation non pris en charge est utilisé.|

### <a name="structures"></a>Structures

|Nom|Description|
|----------|-----------------|
|[DispatchState, structure](dispatchstate-structure.md)|La structure `DispatchState` est utilisée pour transférer l'état à la méthode `IExecutionContext::Dispatch`. Elle décrit les circonstances dans lesquelles la méthode `Dispatch` est appelée sur une interface `IExecutionContext`.|
|[IExecutionContext, structure](iexecutioncontext-structure.md)|Interface avec un contexte d'exécution qui peut s'exécuter sur un processeur virtuel donné et dont le contexte peut être commuté de manière coopérative.|
|[IExecutionResource, structure](iexecutionresource-structure.md)|Abstraction d'un thread matériel.|
|[IResourceManager, structure](iresourcemanager-structure.md)|Interface avec un gestionnaire des ressources du runtime d'accès concurrentiel. Il s'agit de l'interface par laquelle les planificateurs communiquent avec le gestionnaire des ressources.|
|[IScheduler, structure](ischeduler-structure.md)|Interface avec une abstraction d'un planificateur de tâches. Le gestionnaire des ressources du runtime d'accès concurrentiel utilise cette interface pour communiquer avec les planificateurs de tâches.|
|[ISchedulerProxy, structure](ischedulerproxy-structure.md)|Interface par laquelle les planificateurs communiquent avec le gestionnaire des ressources du runtime d'accès concurrentiel pour négocier l'allocation des ressources.|
|[IThreadProxy, structure](ithreadproxy-structure.md)|Abstraction d'un thread d'exécution. Selon la clé de stratégie `SchedulerType` du planificateur que vous créez, le gestionnaire des ressources vous accorde un proxy de thread assorti d'un thread Win32 standard ou d'un thread UMS (User-Mode Scheduling). Les threads UMS sont pris en charge sur les systèmes d'exploitation 64 bits avec Windows 7 et ses versions ultérieures.|
|[ITopologyExecutionResource, structure](itopologyexecutionresource-structure.md)|Interface avec une ressource d'exécution tel que défini par le Gestionnaire de ressources.|
|[ITopologyNode, structure](itopologynode-structure.md)|Interface avec un nœud de topologie, comme défini par le gestionnaire des ressources. Un nœud contient une ou plusieurs ressources d'exécution.|
|[IUMSCompletionList, structure](iumscompletionlist-structure.md)|Représente une liste de saisie semi-automatique UMS. Quand un thread UMS se bloque, le contexte de planification désigné du planificateur est distribué afin de déterminer les éléments à planifier sur la racine du processeur virtuel sous-jacent pendant que le thread d'origine est bloqué. Quand le thread d'origine se débloque, le système d'exploitation le met en attente dans la liste de saisie semi-automatique accessible via cette interface. Le planificateur peut interroger la liste de saisie semi-automatique à propos du contexte de planification désigné ou de tout autre emplacement qu'il recherche pour du travail.|
|[IUMSScheduler, structure](iumsscheduler-structure.md)|Interface avec une abstraction d'un planificateur de tâches qui veut que le gestionnaire des ressources du runtime d'accès concurrentiel lui remette des threads UMS (User-Mode Scheduling). Le gestionnaire des ressources utilise cette interface pour communiquer avec les planificateurs de threads UMS. L'interface `IUMSScheduler` hérite de l'interface `IScheduler` .|
|[IUMSThreadProxy, structure](iumsthreadproxy-structure.md)|Abstraction d'un thread d'exécution. Si vous voulez que votre planificateur reçoive des threads UMS (User-Mode Scheduling), affectez à l'élément de stratégie du planificateur `SchedulerKind` la valeur `UmsThreadDefault`, puis implémentez l'interface `IUMSScheduler`. Les threads UMS sont uniquement pris en charge sur les systèmes d'exploitation 64 bits avec Windows 7 et ses versions ultérieures.|
|[IUMSUnblockNotification, structure](iumsunblocknotification-structure.md)|Représente une notification du gestionnaire des ressources qui indique qu'un proxy de thread qui s'est bloqué et qui a déclenché un retour vers le contexte de planification désigné du planificateur s'est débloqué et est prêt à être planifié. Cette interface n'est pas valide une fois que le contexte d'exécution associé du proxy de thread, retourné à partir de la méthode `GetContext`, est replanifié.|
|[IVirtualProcessorRoot, structure](ivirtualprocessorroot-structure.md)|Abstraction d'un thread matériel sur laquelle un proxy de thread peut s'exécuter.|
|[scheduler_interface, structure](scheduler-interface-structure.md)|Interface du planificateur|
|[scheduler_ptr, structure (runtime d’accès concurrentiel)](scheduler-ptr-structure-concurrency-runtime.md)|Représente un pointeur vers un planificateur. Cette classe existe pour permettre la spécification d’une durée de vie partagée à l’aide de shared_ptr ou simplement une référence simple à l’aide du pointeur brut.|

### <a name="enumerations"></a>Énumérations

|Name|Description|
|----------|-----------------|
|[agent_status](concurrency-namespace-enums.md#agent_status)|États valides d'un `agent`.|
|[Agents_EventType](concurrency-namespace-enums.md#agents_eventtype)|Types d'événements qui peuvent être tracés à l'aide des fonctionnalités de traçage offertes par la bibliothèque d'agents.|
|[ConcRT_EventType](concurrency-namespace-enums.md#concrt_eventtype)|Types d'événements qui peuvent être tracés à l'aide des fonctionnalités de traçage offertes par le runtime d'accès concurrentiel.|
|[Concrt_TraceFlags](concurrency-namespace-enums.md#concrt_traceflags)|Indicateurs de suivi des types d'événements.|
|[CriticalRegionType](concurrency-namespace-enums.md#criticalregiontype)|Type de région critique dans lequel se trouve un contexte.|
|[DynamicProgressFeedbackType](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|Utilisé par la stratégie `DynamicProgressFeedback` pour décrire si les ressources du planificateur sont rééquilibrées d'après les informations statistiques collectées auprès du planificateur ou uniquement en fonction des processeurs virtuels qui entrent dans l'état d'inactivité et en sortent via des appels aux méthodes `Activate` et `Deactivate` sur l'interface `IVirtualProcessorRoot`. Pour plus d’informations sur les stratégies de planificateur disponibles, consultez [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|
|[join_type](concurrency-namespace-enums.md#join_type)|Type d'un bloc de messagerie `join`.|
|[message_status](concurrency-namespace-enums.md#message_status)|Réponses valides à une offre d'objet `message` à un bloc.|
|[PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)|Clés de stratégie qui décrivent certains aspects du comportement du planificateur. Chaque élément de stratégie est décrit par une paire clé-valeur. Pour plus d’informations sur les stratégies de planificateur et leur impact sur les planificateurs, consultez [Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).|
|[SchedulerType](concurrency-namespace-enums.md#schedulertype)|Utilisé par la stratégie `SchedulerKind` pour décrire le type des threads que le planificateur doit utiliser pour les contextes d'exécution sous-jacents. Pour plus d’informations sur les stratégies de planificateur disponibles, consultez [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|
|[SchedulingProtocolType](concurrency-namespace-enums.md#schedulingprotocoltype)|Utilisé par la stratégie `SchedulingProtocol` pour décrire l'algorithme de planification utilisé pour le planificateur. Pour plus d’informations sur les stratégies de planificateur disponibles, consultez [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|
|[SwitchingProxyState](concurrency-namespace-enums.md#switchingproxystate)|Utilisé pour indiquer l'état d'un proxy de thread, quand il exécute un changement de contexte coopératif vers un proxy de thread différent.|
|[task_group_status](concurrency-namespace-enums.md#task_group_status)|Décrit l'état d'exécution d'un objet `task_group` ou `structured_task_group`. Une valeur de ce type est retournée par de nombreuses méthodes qui attendent que les tâches planifiées pour un groupe de tâches se terminent.|
|[WinRTInitializationType](concurrency-namespace-enums.md#winrtinitializationtype)|Utilisé par la stratégie `WinRTInitialization` pour décrire si et comment le Windows Runtime est initialisé sur les threads de planificateur pour une application qui s'exécute sur des systèmes d'exploitation Windows 8 ou versions ultérieures. Pour plus d’informations sur les stratégies de planificateur disponibles, consultez [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|

### <a name="functions"></a>Fonctions

|Nom|Description|
|----------|-----------------|
|[Alloc, fonction](concurrency-namespace-functions.md#alloc)|Alloue un bloc de mémoire de la taille spécifiée depuis le sous-allocateur de mise en cache du runtime d'accès concurrentiel.|
|[asend, fonction](concurrency-namespace-functions.md#asend)|Surchargé. Opération d’envoi asynchrone qui planifie une tâche pour propager les données vers le bloc cible.|
|[cancel_current_task, fonction](concurrency-namespace-functions.md#cancel_current_task)|Annule la tâche en cours d’exécution. Cette fonction peut être appelée à partir du corps d'une tâche pour annuler l'exécution de la tâche et la faire passer à l'état `canceled`.<br /><br /> L'appel de cette fonction en dehors du corps d'un objet `task` n'est pas pris en charge. Cela entraînerait un comportement non défini tel qu'un blocage dans votre application.|
|[create_async, fonction](concurrency-namespace-functions.md#create_async)|Crée une construction asynchrone Windows Runtime basée sur un objet lambda ou de fonction fourni par l'utilisateur. Le type de retour de `create_async` est `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^` ou `IAsyncOperationWithProgress<TResult, TProgress>^` selon la signature de l’objet lambda passée à la méthode.|
|[create_task, fonction](concurrency-namespace-functions.md#create_task)|Surchargé. Crée une bibliothèque de modèles parallèles [tâche](task-class.md) objet. `create_task` peut être utilisé partout où vous auriez utilisé un constructeur de tâche. Il est fourni principalement pour des raisons pratiques, car il permet d'utiliser le mot clé `auto` pendant la création de tâches.|
|[CreateResourceManager, fonction](concurrency-namespace-functions.md#createresourcemanager)|Retourne une interface qui représente l'instance singleton du gestionnaire des ressources du runtime d'accès concurrentiel. Le gestionnaire des ressources est responsable de l'affectation des ressources aux planificateurs qui veulent coopérer.|
|[DisableTracing, fonction](concurrency-namespace-functions.md#disabletracing)|Désactive le traçage dans le runtime d'accès concurrentiel. Cette fonction est déconseillée car le suivi ETW est désinscrit par défaut.|
|[EnableTracing, fonction](concurrency-namespace-functions.md#enabletracing)|Active le traçage dans le runtime d'accès concurrentiel. Cette fonction est déconseillée car le suivi ETW est à présent activé par défaut.|
|[Free (fonction)](concurrency-namespace-functions.md#free)|Libère un bloc de mémoire précédemment alloué par la méthode `Alloc` au sous-allocateur de mise en cache du runtime d'accès concurrentiel.|
|[get_ambient_scheduler, fonction (Runtime d’accès concurrentiel)](concurrency-namespace-functions.md#get_ambient_scheduler)||
|[GetExecutionContextId, fonction](concurrency-namespace-functions.md#getexecutioncontextid)|Retourne un identificateur unique qui peut être affecté à un contexte d'exécution qui implémente l'interface `IExecutionContext`.|
|[GetOSVersion, fonction](concurrency-namespace-functions.md#getosversion)|Retourne la version du système d'exploitation.|
|[GetProcessorCount, fonction](concurrency-namespace-functions.md#getprocessorcount)|Retourne le nombre de threads matériels sur le système sous-jacent.|
|[GetProcessorNodeCount, fonction](concurrency-namespace-functions.md#getprocessornodecount)|Retourne le nombre de nœuds NUMA ou de packages de processeurs sur le système sous-jacent.|
|[GetSchedulerId, fonction](concurrency-namespace-functions.md#getschedulerid)|Retourne un identificateur unique qui peut être affecté à un planificateur qui implémente l'interface `IScheduler`.|
|[interruption_point, fonction](concurrency-namespace-functions.md#interruption_point)|Crée un point d'interruption pour l'annulation. Si une annulation est en cours dans le contexte dans lequel cette fonction est appelée, une exception interne est levée et annule l'exécution du travail parallèle en cours. Si aucune annulation n'est en cours, la fonction ne fait rien.|
|[is_current_task_group_canceling, fonction](concurrency-namespace-functions.md#is_current_task_group_canceling)|Retourne une indication qui détermine si le groupe de tâches qui s'exécute actuellement inline sur le contexte actuel est au beau milieu d'une annulation active (ou le sera bientôt). Notez que si aucun groupe de tâches ne s'exécute actuellement inline sur le contexte actuel, `false` est retourné.|
|[make_choice, fonction](concurrency-namespace-functions.md#make_choice)|Surchargé. Construit un bloc de messagerie `choice` à partir d'un `Scheduler` ou `ScheduleGroup` facultatif et de deux sources d'entrée ou plus.|
|[make_greedy_join, fonction](concurrency-namespace-functions.md#make_greedy_join)|Surchargé. Construit un bloc de messagerie `greedy multitype_join` à partir d'un `Scheduler` ou `ScheduleGroup` facultatif et de deux sources d'entrée ou plus.|
|[make_join, fonction](concurrency-namespace-functions.md#make_join)|Surchargé. Construit un bloc de messagerie `non_greedy multitype_join` à partir d'un `Scheduler` ou `ScheduleGroup` facultatif et de deux sources d'entrée ou plus.|
|[make_task, fonction](concurrency-namespace-functions.md#make_task)|Méthode de fabrique pour la création d'un objet `task_handle`.|
|[parallel_buffered_sort, fonction](concurrency-namespace-functions.md#parallel_buffered_sort)|Surchargé. Réorganise les éléments d’une plage spécifiée dans un ordre non décroissant ou selon un critère de tri spécifié par un prédicat binaire, en parallèle. Cette fonction est sémantiquement similaire à `std::sort` en ce sens qu'il s'agit d'un tri sur place, par comparaison et instable, à l'exception près qu'elle a besoin d'un espace supplémentaire `O(n)` et qu'elle requiert une initialisation par défaut pour les éléments triés.|
|[parallel_for (fonction)](concurrency-namespace-functions.md#parallel_for)|Surchargé. `parallel_for` effectue une itération sur une plage d'index et exécute une fonction fournie par l'utilisateur à chaque itération, en parallèle.|
|[parallel_for_each, fonction](concurrency-namespace-functions.md#parallel_for_each)|Surchargé. `parallel_for_each` applique une fonction spécifiée à chaque élément dans une plage, en parallèle. Sémantiquement, elle équivaut à la fonction `for_each` dans l'espace de noms `std`, si ce n'est que l'itération des éléments est effectuée en parallèle et que l'ordre d'itération n'est pas spécifié. L’argument `_Func` doit prendre en charge un opérateur d’appel de fonction sous la forme de `operator()(T)` où le paramètre `T` est le type d’élément du conteneur en cours d’itération.|
|[parallel_invoke, fonction](concurrency-namespace-functions.md#parallel_invoke)|Surchargé. Exécute les objets de fonction fournis comme paramètres en parallèle et se bloque jusqu'à la fin de leur exécution. Chaque objet de fonction peut être une expression lambda, un pointeur vers une fonction ou tout objet qui prend en charge l’opérateur d’appel de fonction avec la signature `void operator()()`.|
|[parallel_radixsort, fonction](concurrency-namespace-functions.md#parallel_radixsort)|Surchargé. Réorganise les éléments d'une plage spécifiée dans un ordre non décroissant à l'aide d'un algorithme de tri de base. Il s'agit d'une fonction de tri stable qui requiert une fonction de projection capable de projeter les éléments à trier dans des clés de type entiers non signés. L'initialisation par défaut est requise pour les éléments triés.|
|[parallel_reduce, fonction](concurrency-namespace-functions.md#parallel_reduce)|Surchargé. Calcule la somme de tous les éléments d'une plage spécifiée en calculant des sommes partielles successives, ou calcule le résultat des résultats partiels successifs obtenus de la même façon en utilisant une opération binaire spécifiée autre que la somme, en parallèle. `parallel_reduce` est sémantiquement similaire à `std::accumulate`, à l'exception près qu'elle a besoin que l'opération binaire soit associative et qu'elle requiert une valeur d'identité au lieu d'une valeur initiale.|
|[parallel_sort, fonction](concurrency-namespace-functions.md#parallel_sort)|Surchargé. Réorganise les éléments d’une plage spécifiée dans un ordre non décroissant ou selon un critère de tri spécifié par un prédicat binaire, en parallèle. Cette fonction est sémantiquement similaire à `std::sort` en ce sens qu'il s'agit d'un tri sur place, par comparaison et instable.|
|[parallel_transform, fonction](concurrency-namespace-functions.md#parallel_transform)|Surchargé. Applique un objet de fonction spécifié à chaque élément d'une plage source ou à une paire d'éléments de deux plages sources, et copie les valeurs de retour de l'objet de fonction dans une plage de destination, en parallèle. Cette fonction équivaut sémantiquement à `std::transform`.|
|[Receive, fonction](concurrency-namespace-functions.md#receive)|Surchargé. Implémentation générale de la fonction receive, qui permet à un contexte d'attendre des données en provenance d'une seule source exactement et de filtrer les valeurs qui sont acceptées.|
|[run_with_cancellation_token, fonction](concurrency-namespace-functions.md#run_with_cancellation_token)|Exécute un objet de fonction immédiatement et de manière synchrone dans le contexte d’un jeton d’annulation donné.|
|[Send, fonction](concurrency-namespace-functions.md#send)|Surchargé. Opération d’envoi synchrone qui attend que la cible accepte ou refuse le message.|
|[set_ambient_scheduler, fonction (Runtime d’accès concurrentiel)](concurrency-namespace-functions.md#set_ambient_scheduler)||
|[set_task_execution_resources, fonction](concurrency-namespace-functions.md#set_task_execution_resources)|Surchargé. Limite les ressources d'exécution utilisées par les threads de travail interne du runtime d'accès concurrentiel à l'ensemble d'affinités spécifié.<br /><br /> Il est possible d'appeler cette méthode uniquement avant de créer le gestionnaire des ressources, ou entre deux durées de vie de gestionnaires des ressources. Cette méthode peut être appelée plusieurs fois tant que le gestionnaire des ressources n'existe pas au moment de l'appel. Une fois qu'une limite d'affinité a été définie, elle reste en vigueur jusqu'au prochain appel valide à la méthode `set_task_execution_resources`.<br /><br /> Le masque d'affinité fourni n'a pas besoin de correspondre à un sous-ensemble du masque d'affinité du processus. L'affinité du processus est mis à jour si besoin.|
|[Fonction swap](concurrency-namespace-functions.md#swap)|Échange les éléments de deux objets `concurrent_vector`.|
|[task_from_exception, fonction (Runtime d’accès concurrentiel)](concurrency-namespace-functions.md#task_from_exception)||
|[task_from_result, fonction (Runtime d’accès concurrentiel)](concurrency-namespace-functions.md#task_from_result)||
|[Trace_agents_register_name, fonction](concurrency-namespace-functions.md#trace_agents_register_name)|Associe le nom donné au bloc de message ou à l'agent dans le suivi ETW.|
|[try_receive, fonction](concurrency-namespace-functions.md#try_receive)|Surchargé. Implémentation générale de la fonction try-receive, qui permet à un contexte de rechercher des données en provenance d'une seule source exactement et de filtrer les valeurs qui sont acceptées. Si les données ne sont pas prêtes, la méthode retourne false.|
|[Wait, fonction](concurrency-namespace-functions.md#wait)|Suspend le contexte actuel pendant une durée spécifiée.|
|[when_all, fonction](concurrency-namespace-functions.md#when_all)|Crée une tâche qui s’effectue correctement lorsque toutes les tâches fournies comme arguments s’effectuent correctement.|
|[when_any, fonction](concurrency-namespace-functions.md#when_any)|Surchargé. Crée une tâche qui s'effectue quand l'une des tâches fournies en tant qu'arguments s'effectue.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|----------|-----------------|
|[!=, opérateur](concurrency-namespace-operators.md#operator_neq)|Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur n'est pas égal à l'objet `concurrent_vector` situé à droite.|
|[operator&&](concurrency-namespace-operators.md#operator_amp_amp)|Surchargé. Crée une tâche qui s'effectue correctement lorsque les deux tâches fournies comme arguments se déroulent correctement.|
|[operator&#124;&#124;](concurrency-namespace-operators.md#operator_lor)|Surchargé. Crée une tâche qui s’effectue correctement quand l’une des tâches fournies en tant qu’arguments s’effectue correctement.|
|[operator<](concurrency-namespace-operators.md#operator_lt)|Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est inférieur à l'objet `concurrent_vector` situé à droite.|
|[operator<=](concurrency-namespace-operators.md#operator_lt_eq)|Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est inférieur ou égal à l'objet `concurrent_vector` situé à droite.|
|[operator==](concurrency-namespace-operators.md#operator_eq_eq)|Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est égal à l'objet `concurrent_vector` situé à droite.|
|[operator>](concurrency-namespace-operators.md#operator_gt)|Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est supérieur à l'objet `concurrent_vector` situé à droite.|
|[operator>=](concurrency-namespace-operators.md#operator_lt_eq)|Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est supérieur ou égal à l'objet `concurrent_vector` situé à droite.|

### <a name="constants"></a>Constantes

|Nom|Description|
|----------|-----------------|
|[AgentEventGuid](concurrency-namespace-constants1.md#agenteventguid)|GUID de catégorie ({B9B5B78C-0713-4898-A21A-C67949DCED07}) qui décrit les événements ETW déclenchés par la bibliothèque d'agents dans le runtime d'accès concurrentiel.|
|[ChoreEventGuid](concurrency-namespace-constants1.md#choreeventguid)|GUID de catégorie qui décrit les événements ETW déclenchés par le runtime d’accès concurrentiel qui sont directement liés à des tâches.|
|[ConcRT_ProviderGuid](concurrency-namespace-constants1.md#concrt_providerguid)|GUID du fournisseur ETW pour le runtime d'accès concurrentiel.|
|[CONCRT_RM_VERSION_1](concurrency-namespace-constants1.md#concrt_rm_version_1)|Indique la prise en charge de l'interface du gestionnaire des ressources définie dans Visual Studio 2010.|
|[ConcRTEventGuid](concurrency-namespace-constants1.md#concrteventguid)|GUID de catégorie qui décrit les événements ETW déclenchés par le runtime d'accès concurrentiel qui ne sont pas décrits plus précisément par une autre catégorie.|
|[ContextEventGuid](concurrency-namespace-constants1.md#contexteventguid)|GUID de catégorie qui décrit les événements ETW déclenchés par le runtime d'accès concurrentiel qui sont directement liés à des contextes.|
|[COOPERATIVE_TIMEOUT_INFINITE](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|Valeur qui indique qu'une attente ne doit jamais expirer.|
|[COOPERATIVE_WAIT_TIMEOUT](concurrency-namespace-constants1.md#cooperative_wait_timeout)|Valeur qui indique qu'une attente a expiré.|
|[INHERIT_THREAD_PRIORITY](concurrency-namespace-constants1.md#inherit_thread_priority)|Valeur spéciale de la clé de stratégie `ContextPriority` qui indique que la priorité de thread de tous les contextes du planificateur doit être la même que celle du thread qui a créé le planificateur.|
|[LockEventGuid](concurrency-namespace-constants1.md#lockeventguid)|GUID de catégorie qui décrit les événements ETW déclenchés par le runtime d'accès concurrentiel qui sont directement liés à des verrous.|
|[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)|Valeur spéciale pour les clés de stratégie `MinConcurrency` et `MaxConcurrency`. Prend la valeur par défaut du nombre de threads matériels sur l'ordinateur en l'absence d'autres contraintes.|
|[PPLParallelForeachEventGuid](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|GUID de catégorie qui décrit les événements ETW déclenchés par le runtime d'accès concurrentiel qui sont directement liés à l'utilisation de la fonction `parallel_for_each`.|
|[PPLParallelForEventGuid](concurrency-namespace-constants1.md#pplparallelforeventguid)|GUID de catégorie qui décrit les événements ETW déclenchés par le runtime d'accès concurrentiel qui sont directement liés à l'utilisation de la fonction `parallel_for`.|
|[PPLParallelInvokeEventGuid](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|GUID de catégorie qui décrit les événements ETW déclenchés par le runtime d'accès concurrentiel qui sont directement liés à l'utilisation de la fonction `parallel_invoke`.|
|[ResourceManagerEventGuid](concurrency-namespace-constants1.md#resourcemanagereventguid)|GUID de catégorie qui décrit les événements ETW déclenchés par le runtime d'accès concurrentiel qui sont directement liés au gestionnaire des ressources.|
|[ScheduleGroupEventGuid](concurrency-namespace-constants1.md#schedulegroupeventguid)|GUID de catégorie qui décrit les événements ETW déclenchés par le runtime d'accès concurrentiel qui sont directement liés à des groupes de planification.|
|[SchedulerEventGuid](concurrency-namespace-constants1.md#schedulereventguid)|GUID de catégorie qui décrit les événements ETW déclenchés par le runtime d'accès concurrentiel qui sont directement liés à l'activité du planificateur.|
|[VirtualProcessorEventGuid](concurrency-namespace-constants1.md#virtualprocessoreventguid)|GUID de catégorie qui décrit les événements ETW déclenchés par le runtime d'accès concurrentiel qui sont directement liés à des processeurs virtuels.|

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h, concrt.h, concrtrm.h, concurrent_priority_queue.h, concurrent_queue.h, concurrent_unordered_map.h, concurrent_unordered_set.h, concurrent_vector.h, internal_concurrent_hash.h, internal_split_ordered_ List.h, ppl.h, pplcancellation_token.h, pplconcrt.h, pplinterface.h, ppltasks.h

## <a name="see-also"></a>Voir aussi

[Référence](reference-concurrency-runtime.md)
