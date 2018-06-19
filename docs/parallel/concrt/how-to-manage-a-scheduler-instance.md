---
title: 'Comment : gérer une Instance du planificateur | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 699abcbc75dc4f0df40d07d26c0e6987d4711fe3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687658"
---
# <a name="how-to-manage-a-scheduler-instance"></a>Comment : gérer une instance de planificateur
Instances de planificateur vous permettent d’associer des stratégies de planification spécifiques à différents types de charges de travail. Cette rubrique contient deux exemples simples qui montrent comment créer et gérer une instance du planificateur.  
  
 Les exemples créent des planificateurs qui utilisent les stratégies de planificateur par défaut. Pour obtenir un exemple qui crée un planificateur qui utilise une stratégie personnalisée, consultez [Comment : spécifier des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).  
  
### <a name="to-manage-a-scheduler-instance-in-your-application"></a>Pour gérer une instance du planificateur dans votre application  
  
1.  Créer un [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) objet qui contient la stratégie de valeurs pour le planificateur à utiliser.  
  

2.  Appeler le [Concurrency::CurrentScheduler :: Create](reference/currentscheduler-class.md#create) méthode ou la [Concurrency::Scheduler :: Create](reference/scheduler-class.md#create) méthode pour créer une instance du planificateur.  
  
     Si vous utilisez la `Scheduler::Create` méthode, appelez le [Concurrency::Scheduler :: Attach](reference/scheduler-class.md#attach) méthode lorsque vous devez associer le planificateur au contexte actuel.  
  
3.  Appelez le [CreateEvent](http://msdn.microsoft.com/library/windows/desktop/ms682396) fonction permettant de créer un handle vers un objet d’événement non signalé, de réinitialisation automatique.  
  
4.  Passez le handle vers l’objet d’événement que vous venez de créer à la [Concurrency::CurrentScheduler :: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) méthode ou la [Concurrency::Scheduler :: RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) (méthode). Cela enregistre l’événement à définir lorsque le planificateur est détruit.  
  
5.  Effectuez les tâches que vous souhaitez planifier le planificateur actuel.  
  
6.  Appelez le [Concurrency::CurrentScheduler :: Detach](reference/currentscheduler-class.md#detach) méthode pour détacher le planificateur actuel et restaurer le planificateur précédent en tant que l’objet actuel.  
  
     Si vous utilisez la `Scheduler::Create` méthode, appelez le [Concurrency::Scheduler :: Release](reference/scheduler-class.md#release) méthode pour décrémenter le décompte de références de le `Scheduler` objet.  
  
7.  Passez le handle vers l’événement à la [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032) fonction pour attendre l’arrêt du planificateur.  
  
8.  Appelez le [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211) afin de fermer le handle de l’objet d’événement.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre deux façons de gérer une instance du planificateur. Chaque exemple utilise d’abord le planificateur par défaut pour effectuer une tâche qui imprime l’identificateur unique du planificateur actuel. Chaque exemple utilise ensuite une instance du planificateur pour effectuer la même tâche à nouveau. Enfin, chaque exemple restaure le planificateur par défaut en tant que l’objet actuel et exécute la tâche une fois de plus.  
  
 Le premier exemple utilise la [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) classe pour créer une instance du planificateur et l’associer avec le contexte actuel. Le deuxième exemple utilise la [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) classe pour effectuer la même tâche. En règle générale, la `CurrentScheduler` classe est utilisée pour travailler avec le planificateur actuel. Le deuxième exemple, qui utilise le `Scheduler` de classe, est utile lorsque vous souhaitez contrôler lorsque le planificateur est associé au contexte actuel ou lorsque vous souhaitez associer des planificateurs spécifiques à des tâches spécifiques.  
  
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
 [Instances de planificateur](../../parallel/concrt/scheduler-instances.md)   
 [Guide pratique pour spécifier des stratégies de planificateur](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)

