---
title: Tâches légères
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: 19918cf73c2b5b03db895c4751b22b1666ce01de
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326684"
---
# <a name="lightweight-tasks"></a>Tâches légères

Ce document décrit le rôle des tâches légères dans le Runtime d’accès concurrentiel. Un *tâche légère* est une tâche que vous planifiez directement à partir d’un `concurrency::Scheduler` ou `concurrency::ScheduleGroup` objet. Une tâche légère ressemble à la fonction que vous fournissez à l’API Windows [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) (fonction). Par conséquent, les tâches légères sont utiles lorsque vous adaptez du code existant pour utiliser la fonctionnalité de planification du Runtime d’accès concurrentiel. Le Runtime d’accès concurrentiel lui-même utilise des tâches légères pour planifier des agents asynchrones et envoyer des messages entre les blocs de messages asynchrones.

> [!TIP]
>  Le runtime d'accès concurrentiel fournit un planificateur par défaut, et vous n'êtes donc pas obligé d'en créer un dans votre application. Étant donné que le Planificateur de tâches vous aide à optimiser les performances de vos applications, nous vous recommandons de commencer avec le [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) ou [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) si vous êtes nouvelle pour le Runtime d’accès concurrentiel.

Tâches légères présentent moins de traitement que les agents asynchrones et des groupes de tâches. Par exemple, le runtime ne pas informe vous lorsqu’une tâche légère se termine. En outre, le runtime ne pas intercepter ou gérer les exceptions sont levées à partir d’une tâche légère. Pour plus d’informations sur la gestion des exceptions et les tâches légères, consultez [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Pour la plupart des tâches, nous vous recommandons d’utiliser des fonctionnalités plus robustes telles que des groupes de tâches et les algorithmes parallèles, car elles vous permettent de plus facilement diviser les tâches complexes en plus simples. Pour plus d’informations sur les groupes de tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Pour plus d’informations sur les algorithmes parallèles, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

Pour créer une tâche légère, appelez le [Concurrency::ScheduleGroup :: ScheduleTask](reference/schedulegroup-class.md#scheduletask), [Concurrency::CurrentScheduler :: ScheduleTask](reference/currentscheduler-class.md#scheduletask), ou [Concurrency::Scheduler :: ScheduleTask ](reference/scheduler-class.md#scheduletask) (méthode). Pour attendre une tâche légère se termine, attendez que le planificateur parent d’arrêter ou utiliser un mécanisme de synchronisation comme un [concurrency::event](../../parallel/concrt/reference/event-class.md) objet.

## <a name="example"></a>Exemple

Pour obtenir un exemple qui montre comment adapter du code existant pour utiliser une tâche légère, consultez [procédure pas à pas : Adapter le Code existant pour utiliser des tâches légères](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).

## <a name="see-also"></a>Voir aussi

[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Procédure pas à pas : adaptation d’un code existant pour l’utilisation de tâches légères](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)
