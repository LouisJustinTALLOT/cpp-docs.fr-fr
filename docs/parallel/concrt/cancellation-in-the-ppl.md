---
title: Annulation dans la bibliothèque de modèles parallèles
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms, canceling [Concurrency Runtime]
- canceling parallel algorithms [Concurrency Runtime]
- parallel tasks, canceling [Concurrency Runtime]
- cancellation in the PPL
- parallel work trees [Concurrency Runtime]
- canceling parallel tasks [Concurrency Runtime]
ms.assetid: baaef417-b2f9-470e-b8bd-9ed890725b35
ms.openlocfilehash: 27c0ea3cfcf62060800c1c0b034dde7de6357250
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368490"
---
# <a name="cancellation-in-the-ppl"></a>Annulation dans la bibliothèque de modèles parallèles

Ce document explique le rôle de l'annulation dans la bibliothèque de modèles parallèles (PPL), comment annuler un travail parallèle et comment déterminer quand le travail parallèle est annulé.

> [!NOTE]
> Le runtime utilise la gestion des exceptions pour implémenter l'annulation. N'interceptez pas et ne gérez pas ces exceptions dans votre code. De plus, nous vous recommandons d'écrire du code protégé contre les exceptions dans les corps de fonction pour vos tâches. Par exemple, vous pouvez utiliser le modèle *d’acquisition de ressources est initialisation* (RAII) pour vous assurer que les ressources sont correctement gérées lorsqu’une exception est projetée dans le corps d’une tâche. Pour un exemple complet qui utilise le modèle RAII pour nettoyer une ressource dans une tâche annulable, voir [Procédure pas à pas: Supprimer le travail à partir d’un thread utilisateur-interface](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).

## <a name="key-points"></a>Points clés

- L’annulation est coopérative et implique une coordination entre le code qui demande l’annulation et la tâche qui répond à l’annulation.

- Si possible, utilisez des jetons d'annulation pour annuler un travail. La [concordance: :cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) classe définit un jeton d’annulation.

