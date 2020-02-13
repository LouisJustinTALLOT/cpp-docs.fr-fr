---
title: 'Comment : gérer une instance de planificateur'
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: c7ec321eaf0960dc14b61bbd8fdc76b53a31f8c5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141725"
---
# <a name="how-to-manage-a-scheduler-instance"></a>Comment : gérer une instance de planificateur

Les instances de planificateur vous permettent d’associer des stratégies de planification spécifiques à différents genres de charges de travail. Cette rubrique contient deux exemples de base qui montrent comment créer et gérer une instance de planificateur.

Les exemples créent des planificateurs qui utilisent les stratégies de planificateur par défaut. Pour obtenir un exemple qui crée un planificateur qui utilise une stratégie personnalisée, consultez Guide pratique [pour spécifier des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

## <a name="to-manage-a-scheduler-instance-in-your-application"></a>Pour gérer une instance de planificateur dans votre application

1. Créez un objet [Concurrency :: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) qui contient les valeurs de stratégie que le planificateur doit utiliser.

1. Appelez la méthode [Concurrency :: CurrentScheduler :: Create](reference/currentscheduler-class.md#create) ou la méthode [Concurrency :: Scheduler :: Create](reference/scheduler-class.md#create) pour créer une instance de planificateur.

   Si vous utilisez la méthode `Scheduler::Create`, appelez la méthode [Concurrency :: Scheduler :: Attach](reference/scheduler-class.md#attach) lorsque vous devez associer le planificateur au contexte actuel.

1. Appelez la fonction [CreateEvent](/windows/win32/api/synchapi/nf-synchapi-createeventw) pour créer un handle vers un objet d’événement de réinitialisation automatique non signalé.

1. Transmettez le descripteur à l’objet d’événement que vous venez de créer à la méthode [Concurrency :: CurrentScheduler :: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) ou à la méthode [Concurrency :: Scheduler :: RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) . Cela enregistre l’événement à définir lorsque le planificateur est détruit.

1. Effectuez les tâches que vous souhaitez que le planificateur actuel planifie.

1. Appelez la méthode [Concurrency :: CurrentScheduler ::D Etach](reference/currentscheduler-class.md#detach) pour détacher le planificateur actuel et restaurer le planificateur précédent comme celui en cours.

   Si vous utilisez la méthode `Scheduler::Create`, appelez la méthode [Concurrency :: Scheduler :: Release](reference/scheduler-class.md#release) pour décrémenter le décompte de références de l’objet `Scheduler`.

1. Transmettez le descripteur à l’événement à la fonction [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) pour attendre que le planificateur s’arrête.

1. Appelez la fonction [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) pour fermer le handle de l’objet d’événement.

## <a name="example"></a>Exemple

Le code suivant montre deux façons de gérer une instance de planificateur. Chaque exemple utilise tout d’abord le planificateur par défaut pour effectuer une tâche qui imprime l’identificateur unique du planificateur actuel. Chaque exemple utilise ensuite une instance de Scheduler pour effectuer à nouveau la même tâche. Enfin, chaque exemple restaure le planificateur par défaut en tant que planificateur actuel et exécute la tâche une fois de plus.

Le premier exemple utilise la classe [Concurrency :: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) pour créer une instance de planificateur et l’associer au contexte actuel. Le deuxième exemple utilise la classe [Concurrency :: Scheduler](../../parallel/concrt/reference/scheduler-class.md) pour effectuer la même tâche. En général, la classe `CurrentScheduler` est utilisée pour fonctionner avec le planificateur actuel. Le deuxième exemple, qui utilise la classe `Scheduler`, est utile lorsque vous souhaitez contrôler le moment où le planificateur est associé au contexte actuel ou lorsque vous souhaitez associer des planificateurs spécifiques à des tâches spécifiques.

[!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/cpp/how-to-manage-a-scheduler-instance_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
Using CurrentScheduler class...

Current scheduler id: 0
Creating and attaching scheduler...
Current scheduler id: 1
Detaching scheduler...
Current scheduler id: 0

Using Scheduler class...

Current scheduler id: 0
Creating scheduler...
Attaching scheduler...
Current scheduler id: 2
Detaching scheduler...
Current scheduler id: 0
```

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `scheduler-instance.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc Scheduler-instance. cpp**

## <a name="see-also"></a>Voir aussi

[Instances de planificateur](../../parallel/concrt/scheduler-instances.md)<br/>
[Guide pratique pour spécifier des stratégies de planificateur](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)
