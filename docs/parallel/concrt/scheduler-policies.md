---
title: Stratégies de planificateur
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: 0f90b461ecba702501c2f6919572dc828c80907f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142280"
---
# <a name="scheduler-policies"></a>Stratégies de planificateur

Ce document décrit le rôle des stratégies du planificateur dans la runtime d’accès concurrentiel. Une *stratégie de planificateur* contrôle la stratégie que le planificateur utilise lorsqu’il gère des tâches. Par exemple, considérez une application qui nécessite que certaines tâches s’exécutent à `THREAD_PRIORITY_NORMAL` et d’autres tâches à exécuter sur `THREAD_PRIORITY_HIGHEST`.  Vous pouvez créer deux instances de planificateur : une qui spécifie la stratégie de `ContextPriority` à `THREAD_PRIORITY_NORMAL` et une autre qui spécifie la même stratégie `THREAD_PRIORITY_HIGHEST`.

En utilisant des stratégies de planificateur, vous pouvez diviser les ressources de traitement disponibles et affecter un ensemble fixe de ressources à chaque planificateur. Par exemple, imaginez un algorithme parallèle qui ne s’étend pas au-delà de quatre processeurs. Vous pouvez créer une stratégie de planificateur qui limite ses tâches à n’utiliser que quatre processeurs simultanément.

> [!TIP]
> Le runtime d’accès concurrentiel fournit un planificateur par défaut. Par conséquent, vous n’avez pas besoin d’en créer un dans votre application. Étant donné que le Planificateur de tâches vous aide à ajuster les performances de vos applications, nous vous recommandons de commencer avec la [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) ou la [bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) si vous débutez avec le runtime d’accès concurrentiel.

Quand vous utilisez la méthode [Concurrency :: CurrentScheduler :: Create](reference/currentscheduler-class.md#create), [Concurrency :: Scheduler :: Create](reference/scheduler-class.md#create)ou [Concurrency :: Scheduler :: SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) pour créer une instance du planificateur, vous fournissez un objet [Concurrency :: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) qui contient une collection de paires clé-valeur qui spécifient le comportement du planificateur. Le constructeur `SchedulerPolicy` accepte un nombre variable d’arguments. Le premier argument est le nombre d’éléments de stratégie que vous allez spécifier. Les arguments restants sont des paires clé-valeur pour chaque élément de stratégie. L’exemple suivant crée un objet `SchedulerPolicy` qui spécifie trois éléments de stratégie. Le runtime utilise les valeurs par défaut pour les clés de stratégie qui ne sont pas spécifiées.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

L’énumération [Concurrency ::P olicyelementkey](reference/concurrency-namespace-enums.md#policyelementkey) définit les clés de stratégie associées au planificateur de tâches. Le tableau suivant décrit les clés de stratégie et la valeur par défaut que le runtime utilise pour chacun d’eux.

|Clé de stratégie|Description|Valeur par défaut|
|----------------|-----------------|-------------------|
|`SchedulerKind`|Valeur [Concurrency :: SchedulerType,](reference/concurrency-namespace-enums.md#schedulertype) qui spécifie le type de threads à utiliser pour planifier des tâches.|`ThreadScheduler` (utiliser des threads normaux). Il s’agit de la seule valeur valide pour cette clé.|
|`MaxConcurrency`|Valeur `unsigned int` qui spécifie le nombre maximal de ressources d’accès concurrentiel utilisées par le planificateur.|[concurrence :: MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|
|`MinConcurrency`|Valeur `unsigned int` qui spécifie le nombre minimal de ressources concurrentielles utilisées par le planificateur.|`1`|
|`TargetOversubscriptionFactor`|`unsigned int` valeur qui spécifie le nombre de threads à allouer à chaque ressource de traitement.|`1`|
|`LocalContextCacheSize`|`unsigned int` valeur qui spécifie le nombre maximal de contextes qui peuvent être mis en cache dans la file d’attente locale de chaque processeur virtuel.|`8`|
|`ContextStackSize`|`unsigned int` valeur qui spécifie la taille de la pile, en kilo-octets, à réserver pour chaque contexte.|`0` (utiliser la taille de pile par défaut)|
|`ContextPriority`|`int` valeur qui spécifie la priorité de thread de chaque contexte. Il peut s’agir de n’importe quelle valeur que vous pouvez passer à [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) ou `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|

|`SchedulingProtocol`| Valeur [Concurrency :: SchedulingProtocolType,](reference/concurrency-namespace-enums.md#schedulingprotocoltype) qui spécifie l’algorithme de planification à utiliser. |`EnhanceScheduleGroupLocality`| |`DynamicProgressFeedback`| Valeur d' [accès concurrentiel ::D ynamicprogressfeedbacktype](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) qui spécifie s’il faut rééquilibrer les ressources en fonction des informations de progression basées sur les statistiques.<br /><br /> **Remarque** Ne définissez pas cette stratégie sur `ProgressFeedbackDisabled`, car elle est réservée à une utilisation par le Runtime. |`ProgressFeedbackEnabled`|

Chaque planificateur utilise sa propre stratégie lors de la planification des tâches. Les stratégies associées à un planificateur n’affectent pas le comportement d’un autre planificateur. En outre, vous ne pouvez pas modifier la stratégie du planificateur après avoir créé l’objet `Scheduler`.

> [!IMPORTANT]
> Utilisez uniquement des stratégies de planificateur pour contrôler les attributs des threads créés par le Runtime. Ne modifiez pas l’affinité de thread ou la priorité des threads créés par le runtime, car cela peut entraîner un comportement indéfini.

Le runtime crée un planificateur par défaut pour vous si vous n’en créez pas explicitement un. Si vous souhaitez utiliser le planificateur par défaut dans votre application, mais que vous souhaitez spécifier une stratégie que ce planificateur doit utiliser, appelez la méthode [Concurrency :: Scheduler :: SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) avant de planifier le travail parallèle. Si vous n’appelez pas la méthode `Scheduler::SetDefaultSchedulerPolicy`, le runtime utilise les valeurs de stratégie par défaut de la table.

Utilisez l' [accès concurrentiel :: CurrentScheduler :: GetPolicy](reference/currentscheduler-class.md#getpolicy) et les méthodes [Concurrency :: Scheduler :: GetPolicy](reference/scheduler-class.md#getpolicy) pour récupérer une copie de la stratégie du planificateur. Les valeurs de stratégie que vous recevez à partir de ces méthodes peuvent différer des valeurs de stratégie que vous spécifiez lors de la création du planificateur.

## <a name="example"></a>Exemple

Pour examiner des exemples qui utilisent des stratégies de planificateur spécifiques pour contrôler le comportement du planificateur, consultez [Comment : spécifier des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) et [Comment : créer des agents qui utilisent des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="see-also"></a>Voir aussi

[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Guide pratique pour spécifier des stratégies de planificateur](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[Guide pratique pour créer des agents qui utilisent des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
