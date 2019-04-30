---
title: Stratégies de planificateur
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: e2acfc199e7ad9edf3965dc8ccb4103eb615a66b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408002"
---
# <a name="scheduler-policies"></a>Stratégies de planificateur

Ce document décrit le rôle des stratégies de planificateur dans le Runtime d’accès concurrentiel. Un *planificateur stratégie* contrôle la stratégie utilisée par le planificateur lorsqu’il gère des tâches. Par exemple, considérez une application qui requiert certaines tâches à exécuter au niveau `THREAD_PRIORITY_NORMAL` et d’autres tâches à exécuter au niveau `THREAD_PRIORITY_HIGHEST`.  Vous pouvez créer deux instances de planificateur : une qui spécifie le `ContextPriority` la stratégie `THREAD_PRIORITY_NORMAL` et une autre qui spécifie la même stratégie pour être `THREAD_PRIORITY_HIGHEST`.

À l’aide de stratégies de planificateur, vous pouvez répartir les ressources de traitement disponibles et affecter un ensemble fixe de ressources à chaque planificateur. Par exemple, considérez un algorithme parallèle qui n’évolue pas au-delà de quatre processeurs. Vous pouvez créer une stratégie du planificateur qui limite ses tâches pour utiliser pas plus de quatre processeurs simultanément.

> [!TIP]
>  Le Runtime d’accès concurrentiel fournit un planificateur par défaut. Par conséquent, vous n’êtes pas obligé de créer un dans votre application. Étant donné que le Planificateur de tâches vous aide à optimiser les performances de vos applications, nous vous recommandons de commencer avec le [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) ou [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) si vous êtes nouvelle pour le Runtime d’accès concurrentiel.

Lorsque vous utilisez le [Concurrency::CurrentScheduler :: Create](reference/currentscheduler-class.md#create), [Concurrency::Scheduler :: Create](reference/scheduler-class.md#create), ou [:: SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) méthode pour créer une instance de planificateur, vous fournissez un [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) objet qui contient une collection de paires clé-valeur qui spécifient le comportement du planificateur. Le `SchedulerPolicy` constructeur accepte un nombre variable d’arguments. Le premier argument est le nombre d’éléments de stratégie que vous allez spécifier. Les arguments restants sont des paires clé-valeur pour chaque élément de stratégie. L’exemple suivant crée un `SchedulerPolicy` objet qui spécifie trois éléments de la stratégie. Le runtime utilise les valeurs par défaut pour les clés de stratégie qui ne sont pas spécifiés.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

Le [concurrency::PolicyElementKey](reference/concurrency-namespace-enums.md#policyelementkey) énumération définit les clés de stratégie qui sont associés dans le Planificateur de tâches. Le tableau suivant décrit les clés de stratégie et la valeur par défaut que le runtime utilise pour chacun d’eux.

|Clé de la stratégie|Description|Valeur par défaut|
|----------------|-----------------|-------------------|
|`SchedulerKind`|Un [concurrency::SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) valeur qui spécifie le type de threads à utiliser pour planifier des tâches.|`ThreadScheduler` (utiliser des threads normaux). Il s’agit de la seule valeur valide pour cette clé.|
|`MaxConcurrency`|Un `unsigned int` valeur qui spécifie le nombre maximal de ressources d’accès concurrentiel qui utilise le planificateur.|[concurrency::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|
|`MinConcurrency`|Un `unsigned int` valeur qui spécifie le nombre minimal de ressources d’accès concurrentiel qui utilise le planificateur.|`1`|
|`TargetOversubscriptionFactor`|Un `unsigned int` valeur qui spécifie le nombre de threads à allouer à chaque ressource de traitement.|`1`|
|`LocalContextCacheSize`|Un `unsigned int` valeur qui spécifie le nombre maximal de contextes qui peuvent être mis en cache dans la file d’attente locale de chaque processeur virtuel.|`8`|
|`ContextStackSize`|Un `unsigned int` valeur qui spécifie la taille de la pile, en kilo-octets, à réserver pour chaque contexte.|`0` (utiliser la taille de pile par défaut)|
|`ContextPriority`|Un `int` valeur qui spécifie la priorité de thread de chaque contexte. Cela peut être toute valeur que vous pouvez transmettre à [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) ou `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|

|`SchedulingProtocol`| Un [concurrency::SchedulingProtocolType](reference/concurrency-namespace-enums.md#schedulingprotocoltype) valeur qui spécifie l’algorithme de planification à utiliser. | `EnhanceScheduleGroupLocality`| | `DynamicProgressFeedback`| Un [concurrency::DynamicProgressFeedbackType](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) valeur qui spécifie s’il faut rééquilibrer les ressources en fonction des informations sur la progression en fonction des statistiques.<br /><br /> **Remarque** ne définissez pas cette stratégie sur `ProgressFeedbackDisabled` , car il est réservé pour une utilisation par le runtime. |`ProgressFeedbackEnabled`|

Chaque planificateur utilise sa propre stratégie lorsqu’il planifie les tâches. Les stratégies qui sont associés à un planificateur n’affectent pas le comportement de n’importe quel autre planificateur. En outre, vous ne pouvez pas modifier la stratégie du planificateur après avoir créé le `Scheduler` objet.

> [!IMPORTANT]
>  Utilisez uniquement les stratégies de planificateur pour contrôler les attributs pour les threads qui crée le runtime. Ne modifiez pas l’affinité de thread ou de la priorité des threads qui sont créés par le runtime, car le risque de provoquer un comportement non défini.

Le runtime crée un planificateur par défaut si vous ne pas créez explicitement un. Si vous souhaitez utiliser le planificateur par défaut dans votre application, mais que vous souhaitez spécifier une stratégie pour que le planificateur à utiliser, appelez le [:: SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) méthode avant de planifier un travail parallèle. Si vous n’appelez pas la `Scheduler::SetDefaultSchedulerPolicy` (méthode), le runtime utilise la stratégie par défaut des valeurs de la table.

Utilisez le [Concurrency::CurrentScheduler :: GetPolicy](reference/currentscheduler-class.md#getpolicy) et [Concurrency::Scheduler :: GetPolicy](reference/scheduler-class.md#getpolicy) méthodes pour récupérer une copie de la stratégie du planificateur. Les valeurs de stratégie que vous recevez à partir de ces méthodes peuvent différer les valeurs de stratégie que vous spécifiez lorsque vous créez le planificateur.

## <a name="example"></a>Exemple

Pour examiner des exemples qui utilisent des stratégies de planificateur spécifiques pour contrôler le comportement du planificateur, consultez [Comment : Spécifier des stratégies de planificateur](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) et [Comment : Créer des Agents qui utilisent des stratégies de planificateur spécifiques](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="see-also"></a>Voir aussi

[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Guide pratique pour spécifier des stratégies de Scheduler](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[Guide pratique pour créer des agents qui utilisent des stratégies spécifiques de Scheduler](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
