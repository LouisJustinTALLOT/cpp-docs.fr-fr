---
description: 'En savoir plus sur : annulation dans la bibliothèque de modèles parallèles'
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
ms.openlocfilehash: c15d3901df8968dd6d410e8305880585637a3fee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250671"
---
# <a name="cancellation-in-the-ppl"></a>Annulation dans la bibliothèque de modèles parallèles

Ce document explique le rôle de l'annulation dans la bibliothèque de modèles parallèles (PPL), comment annuler un travail parallèle et comment déterminer quand le travail parallèle est annulé.

> [!NOTE]
> Le runtime utilise la gestion des exceptions pour implémenter l'annulation. N'interceptez pas et ne gérez pas ces exceptions dans votre code. De plus, nous vous recommandons d'écrire du code protégé contre les exceptions dans les corps de fonction pour vos tâches. Par exemple, vous pouvez utiliser le modèle RAII ( *Resource Acquisition Is Initialization* ) pour vous assurer que les ressources sont correctement gérées lorsqu’une exception est levée dans le corps d’une tâche. Pour obtenir un exemple complet qui utilise le modèle RAII pour nettoyer une ressource dans une tâche annulable, consultez [procédure pas à pas : suppression de travail d’un thread de User-Interface](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).

## <a name="key-points"></a>Points clés

- L’annulation est coopérative et implique une coordination entre le code qui demande l’annulation et la tâche qui répond à l’annulation.

- Si possible, utilisez des jetons d'annulation pour annuler un travail. La classe [Concurrency :: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) définit un jeton d’annulation.

