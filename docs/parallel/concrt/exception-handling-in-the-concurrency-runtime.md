---
title: Gestion des exceptions dans le runtime d’accès concurrentiel
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
ms.openlocfilehash: f85bf5c96ef31944e84473f1fedb077123801153
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230400"
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>Gestion des exceptions dans le runtime d’accès concurrentiel

Le runtime d’accès concurrentiel utilise la gestion des exceptions C++ pour communiquer de nombreux types d’erreurs. Ces erreurs incluent l’utilisation non valide du runtime, les erreurs d’exécution, telles que l’échec d’acquisition d’une ressource, et les erreurs qui se produisent dans les fonctions de travail que vous fournissez aux tâches et aux groupes de tâches. Lorsqu’une tâche ou un groupe de tâches lève une exception, le runtime maintient cette exception et la marshale dans le contexte qui attend que la tâche ou le groupe de tâches se termine. Pour des composants tels que des tâches et des agents légers, le runtime ne gère pas les exceptions pour vous. Dans ce cas, vous devez implémenter votre propre mécanisme de gestion des exceptions. Cette rubrique décrit comment le Runtime gère les exceptions levées par les tâches, les groupes de tâches, les tâches légères et les agents asynchrones, et comment répondre aux exceptions dans vos applications.

## <a name="key-points"></a>Points clés

- Lorsqu’une tâche ou un groupe de tâches lève une exception, le runtime maintient cette exception et la marshale dans le contexte qui attend que la tâche ou le groupe de tâches se termine.

