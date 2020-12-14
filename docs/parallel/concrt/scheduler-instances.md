---
description: 'En savoir plus sur : instances de planificateur'
title: Instances de planificateur
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
ms.openlocfilehash: a11c22815c7a73c39033e51ccf47a64ceb47a92d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188051"
---
# <a name="scheduler-instances"></a>Instances de planificateur

Ce document décrit le rôle des instances du planificateur dans la runtime d’accès concurrentiel et explique comment utiliser les classes [Concurrency :: Scheduler](../../parallel/concrt/reference/scheduler-class.md) et [Concurrency :: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) pour créer et gérer des instances de planificateur. Les instances de planificateur sont utiles lorsque vous souhaitez associer des stratégies de planification explicites à des types de charges de travail spécifiques. Par exemple, vous pouvez créer une instance du planificateur pour effectuer certaines tâches avec une priorité de thread élevée et utiliser le planificateur par défaut pour effectuer d’autres tâches avec une priorité de thread normale.

> [!TIP]
> Le runtime d'accès concurrentiel fournit un planificateur par défaut, et vous n'êtes donc pas obligé d'en créer un dans votre application. Étant donné que le Planificateur de tâches vous aide à ajuster les performances de vos applications, nous vous recommandons de commencer avec la [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) ou la [bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) si vous débutez avec le runtime d’accès concurrentiel.

## <a name="sections"></a><a name="top"></a> Sections