- Lorsque vous utilisez des jetons d’annulation, utilisez la méthode [Concurrency :: cancellation_token_source :: Cancel](reference/cancellation-token-source-class.md#cancel) pour initier l’annulation et la fonction [Concurrency :: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) pour répondre à l’annulation. Utilisez la méthode [Concurrency :: cancellation_token :: is_canceled](reference/cancellation-token-class.md#is_canceled) pour vérifier si une autre tâche a demandé l’annulation.

- L'annulation ne se produit pas immédiatement. Bien que le nouveau travail ne soit pas démarré si une tâche ou un groupe de tâches est annulé, le travail actif doit vérifier et répondre à l’annulation.

- Une continuation basée sur des valeurs hérite du jeton d'annulation de sa tâche antécédente. Une continuation basée sur des tâches n‘hérite jamais du jeton de sa tâche antécédente.

- Utilisez la méthode [Concurrency :: cancellation_token :: None](reference/cancellation-token-class.md#none) quand vous appelez un constructeur ou une fonction qui prend un `cancellation_token` objet, mais que vous ne voulez pas que l’opération soit annulable. En outre, si vous ne transmettez pas de jeton d’annulation au constructeur [Concurrency :: Task](../../parallel/concrt/reference/task-class.md) ou à la fonction [Concurrency :: create_task](reference/concurrency-namespace-functions.md#create_task) , cette tâche ne peut pas être annulée.

## <a name="in-this-document"></a><a name="top"></a> Dans ce document

- [Arborescences de travail parallèle](#trees)

- [Annulation de tâches parallèles](#tasks)

  - [Utilisation d'un jeton d'annulation pour annuler le travail parallèle](#tokens)

  - [Utilisation de la méthode cancel pour annuler un travail parallèle](#cancel)

  - [Utilisation d'exceptions pour annuler un travail parallèle](#exceptions)

- [Annulation d'algorithmes parallèles](#algorithms)

- [Quand ne pas utiliser l'annulation](#when)

## <a name="parallel-work-trees"></a><a name="trees"></a> Arborescences de travail parallèles

La bibliothèque de modèles parallèles (PPL) utilise des tâches et des groupes de tâches pour gérer les tâches et les calculs affinés. Vous pouvez imbriquer des groupes de tâches pour former des *arborescences* de travail parallèle. L’illustration suivante montre une arborescence de travail parallèle. Dans cette illustration, `tg1` et `tg2` représentent des groupes de tâches ; `t1`, `t2`, `t3`, `t4` et `t5` représentent le travail que les groupes de tâches effectuent.

![Arborescence de travail parallèle](../../parallel/concrt/media/parallelwork_trees.png "Arborescence de travail parallèle")

L’exemple suivant montre le code requis pour créer l’arborescence dans l’illustration. Dans cet exemple, `tg1` et `tg2` sont [Concurrency :: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objets ; `t1` , `t2` , `t3` , `t4` et `t5` sont des objets [Concurrency :: task_handle](../../parallel/concrt/reference/task-handle-class.md) .

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

Vous pouvez également utiliser la classe [Concurrency :: task_group](reference/task-group-class.md) pour créer une arborescence de travail similaire. La classe [Concurrency :: Task](../../parallel/concrt/reference/task-class.md) prend également en charge la notion d’arborescence de travail. Toutefois, une arborescence `task` est une arborescence des dépendances. Dans une arborescence `task`, le travail futur s'accomplit après le travail en cours. Dans une arborescence de groupes de tâches, le travail interne s'accomplit avant le travail externe. Pour plus d’informations sur les différences entre les tâches et les groupes de tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

[[Haut](#top)]

## <a name="canceling-parallel-tasks"></a><a name="tasks"></a> Annulation de tâches parallèles

Il existe plusieurs façons d'annuler un travail parallèle. Le meilleur moyen consiste à utiliser un jeton d'annulation. Les groupes de tâches prennent également en charge la méthode [Concurrency :: task_group :: Cancel](reference/task-group-class.md#cancel) et la méthode [Concurrency :: structured_task_group :: Cancel](reference/structured-task-group-class.md#cancel) . La dernière façon consiste à lever une exception dans le corps d’une fonction de travail de tâche. Quelle que soit la méthode choisie, comprenez bien que l'annulation ne se produit pas immédiatement. Bien que le nouveau travail ne soit pas démarré si une tâche ou un groupe de tâches est annulé, le travail actif doit vérifier et répondre à l’annulation.

Pour obtenir plus d’exemples d’annulation de tâches parallèles, consultez [procédure pas à pas : connexion à l’aide de tâches et de requêtes http XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [Comment : utiliser l’annulation pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)et [Comment : utiliser la gestion des exceptions pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

### <a name="using-a-cancellation-token-to-cancel-parallel-work"></a><a name="tokens"></a> Utilisation d’un jeton d’annulation pour annuler un travail parallèle

Les classes `task`, `task_group` et `structured_task_group` prennent en charge l'annulation via l'utilisation de jetons d'annulation. La bibliothèque de modèles parallèles définit les classes [Concurrency :: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) et [Concurrency :: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) à cet effet. Lorsque vous utilisez un jeton d'annulation pour annuler un travail, le runtime ne démarre pas le nouveau processus qui souscrit à ce jeton. Le travail qui est déjà actif peut utiliser la fonction membre [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) pour surveiller le jeton d’annulation et s’arrêter lorsqu’il peut.

Pour initier l’annulation, appelez la méthode [Concurrency :: cancellation_token_source :: Cancel](reference/cancellation-token-source-class.md#cancel) . Vous répondez à l'annulation des façons suivantes :

- Pour les `task` objets, utilisez la fonction [Concurrency :: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) . `cancel_current_task` annule la tâche en cours et toutes ses continuations basées sur des valeurs. (Cela n’annule pas le *jeton* d’annulation associé à la tâche ou ses continuations.)

- Pour les groupes de tâches et les algorithmes parallèles, utilisez la fonction [Concurrency :: is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) pour détecter l’annulation et retourner le plus rapidement possible à partir du corps de la tâche lorsque cette fonction est retournée **`true`** . (N’appelez pas `cancel_current_task` à partir d’un groupe de tâches.)

L'exemple suivant montre le premier modèle de base pour l'annulation de tâches. Le corps de la tâche vérifie parfois l'annulation dans une boucle.

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

La fonction `cancel_current_task` se lance ; par conséquent, il est inutile de retourner explicitement un résultat à partir de la boucle ou fonction actuelle.

> [!TIP]
> Vous pouvez également appeler la fonction [Concurrency :: interruption_point](reference/concurrency-namespace-functions.md#interruption_point) à la place de `cancel_current_task` .

Il est important d’appeler `cancel_current_task` quand vous répondez à l’annulation, car cela fait passer la tâche à l’état annulé. Si vous retournez un résultat trop tôt au lieu d'appeler `cancel_current_task`, l'opération passe à l'état terminé et toutes les continuations basées sur des valeurs sont exécutées.

> [!CAUTION]
> Ne levez jamais `task_canceled` à partir de votre code. Appelez `cancel_current_task` à la place.

Quand une tâche se termine à l’état annulé, la méthode [Concurrency :: Task :: Get](reference/task-class.md#get) lève [Concurrency :: task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (À l’inverse, [Concurrency :: Task :: wait](reference/task-class.md#wait) retourne [task_status :: Canceled](reference/concurrency-namespace-enums.md#task_group_status) et ne lève pas d’exception.) L’exemple suivant illustre ce comportement pour une continuation basée sur des tâches. Une continuation basée sur des tâches est toujours appelée, même quand la tâche antécédente est annulée.

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

Étant donné que les continuations basées sur des valeurs héritent du jeton de leur tâche antécédente, sauf si elles ont été créées avec un jeton explicite, les continuations entrent immédiatement dans l’état annulé même quand la tâche antécédente est encore en cours d’exécution. Par conséquent, toute exception levée par la tâche antécédente, après l’annulation n’est pas propagée vers les tâches de continuation. L'annulation remplace toujours l'état de la tâche antécédente. L'exemple suivant ressemble au précédent, mais il illustre le comportement d'une continuation basée sur des valeurs.

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> Si vous ne transmettez pas de jeton d’annulation au `task` constructeur ou à la fonction [Concurrency :: create_task](reference/concurrency-namespace-functions.md#create_task) , cette tâche ne peut pas être annulée. En outre, vous devez passer le même jeton d’annulation au constructeur de toutes les tâches imbriquées (autrement dit, les tâches qui sont créées dans le corps d’une autre tâche) pour annuler toutes les tâches simultanément.

Vous voulez peut-être exécuter du code arbitraire quand un jeton d'annulation est annulé. Par exemple, si votre utilisateur choisit un bouton **Annuler** sur l’interface utilisateur pour annuler l’opération, vous pouvez désactiver ce bouton jusqu’à ce que l’utilisateur démarre une autre opération. L’exemple suivant montre comment utiliser la méthode [Concurrency :: cancellation_token :: register_callback](reference/cancellation-token-class.md#register_callback) pour inscrire une fonction de rappel qui s’exécute lorsqu’un jeton d’annulation est annulé.

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

Le [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md) de document explique la différence entre les continuations basées sur les valeurs et les continuations basées sur les tâches. Si vous ne fournissez pas un objet `cancellation_token` à une tâche de continuation, la continuation hérite du jeton d’annulation de la tâche antécédente comme suit :

- Une continuation basée sur des valeurs hérite toujours du jeton d‘annulation de la tâche antécédente.

- Une continuation basée sur des tâches n'hérite jamais du jeton d'annulation de la tâche antécédente. La seule façon de rendre une continuation basée sur des tâches annulable consiste à passer explicitement un jeton d'annulation.

Ces comportements ne sont pas affectés par une tâche qui a échoué (autrement dit, une tâche qui lève une exception). Dans ce cas, une continuation basée sur des valeurs est annulée ; une continuation basée sur des tâches n’est pas annulée.

> [!CAUTION]
> Une tâche créée dans une autre tâche (en d'autres termes, une tâche imbriquée) n'hérite pas du jeton d'annulation de la tâche parente. Seule une continuation basée sur des valeurs hérite du jeton d'annulation de sa tâche antécédente.

> [!TIP]
> Utilisez la méthode [Concurrency :: cancellation_token :: None](reference/cancellation-token-class.md#none) quand vous appelez un constructeur ou une fonction qui prend un `cancellation_token` objet et que vous ne souhaitez pas que l’opération soit annulable.

Vous pouvez également fournir un jeton d'annulation au constructeur d'un objet `task_group` ou `structured_task_group`. Autre aspect important : les groupes de tâches enfants héritent de ce jeton d'annulation. Pour obtenir un exemple qui illustre ce concept à l’aide de la fonction [Concurrency :: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) à exécuter pour appeler `parallel_for` , consultez [annulation des algorithmes parallèles](#algorithms) plus loin dans ce document.

[[Haut](#top)]

#### <a name="cancellation-tokens-and-task-composition"></a>Jetons d'annulation et composition de la tâche

Les fonctions [Concurrency :: when_all](reference/concurrency-namespace-functions.md#when_all) et [Concurrency :: when_any](reference/concurrency-namespace-functions.md#when_all) peuvent vous aider à composer plusieurs tâches pour implémenter des modèles courants. Cette section décrit la manière dont ces fonctions utilisent des jetons d'annulation.

Quand vous fournissez un jeton d’annulation à `when_all` la `when_any` fonction et, cette fonction annule uniquement quand ce jeton d’annulation est annulé ou lorsque l’une des tâches participantes se termine dans un état annulé ou lève une exception.

La fonction `when_all` hérite du jeton d’annulation de chaque tâche qui compose l’opération globale quand vous ne lui fournissez pas de jeton d’annulation. La tâche retournée à partir de `when_all` est annulée quand l’un de ces jetons est annulé et qu’au moins une des tâches participantes n’a pas encore démarré ou est en cours d’exécution. Un comportement similaire se produit lorsque l’une des tâches lève une exception : la tâche retournée par `when_all` est immédiatement annulée avec cette exception.

Le runtime sélectionne le jeton d’annulation de la tâche retournée de la fonction `when_any` quand cette tâche se termine. Si aucune des tâches participantes ne se termine dans un état terminé et qu’une ou plusieurs tâches lèvent une exception, une des tâches déclenchées est choisie pour effectuer l’opération `when_any` et son jeton est choisi en tant que jeton pour la tâche finale. Si plusieurs tâches se terminent dans l’état terminé, la tâche retournée de la tâche `when_any` se termine dans un état terminé. Le runtime essaie de sélectionner une tâche terminée dont le jeton n’est pas annulé au moment de l’exécution pour que la tâche retournée de `when_any` ne soit pas immédiatement annulée même si d’autres tâches en cours d’exécution risquent de se terminer plus tard.

[[Haut](#top)]

### <a name="using-the-cancel-method-to-cancel-parallel-work"></a><a name="cancel"></a> Utilisation de la méthode Cancel pour annuler un travail parallèle

Les méthodes [Concurrency :: task_group :: Cancel](reference/task-group-class.md#cancel) et [Concurrency :: structured_task_group :: Cancel](reference/structured-task-group-class.md#cancel) définissent un groupe de tâches à l’état annulé. Après avoir appelé `cancel`, le groupe de tâches ne démarre pas les tâches futures. Les méthodes `cancel` peuvent être appelées par plusieurs tâches enfants. Une tâche annulée fait en sorte que les méthodes [Concurrency :: task_group :: wait](reference/task-group-class.md#wait) et [concurrency :: structured_task_group :: wait](reference/structured-task-group-class.md#wait) retournent l' [accès concurrentiel :: Canceled](reference/concurrency-namespace-enums.md#task_group_status).

Si un groupe de tâches est annulé, les appels de chaque tâche enfant dans le runtime peuvent déclencher un *point d’interruption*, ce qui amène le runtime à lever et intercepter un type d’exception interne pour annuler les tâches actives. Le runtime d'accès concurrentiel ne définit pas de points d'interruption spécifiques ; ils peuvent se produire dans tout appel au runtime. Le runtime doit gérer les exceptions qu'il lève pour effectuer l'annulation. Par conséquent, ne gérez pas les exceptions inconnues dans le corps d'une tâche.

Si une tâche enfant effectue une opération chronophage et n'appelle pas dans le runtime, elle doit régulièrement vérifier l'annulation et se fermer en temps voulu. L'exemple suivant montre une façon de déterminer le moment auquel le travail est annulé. La tâche `t4` annule le groupe de tâches parent quand elle rencontre une erreur. La tâche `t5` appelle de temps en temps la méthode `structured_task_group::is_canceling` pour vérifier l'annulation. Si le groupe de tâches parent est annulé, la tâche `t5` imprime un message et se ferme.

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

Cet exemple vérifie l’annulation à<sup>chaque itération 100</sup> de la boucle de tâches. La fréquence à laquelle vous vérifiez l'annulation dépend de la quantité de travail effectuée par votre tâche et de la vitesse à laquelle vous avez besoin que les tâches répondent à l'annulation.

Si vous n’avez pas accès à l’objet de groupe de tâches parent, appelez la fonction [Concurrency :: is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) pour déterminer si le groupe de tâches parent est annulé.

La méthode `cancel` affecte uniquement les tâches enfants. Par exemple, si vous annulez le groupe de tâches `tg1` dans l'illustration de l'arborescence de travail parallèle, toutes les tâches de l'arborescence (`t1`, `t2`, `t3`, `t4` et `t5`) sont affectées. Si vous annulez le groupe de tâches imbriqué, `tg2`, seules les tâches `t4` et `t5` sont affectées.

Quand vous appelez la méthode `cancel`, tous les groupes de tâches enfants sont également annulés. Toutefois, l'annulation n'affecte pas les parents du groupe de tâches dans une arborescence de travail parallèle. Les exemples suivants illustrent ce point en s'appuyant sur l'illustration de l'arborescence de travail parallèle.

Le premier de ces exemples crée une fonction de travail pour la tâche `t4`, qui est un enfant du groupe de tâches `tg2`. La fonction de travail appelle la fonction `work` dans une boucle. Si un appel à `work` échoue, la tâche annule son groupe de tâches parent. Cette annulation entraîne l'entrée du groupe de tâches `tg2` dans l'état annulé, mais elle n'annule pas le groupe de tâches `tg1`.

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

Ce deuxième exemple ressemble au premier, sauf que la tâche annule le groupe de tâches `tg1`. Cette annulation affecte toutes les tâches de l'arborescence (`t1`, `t2`, `t3`, `t4` et `t5`).

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

La classe `structured_task_group` n'est pas thread-safe. Par conséquent, une tâche enfant qui appelle une méthode de son objet `structured_task_group` parent entraîne un comportement non spécifié. Les exceptions à cette règle sont les `structured_task_group::cancel` méthodes et [Concurrency :: structured_task_group :: is_canceling](reference/structured-task-group-class.md#is_canceling) . Une tâche enfant peut appeler ces méthodes pour annuler le groupe de tâches parent et vérifier l'annulation.

> [!CAUTION]
> Bien que vous puissiez utiliser un jeton d’annulation pour annuler un travail effectué par un groupe de tâches qui s’exécute en tant qu’enfant d’un objet `task`, vous ne pouvez pas utiliser les méthodes `task_group::cancel` ou `structured_task_group::cancel` pour annuler des objets `task` qui s’exécutent dans un groupe de tâches.

[[Haut](#top)]

### <a name="using-exceptions-to-cancel-parallel-work"></a><a name="exceptions"></a> Utilisation d’exceptions pour annuler un travail parallèle

L’utilisation de jetons d’annulation et la méthode `cancel` sont plus efficaces que la gestion des exceptions pour annuler une arborescence de travail parallèle. Les jetons d’annulation et la méthode `cancel` annulent une tâche et toutes les tâches enfants de haut en bas. À l’inverse, la gestion des exceptions fonctionne de bas en haut et doit annuler chaque groupe de tâches enfant indépendamment puisque l’exception se propage vers le haut. La rubrique [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) explique comment l’Runtime d’accès concurrentiel utilise des exceptions pour communiquer des erreurs. Toutefois, toutes les exceptions n'indiquent pas une erreur. Par exemple, un algorithme de recherche peut annuler sa tâche associée quand il trouve le résultat. Toutefois, comme mentionné précédemment, la gestion des exceptions est moins efficace que l'utilisation de la méthode `cancel` pour annuler un travail parallèle.

> [!CAUTION]
> Nous vous recommandons d'utiliser des exceptions pour annuler un travail parallèle uniquement quand cela est nécessaire. Les jetons d'annulation et les méthodes `cancel` de  groupe de tâches sont plus efficaces et moins sujets à erreur.

Quand vous levez une exception dans le corps d'une fonction de travail que vous passez à un groupe de tâches, le runtime stocke cette exception et la marshale vers le contexte qui attend que le groupe de tâches se termine. Comme avec la méthode `cancel`, le runtime ignore les tâches qui n’ont pas encore démarré et qui n’acceptent pas de nouvelles tâches.

Ce troisième exemple ressemble au deuxième, sauf que la tâche `t4` lève une exception pour annuler le groupe de tâches `tg2`. Cet exemple utilise un **`try`** - **`catch`** bloc pour vérifier l’annulation lorsque le groupe de tâches `tg2` attend que ses tâches enfants se terminent. Comme le premier exemple, cela entraîne l'entrée du groupe de tâches `tg2` dans l'état annulé, mais cela n'annule pas le groupe de tâches `tg1`.

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

Ce quatrième exemple utilise la gestion des exceptions pour annuler toute l’arborescence de travail. L’exemple intercepte l’exception quand le groupe de tâches `tg1` attend que ses tâches enfants se terminent plutôt que quand le groupe de tâches `tg2` attend ses tâches enfants. Comme le deuxième exemple, cela entraîne l'entrée des deux groupes de tâches de l'arborescence, `tg1` et `tg2`, dans l'état annulé.

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

Étant donné que les méthodes `task_group::wait` et `structured_task_group::wait` se déclenchent quand une tâche enfant lève une exception, vous ne recevez pas de valeur de retour de leur part.

[[Haut](#top)]

## <a name="canceling-parallel-algorithms"></a><a name="algorithms"></a> Annulation des algorithmes parallèles

Les algorithmes parallèles de la bibliothèque de modèles parallèles (PPL), par exemple, `parallel_for`, s’appuient sur des groupes de tâches. Par conséquent, vous pouvez utiliser nombre des mêmes techniques pour annuler un algorithme parallèle.

Les exemples suivants illustrent plusieurs manières d'annuler un algorithme parallèle.

L'exemple suivant utilise la fonction `run_with_cancellation_token` pour appeler l'algorithme `parallel_for`. La fonction `run_with_cancellation_token` prend un jeton d'annulation en tant qu'argument et appelle la fonction de travail fournie de manière synchrone. Étant donné que les algorithmes parallèles s'appuient sur des tâches, ils héritent du jeton d'annulation de la tâche parent. Par conséquent, `parallel_for` peut répondre à l'annulation.

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

L’exemple suivant utilise la méthode [Concurrency :: structured_task_group :: run_and_wait](reference/structured-task-group-class.md#run_and_wait) pour appeler l' `parallel_for` algorithme. La méthode `structured_task_group::run_and_wait` attend que la tâche fournie se termine. L’objet `structured_task_group` permet à la fonction de travail d’annuler la tâche.

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

[[Haut](#top)]

## <a name="when-not-to-use-cancellation"></a><a name="when"></a> Quand ne pas utiliser l’annulation

L'utilisation de l'annulation est appropriée quand chaque membre d'un groupe de tâches connexes peut quitter le groupe en temps voulu. Toutefois, il existe certains scénarios où l'annulation peut ne pas convenir à votre application. Par exemple, étant donné que l’annulation de tâches est coopérative, l’ensemble des tâches n’est pas annulé si une tâches individuelle est bloquée. Par exemple, si une seule tâche n’a pas encore démarré, mais qu’elle débloque une autre tâche active, elle ne démarre pas si le groupe de tâches est annulé. Il existe alors un risque d'interblocage dans votre application. Deuxième exemple d’utilisation inappropriée de l’annulation : quand une tâche est annulée, alors que sa tâche enfant effectue une opération importante, comme la libération d’une ressource. Étant donné que l’ensemble des tâches est annulé quand la tâche parente est annulée, cette opération ne s’exécute pas. Pour obtenir un exemple qui illustre ce point, consultez la section [comprendre comment l’annulation et la gestion des exceptions affectent la destruction d’objets](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) dans la rubrique meilleures pratiques de la bibliothèque de modèles parallèles.

[[Haut](#top)]

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Comment : utiliser l’annulation pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Montre comment utiliser l'annulation pour implémenter un algorithme de recherche parallèle.|
|[Comment : utiliser la gestion des exceptions pour rompre une boucle parallèle](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Montre comment utiliser la classe `task_group` pour écrire un algorithme de recherche pour une arborescence de base.|
|[Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Décrit comment le runtime gère les exceptions levées par des groupes de tâches, des tâches légères et des agents asynchrones, ainsi que comment répondre aux exceptions dans vos applications.|
|[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Décrit les relations entre les tâches et les groupes de tâches, ainsi que comment vous pouvez utiliser des tâches structurées et non structurées dans vos applications.|
|[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)|Décrit les algorithmes parallèles, qui exécutent simultanément du travail sur des collections de données.|
|[Bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md)|Fournit une vue d'ensemble de la bibliothèque de modèles parallèles.|

## <a name="reference"></a>Informations de référence

[Classe de tâche (runtime d’accès concurrentiel)](../../parallel/concrt/reference/task-class.md)

[Classe cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)

[Classe cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)

[Classe task_group](reference/task-group-class.md)

[Classe structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)

[parallel_for, fonction](reference/concurrency-namespace-functions.md#parallel_for)
