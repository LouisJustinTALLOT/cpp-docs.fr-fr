---
title: 'Procédure : Créer une tâche qui se termine après un certain délai'
description: Créer une tâche qui se termine après un certain délai à l’aide de la bibliothèque PPL ConcRT.
ms.date: 10/19/2020
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 694b6190a7ec60043a5674e920dc54e6e7bf0eb6
ms.sourcegitcommit: 19016630f9d35f365e9ba249e0f3617515d7ca33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92274559"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Procédure : Créer une tâche qui se termine après un certain délai

Cet exemple montre comment utiliser les [`concurrency::task`](../../parallel/concrt/reference/task-class.md) classes, [`concurrency::cancellation_token_source`](../../parallel/concrt/reference/cancellation-token-source-class.md) , [`concurrency::cancellation_token`](../../parallel/concrt/reference/cancellation-token-class.md) , [`concurrency::task_completion_event`](../../parallel/concrt/reference/task-completion-event-class.md) , [`concurrency::timer`](../../parallel/concrt/reference/timer-class.md) et [`concurrency::call`](../../parallel/concrt/reference/call-class.md) pour créer une tâche qui se termine après un certain délai. Vous pouvez utiliser cette méthode pour générer des boucles qui interrogent occasionnellement les données. Vous pouvez également introduire des délais d’attente, gérer les retards de l’entrée d’utilisateur pendant une durée prédéterminée, et ainsi de suite.

## <a name="example-complete_after-and-cancel_after_timeout-functions"></a>Exemple : fonctions complete_after et cancel_after_timeout

L'exemple suivant illustre les fonctions `complete_after` et `cancel_after_timeout`. La fonction `complete_after` crée un objet `task` qui se termine après le délai spécifié. Elle utilise un objet `timer` et un objet `call` pour définir un objet `task_completion_event` après le délai spécifié. À l'aide de la classe `task_completion_event`, vous pouvez définir une tâche qui se termine lorsqu'un thread ou une autre tâche indique qu'une valeur est disponible. Lorsque l'événement est défini, les tâches de l'écouteur s'achèvent et leurs continuations sont planifiées pour s'exécuter.

> [!TIP]
> Pour plus d’informations sur `timer` les `call` classes et, qui font partie de la bibliothèque des agents asynchrones, consultez [blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md).

La `cancel_after_timeout` fonction s’appuie sur la `complete_after` fonction pour annuler une tâche si cette tâche ne se termine pas avant un délai d’attente donné. La fonction `cancel_after_timeout` crée deux tâches. La première tâche indique la réussite et se termine une fois la tâche fournie terminée. La deuxième tâche indique un échec et se termine après le délai d’expiration spécifié. La fonction `cancel_after_timeout` crée une tâche de continuation qui s’exécute lorsque la tâche de réussite ou d’échec s’achève. Si la tâche d’échec est terminée en premier, la continuation annule la source des jetons pour annuler la tâche globale.

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example-compute-count-of-prime-numbers"></a>Exemple : nombre de calculs de nombres premiers

L'exemple suivant calcule à plusieurs reprises la quantité de nombres premiers dans la plage [0, 100000]. L’opération échoue si elle ne se termine pas dans un délai donné. La fonction `count_primes` indique comment utiliser la fonction `cancel_after_timeout`. Elle compte le nombre de premiers dans la plage donnée et échoue si la tâche ne se termine pas dans l’heure fournie. La fonction `wmain` appelle la fonction `count_primes` à plusieurs reprises. Chaque fois, cela divise par deux le délai. Le programme se termine une fois que l’opération ne s’est pas terminée dans le délai imparti.

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

Lorsque vous utilisez cette technique pour annuler des tâches après un certain délai, les tâches non démarrées ne démarrent pas après l’annulation de la tâche globale. Toutefois, il est important que les tâches de longue durée répondent rapidement à l’annulation. Pour plus d’informations sur l’annulation de tâches, consultez [annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md).

## <a name="complete-code-example"></a>Exemple de code complet

Voici le code complet pour cet exemple :

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le, puis collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `task-delay.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**cl.exe/EHsc Task-Delay. cpp**

## <a name="see-also"></a>Voir aussi

[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Classe de tâche (runtime d’accès concurrentiel)](../../parallel/concrt/reference/task-class.md)<br/>
[Classe cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[Classe cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[Classe task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[Timer (classe)](../../parallel/concrt/reference/timer-class.md)<br/>
[Call (classe)](../../parallel/concrt/reference/call-class.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)
