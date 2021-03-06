---
description: 'En savoir plus sur : procédure pas à pas : adaptation du code existant pour utiliser des tâches légères'
title: 'Procédure pas à pas : adaptation d’un code existant pour l’utilisation de tâches légères'
ms.date: 04/25/2019
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: 1c3de0f49dc1edc3392a436bb911e005ef84bcf0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271406"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>Procédure pas à pas : adaptation d’un code existant pour l’utilisation de tâches légères

Cette rubrique montre comment adapter le code existant qui utilise l’API Windows pour créer et exécuter un thread afin d’utiliser une tâche légère.

Une *tâche légère* est une tâche que vous planifiez directement à partir d’un objet [Concurrency :: Scheduler](../../parallel/concrt/reference/scheduler-class.md) ou [Concurrency :: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) . Les tâches légères s’avèrent utiles quand vous adaptez du code existant pour utiliser les fonctionnalités de planification du runtime d’accès concurrentiel.

## <a name="prerequisites"></a>Prérequis

Avant de commencer cette procédure pas à pas, lisez la rubrique [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre l’utilisation classique de l’API Windows pour créer et exécuter un thread. Cet exemple utilise la fonction [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) pour appeler le `MyThreadFunction` sur un thread distinct.

### <a name="initial-code"></a>Code initial

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
Parameters = 50, 100
```

Les étapes suivantes montrent comment adapter l’exemple de code pour utiliser la runtime d’accès concurrentiel pour effectuer la même tâche.

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>Pour adapter l’exemple afin d’utiliser une tâche légère

1. Ajoutez une `#include` directive pour le fichier d’en-tête concrt. h.

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. Ajoutez une **`using`** directive pour l' `concurrency` espace de noms.

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. Modifiez la déclaration de `MyThreadFunction` pour utiliser la **`__cdecl`** Convention d’appel et pour retourner **`void`** .

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. Modifiez la `MyData` structure pour inclure un objet [Concurrency :: Event](../../parallel/concrt/reference/event-class.md) qui signale à l’application principale que la tâche est terminée.

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. Remplacez l’appel à `CreateThread` par un appel à la méthode [Concurrency :: CurrentScheduler :: ScheduleTask](reference/currentscheduler-class.md#scheduletask) .

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. Remplacez l’appel à `WaitForSingleObject` par un appel à la méthode [Concurrency :: Event :: wait](reference/event-class.md#wait) pour attendre la fin de la tâche.

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. Supprimez l’appel à `CloseHandle` .

1. Modifiez la signature de la définition de `MyThreadFunction` pour qu’elle corresponde à l’étape 3.

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

1. À la fin de la `MyThreadFunction` fonction, appelez la méthode [Concurrency :: Event :: Set](reference/event-class.md#set) pour signaler à l’application principale que la tâche est terminée.

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

1. Supprimez l' **`return`** instruction de `MyThreadFunction` .

### <a name="completed-code"></a>Code terminé

L’exemple complet suivant montre un code qui utilise une tâche légère pour appeler la `MyThreadFunction` fonction.

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

## <a name="see-also"></a>Voir aussi

[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler, classe](../../parallel/concrt/reference/scheduler-class.md)