- Lorsque cela est possible, entourez chaque appel à [Concurrency :: Task :: obten](reference/task-class.md#get) et [Concurrency :: Task :: wait](reference/task-class.md#wait) avec un **`try`** / **`catch`** bloc pour gérer les erreurs à partir desquelles vous pouvez effectuer une récupération. Le Runtime met fin à l’application si une tâche lève une exception et que cette exception n’est pas interceptée par la tâche, l’une de ses continuations ou l’application principale.

- Une continuation basée sur des tâches est toujours exécutée ; peu importe si la tâche antécédente s’est terminée avec succès, a levé une exception ou a été annulée. Une continuation basée sur des valeurs ne s’exécute pas si la tâche antécédente est levée ou annulée.

- Étant donné que les continuations basées sur les tâches s’exécutent toujours, déterminez s’il faut ajouter une continuation basée sur des tâches à la fin de votre chaîne de continuation. Cela peut aider à garantir que votre code observe toutes les exceptions.

- Le runtime lève [Concurrency :: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) lorsque vous appelez [Concurrency :: Task :: Get](reference/task-class.md#get) et que la tâche est annulée.

- Le runtime ne gère pas les exceptions pour les tâches et les agents légers.

## <a name="in-this-document"></a><a name="top"></a>Dans ce document

- [Tâches et continuations](#tasks)

- [Groupes de tâches et algorithmes parallèles](#task_groups)

- [Exceptions levées par le Runtime](#runtime)

- [Exceptions multiples](#multiple)

- [Annulation](#cancellation)

- [Tâches légères](#lwts)

- [Agents asynchrones](#agents)

## <a name="tasks-and-continuations"></a><a name="tasks"></a>Tâches et continuations

Cette section décrit comment le Runtime gère les exceptions levées par les objets [Concurrency :: Task](../../parallel/concrt/reference/task-class.md) et leurs continuations. Pour plus d’informations sur la tâche et le modèle de continuation, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Quand vous levez une exception dans le corps d’une fonction de travail que vous transmettez à un `task` objet, le runtime stocke cette exception et la marshale vers le contexte qui appelle [Concurrency :: Task :: Get](reference/task-class.md#get) ou [Concurrency :: Task :: wait](reference/task-class.md#wait). Le [parallélisme de tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md) de document décrit les continuations basées sur les tâches et les continuations basées sur les valeurs, mais pour résumer, une continuation basée sur des valeurs prend un paramètre de type `T` et une continuation basée sur des tâches prend un paramètre de type `task<T>` . Si une tâche qui lève une exception a une ou plusieurs continuations basées sur des valeurs, ces continuations ne sont pas planifiées pour s’exécuter. L'exemple suivant illustre ce comportement :

[!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]

Une continuation basée sur des tâches vous permet de gérer toute exception levée par la tâche antécédente. Une continuation basée sur des tâches est toujours exécutée ; peu importe si la tâche s’est terminée avec succès, a levé une exception ou a été annulée. Lorsqu’une tâche lève une exception, ses continuations basées sur des tâches sont planifiées pour s’exécuter. L’exemple suivant montre une tâche qui lève toujours une exception. La tâche a deux continuations ; l’une est basée sur la valeur et l’autre est basée sur les tâches. L’exception basée sur les tâches s’exécute toujours et peut donc intercepter l’exception qui est levée par la tâche antécédente. Lorsque l’exemple attend que les deux continuations se terminent, l’exception est levée à nouveau, car l’exception de tâche est toujours levée lorsque `task::get` ou `task::wait` est appelé.

[!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]

Nous vous recommandons d’utiliser des continuations basées sur des tâches pour intercepter les exceptions que vous êtes en mesure de gérer. Étant donné que les continuations basées sur les tâches s’exécutent toujours, déterminez s’il faut ajouter une continuation basée sur des tâches à la fin de votre chaîne de continuation. Cela peut aider à garantir que votre code observe toutes les exceptions. L’exemple suivant illustre une chaîne de continuation de base basée sur des valeurs. La troisième tâche de la chaîne lève, et par conséquent, toutes les continuations basées sur des valeurs qui la suivent ne sont pas exécutées. Toutefois, la continuation finale est basée sur les tâches et, par conséquent, s’exécute toujours. Cette continuation finale gère l’exception levée par la troisième tâche.

Nous vous recommandons d’intercepter les exceptions les plus spécifiques que vous pouvez. Vous pouvez omettre cette continuation basée sur les tâches finale si vous n’avez pas d’exceptions spécifiques à intercepter. Toute exception reste non gérée et peut terminer l’application.

[!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]

> [!TIP]
> Vous pouvez utiliser la méthode [Concurrency :: task_completion_event :: set_exception](../../parallel/concrt/reference/task-completion-event-class.md) pour associer une exception à un événement d’achèvement de tâche. Le [parallélisme de tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md) de document décrit la classe [Concurrency :: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) plus en détail.

[Concurrency :: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) est un type d’exception Runtime important qui est associé à `task` . Le runtime lève une exception `task_canceled` lorsque vous appelez `task::get` et que cette tâche est annulée. (À l’inverse, `task::wait` retourne [task_status :: Canceled](reference/concurrency-namespace-enums.md#task_group_status) et ne lève pas d’exception.) Vous pouvez intercepter et gérer cette exception à partir d’une continuation basée sur des tâches ou lorsque vous appelez `task::get` . Pour plus d’informations sur l’annulation de tâches, consultez [annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md).

> [!CAUTION]
> Ne levez jamais `task_canceled` à partir de votre code. Appelez [Concurrency :: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) à la place.

Le Runtime met fin à l’application si une tâche lève une exception et que cette exception n’est pas interceptée par la tâche, l’une de ses continuations ou l’application principale. Si votre application se bloque, vous pouvez configurer Visual Studio pour qu’il s’arrête lorsque des exceptions C++ sont levées. Après avoir diagnostiqué l’emplacement de l’exception non gérée, utilisez une continuation basée sur des tâches pour la gérer.

La section [exceptions levées par le runtime](#runtime) dans ce document décrit comment utiliser les exceptions Runtime plus en détail.

[[Haut](#top)]

## <a name="task-groups-and-parallel-algorithms"></a><a name="task_groups"></a>Groupes de tâches et algorithmes parallèles

Cette section décrit comment le Runtime gère les exceptions qui sont levées par les groupes de tâches. Cette section s’applique également aux algorithmes parallèles comme l' [accès concurrentiel ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for), car ces algorithmes sont générés sur des groupes de tâches.

> [!CAUTION]
> Assurez-vous que vous comprenez les effets des exceptions sur les tâches dépendantes. Pour obtenir des pratiques recommandées sur l’utilisation de la gestion des exceptions avec des tâches ou des algorithmes parallèles, consultez la section [comprendre comment l’annulation et la gestion des exceptions affectent la destruction d’objets](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) dans la rubrique meilleures pratiques de la bibliothèque de modèles parallèles.

Pour plus d’informations sur les groupes de tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Pour plus d’informations sur les algorithmes parallèles, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

Quand vous levez une exception dans le corps d’une fonction de travail que vous transmettez à un [accès concurrentiel :: task_group](reference/task-group-class.md) ou [Concurrency :: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objet, le runtime stocke cette exception et la marshale vers le contexte qui appelle [Concurrency :: task_group :: wait](reference/task-group-class.md#wait), [concurrentielle :: structured_task_group :: wait](reference/structured-task-group-class.md#wait), [Concurrency :: task_group :: run_and_wait](reference/task-group-class.md#run_and_wait)ou [Concurrency :: structured_task_group :: run_and_wait](reference/structured-task-group-class.md#run_and_wait). Le runtime arrête également toutes les tâches actives qui se trouvent dans le groupe de tâches (y compris celles des groupes de tâches enfants) et ignore toutes les tâches qui n’ont pas encore démarré.

L’exemple suivant illustre la structure de base d’une fonction de travail qui lève une exception. L’exemple utilise un `task_group` objet pour imprimer les valeurs de deux `point` objets en parallèle. La `print_point` fonction travail imprime les valeurs d’un `point` objet dans la console. La fonction de travail lève une exception si la valeur d’entrée est `NULL` . Le runtime stocke cette exception et la marshale dans le contexte qui appelle `task_group::wait` .

[!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]

Cet exemple produit la sortie suivante.

```Output
X = 15, Y = 30Caught exception: point is NULL.
```

Pour obtenir un exemple complet qui utilise la gestion des exceptions dans un groupe de tâches, consultez [Comment : utiliser la gestion des exceptions pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

[[Haut](#top)]

## <a name="exceptions-thrown-by-the-runtime"></a><a name="runtime"></a>Exceptions levées par le Runtime

Une exception peut résulter d’un appel au Runtime. La plupart des types d’exceptions, à l’exception de [Concurrency :: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) et [Concurrency :: operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md), indiquent une erreur de programmation. Ces erreurs sont généralement irrécupérables et ne doivent donc pas être interceptées ou gérées par le code de l’application. Nous vous suggérons d’intercepter ou de gérer uniquement les erreurs irrécupérables dans votre code d’application lorsque vous devez diagnostiquer des erreurs de programmation. Toutefois, la compréhension des types d’exception définis par le runtime peut vous aider à diagnostiquer les erreurs de programmation.

Le mécanisme de gestion des exceptions est le même pour les exceptions levées par le runtime comme des exceptions levées par les fonctions de travail. Par exemple, la fonction [Concurrency :: Receive](reference/concurrency-namespace-functions.md#receive) lève `operation_timed_out` une exception lorsqu’elle ne reçoit pas de message dans le laps de temps spécifié. Si `receive` lève une exception dans une fonction de travail que vous transmettez à un groupe de tâches, le runtime stocke cette exception et la marshale vers le contexte qui appelle `task_group::wait` , `structured_task_group::wait` , `task_group::run_and_wait` ou `structured_task_group::run_and_wait` .

L’exemple suivant utilise l’algorithme [Concurrency ::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) pour exécuter deux tâches en parallèle. La première tâche attend cinq secondes, puis envoie un message à une mémoire tampon de messages. La deuxième tâche utilise la `receive` fonction pour attendre trois secondes pour recevoir un message de la même mémoire tampon de message. La `receive` fonction lève une exception `operation_timed_out` si elle ne reçoit pas le message au cours de la période.

[!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]

Cet exemple produit la sortie suivante.

```Output
The operation timed out.
```

Pour éviter l’arrêt anormal de votre application, assurez-vous que votre code gère les exceptions lorsqu’il appelle le Runtime. Gérez également les exceptions lorsque vous appelez du code externe qui utilise la runtime d’accès concurrentiel, par exemple, une bibliothèque tierce.

[[Haut](#top)]

## <a name="multiple-exceptions"></a><a name="multiple"></a>Exceptions multiples

Si une tâche ou un algorithme parallèle reçoit plusieurs exceptions, le runtime marshale uniquement l’une de ces exceptions au contexte d’appel. Le runtime ne garantit pas l’exception qu’il marshale.

L’exemple suivant utilise l' `parallel_for` algorithme pour imprimer des nombres sur la console. Elle lève une exception si la valeur d’entrée est inférieure à une valeur minimale ou supérieure à une valeur maximale. Dans cet exemple, plusieurs fonctions de travail peuvent lever une exception.

[!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]

Le code suivant montre un exemple de sortie pour cet exemple.

```Output
8293104567Caught exception: -5: the value is less than the minimum.
```

[[Haut](#top)]

## <a name="cancellation"></a><a name="cancellation"></a>Ference

Toutes les exceptions ne signalent pas une erreur. Par exemple, un algorithme de recherche peut utiliser la gestion des exceptions pour arrêter sa tâche associée lorsqu’il trouve le résultat. Pour plus d’informations sur l’utilisation des mécanismes d’annulation dans votre code, consultez [annulation dans la bibliothèque de modèles parallèles](../../parallel/concrt/cancellation-in-the-ppl.md).

[[Haut](#top)]

## <a name="lightweight-tasks"></a><a name="lwts"></a>Tâches légères

Une tâche légère est une tâche que vous planifiez directement à partir d’un objet [Concurrency :: Scheduler](../../parallel/concrt/reference/scheduler-class.md) . Les tâches légères bénéficient d’une surcharge inférieure aux tâches ordinaires. Toutefois, le runtime n’intercepte pas les exceptions levées par des tâches légères. Au lieu de cela, l’exception est interceptée par le gestionnaire d’exceptions non gérées, qui, par défaut, met fin au processus. Par conséquent, utilisez un mécanisme de gestion des erreurs approprié dans votre application. Pour plus d’informations sur les tâches légères, consultez [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Haut](#top)]

## <a name="asynchronous-agents"></a><a name="agents"></a>Agents asynchrones

À l’instar des tâches légères, le runtime ne gère pas les exceptions levées par les agents asynchrones.

L’exemple suivant montre une manière de gérer des exceptions dans une classe qui dérive de [Concurrency :: agent](../../parallel/concrt/reference/agent-class.md). Cet exemple définit la `points_agent` classe. La `points_agent::run` méthode lit les `point` objets à partir de la mémoire tampon des messages et les imprime sur la console. La `run` méthode lève une exception si elle reçoit un `NULL` pointeur.

La `run` méthode entoure tout le travail dans un **`try`** - **`catch`** bloc. Le **`catch`** bloc stocke l’exception dans une mémoire tampon de message. L’application vérifie si l’agent a rencontré une erreur en lisant cette mémoire tampon après la fin de l’agent.

[!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]

Cet exemple produit la sortie suivante.

```Output
X: 10 Y: 20
X: 20 Y: 30
error occurred in agent: point must not be NULL
the status of the agent is: done
```

Étant donné que le **`try`** - **`catch`** bloc existe en dehors de la **`while`** boucle, l’agent termine le traitement lorsqu’il rencontre la première erreur. Si le **`try`** - **`catch`** bloc se trouvait à l’intérieur de la **`while`** boucle, l’agent continuerait après une erreur.

Cet exemple stocke des exceptions dans un tampon de messages afin qu’un autre composant puisse surveiller les erreurs de l’agent lors de son exécution. Cet exemple utilise un objet [Concurrency :: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) pour stocker l’erreur. Dans le cas où un agent gère plusieurs exceptions, la `single_assignment` classe stocke uniquement le premier message qui lui est passé. Pour stocker uniquement la dernière exception, utilisez la classe [Concurrency :: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) . Pour stocker toutes les exceptions, utilisez la classe [Concurrency :: unbounded_buffer](reference/unbounded-buffer-class.md) . Pour plus d’informations sur ces blocs de messages, consultez [blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md).

Pour plus d’informations sur les agents asynchrones, consultez [agents asynchrones](../../parallel/concrt/asynchronous-agents.md).

[[Haut](#top)]

## <a name="summary"></a><a name="summary"></a> Résumé

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)
