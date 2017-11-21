---
title: "Gestion des exceptions dans le Runtime d’accès concurrentiel | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
caps.latest.revision: "29"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8a2820daea9508145a200fc5dfd82098ac2572b1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>Gestion des exceptions dans le runtime d’accès concurrentiel
Le Runtime d’accès concurrentiel utilise des exceptions C++ pour communiquer de nombreux types d’erreurs. Ces erreurs incluent l’utilisation non valide du runtime, les erreurs d’exécution tel que l’échec d’acquisition d’une ressource et les erreurs qui se produisent dans les fonctions de travail que vous fournissez à des tâches et des groupes de tâches. Lorsqu’une tâche ou un groupe de tâches lève une exception, le runtime conserve cette exception et la marshale au contexte qui attend que la tâche ou le groupe de tâches se termine. Pour les composants tels que les tâches légères et des agents, le runtime ne gère pas les exceptions pour vous. Dans ce cas, vous devez implémenter votre propre mécanisme de gestion des exceptions. Cette rubrique décrit comment le runtime gère les exceptions levées par des tâches, des groupes de tâches, des tâches légères et des agents asynchrones et comment répondre aux exceptions dans vos applications.  
  
## <a name="key-points"></a>Points clés  
  
-   Lorsqu’une tâche ou un groupe de tâches lève une exception, le runtime conserve cette exception et la marshale au contexte qui attend que la tâche ou le groupe de tâches se termine.  
  
