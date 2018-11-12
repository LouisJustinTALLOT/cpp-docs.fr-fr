---
title: 'Comment : gérer une instance de planificateur'
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: 8c19eb801c7761b85580526e1ff8bed89112cc5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437815"
---
# <a name="how-to-manage-a-scheduler-instance"></a>Comment : gérer une instance de planificateur

Instances de planificateur vous permettent d’associer des stratégies de planification spécifiques à différents types de charges de travail. Cette rubrique contient deux exemples simples qui montrent comment créer et gérer une instance du planificateur.

Les exemples créent des planificateurs qui utilisent les stratégies de planificateur par défaut. Pour un exemple qui crée un planificateur qui utilise une stratégie personnalisée, consultez [Comment : spécifier des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

### <a name="to-manage-a-scheduler-instance-in-your-application"></a>Pour gérer une instance du planificateur dans votre application

1. Créer un [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) objet qui contient la stratégie de valeurs pour le planificateur à utiliser.

1. Appelez le [Concurrency::CurrentScheduler :: Create](reference/currentscheduler-class.md#create) méthode ou le [Concurrency::Scheduler :: Create](reference/scheduler-class.md#create) méthode pour créer une instance de planificateur.

   Si vous utilisez le `Scheduler::Create` méthode, appelez le [Concurrency::Scheduler :: Attach](reference/scheduler-class.md#attach) méthode lorsque vous devez associer le planificateur au contexte actuel.

1. Appelez le [CreateEvent](/windows/desktop/api/synchapi/nf-synchapi-createeventa) fonction permettant de créer un handle vers un objet d’événement non signalé, de réinitialisation automatique.

1. Passez le handle vers l’objet d’événement que vous venez de créer pour le [Concurrency::CurrentScheduler :: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) méthode ou le [Concurrency::Scheduler :: RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) (méthode). Cela enregistre l’événement à définir lorsque le planificateur est détruit.

1. Effectuer les tâches que vous souhaitez que le planificateur actuel pour planifier.

1. Appelez le [Concurrency::CurrentScheduler :: Detach](reference/currentscheduler-class.md#detach) méthode pour détacher le planificateur actuel et de restaurer le planificateur précédent en tant que celle en cours.

   Si vous utilisez le `Scheduler::Create` méthode, appelez le [Concurrency::Scheduler :: Release](reference/scheduler-class.md#release) méthode décrémente le décompte de références le `Scheduler` objet.

1. Passez le handle vers l’événement à la [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) fonction pour attendre l’arrêt du planificateur.

1. Appelez le [CloseHandle](https://msdn.microsoft.com/library/windows/desktop/ms724211) (fonction) pour fermer le handle vers l’objet d’événement.

## <a name="example"></a>Exemple

Le code suivant montre deux façons de gérer une instance du planificateur. Chaque exemple utilise d’abord le planificateur par défaut pour effectuer une tâche qui imprime l’identificateur unique du planificateur actuel. Chaque exemple utilise ensuite une instance de planificateur pour effectuer la même tâche à nouveau. Enfin, chaque exemple restaure le planificateur par défaut que celui en cours et effectue la tâche une fois de plus.

Le premier exemple utilise le [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) classe pour créer une instance de planificateur et l’associer avec le contexte actuel. Le deuxième exemple utilise le [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) classe pour effectuer la même tâche. En règle générale, la `CurrentScheduler` classe est utilisée pour travailler avec le planificateur actuel. Le deuxième exemple, qui utilise le `Scheduler` class, est utile lorsque vous souhaitez contrôler quand le planificateur est associé au contexte actuel ou lorsque vous souhaitez associer des planificateurs spécifiques à des tâches spécifiques.

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

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `scheduler-instance.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL.exe /EHsc scheduler-instance.cpp**

## <a name="see-also"></a>Voir aussi

[Instances de planificateur](../../parallel/concrt/scheduler-instances.md)<br/>
[Guide pratique pour spécifier des stratégies de planificateur](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)

