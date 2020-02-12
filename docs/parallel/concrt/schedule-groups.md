---
title: Groupes de planification
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
ms.openlocfilehash: 1765c10f4cf8fe499aed1a140d2bba1ecaaf2300
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142310"
---
# <a name="schedule-groups"></a>Groupes de planification

Ce document décrit le rôle des groupes de planification dans le runtime d’accès concurrentiel. *Groupe de planification* affinité entre, ou groupes, tâches associées. Chaque planificateur possède un ou plusieurs groupes de planification. Utilisez des groupes de planification quand vous avez besoin d’un degré élevé de localité entre les tâches, par exemple, quand un groupe de tâches connexes tire parti d’une exécution sur le même nœud de processeur. Inversement, utilisez des instances de Scheduler lorsque votre application a des exigences de qualité spécifiques, par exemple, lorsque vous souhaitez limiter la quantité de ressources de traitement allouées à un ensemble de tâches. Pour plus d’informations sur les instances de planificateur, consultez [instances du planificateur](../../parallel/concrt/scheduler-instances.md).

> [!TIP]
> Le runtime d'accès concurrentiel fournit un planificateur par défaut, et vous n'êtes donc pas obligé d'en créer un dans votre application. Étant donné que le Planificateur de tâches vous aide à ajuster les performances de vos applications, nous vous recommandons de commencer avec la [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) ou la [bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) si vous débutez avec le runtime d’accès concurrentiel.

Chaque objet `Scheduler` possède un groupe de planification par défaut pour chaque nœud de planification. Un *nœud de planification* est mappé à la topologie du système sous-jacent. Le runtime crée un nœud de planification pour chaque package de processeur ou nœud NUMA (non-Uniform Memory Architecture), quel que soit le nombre supérieur. Si vous n’associez pas explicitement une tâche à un groupe de planification, le planificateur choisit le groupe auquel ajouter la tâche.

La stratégie du planificateur `SchedulingProtocol` influence l’ordre dans lequel le planificateur exécute les tâches dans chaque groupe de planification. Lorsque `SchedulingProtocol` a la valeur `EnhanceScheduleGroupLocality` (valeur par défaut), le Planificateur de tâches choisit la tâche suivante à partir du groupe de planification sur lequel il travaille lorsque la tâche en cours se termine ou se produit de manière coopérative. L’Planificateur de tâches recherche dans le groupe de planification actuel le travail avant de passer au groupe disponible suivant. À l’inverse, lorsque `SchedulingProtocol` est défini sur `EnhanceForwardProgress`, le planificateur passe au groupe de planification suivant une fois que chaque tâche se termine ou génère. Pour obtenir un exemple de comparaison de ces stratégies, consultez [Comment : utiliser des groupes de planification pour influencer l’ordre d’exécution](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

Le runtime utilise la classe [Concurrency :: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) pour représenter des groupes de planification. Pour créer un objet `ScheduleGroup`, appelez la méthode [Concurrency :: CurrentScheduler :: CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) ou [Concurrency :: Scheduler :: CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup) . Le runtime utilise un mécanisme de décompte de références pour contrôler la durée de vie des objets `ScheduleGroup`, tout comme c’est le cas avec les objets `Scheduler`. Lorsque vous créez un objet `ScheduleGroup`, le runtime définit le compteur de référence sur un. La méthode [Concurrency :: ScheduleGroup :: Reference](reference/schedulegroup-class.md#reference) incrémente le compteur de référence d’une unité. La méthode [Concurrency :: ScheduleGroup :: Release](reference/schedulegroup-class.md#release) décrémente le compteur de référence d’une unité.

De nombreux types dans le runtime d’accès concurrentiel vous permettent d’associer un objet à un groupe de planification. Par exemple, la classe [Concurrency :: agent](../../parallel/concrt/reference/agent-class.md) et les classes de bloc de message, telles que [Concurrency :: unbounded_buffer](reference/unbounded-buffer-class.md), [concurrentielle :: Join](../../parallel/concrt/reference/join-class.md)et Concurrency ::[Timer](reference/timer-class.md), fournissent des versions surchargées du constructeur qui acceptent un objet `ScheduleGroup`. Le runtime utilise l’objet `Scheduler` associé à cet objet `ScheduleGroup` pour planifier la tâche.

Vous pouvez également utiliser la méthode [Concurrency :: ScheduleGroup :: ScheduleTask](reference/schedulegroup-class.md#scheduletask) pour planifier une tâche légère. Pour plus d’informations sur les tâches légères, consultez [tâches légères](../../parallel/concrt/lightweight-tasks.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise des groupes de planification pour contrôler l’ordre d’exécution des tâches, consultez [Comment : utiliser des groupes de planification pour influencer l’ordre d’exécution](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="see-also"></a>Voir aussi

[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instances de planificateur](../../parallel/concrt/scheduler-instances.md)<br/>
[Guide pratique pour utiliser des groupes de planification pour influencer l’ordre d’exécution](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)
