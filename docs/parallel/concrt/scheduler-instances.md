---
title: Instances de planificateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f09a5708fd9140619eea60fb8e483c2e26165d1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693859"
---
# <a name="scheduler-instances"></a>Instances de planificateur
Ce document décrit le rôle des instances de planificateur dans le Runtime d’accès concurrentiel et comment utiliser le [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) et [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) classes pour créer et gérer instances de planificateur. Instances de planificateur sont utiles lorsque vous souhaitez associer des stratégies de planification explicites à des types spécifiques de charges de travail. Par exemple, vous pouvez créer une instance du planificateur pour effectuer certaines tâches avec une priorité de thread élevée et utiliser le planificateur par défaut pour effectuer d’autres tâches avec une priorité de thread normale.  
  
> [!TIP]
>  Le runtime d'accès concurrentiel fournit un planificateur par défaut, et vous n'êtes donc pas obligé d'en créer un dans votre application. Étant donné que le Planificateur de tâches vous aide à optimiser les performances de vos applications, nous vous recommandons de commencer avec la [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) ou [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) si vous êtes nouveau pour le Runtime d’accès concurrentiel.  
  
##  <a name="top"></a> Sections  
  
-   [Le planificateur et les Classes de CurrentScheduler](#classes)  
  
-   [Création d’une Instance de planificateur](#creating)  
  
-   [La gestion de la durée de vie d’une Instance du planificateur](#managing)  
  
-   [Méthodes et fonctionnalités](#features)  
  
-   [Exemple](#example)  
  
##  <a name="classes"></a> Le planificateur et les Classes de CurrentScheduler  
 Le Planificateur de tâches permet aux applications d’utiliser une ou plusieurs *instances de planificateur* pour planifier le travail. Le [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) classe représente une instance du planificateur et encapsule la fonctionnalité qui est liée à la planification des tâches.  
  
 Un thread qui est attaché à un planificateur est appelé un *contexte d’exécution*, ou simplement *contexte*. Un planificateur peut être actif sur le contexte actuel à tout moment. Le planificateur actif est également appelé le *planificateur actuel*. Le Runtime d’accès concurrentiel utilise le [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) classe pour fournir l’accès au planificateur actuel. Le planificateur actuel pour un contexte peut différer du planificateur actuel d’un autre contexte. Le runtime ne fournit pas une représentation sous forme de niveau processus du planificateur actuel.  
  
 En règle générale, la `CurrentScheduler` classe est utilisée pour accéder au planificateur actuel. La `Scheduler` classe est utile lorsque vous avez besoin gérer un planificateur qui n’est pas celle en cours.  
  
 Les sections suivantes décrivent comment créer et gérer une instance du planificateur. Pour obtenir un exemple complet qui illustre ces tâches, consultez [Comment : gérer une Instance du planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).  
  
 [[Haut](#top)]  
  
##  <a name="creating"></a> Création d’une Instance de planificateur  
 Il existe trois manières de créer un `Scheduler` objet :  
  
-   Si aucun planificateur n’existe, le runtime crée un planificateur par défaut lorsque vous utilisez la fonctionnalité d’exécution, par exemple, un algorithme parallèle, pour effectuer le travail. Le planificateur par défaut devient le planificateur actuel pour le contexte qui initie le travail parallèle.  
  

-   Le [Concurrency::CurrentScheduler :: Create](reference/currentscheduler-class.md#create) méthode crée un `Scheduler` objet qui utilise une stratégie spécifique et associe ce planificateur au contexte actuel.  
  
-   Le [Concurrency::Scheduler :: Create](reference/scheduler-class.md#create) méthode crée un `Scheduler` objet qui utilise une stratégie spécifique, mais ne les associez pas avec le contexte actuel.  

  
 Autoriser le runtime créer un planificateur par défaut permet à toutes les tâches simultanées de partager le même planificateur. En règle générale, la fonctionnalité fournie par le [bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) ou la [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) est utilisé pour effectuer un travail parallèle. Par conséquent, vous n’avez pas de travailler directement avec le planificateur pour contrôler sa stratégie ou la durée de vie. Lorsque vous utilisez la bibliothèque PPL ou la bibliothèque d’Agents, le runtime crée le planificateur par défaut si elle n’existe pas et rend le planificateur actuel pour chaque contexte. Lorsque vous créez un planificateur et définissez en tant que le planificateur actuel, le runtime utilise ce planificateur pour planifier des tâches. Créer des instances de planificateur supplémentaires uniquement lorsque vous avez besoin d’une stratégie de planification spécifique. Pour plus d’informations sur les stratégies qui sont associés à un planificateur, consultez [des stratégies de planificateur](../../parallel/concrt/scheduler-policies.md).  
  
 [[Haut](#top)]  
  
##  <a name="managing"></a> La gestion de la durée de vie d’une Instance du planificateur  
 Le runtime utilise un mécanisme de comptage de références pour contrôler la durée de vie de `Scheduler` objets.  
  

 Lorsque vous utilisez la `CurrentScheduler::Create` (méthode) ou le `Scheduler::Create` méthode pour créer un `Scheduler` de l’objet, le runtime définit le décompte de références initial de ce planificateur à un. Le runtime incrémente le décompte de références lorsque vous appelez le [Concurrency::Scheduler :: Attach](reference/scheduler-class.md#attach) (méthode). Le `Scheduler::Attach` méthode associe le `Scheduler` objet ainsi que le contexte actuel. Cela rend le planificateur actuel. Lorsque vous appelez le `CurrentScheduler::Create` méthode, le runtime crée un `Scheduler` de l’objet et attache au contexte actuel (et définit le nombre de références à un). Vous pouvez également utiliser le [Concurrency::Scheduler :: Reference](reference/scheduler-class.md#reference) méthode pour incrémenter le décompte de références d’un `Scheduler` objet.  
  
 Le runtime décrémente le décompte de références lorsque vous appelez le [Concurrency::CurrentScheduler :: Detach](reference/currentscheduler-class.md#detach) méthode pour détacher le planificateur actuel, ou appelez le [Concurrency::Scheduler :: Release](reference/scheduler-class.md#release) (méthode). Lorsque le décompte de références atteint zéro, le runtime détruit le `Scheduler` objet une fois toutes les tâches planifiées terminées. Une tâche en cours d’exécution est autorisée à incrémenter le décompte de références du planificateur actuel. Par conséquent, si le décompte de références atteint zéro, une tâche incrémente le décompte de références, le runtime ne détruit pas les `Scheduler` de l’objet jusqu'à ce que le nombre de références atteint zéro, et toutes les tâches terminées.  

  
 Le runtime conserve une pile interne du `Scheduler` objets pour chaque contexte. Lorsque vous appelez le `Scheduler::Attach` ou `CurrentScheduler::Create` méthode, le runtime exécute un push qui `Scheduler` objet dans la pile pour le contexte actuel. Cela rend le planificateur actuel. Lorsque vous appelez `CurrentScheduler::Detach`, le runtime dépile le planificateur actuel de la pile pour le contexte actuel et définit le précédent comme planificateur actuel.  
  
 Le runtime fournit plusieurs façons de gérer la durée de vie d’une instance du planificateur. Le tableau suivant montre la méthode appropriée qui libère ou détache le planificateur du contexte actuel pour chaque méthode qui crée ou attache un planificateur au contexte actuel.  
  
|Créer ou attach (méthode)|Libérer ou detach (méthode)|  
|-----------------------------|------------------------------|  
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|  
|`Scheduler::Create`|`Scheduler::Release`|  
|`Scheduler::Attach`|`CurrentScheduler::Detach`|  
|`Scheduler::Reference`|`Scheduler::Release`|  
  
 L’inappropriée de l’appel de libération ou de détachement méthode produit un comportement non spécifié dans le runtime.  
  
 Lorsque vous utilisez des fonctionnalités, par exemple, la bibliothèque de modèles parallèles, qui provoque le runtime crée le planificateur par défaut, ne pas libérer ou détacher ce planificateur. Le runtime gère la durée de vie de tout planificateur qu’il crée.  
  

 Étant donné que le runtime ne détruit pas un `Scheduler` objet avant que toutes les tâches soient terminées, vous pouvez utiliser la [Concurrency::Scheduler :: RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) méthode ou la [concurrency::CurrentScheduler :: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) méthode pour recevoir une notification lorsqu’un `Scheduler` objet est détruit. Cela est utile lorsque vous devez attendre pour chaque tâche planifiée par un `Scheduler` objet se termine.  
  
 [[Haut](#top)]  
  
##  <a name="features"></a> Méthodes et fonctionnalités  
 Cette section résume les méthodes importantes de la `CurrentScheduler` et `Scheduler` classes.  
  
 Pensez au `CurrentScheduler` classe comme un programme d’assistance pour la création d’un planificateur à utiliser sur le contexte actuel. La `Scheduler` classe vous permet de contrôler un planificateur qui appartient à un autre contexte.  
  
 Le tableau suivant présente les méthodes importantes sont définis par le `CurrentScheduler` classe.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Créer](reference/currentscheduler-class.md#create)|Crée un `Scheduler` objet qui utilise la stratégie spécifiée et l’associe au contexte actuel.|  
|[Get](reference/currentscheduler-class.md#get)|Récupère un pointeur vers le `Scheduler` objet qui est associé au contexte actuel. Cette méthode n’incrémente pas le décompte de références de le `Scheduler` objet.|  
|[Détacher](reference/currentscheduler-class.md#detach)|Détache le planificateur actuel dans le contexte actuel et définit le précédent comme planificateur actuel.|  
|[RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)|Enregistre un événement que le runtime définit lorsque le planificateur actuel est détruit.|  
|[CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)|Crée un [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objet dans le planificateur actuel.|  
|[ScheduleTask](reference/currentscheduler-class.md#scheduletask)|Ajoute une tâche légère à la planification de la file d’attente du planificateur actuel.|  
|[GetPolicy](reference/currentscheduler-class.md#getpolicy)|Récupère une copie de la stratégie associée au planificateur actuel.|  
  
 Le tableau suivant présente les méthodes importantes sont définis par le `Scheduler` classe.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Créer](reference/scheduler-class.md#create)|Crée un `Scheduler` objet qui utilise la stratégie spécifiée.|  
|[Attacher](reference/scheduler-class.md#attach)|Associe le `Scheduler` objet ainsi que le contexte actuel.|  
|[Référence](reference/scheduler-class.md#reference)|Incrémente le compteur de références de le `Scheduler` objet.|  
|[Version release](reference/scheduler-class.md#release)|Décrémente le compteur de références de le `Scheduler` objet.|  
|[RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)|Enregistre un événement que le runtime définit lorsque le `Scheduler` objet est détruit.|  
|[CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)|Crée un [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) de l’objet dans le `Scheduler` objet.|  
|[ScheduleTask](reference/scheduler-class.md#scheduletask)|Planifie une tâche légère à partir de la `Scheduler` objet.|  
|[GetPolicy](reference/scheduler-class.md#getpolicy)|Récupère une copie de la stratégie qui est associée à la `Scheduler` objet.|  
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|Définit la stratégie pour le runtime à utiliser lorsqu’il crée le planificateur par défaut.|  
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|Restaure la stratégie par défaut à celle qui était active avant l’appel à `SetDefaultSchedulerPolicy`. Si le planificateur par défaut est créé après cet appel, le runtime utilise les paramètres de stratégie par défaut pour créer le planificateur.|  

  
 [[Haut](#top)]  
  
##  <a name="example"></a> Exemple  
 Pour obtenir des exemples simples montrant comment créer et gérer une instance de planificateur, consultez [Comment : gérer une Instance du planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Comment : gérer une Instance de planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [Stratégies de planificateur](../../parallel/concrt/scheduler-policies.md)   
 [Groupes de planification](../../parallel/concrt/schedule-groups.md)

