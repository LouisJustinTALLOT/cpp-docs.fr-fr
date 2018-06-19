---
title: 'Procédure pas à pas : Adaptation d’un Code existant pour l’utilisation de tâches légères | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4fe3bb4b576bd1f9160b4a3cdc3142be5cdff05
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688542"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>Procédure pas à pas : adaptation d’un code existant pour l’utilisation de tâches légères
Cette rubrique montre comment adapter du code existant qui utilise l’API Windows pour créer et exécuter un thread pour utiliser une tâche légère.  
  
 A *tâche légère* est une tâche que vous planifiez directement à partir d’un [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) ou [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objet. Les tâches légères s’avèrent utiles quand vous adaptez du code existant pour utiliser les fonctionnalités de planification du runtime d’accès concurrentiel.  
  
## <a name="prerequisites"></a>Prérequis  
 Avant de commencer cette procédure pas à pas, consultez la rubrique [du Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant illustre une utilisation typique de l’API Windows pour créer et exécuter un thread. Cet exemple utilise le [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) fonction à appeler le `MyThreadFunction` sur un thread distinct.  
  
### <a name="code"></a>Code  
 [!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]  
  
### <a name="comments"></a>Commentaires  
 Cet exemple produit la sortie suivante.  
  
```Output  
Parameters = 50, 100  
```  
  
 Les étapes suivantes montrent comment adapter l’exemple de code pour utiliser le Runtime d’accès concurrentiel pour effectuer la même tâche.  
  
### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>Pour adapter l’exemple pour utiliser une tâche légère  
  
1.  Ajouter un `#include` directive pour le fichier d’en-tête concrt.h.  
  
 [!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]  
  
2.  Ajouter un `using` directive pour le `concurrency` espace de noms.  
  
 [!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]  
  
3.  Modifiez la déclaration de `MyThreadFunction` à utiliser le `__cdecl` convention d’appel et retourner `void`.  
  
 [!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]  
  
4.  Modifier la `MyData` structure à inclure un [concurrency::event](../../parallel/concrt/reference/event-class.md) objet qui signale à l’application principale que la tâche s’est terminée.  
  
 [!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]  
  
5.  Remplacez l’appel à `CreateThread` avec un appel à la [Concurrency::CurrentScheduler :: ScheduleTask](reference/currentscheduler-class.md#scheduletask) (méthode).  

  
 [!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]  
  

6.  Remplacez l’appel à `WaitForSingleObject` avec un appel à la [Concurrency::Event :: wait](reference/event-class.md#wait) méthode pour attendre la tâche se termine.  

 [!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]  
  
7.  Supprimez l’appel à `CloseHandle`.  
  
8.  Modifier la signature de la définition de `MyThreadFunction` pour correspondre à l’étape 3.  
  
 [!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]  
  
9. À la fin de la `MyThreadFunction` de fonction, appelez le [concurrency::event::set](reference/event-class.md#set) méthode pour signaler à l’application principale que la tâche s’est terminée.  
  
 [!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]  
  
10. Supprimer le `return` instruction à partir de `MyThreadFunction`.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant montre le code qui utilise une tâche légère pour appeler le `MyThreadFunction` (fonction).  
  
### <a name="code"></a>Code  
 [!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]  
  
### <a name="comments"></a>Commentaires  
  
## <a name="see-also"></a>Voir aussi  
 [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Scheduler, classe](../../parallel/concrt/reference/scheduler-class.md)