- Lorsque vous utilisez des jetons d’annulation, utilisez la [concordance::cancellation_token_source::annuler](reference/cancellation-token-source-class.md#cancel) la méthode pour initier l’annulation et la [concordance::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) fonction pour répondre à l’annulation. Utilisez la [concordance::cancellation_token::is_canceled](reference/cancellation-token-class.md#is_canceled) méthode pour vérifier si une autre tâche a demandé l’annulation.

- L'annulation ne se produit pas immédiatement. Bien que de nouveaux travaux ne soient pas entrepris si une tâche ou un groupe de travail est annulé, le travail actif doit vérifier et répondre à l’annulation.

- Une continuation basée sur des valeurs hérite du jeton d'annulation de sa tâche antécédente. Une continuation basée sur des tâches n‘hérite jamais du jeton de sa tâche antécédente.

- Utilisez la [concordance::cancellation_token::aucune](reference/cancellation-token-class.md#none) méthode lorsque vous appelez un constructeur ou `cancellation_token` une fonction qui prend un objet, mais vous ne voulez pas que l’opération soit cancellable. Aussi, si vous ne passez pas un jeton d’annulation à la [concordance::constructeur de tâches](../../parallel/concrt/reference/task-class.md) ou la [concordance::create_task](reference/concurrency-namespace-functions.md#create_task) fonction, cette tâche n’est pas cancellable.

## <a name="in-this-document"></a><a name="top"></a>Dans ce document

- [Arborescences de travail parallèle](#trees)

- [Annulation de tâches parallèles](#tasks)

  - [Utilisation d'un jeton d'annulation pour annuler le travail parallèle](#tokens)

  - [Utilisation de la méthode cancel pour annuler un travail parallèle](#cancel)

  - [Utilisation d'exceptions pour annuler un travail parallèle](#exceptions)

- [Annulation d'algorithmes parallèles](#algorithms)

- [Quand ne pas utiliser l'annulation](#when)

## <a name="parallel-work-trees"></a><a name="trees"></a>Arbres de travail parallèles

La bibliothèque de modèles parallèles (PPL) utilise des tâches et des groupes de tâches pour gérer les tâches et les calculs affinés. Vous pouvez nicher des groupes de travail pour former des *arbres* de travail parallèle. L’illustration suivante montre une arborescence de travail parallèle. Dans cette illustration, `tg1` et `tg2` représentent des groupes de tâches ; `t1`, `t2`, `t3`, `t4` et `t5` représentent le travail que les groupes de tâches effectuent.

![Arborescence de travail parallèle](../../parallel/concrt/media/parallelwork_trees.png "Arborescence de travail parallèle")

L’exemple suivant montre le code requis pour créer l’arborescence dans l’illustration. Dans cet `tg1` exemple, et `tg2` sont [d’accord::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objets; `t1`, `t2` `t3`, `t4`, `t5` et sont [d’accord::task_handle](../../parallel/concrt/reference/task-handle-class.md) objets.

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

Vous pouvez également utiliser la [concordance::task_group](reference/task-group-class.md) classe pour créer un arbre de travail similaire. La [concordance: :la](../../parallel/concrt/reference/task-class.md) classe de travail soutient également la notion d’arbre de travail. Toutefois, une arborescence `task` est une arborescence des dépendances. Dans une arborescence `task`, le travail futur s'accomplit après le travail en cours. Dans une arborescence de groupes de tâches, le travail interne s'accomplit avant le travail externe. Pour plus d’informations sur les différences entre les tâches et les groupes de tâches, voir [Le parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

[[Top](#top)]

## <a name="canceling-parallel-tasks"></a><a name="tasks"></a>Annulation des tâches parallèles

Il existe plusieurs façons d'annuler un travail parallèle. Le meilleur moyen consiste à utiliser un jeton d'annulation. Les groupes de travail soutiennent également la [concurrence : task_group : : annuler](reference/task-group-class.md#cancel) la méthode et la [concordance : : structured_task_group : : annuler](reference/structured-task-group-class.md#cancel) la méthode. La dernière façon consiste à lever une exception dans le corps d’une fonction de travail de tâche. Quelle que soit la méthode choisie, comprenez bien que l'annulation ne se produit pas immédiatement. Bien que de nouveaux travaux ne soient pas entrepris si une tâche ou un groupe de travail est annulé, le travail actif doit vérifier et répondre à l’annulation.

Pour plus d’exemples qui annulent les tâches parallèles, voir Procédure pas à [pas: Connecting Using Tasks et XML HTTP Demandes](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [Comment: Utilisez l’annulation de break à partir d’une boucle parallèle](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md), et [comment: Utilisez la manipulation d’exception pour rompre à partir d’une boucle parallèle](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

### <a name="using-a-cancellation-token-to-cancel-parallel-work"></a><a name="tokens"></a>Utilisation d’un jeton d’annulation pour annuler les travaux parallèles

Les classes `task`, `task_group` et `structured_task_group` prennent en charge l'annulation via l'utilisation de jetons d'annulation. La PPL définit la [concordance : cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) et [la concordance : : cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) cours à cet effet. Lorsque vous utilisez un jeton d'annulation pour annuler un travail, le runtime ne démarre pas le nouveau processus qui souscrit à ce jeton. Les travaux déjà actifs peuvent utiliser la fonction [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) membre pour surveiller le jeton d’annulation et s’arrêter quand il le peut.

Pour initier l’annulation, appelez la [concordance::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) méthode. Vous répondez à l'annulation des façons suivantes :

- Pour `task` les objets, utilisez la [concordance : : cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) fonction. `cancel_current_task` annule la tâche en cours et toutes ses continuations basées sur des valeurs. (Il n’annule pas le *jeton d’annulation* qui est associé à la tâche ou à ses continuations.)

- Pour les groupes de tâches et les algorithmes parallèles, utilisez la [concordance: ::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) fonction pour détecter l’annulation et le retour dès que possible de l’organisme de tâche lorsque cette fonction revient **vrai**. (N’appelez pas `cancel_current_task` à partir d’un groupe de tâches.)

L'exemple suivant montre le premier modèle de base pour l'annulation de tâches. Le corps de la tâche vérifie parfois l'annulation dans une boucle.

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

La fonction `cancel_current_task` se lance ; par conséquent, il est inutile de retourner explicitement un résultat à partir de la boucle ou fonction actuelle.

> [!TIP]
> Alternativement, vous pouvez appeler la [concurrence::interruption_point](reference/concurrency-namespace-functions.md#interruption_point) fonction au `cancel_current_task`lieu de .

Il est important d’appeler `cancel_current_task` quand vous répondez à l’annulation, car cela fait passer la tâche à l’état annulé. Si vous retournez un résultat trop tôt au lieu d'appeler `cancel_current_task`, l'opération passe à l'état terminé et toutes les continuations basées sur des valeurs sont exécutées.

> [!CAUTION]
> Ne levez jamais `task_canceled` à partir de votre code. Appelez `cancel_current_task` à la place.

Quand une tâche se termine dans l’état annulé, la [concordance::task::get](reference/task-class.md#get) method jette [la concordance::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (Inversement, [la concurrence::tâche::wait](reference/task-class.md#wait) returns [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) and does not throw.) L’exemple suivant illustre ce comportement pour une suite basée sur les tâches. Une continuation basée sur des tâches est toujours appelée, même quand la tâche antécédente est annulée.

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

Étant donné que les continuations basées sur des valeurs héritent du jeton de leur tâche antécédente, sauf si elles ont été créées avec un jeton explicite, les continuations entrent immédiatement dans l’état annulé même quand la tâche antécédente est encore en cours d’exécution. Par conséquent, toute exception levée par la tâche antécédente, après l’annulation n’est pas propagée vers les tâches de continuation. L'annulation remplace toujours l'état de la tâche antécédente. L'exemple suivant ressemble au précédent, mais il illustre le comportement d'une continuation basée sur des valeurs.

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> Si vous ne passez pas un `task` jeton d’annulation au constructeur ou à la [concordance ::create_task](reference/concurrency-namespace-functions.md#create_task) fonction, cette tâche n’est pas cancellable. En outre, vous devez passer le même jeton d’annulation au constructeur de toutes les tâches imbriquées (autrement dit, les tâches qui sont créées dans le corps d’une autre tâche) pour annuler toutes les tâches simultanément.

Vous voulez peut-être exécuter du code arbitraire quand un jeton d'annulation est annulé. Par exemple, si votre utilisateur choisit un bouton **Annuler** sur l’interface utilisateur pour annuler l’opération, vous pouvez désactiver ce bouton jusqu’à ce que l’utilisateur démarre une autre opération. L’exemple suivant montre comment utiliser la [concordance: :cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) méthode pour enregistrer une fonction de rappel qui s’exécute quand un jeton d’annulation est annulé.

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

Le document [Task Parallelism](../../parallel/concrt/task-parallelism-concurrency-runtime.md) explique la différence entre les continuations basées sur la valeur et les poursuites fondées sur les tâches. Si vous ne fournissez pas un objet `cancellation_token` à une tâche de continuation, la continuation hérite du jeton d’annulation de la tâche antécédente comme suit :

- Une continuation basée sur des valeurs hérite toujours du jeton d‘annulation de la tâche antécédente.

- Une continuation basée sur des tâches n'hérite jamais du jeton d'annulation de la tâche antécédente. La seule façon de rendre une continuation basée sur des tâches annulable consiste à passer explicitement un jeton d'annulation.

Ces comportements ne sont pas affectés par une tâche qui a échoué (autrement dit, une tâche qui lève une exception). Dans ce cas, une continuation fondée sur la valeur est annulée; une continuation basée sur les tâches n’est pas annulée.

> [!CAUTION]
> Une tâche créée dans une autre tâche (en d'autres termes, une tâche imbriquée) n'hérite pas du jeton d'annulation de la tâche parente. Seule une continuation basée sur des valeurs hérite du jeton d'annulation de sa tâche antécédente.

> [!TIP]
> Utilisez la [concordance::cancellation_token::aucune](reference/cancellation-token-class.md#none) méthode lorsque vous appelez un constructeur ou `cancellation_token` une fonction qui prend un objet et vous ne voulez pas que l’opération soit cancellable.

Vous pouvez également fournir un jeton d'annulation au constructeur d'un objet `task_group` ou `structured_task_group`. Autre aspect important : les groupes de tâches enfants héritent de ce jeton d'annulation. Par exemple qui démontre ce concept en utilisant la [concordance::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) fonction `parallel_for`pour exécuter pour appeler , voir [Annuler les algorithmes parallèles](#algorithms) plus tard dans ce document.

[[Top](#top)]

#### <a name="cancellation-tokens-and-task-composition"></a>Jetons d'annulation et composition de la tâche

La [concordance: :when_all](reference/concurrency-namespace-functions.md#when_all) et [la concurrence::when_any](reference/concurrency-namespace-functions.md#when_all) fonctions peuvent vous aider à composer plusieurs tâches pour implémenter des modèles communs. Cette section décrit la manière dont ces fonctions utilisent des jetons d'annulation.

Lorsque vous fournissez un jeton `when_any` d’annulation à l’un ou l’autre et la `when_all` fonction, cette fonction n’annule que lorsque ce jeton d’annulation est annulé ou lorsque l’une des tâches participantes se termine dans un état annulé ou jette une exception.

La fonction `when_all` hérite du jeton d’annulation de chaque tâche qui compose l’opération globale quand vous ne lui fournissez pas de jeton d’annulation. La tâche qui `when_all` est retournée est annulée lorsque l’un de ces jetons est annulé et au moins une des tâches participantes n’a pas encore commencé ou est en cours d’exécution. Un comportement similaire se produit lorsque l’une des tâches `when_all` jette une exception - la tâche qui est retournée est immédiatement annulée à cette exception.

Le runtime sélectionne le jeton d’annulation de la tâche retournée de la fonction `when_any` quand cette tâche se termine. Si aucune des tâches participantes ne se termine dans un état terminé et qu’une ou plusieurs tâches lèvent une exception, une des tâches déclenchées est choisie pour effectuer l’opération `when_any` et son jeton est choisi en tant que jeton pour la tâche finale. Si plusieurs tâches se terminent dans l’état terminé, la tâche retournée de la tâche `when_any` se termine dans un état terminé. Le runtime essaie de sélectionner une tâche terminée dont le jeton n’est pas annulé au moment de l’exécution pour que la tâche retournée de `when_any` ne soit pas immédiatement annulée même si d’autres tâches en cours d’exécution risquent de se terminer plus tard.

[[Top](#top)]

### <a name="using-the-cancel-method-to-cancel-parallel-work"></a><a name="cancel"></a>Utilisation de la méthode d’annulation pour annuler les travaux parallèles

La [concordance::task_group::cancel](reference/task-group-class.md#cancel) and [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) methods set a task group to the canceled state. Après avoir appelé `cancel`, le groupe de tâches ne démarre pas les tâches futures. Les méthodes `cancel` peuvent être appelées par plusieurs tâches enfants. Une tâche annulée provoque la [concordance::task_group::wait](reference/task-group-class.md#wait) and [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait) methods to return [concurrency::canceled](reference/concurrency-namespace-enums.md#task_group_status).

Si un groupe de travail est annulé, les appels de chaque tâche d’enfant dans le temps d’exécution peuvent déclencher un *point d’interruption,* ce qui provoque le temps d’exécution de lancer et d’attraper un type d’exception interne pour annuler les tâches actives. Le runtime d'accès concurrentiel ne définit pas de points d'interruption spécifiques ; ils peuvent se produire dans tout appel au runtime. Le runtime doit gérer les exceptions qu'il lève pour effectuer l'annulation. Par conséquent, ne gérez pas les exceptions inconnues dans le corps d'une tâche.

Si une tâche enfant effectue une opération chronophage et n'appelle pas dans le runtime, elle doit régulièrement vérifier l'annulation et se fermer en temps voulu. L'exemple suivant montre une façon de déterminer le moment auquel le travail est annulé. La tâche `t4` annule le groupe de tâches parent quand elle rencontre une erreur. La tâche `t5` appelle de temps en temps la méthode `structured_task_group::is_canceling` pour vérifier l'annulation. Si le groupe de tâches parent est annulé, la tâche `t5` imprime un message et se ferme.

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

Cet exemple vérifie l’annulation sur chaque itération de 100<sup>e</sup> de la boucle de tâche. La fréquence à laquelle vous vérifiez l'annulation dépend de la quantité de travail effectuée par votre tâche et de la vitesse à laquelle vous avez besoin que les tâches répondent à l'annulation.

Si vous n’avez pas accès à l’objet du groupe de travail parent, appelez la [concurrence : : is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) fonction pour déterminer si le groupe de travail parent est annulé.

La méthode `cancel` affecte uniquement les tâches enfants. Par exemple, si vous annulez le groupe de tâches `tg1` dans l'illustration de l'arborescence de travail parallèle, toutes les tâches de l'arborescence (`t1`, `t2`, `t3`, `t4` et `t5`) sont affectées. Si vous annulez le groupe de tâches imbriqué, `tg2`, seules les tâches `t4` et `t5` sont affectées.

Quand vous appelez la méthode `cancel`, tous les groupes de tâches enfants sont également annulés. Toutefois, l'annulation n'affecte pas les parents du groupe de tâches dans une arborescence de travail parallèle. Les exemples suivants illustrent ce point en s'appuyant sur l'illustration de l'arborescence de travail parallèle.

Le premier de ces exemples crée une fonction de travail pour la tâche `t4`, qui est un enfant du groupe de tâches `tg2`. La fonction de travail appelle la fonction `work` dans une boucle. Si un appel à `work` échoue, la tâche annule son groupe de tâches parent. Cette annulation entraîne l'entrée du groupe de tâches `tg2` dans l'état annulé, mais elle n'annule pas le groupe de tâches `tg1`.

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

Ce deuxième exemple ressemble au premier, sauf que la tâche annule le groupe de tâches `tg1`. Cette annulation affecte toutes les tâches de l'arborescence (`t1`, `t2`, `t3`, `t4` et `t5`).

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

La classe `structured_task_group` n'est pas thread-safe. Par conséquent, une tâche enfant qui appelle une méthode de son objet `structured_task_group` parent entraîne un comportement non spécifié. Les exceptions à cette `structured_task_group::cancel` règle sont la concordance et [la concordance::structured_task_group::is_canceling](reference/structured-task-group-class.md#is_canceling) méthodes. Une tâche enfant peut appeler ces méthodes pour annuler le groupe de tâches parent et vérifier l'annulation.

> [!CAUTION]
> Bien que vous puissiez utiliser un jeton d’annulation pour annuler un travail effectué par un groupe de tâches qui s’exécute en tant qu’enfant d’un objet `task`, vous ne pouvez pas utiliser les méthodes `task_group::cancel` ou `structured_task_group::cancel` pour annuler des objets `task` qui s’exécutent dans un groupe de tâches.

[[Top](#top)]

### <a name="using-exceptions-to-cancel-parallel-work"></a><a name="exceptions"></a>Utilisation d’exceptions pour annuler les travaux parallèles

L’utilisation de jetons d’annulation et la méthode `cancel` sont plus efficaces que la gestion des exceptions pour annuler une arborescence de travail parallèle. Les jetons d’annulation et la méthode `cancel` annulent une tâche et toutes les tâches enfants de haut en bas. À l’inverse, la gestion des exceptions fonctionne de bas en haut et doit annuler chaque groupe de tâches enfant indépendamment puisque l’exception se propage vers le haut. Le sujet [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) explique comment le Concurrency Runtime utilise des exceptions pour communiquer des erreurs. Toutefois, toutes les exceptions n'indiquent pas une erreur. Par exemple, un algorithme de recherche peut annuler sa tâche associée quand il trouve le résultat. Toutefois, comme mentionné précédemment, la gestion des exceptions est moins efficace que l'utilisation de la méthode `cancel` pour annuler un travail parallèle.

> [!CAUTION]
> Nous vous recommandons d'utiliser des exceptions pour annuler un travail parallèle uniquement quand cela est nécessaire. Les jetons d'annulation et les méthodes `cancel` de  groupe de tâches sont plus efficaces et moins sujets à erreur.

Quand vous levez une exception dans le corps d'une fonction de travail que vous passez à un groupe de tâches, le runtime stocke cette exception et la marshale vers le contexte qui attend que le groupe de tâches se termine. Comme avec la méthode `cancel`, le runtime ignore les tâches qui n’ont pas encore démarré et qui n’acceptent pas de nouvelles tâches.

Ce troisième exemple ressemble au deuxième, sauf que la tâche `t4` lève une exception pour annuler le groupe de tâches `tg2`. Cet exemple `try` - `catch` utilise un bloc pour vérifier `tg2` l’annulation lorsque le groupe de travail attend que ses tâches pour enfants se terminent. Comme le premier exemple, cela entraîne l'entrée du groupe de tâches `tg2` dans l'état annulé, mais cela n'annule pas le groupe de tâches `tg1`.

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

Ce quatrième exemple utilise la gestion des exceptions pour annuler toute l’arborescence de travail. L’exemple intercepte l’exception quand le groupe de tâches `tg1` attend que ses tâches enfants se terminent plutôt que quand le groupe de tâches `tg2` attend ses tâches enfants. Comme le deuxième exemple, cela entraîne l'entrée des deux groupes de tâches de l'arborescence, `tg1` et `tg2`, dans l'état annulé.

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

Étant donné que les méthodes `task_group::wait` et `structured_task_group::wait` se déclenchent quand une tâche enfant lève une exception, vous ne recevez pas de valeur de retour de leur part.

[[Top](#top)]

## <a name="canceling-parallel-algorithms"></a><a name="algorithms"></a>Annulation d’algorithmes parallèles

Les algorithmes parallèles de la bibliothèque de modèles parallèles (PPL), par exemple, `parallel_for`, s’appuient sur des groupes de tâches. Par conséquent, vous pouvez utiliser nombre des mêmes techniques pour annuler un algorithme parallèle.

Les exemples suivants illustrent plusieurs manières d'annuler un algorithme parallèle.

L'exemple suivant utilise la fonction `run_with_cancellation_token` pour appeler l'algorithme `parallel_for`. La fonction `run_with_cancellation_token` prend un jeton d'annulation en tant qu'argument et appelle la fonction de travail fournie de manière synchrone. Étant donné que les algorithmes parallèles s'appuient sur des tâches, ils héritent du jeton d'annulation de la tâche parent. Par conséquent, `parallel_for` peut répondre à l'annulation.

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

L’exemple suivant utilise la [concordance::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) méthode pour appeler `parallel_for` l’algorithme. La méthode `structured_task_group::run_and_wait` attend que la tâche fournie se termine. L’objet `structured_task_group` permet à la fonction de travail d’annuler la tâche.

[!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]

Cet exemple produit la sortie suivante.

```Output
The task group status is: canceled.
```

L'exemple suivant utilise la gestion des exceptions pour annuler une boucle `parallel_for`. Le runtime marshale l’exception vers le contexte d’appel.

[!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]

Cet exemple produit la sortie suivante.

```Output
Caught 50
```

L'exemple suivant utilise un indicateur booléen pour coordonner l'annulation dans une boucle `parallel_for`. Chaque tâche s'exécute car cet exemple n'utilise pas la méthode `cancel` ou la gestion des exceptions pour annuler l'ensemble des tâches. Par conséquent, cette technique peut imposer une charge de calcul plus importante qu'un mécanisme d'annulation.

[!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]

Chaque méthode d'annulation présente des avantages par rapport aux autres. Choisissez la méthode qui répond à vos besoins spécifiques.

[[Top](#top)]

## <a name="when-not-to-use-cancellation"></a><a name="when"></a>Lorsque vous n’utilisez pas l’annulation

L'utilisation de l'annulation est appropriée quand chaque membre d'un groupe de tâches connexes peut quitter le groupe en temps voulu. Toutefois, il existe certains scénarios où l'annulation peut ne pas convenir à votre application. Par exemple, étant donné que l’annulation de tâches est coopérative, l’ensemble des tâches n’est pas annulé si une tâches individuelle est bloquée. Par exemple, si une seule tâche n’a pas encore démarré, mais qu’elle débloque une autre tâche active, elle ne démarre pas si le groupe de tâches est annulé. Il existe alors un risque d'interblocage dans votre application. Deuxième exemple d’utilisation inappropriée de l’annulation : quand une tâche est annulée, alors que sa tâche enfant effectue une opération importante, comme la libération d’une ressource. Étant donné que l’ensemble des tâches est annulé quand la tâche parente est annulée, cette opération ne s’exécute pas. Par exemple, voir la section [Comprendre comment l’annulation et](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) la manipulation des exceptions affectent la destruction des objets dans le sujet des pratiques exemplaires dans le thème de la Bibliothèque des modèles parallèles.

[[Top](#top)]

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Comment : utiliser l'annulation pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Montre comment utiliser l'annulation pour implémenter un algorithme de recherche parallèle.|
|[Comment : utiliser la gestion des exceptions pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Montre comment utiliser la classe `task_group` pour écrire un algorithme de recherche pour une arborescence de base.|
|[Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Décrit comment le runtime gère les exceptions levées par des groupes de tâches, des tâches légères et des agents asynchrones, ainsi que comment répondre aux exceptions dans vos applications.|
|[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Décrit les relations entre les tâches et les groupes de tâches, ainsi que comment vous pouvez utiliser des tâches structurées et non structurées dans vos applications.|
|[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)|Décrit les algorithmes parallèles, qui exécutent simultanément du travail sur des collections de données.|
|[Bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md)|Fournit une vue d'ensemble de la bibliothèque de modèles parallèles.|

## <a name="reference"></a>Informations de référence

[task (Concurrency Runtime), classe](../../parallel/concrt/reference/task-class.md)

[Classe cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)

[Classe cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)

[Classe task_group](reference/task-group-class.md)

[structured_task_group, classe](../../parallel/concrt/reference/structured-task-group-class.md)

[parallel_for, fonction](reference/concurrency-namespace-functions.md#parallel_for)