-   Lorsque cela est possible, mettez chaque appel à [Concurrency::Task :: Get](reference/task-class.md#get) et [Concurrency::Task :: wait](reference/task-class.md#wait) avec un `try` / `catch` bloc pour gérer les erreurs que vous pouvez récupérer De. Le runtime met fin à l’application si une tâche lève une exception et que cette exception n’est pas interceptée par la tâche, un des ses continuations ou l’application principale.  
  
-   Toujours une continuation basée sur la tâche s’exécute ; peu importe si la tâche antécédente est terminée avec succès, a levé une exception ou a été annulée. Une continuation basée sur une valeur ne s’exécute pas si l’antécédent lève ou annule.  
  
-   Puisque les continuations basées sur les tâches s’exécutent toujours, pensez à ajouter une continuation basée sur une tâche à la fin de votre chaîne de continuation. Cela peut aider à garantir que votre code observe toutes les exceptions.  
  
-   Le runtime lève [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) lorsque vous appelez [Concurrency::Task :: Get](reference/task-class.md#get) et que cette tâche est annulée.  

  
-   Le runtime ne gère pas les exceptions pour les tâches légères et les agents.  
  
##  <a name="top"></a>Dans ce Document  
  
- [Tâches et Continuations](#tasks)  
  
- [Groupes de tâches et des algorithmes parallèles](#task_groups)  
  
- [Exceptions levées par le Runtime](#runtime)  
  
- [Plusieurs Exceptions](#multiple)  
  
- [Annulation](#cancellation)  
  
- [Tâches légères](#lwts)  
  
- [Agents asynchrones](#agents)  
  
##  <a name="tasks"></a>Tâches et Continuations  
 Cette section décrit comment le runtime gère les exceptions levées par [concurrency::task](../../parallel/concrt/reference/task-class.md) objets et leurs continuations. Pour plus d’informations sur le modèle de tâche et de continuation, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Lorsque vous levez une exception dans le corps d’une fonction de travail que vous passez à un `task` de l’objet, le runtime stocke cette exception et la marshale au contexte qui appelle [Concurrency::Task :: Get](reference/task-class.md#get) ou [concurrency :: Task::wait](reference/task-class.md#wait). Le document [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md) décrit des tâches et les continuations valeur, mais au résumé, une continuation basée sur la valeur prend un paramètre de type `T` et une continuation basée sur une tâche prend un paramètre de type `task<T>`. Si une tâche qui lève une ou plusieurs continuations basée sur une valeur, les continuations ne sont pas planifiées pour s’exécuter. L'exemple suivant illustre ce comportement :  

  
 [!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]  
  
 Une continuation basée sur des tâches vous permet de gérer toute exception qui est levée par la tâche antécédente. Toujours une continuation basée sur la tâche s’exécute ; peu importe si la tâche s’est terminée avec succès, a levé une exception ou a été annulée. Lorsqu’une tâche lève une exception, ses continuations basé sur les tâches sont planifiées pour s’exécuter. L’exemple suivant montre une tâche qui lève toujours une exception. La tâche a deux continuités ; un est basée sur la valeur et l’autre est basé sur des tâches. L’exception basée sur la tâche s’exécute toujours et par conséquent la peut intercepter l’exception qui est levée par la tâche antécédente. Lorsque l’exemple attend que les continuations terminer, l’exception est levée à nouveau, car la tâche exception est toujours levée lorsque `task::get` ou `task::wait` est appelée.  
  
 [!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]  
  
 Nous vous recommandons d’utiliser les continuations basées sur une tâche pour intercepter les exceptions que vous êtes en mesure de gérer. Puisque les continuations basées sur les tâches s’exécutent toujours, pensez à ajouter une continuation basée sur une tâche à la fin de votre chaîne de continuation. Cela peut aider à garantir que votre code observe toutes les exceptions. L’exemple suivant montre une chaîne de continuation sur la valeur de base. La troisième tâche dans la chaîne génère, et par conséquent, toutes les continuations basée sur une valeur qui la suivent ne sont pas exécutées. Toutefois, la continuation finale est basé sur des tâches et par conséquent s’exécute toujours. Cette continuation finale gère l’exception qui est levée par la tâche de tiers.  
  
 Nous vous recommandons d’intercepter les exceptions plus spécifiques que vous pouvez. Vous pouvez omettre cette continuation finale basé sur des tâches si vous n’avez pas à intercepter des exceptions spécifiques. Toute exception reste non gérée et peut mettre fin à l’application.  
  
 [!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]  
  
> [!TIP]
>  Vous pouvez utiliser la [concurrency::task_completion_event::set_exception](../../parallel/concrt/reference/task-completion-event-class.md) méthode permet d’associer une exception avec un événement d’achèvement de tâche. Le document [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md) décrit le [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) classe plus en détail.  
  

 [Concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) est un type d’exception runtime importantes relatives à `task`. Le runtime lève `task_canceled` lorsque vous appelez `task::get` et que cette tâche est annulée. (À l’inverse, `task::wait` retourne [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) et ne lève pas.) Vous pouvez intercepter et gérer cette exception à partir d’une continuation basée sur une tâche ou lorsque vous appelez `task::get`. Pour plus d’informations sur l’annulation de tâches, consultez [l’annulation dans la bibliothèque PPL](cancellation-in-the-ppl.md).  

  
> [!CAUTION]
>  Ne levez jamais `task_canceled` à partir de votre code. Appelez [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) à la place.  
  
 Le runtime met fin à l’application si une tâche lève une exception et que cette exception n’est pas interceptée par la tâche, un des ses continuations ou l’application principale. Si votre application tombe en panne, vous pouvez configurer Visual Studio de s’arrêter lorsque levées des exceptions C++. Une fois que vous diagnostiquez l’emplacement de l’exception non gérée, utilisez une continuation basée sur une tâche pour le manipuler.  
  
 La section [les Exceptions levées par le Runtime](#runtime) dans ce document décrit comment utiliser des exceptions du runtime de manière plus détaillée.  
  
 [[Haut](#top)]  
  
##  <a name="task_groups"></a>Groupes de tâches et des algorithmes parallèles  

 Cette section décrit comment le runtime gère les exceptions levées par des groupes de tâches. Cette section s’applique également aux algorithmes parallèles tels que [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), car ces algorithmes reposent sur les groupes de tâches.  
  
> [!CAUTION]
>  Assurez-vous que vous comprenez les effets des exceptions sur les tâches dépendantes. Pour obtenir des pratiques recommandées sur l’utilisation des exceptions avec les tâches ou les algorithmes parallèles, consultez la [comprendre comment l’annulation et la gestion des affectent Destruction d’objets](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) section dans les meilleures pratiques en parallèle Rubrique de bibliothèque de modèles.  
  
 Pour plus d’informations sur les groupes de tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Pour plus d’informations sur les algorithmes parallèles, consultez [des algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).  

 Lorsque vous levez une exception dans le corps d’une fonction de travail que vous passez à un [concurrency::task_group](reference/task-group-class.md) ou [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) de l’objet, le runtime stocke cette exception et la marshale dans le contexte qui appelle [Concurrency::task_group :: wait](reference/task-group-class.md#wait), [Concurrency::structured_task_group :: wait](reference/structured-task-group-class.md#wait), [Concurrency::task_group :: run_and_wait](reference/task-group-class.md#run_and_wait), ou [Concurrency::structured_task_group :: run_and_wait](reference/structured-task-group-class.md#run_and_wait). Également, le runtime arrête toutes les tâches actives qui se trouvent dans le groupe de tâches (y compris celles figurant dans les groupes de tâches enfants) et ignore les tâches qui n’ont pas encore démarré.  

  
 L’exemple suivant montre la structure de base d’une fonction de travail qui lève une exception. L’exemple utilise un `task_group` objet pour imprimer les valeurs de deux `point` objets en parallèle. Le `print_point` fonction de travail imprime les valeurs d’un `point` objet dans la console. La fonction de travail lève une exception si la valeur d’entrée est `NULL`. Le runtime stocke cette exception et la marshale au contexte qui appelle `task_group::wait`.  
  
 [!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]  
  
 Cet exemple produit la sortie suivante.  
  
```Output  
X = 15, Y = 30Caught exception: point is NULL.  
```  
  
 Pour obtenir un exemple complet qui utilise la gestion des exceptions dans un groupe de tâches, consultez [Comment : utiliser des exceptions pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).  
  
 [[Haut](#top)]  
  
##  <a name="runtime"></a>Exceptions levées par le Runtime  
 Une exception peut être dû à un appel à l’exécution. La plupart des types d’exceptions, à l’exception de [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) et [concurrency::operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md), indiquer une erreur de programmation. Ces erreurs sont généralement irrécupérables et par conséquent ne doivent pas être interceptées ou gérées par le code d’application. Nous vous conseillons uniquement interceptez ou gérez les erreurs irrécupérables dans votre code d’application lorsque vous avez besoin diagnostiquer les erreurs de programmation. Toutefois, comprendre les types d’exceptions qui sont définis par le runtime peut vous aider à diagnostiquer les erreurs de programmation.  
  
 Le mécanisme de gestion des exceptions sont identique pour les exceptions levées par le runtime en tant qu’exceptions levées par des fonctions de travail. Par exemple, le [concurrency::receive](reference/concurrency-namespace-functions.md#receive) fonction lève une exception `operation_timed_out` lorsqu’il ne reçoit pas un message dans la période spécifiée. Si `receive` lève une exception dans une fonction de travail que vous passez à un groupe de tâches, le runtime stocke cette exception et la marshale au contexte qui appelle `task_group::wait`, `structured_task_group::wait`, `task_group::run_and_wait`, ou `structured_task_group::run_and_wait`.  
  
 L’exemple suivant utilise le [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorithme pour exécuter deux tâches en parallèle. La première tâche attend cinq secondes, puis envoie un message à un tampon de messages. La deuxième tâche utilise la `receive` fonction à attendre trois secondes pour recevoir un message à partir de la même mémoire tampon de message. Le `receive` fonction lève une exception `operation_timed_out` si elle ne reçoit pas le message dans la période de temps.  
  
 [!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]  
  
 Cet exemple produit la sortie suivante.  
  
```Output  
The operation timed out.  
```  
  
 Pour empêcher tout arrêt anormal de votre application, assurez-vous que votre code gère les exceptions lorsqu’il appelle dans le runtime. Gestion des exceptions également quand vous appelez le code externe qui utilise le Runtime d’accès concurrentiel, par exemple, une bibliothèque tierce.  
  
 [[Haut](#top)]  
  
##  <a name="multiple"></a>Plusieurs Exceptions  
 Si un tâche ou un algorithme parallèle reçoit plusieurs exceptions, le runtime marshale une seule de ces exceptions au contexte d’appel. Le runtime ne garantit pas quelle exception il marshale.  
  
 L’exemple suivant utilise le `parallel_for` algorithme pour imprimer des nombres sur la console. Elle lève une exception si la valeur d’entrée est inférieure à une valeur minimale ou supérieur à une valeur maximale. Dans cet exemple, plusieurs fonctions de travail peut lever une exception.  
  
 [!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]  
  
 Le code suivant illustre un exemple de sortie pour cet exemple.  
  
```Output  
8293104567Caught exception: -5: the value is less than the minimum.  
```  
  
 [[Haut](#top)]  
  
##  <a name="cancellation"></a>Annulation  
 Pas toutes les exceptions indiquent une erreur. Par exemple, un algorithme de recherche peut utiliser la gestion des exceptions pour arrêter sa tâche associée quand il trouve le résultat. Pour plus d’informations sur l’utilisation des mécanismes d’annulation dans votre code, consultez [l’annulation dans la bibliothèque PPL](../../parallel/concrt/cancellation-in-the-ppl.md).  
  
 [[Haut](#top)]  
  
##  <a name="lwts"></a>Tâches légères  
 Une tâche légère est une tâche que vous planifiez directement à partir d’un [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) objet. Tâches légères présentent moins de traitement que les tâches ordinaires. Toutefois, le runtime n’intercepte pas les exceptions levées par des tâches légères. Au lieu de cela, l’exception est interceptée par le Gestionnaire d’exception non gérée, qui par défaut met fin au processus. Par conséquent, utilisez un mécanisme de gestion des erreurs approprié dans votre application. Pour plus d’informations sur les tâches légères, consultez [du Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 [[Haut](#top)]  
  
##  <a name="agents"></a>Agents asynchrones  
 Comme les tâches légères, le runtime ne gère pas les exceptions levées par les agents asynchrones.  
  
 L’exemple suivant montre une façon de gérer les exceptions dans une classe qui dérive de [concurrency::agent](../../parallel/concrt/reference/agent-class.md). Cet exemple définit la `points_agent` classe. Le `points_agent::run` méthode lit `point` des objets de la mémoire tampon des messages et les imprime sur la console. Le `run` méthode lève une exception si elle reçoit un `NULL` pointeur.  
  
 Le `run` méthode entoure tout le travail dans un `try` - `catch` bloc. Le `catch` bloc stocke l’exception dans un tampon de messages. L’application vérifie si l’agent a rencontré une erreur en effectuant la lecture à partir de cette mémoire tampon à l’issue de l’agent.  
  
 [!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]  
  
 Cet exemple produit la sortie suivante.  
  
```Output  
X: 10 Y: 20  
X: 20 Y: 30  
error occurred in agent: point must not be NULL  
the status of the agent is: done  
```  
  
 Étant donné que la `try` - `catch` bloc existe en dehors de la `while` boucle, l’agent met fin au traitement lorsqu’il rencontre la première erreur. Si le `try` - `catch` bloc était à l’intérieur du `while` boucle, l’agent continue après une erreur se produit.  
  
 Cet exemple stocke les exceptions dans une mémoire tampon de message afin qu’un autre composant peut contrôler l’agent pour les erreurs en cours d’exécution. Cet exemple utilise un [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) objet pour stocker l’erreur. Dans le cas où un agent gère plusieurs exceptions, la `single_assignment` classe stocke uniquement le premier message qui est passé. Pour stocker uniquement la dernière exception, utilisez la [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) classe. Pour stocker toutes les exceptions, utilisez la [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) classe. Pour plus d’informations sur ces blocs de messages, consultez [des blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md).  
  
 Pour plus d’informations sur les agents asynchrones, consultez [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md).  
  
 [[Haut](#top)]  
  
##  <a name="summary"></a> Résumé  
 [[Haut](#top)]  
  
## <a name="see-also"></a>Voir aussi  
 [Runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)   
 [Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)   
 [Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)   
 [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)