- [Les classes Scheduler et CurrentScheduler](#classes)

- [Création d’une instance de planificateur](#creating)

- [Gestion de la durée de vie d’une instance de planificateur](#managing)

- [Méthodes et fonctionnalités](#features)

- [Exemple](#example)

## <a name="the-scheduler-and-currentscheduler-classes"></a><a name="classes"></a> Les classes Scheduler et CurrentScheduler

Le Planificateur de tâches permet aux applications d’utiliser une ou plusieurs *instances de planificateur* pour planifier le travail. La classe [Concurrency :: Scheduler](../../parallel/concrt/reference/scheduler-class.md) représente une instance du planificateur et encapsule les fonctionnalités liées à la planification des tâches.

Un thread attaché à un planificateur est connu sous le nom de *contexte d’exécution*, ou simplement de *contexte*. Un planificateur peut être actif sur le contexte actuel à tout moment. Le planificateur actif est également connu sous le nom de *planificateur actuel*. L’runtime d’accès concurrentiel utilise la classe [Concurrency :: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) pour fournir l’accès au planificateur actuel. Le planificateur actuel d’un contexte peut être différent du planificateur actuel pour un autre contexte. Le runtime ne fournit pas de représentation au niveau du processus du planificateur actuel.

En général, la `CurrentScheduler` classe est utilisée pour accéder au planificateur actuel. La `Scheduler` classe est utile lorsque vous devez gérer un planificateur qui n’est pas celui en cours.

Les sections suivantes décrivent comment créer et gérer une instance de planificateur. Pour obtenir un exemple complet qui illustre ces tâches, consultez [Comment : gérer une instance de planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).

[[Haut](#top)]

## <a name="creating-a-scheduler-instance"></a><a name="creating"></a> Création d’une instance de planificateur

Il existe trois façons de créer un `Scheduler` objet :

- Si aucun planificateur n’existe, le runtime crée un planificateur par défaut pour vous lorsque vous utilisez la fonctionnalité d’exécution, par exemple, un algorithme parallèle, pour effectuer le travail. Le planificateur par défaut devient le planificateur actuel du contexte qui initie le travail parallèle.

- La méthode [Concurrency :: CurrentScheduler :: Create](reference/currentscheduler-class.md#create) crée un `Scheduler` objet qui utilise une stratégie spécifique et associe ce planificateur au contexte actuel.

- La méthode [Concurrency :: Scheduler :: Create](reference/scheduler-class.md#create) crée un `Scheduler` objet qui utilise une stratégie spécifique, mais ne l’associe pas au contexte actuel.

Autoriser le runtime à créer un planificateur par défaut permet à toutes les tâches simultanées de partager le même planificateur. En règle générale, les fonctionnalités fournies par la [bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) ou la [bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) sont utilisées pour effectuer un travail parallèle. Par conséquent, vous n’avez pas besoin de travailler directement avec le planificateur pour contrôler sa stratégie ou sa durée de vie. Quand vous utilisez la bibliothèque PPL ou la bibliothèque d’agents, le runtime crée le planificateur par défaut s’il n’existe pas et en fait le planificateur actuel pour chaque contexte. Lorsque vous créez un planificateur et le définissez comme planificateur actuel, le runtime utilise ce planificateur pour planifier les tâches. Créez des instances de planificateur supplémentaires uniquement lorsque vous avez besoin d’une stratégie de planification spécifique. Pour plus d’informations sur les stratégies associées à un planificateur, consultez stratégies de [planification](../../parallel/concrt/scheduler-policies.md).

[[Haut](#top)]

## <a name="managing-the-lifetime-of-a-scheduler-instance"></a><a name="managing"></a> Gestion de la durée de vie d’une instance de planificateur

Le runtime utilise un mécanisme de décompte de références pour contrôler la durée de vie des `Scheduler` objets.

Lorsque vous utilisez la `CurrentScheduler::Create` méthode ou la `Scheduler::Create` méthode pour créer un `Scheduler` objet, le runtime définit le décompte de références initial de ce planificateur sur un. Le runtime incrémente le nombre de références lorsque vous appelez la méthode [Concurrency :: Scheduler :: Attach](reference/scheduler-class.md#attach) . La `Scheduler::Attach` méthode associe l' `Scheduler` objet au contexte actuel. Cela en fait le planificateur actuel. Quand vous appelez la `CurrentScheduler::Create` méthode, le runtime crée un `Scheduler` objet et l’attache au contexte actuel (et définit le décompte de références à un). Vous pouvez également utiliser la méthode [Concurrency :: Scheduler :: Reference](reference/scheduler-class.md#reference) pour incrémenter le décompte de références d’un `Scheduler` objet.

Le runtime décrémente le décompte de références lorsque vous appelez la méthode [Concurrency :: CurrentScheduler ::D Etach](reference/currentscheduler-class.md#detach) pour détacher le planificateur actuel ou appeler la méthode [Concurrency :: Scheduler :: Release](reference/scheduler-class.md#release) . Lorsque le nombre de références atteint zéro, le runtime détruit l' `Scheduler` objet une fois toutes les tâches planifiées terminées. Une tâche en cours d’exécution est autorisée à incrémenter le décompte de références du planificateur actuel. Par conséquent, si le décompte de références atteint zéro et qu’une tâche incrémente le nombre de références, le runtime ne détruit pas l' `Scheduler` objet tant que le décompte de références n’atteint pas zéro et que toutes les tâches se terminent.

Le Runtime gère une pile d' `Scheduler` objets interne pour chaque contexte. Quand vous appelez la `Scheduler::Attach` `CurrentScheduler::Create` méthode ou, le runtime exécute un push de cet `Scheduler` objet sur la pile du contexte actuel. Cela en fait le planificateur actuel. Lorsque vous appelez `CurrentScheduler::Detach` , le runtime dépile le planificateur actuel de la pile pour le contexte actuel et définit le précédent comme planificateur actuel.

Le Runtime fournit plusieurs moyens de gérer la durée de vie d’une instance de planificateur. Le tableau suivant montre la méthode appropriée qui libère ou détache le planificateur du contexte actuel pour chaque méthode qui crée ou attache un planificateur au contexte actuel.

|Créer ou attacher une méthode|Méthode Release ou Detach|
|-----------------------------|------------------------------|
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|
|`Scheduler::Create`|`Scheduler::Release`|
|`Scheduler::Attach`|`CurrentScheduler::Detach`|
|`Scheduler::Reference`|`Scheduler::Release`|

L’appel de la méthode Release ou Detach inappropriée produit un comportement non spécifié dans le Runtime.

Lorsque vous utilisez des fonctionnalités, par exemple la bibliothèque PPL, qui oblige le runtime à créer le planificateur par défaut pour vous, ne libérez pas ou ne Détachez pas ce planificateur. Le Runtime gère la durée de vie d’un planificateur qu’il crée.

Étant donné que le runtime ne détruit pas un `Scheduler` objet avant la fin de toutes les tâches, vous pouvez utiliser la méthode [Concurrency :: Scheduler :: RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) ou la méthode [Concurrency :: CurrentScheduler :: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) pour recevoir une notification lorsqu’un `Scheduler` objet est détruit. Cela est utile lorsque vous devez attendre la fin de chaque tâche planifiée par un `Scheduler` objet.

[[Haut](#top)]

## <a name="methods-and-features"></a><a name="features"></a> Méthodes et fonctionnalités

Cette section résume les méthodes importantes des `CurrentScheduler` `Scheduler` classes et.

Considérez la `CurrentScheduler` classe comme une application d’assistance pour la création d’un planificateur à utiliser sur le contexte actuel. La `Scheduler` classe vous permet de contrôler un planificateur qui appartient à un autre contexte.

Le tableau suivant présente les méthodes importantes définies par la `CurrentScheduler` classe.

|Méthode|Description|
|------------|-----------------|
|[Créer](reference/currentscheduler-class.md#create)|Crée un `Scheduler` objet qui utilise la stratégie spécifiée et l’associe au contexte actuel.|
|[Get](reference/currentscheduler-class.md#get)|Récupère un pointeur vers l' `Scheduler` objet associé au contexte actuel. Cette méthode n’incrémente pas le décompte de références de l' `Scheduler` objet.|
|[Détacher](reference/currentscheduler-class.md#detach)|Détache le planificateur actuel du contexte actuel et définit l’objet précédent comme planificateur actuel.|
|[RegisterShutdownEvent,](reference/currentscheduler-class.md#registershutdownevent)|Inscrit un événement que le runtime définit lorsque le planificateur actuel est détruit.|
|[CreateScheduleGroup,](reference/currentscheduler-class.md#createschedulegroup)|Crée un objet [Concurrency :: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) dans le planificateur actuel.|
|[ScheduleTask,](reference/currentscheduler-class.md#scheduletask)|Ajoute une tâche légère à la file d’attente de planification du planificateur actuel.|
|[GetPolicy](reference/currentscheduler-class.md#getpolicy)|Récupère une copie de la stratégie associée au planificateur actuel.|

Le tableau suivant présente les méthodes importantes définies par la `Scheduler` classe.

|Méthode|Description|
|------------|-----------------|
|[Créer](reference/scheduler-class.md#create)|Crée un `Scheduler` objet qui utilise la stratégie spécifiée.|
|[Attacher](reference/scheduler-class.md#attach)|Associe l' `Scheduler` objet au contexte actuel.|
|[Référence](reference/scheduler-class.md#reference)|Incrémente le compteur de références de l' `Scheduler` objet.|
|[Version release](reference/scheduler-class.md#release)|Décrémente le compteur de références de l' `Scheduler` objet.|
|[RegisterShutdownEvent,](reference/scheduler-class.md#registershutdownevent)|Inscrit un événement que le runtime définit lorsque l' `Scheduler` objet est détruit.|
|[CreateScheduleGroup,](reference/scheduler-class.md#createschedulegroup)|Crée un objet [Concurrency :: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) dans l' `Scheduler` objet.|
|[ScheduleTask,](reference/scheduler-class.md#scheduletask)|Planifie une tâche légère à partir de l' `Scheduler` objet.|
|[GetPolicy](reference/scheduler-class.md#getpolicy)|Récupère une copie de la stratégie associée à l' `Scheduler` objet.|
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|Définit la stratégie que le runtime doit utiliser lorsqu’il crée le planificateur par défaut.|
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|Restaure la stratégie par défaut à celle qui était active avant l’appel à `SetDefaultSchedulerPolicy` . Si le planificateur par défaut est créé après cet appel, le runtime utilise les paramètres de stratégie par défaut pour créer le planificateur.|

[[Haut](#top)]

## <a name="example"></a><a name="example"></a> Exemple

Pour obtenir des exemples de base de la création et de la gestion d’une instance de planificateur, consultez [Comment : gérer une instance de planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).

## <a name="see-also"></a>Voir aussi

[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Comment : gérer une instance de planificateur](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[Stratégies de planificateur](../../parallel/concrt/scheduler-policies.md)<br/>
[Groupes de planification](../../parallel/concrt/schedule-groups.md)
