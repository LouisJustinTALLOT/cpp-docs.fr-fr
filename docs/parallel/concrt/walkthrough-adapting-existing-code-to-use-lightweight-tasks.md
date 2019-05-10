---
title: 'Procédure pas à pas : Adapter le Code existant pour utiliser des tâches légères'
ms.date: 04/25/2019
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: 658cc82442bf362b7f50e787169ce75373275d9c
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857029"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>Procédure pas à pas : Adapter le Code existant pour utiliser des tâches légères

Cette rubrique montre comment adapter du code existant qui utilise l’API Windows pour créer et exécuter un thread pour utiliser une tâche légère.

Un *tâche légère* est une tâche que vous planifiez directement à partir d’un [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) ou [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objet. Les tâches légères s’avèrent utiles quand vous adaptez du code existant pour utiliser les fonctionnalités de planification du runtime d’accès concurrentiel.

## <a name="prerequisites"></a>Prérequis

Avant de commencer cette procédure pas à pas, lisez la rubrique [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant illustre une utilisation typique de l’API Windows pour créer et exécuter un thread. Cet exemple utilise le [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) fonction à appeler le `MyThreadFunction` sur un thread distinct.

### <a name="code"></a>Code

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

### <a name="comments"></a>Commentaires

Cet exemple produit la sortie suivante.

```Output
Parameters = 50, 100
```

Les étapes suivantes montrent comment adapter l’exemple de code pour utiliser le Runtime d’accès concurrentiel pour effectuer la même tâche.

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>Pour adapter l’exemple pour utiliser une tâche légère

1. Ajouter un `#include` directive pour le fichier d’en-tête concrt.h.

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. Ajouter un `using` directive pour le `concurrency` espace de noms.

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. Modifiez la déclaration de `MyThreadFunction` à utiliser le `__cdecl` convention d’appel et retourner `void`.

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. Modifier le `MyData` structure pour inclure un [concurrency::event](../../parallel/concrt/reference/event-class.md) objet qui signale à l’application principale que la tâche est terminée.

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. Remplacez l’appel à `CreateThread` avec un appel à la [Concurrency::CurrentScheduler :: ScheduleTask](reference/currentscheduler-class.md#scheduletask) (méthode).

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. Remplacez l’appel à `WaitForSingleObject` avec un appel à la [Concurrency::Event :: wait](reference/event-class.md#wait) méthode pour attendre la tâche se termine.

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. Supprimez l’appel à `CloseHandle`.

1. Modifier la signature de la définition de `MyThreadFunction` pour correspondre à l’étape 3.

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

9. À la fin de la `MyThreadFunction` de fonction, appelez le [concurrency::event::set](reference/event-class.md#set) méthode pour signaler à l’application principale que la tâche est terminée.

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

10. Supprimer le `return` instruction à partir de `MyThreadFunction`.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple complet suivant montre le code qui utilise une tâche légère pour appeler le `MyThreadFunction` (fonction).

### <a name="code"></a>Code

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

### <a name="comments"></a>Commentaires

## <a name="see-also"></a>Voir aussi

[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler, classe](../../parallel/concrt/reference/scheduler-class.md)
