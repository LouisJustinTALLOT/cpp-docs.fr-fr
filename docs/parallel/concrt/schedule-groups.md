---
title: Groupes de planification | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fa61772af96ba0d2602ff42a6a43b2b3a13a4e6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385897"
---
# <a name="schedule-groups"></a>Groupes de planification

Ce document décrit le rôle de groupes de planification dans le Runtime d’accès concurrentiel. Un *groupe de planification* l’affinité entre l’ou les regroupe, les tâches associées. Chaque planificateur possède un ou plusieurs groupes de planification. Utilisez des groupes de planification quand vous avez besoin d’un degré élevé de localité entre les tâches, par exemple, quand un groupe de tâches connexes tire parti d’une exécution sur le même nœud de processeur. À l’inverse, utilisez des instances de planificateur lorsque votre application a des exigences de qualité spécifiques, par exemple, lorsque vous souhaitez limiter la quantité de ressources de traitement qui sont allouées à un ensemble de tâches. Pour plus d’informations sur les instances de planificateur, consultez [Instances de planificateur](../../parallel/concrt/scheduler-instances.md).

> [!TIP]
>  Le runtime d'accès concurrentiel fournit un planificateur par défaut, et vous n'êtes donc pas obligé d'en créer un dans votre application. Étant donné que le Planificateur de tâches vous aide à optimiser les performances de vos applications, nous vous recommandons de commencer avec le [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) ou [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) si vous êtes nouvelle pour le Runtime d’accès concurrentiel.

Chaque `Scheduler` objet a un groupe de planification par défaut pour chaque nœud de planification. Un *planification nœud* est mappé à la topologie de système sous-jacent. Le runtime crée un nœud de planification pour chaque package de processeur ou nœud de l’Architecture de mémoire Non uniforme (NUMA), selon le nombre est supérieur. Si vous n’associez pas explicitement d’une tâche à un groupe de planification, le planificateur choisit le groupe à ajouter la tâche.

Le `SchedulingProtocol` planificateur stratégie détermine l’ordre dans lequel le planificateur exécute les tâches dans chaque groupe de planification. Lorsque `SchedulingProtocol` a la valeur `EnhanceScheduleGroupLocality` (qui est la valeur par défaut), le Planificateur de tâches choisit la tâche suivante dans le groupe de planification qui fonctionne sur lorsque la tâche en cours se termine ou cède de manière coopérative. Le Planificateur de tâches recherche dans le groupe actuel de la planification de travail avant de passer au groupe disponible suivant. À l’inverse, lorsque `SchedulingProtocol` est défini sur `EnhanceForwardProgress`, le planificateur passe au groupe de planification suivant une fois que chaque tâche se termine ou qu’il génère. Pour obtenir un exemple qui compare ces stratégies, consultez [Comment : utiliser des groupes de planification pour Influence ordre d’exécution](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

Le runtime utilise le [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) classe pour représenter des groupes de planification. Pour créer un `ScheduleGroup` de l’objet, appelez le [Concurrency::CurrentScheduler :: CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) ou [Concurrency::Scheduler :: CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup) (méthode). Le runtime utilise un mécanisme de comptage de références pour contrôler la durée de vie de `ScheduleGroup` objets, comme il le fait avec `Scheduler` objets. Lorsque vous créez un `ScheduleGroup` de l’objet, le runtime définit la référence compteur à un. Le [Concurrency::ScheduleGroup](reference/schedulegroup-class.md#reference) méthode incrémente le compteur de références d’une unité. Le [Concurrency::ScheduleGroup :: Release](reference/schedulegroup-class.md#release) méthode décrémente le compteur de références d’une unité.

De nombreux types dans le Runtime d’accès concurrentiel vous permettent d’associer un objet avec un groupe de planification. Par exemple, le [concurrency::agent](../../parallel/concrt/reference/agent-class.md) bloc de classe et le message classes telles que [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency::join](../../parallel/concrt/reference/join-class.md)et la concurrence ::[ minuteur](reference/timer-class.md), fournissent des versions surchargées du constructeur qui prennent un `ScheduleGroup` objet. Le runtime utilise le `Scheduler` objet qui est associé à ce `ScheduleGroup` objet pour planifier la tâche.

Vous pouvez également utiliser le [Concurrency::ScheduleGroup :: ScheduleTask](reference/schedulegroup-class.md#scheduletask) méthode pour planifier une tâche légère. Pour plus d’informations sur les tâches légères, consultez [tâches légères](../../parallel/concrt/lightweight-tasks.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise des groupes pour contrôler l’ordre d’exécution des tâches de planification, consultez [Comment : utiliser des groupes de planification pour Influence ordre d’exécution](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="see-also"></a>Voir aussi

[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instances de planificateur](../../parallel/concrt/scheduler-instances.md)<br/>
[Guide pratique pour utiliser des groupes de planification pour influencer l’ordre d’exécution](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)

