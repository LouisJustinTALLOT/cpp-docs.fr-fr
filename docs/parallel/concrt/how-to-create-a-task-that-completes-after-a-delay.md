---
title: 'Procédure : Créer une tâche qui se termine après un certain délai'
ms.date: 11/04/2016
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 3292043d7900d5dc2bfba0afa5fdc237853a5be0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272256"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Procédure : Créer une tâche qui se termine après un certain délai

Cet exemple montre comment utiliser le [concurrency::task](../../parallel/concrt/reference/task-class.md), [concurrency::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [ Concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [concurrency::timer](../../parallel/concrt/reference/timer-class.md), et [concurrency::call](../../parallel/concrt/reference/call-class.md) classes pour créer une tâche qui se termine après un certain délai. Vous pouvez utiliser cette méthode pour générer des boucles qui, occasionnellement, sondent les données, introduisent des délais, diffèrent la gestion des entrées d'utilisateur pendant une durée prédéterminée, et ainsi de suite.

## <a name="example"></a>Exemple

L'exemple suivant illustre les fonctions `complete_after` et `cancel_after_timeout`. La fonction `complete_after` crée un objet `task` qui se termine après le délai spécifié. Elle utilise un objet `timer` et un objet `call` pour définir un objet `task_completion_event` après le délai spécifié. À l'aide de la classe `task_completion_event`, vous pouvez définir une tâche qui se termine lorsqu'un thread ou une autre tâche indique qu'une valeur est disponible. Lorsque l'événement est défini, les tâches de l'écouteur s'achèvent et leurs continuations sont planifiées pour s'exécuter.

> [!TIP]
>  Pour plus d’informations sur la `timer` et `call` des classes qui font partie de la bibliothèque d’Agents asynchrones, consultez [des blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md).

La fonction `cancel_after_timeout` repose sur la fonction `complete_after` pour annuler une tâche si cette tâche ne se termine pas avant le délai spécifié. La fonction `cancel_after_timeout` crée deux tâches. La première tâche indique que l’opération a réussi et se termine une fois que la tâche fournie s’achève ; la deuxième tâche indique que l’opération a échoué et se termine après le délai d’attente spécifié. La fonction `cancel_after_timeout` crée une tâche de continuation qui s’exécute lorsque la tâche de réussite ou d’échec s’achève. Si la tâche d’échec est terminée en premier, la continuation annule la source des jetons pour annuler la tâche globale.

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example"></a>Exemple

L'exemple suivant calcule à plusieurs reprises la quantité de nombres premiers dans la plage [0, 100000]. L'opération échoue si elle ne se termine pas dans un intervalle de temps donné. La fonction `count_primes` indique comment utiliser la fonction `cancel_after_timeout`. Elle compte les nombres premiers dans la plage donnée et échoue si la tâche ne se termine pas dans le temps spécifié. La fonction `wmain` appelle la fonction `count_primes` à plusieurs reprises. Chaque fois, cela divise par deux le délai. Le programme se termine lorsque l'opération ne se termine pas dans le délai imparti.

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

Lorsque vous utilisez cette technique pour annuler les tâches après un délai, aucune tâche non débutée ne démarrera après l’annulation de la tâche générale. Toutefois, il est important que toutes les tâches de longue durée répondent à l’annulation en temps voulu. Pour plus d’informations sur l’annulation de tâches, consultez [l’annulation dans la bibliothèque PPL](cancellation-in-the-ppl.md).

## <a name="example"></a>Exemple

Voici le code complet pour cet exemple :

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `task-delay.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**cl.exe /EHsc task-delay.cpp**

## <a name="see-also"></a>Voir aussi

[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[task (Concurrency Runtime), classe](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source, classe](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token, classe](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event, classe](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[timer, classe](../../parallel/concrt/reference/timer-class.md)<br/>
[call, classe](../../parallel/concrt/reference/call-class.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)
