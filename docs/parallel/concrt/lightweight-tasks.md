---
title: Tâches légères
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: be417052ffab19c1bc2d2ba6f35094f98e315812
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141852"
---
# <a name="lightweight-tasks"></a>Tâches légères

Ce document décrit le rôle des tâches légères dans le runtime d’accès concurrentiel. Une *tâche légère* est une tâche que vous planifiez directement à partir d’un objet `concurrency::Scheduler` ou `concurrency::ScheduleGroup`. Une tâche légère ressemble à la fonction que vous fournissez à la fonction d’API Windows [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) . Par conséquent, les tâches légères sont utiles quand vous adaptez du code existant pour utiliser la fonctionnalité de planification de la runtime d’accès concurrentiel. Le runtime d’accès concurrentiel lui-même utilise des tâches légères pour planifier des agents asynchrones et envoyer des messages entre des blocs de messages asynchrones.

> [!TIP]
> Le runtime d'accès concurrentiel fournit un planificateur par défaut, et vous n'êtes donc pas obligé d'en créer un dans votre application. Étant donné que le Planificateur de tâches vous aide à ajuster les performances de vos applications, nous vous recommandons de commencer avec la [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) ou la [bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) si vous débutez avec le runtime d’accès concurrentiel.

Les tâches légères comportent moins de charge que les agents asynchrones et les groupes de tâches. Par exemple, le runtime ne vous informe pas quand une tâche légère se termine. En outre, le runtime n’intercepte pas ou ne gère pas les exceptions levées à partir d’une tâche légère. Pour plus d’informations sur la gestion des exceptions et les tâches légères, consultez [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Pour la plupart des tâches, nous vous recommandons d’utiliser des fonctionnalités plus robustes, telles que des groupes de tâches et des algorithmes parallèles, car elles vous permettent de fractionner plus facilement les tâches complexes en fonctions plus basiques. Pour plus d’informations sur les groupes de tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Pour plus d’informations sur les algorithmes parallèles, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

Pour créer une tâche légère, appelez la méthode [Concurrency :: ScheduleGroup :: ScheduleTask](reference/schedulegroup-class.md#scheduletask), [Concurrency :: CurrentScheduler :: ScheduleTask](reference/currentscheduler-class.md#scheduletask)ou [Concurrency :: Scheduler :: ScheduleTask](reference/scheduler-class.md#scheduletask) . Pour attendre la fin d’une tâche légère, attendez que le planificateur parent s’arrête ou utilisez un mécanisme de synchronisation tel qu’un objet [Concurrency :: Event](../../parallel/concrt/reference/event-class.md) .

## <a name="example"></a>Exemple

Pour obtenir un exemple qui montre comment adapter du code existant pour utiliser une tâche légère, consultez [procédure pas à pas : adaptation du code existant pour utiliser des tâches légères](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).

## <a name="see-also"></a>Voir aussi

[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Procédure pas à pas : adaptation d’un code existant pour l’utilisation de tâches légères](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)
