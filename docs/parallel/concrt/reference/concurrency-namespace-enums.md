---
title: concurrency, énumérations de l’espace de noms
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::Agents_EventType
- CONCRT/concurrency::Concrt_TraceFlags
- CONCRT/concurrency::CriticalRegionType
- CONCRT/concurrency::PolicyElementKey
- CONCRT/concurrency::SchedulerType
- CONCRT/concurrency::SwitchingProxyState
- CONCRT/concurrency::WinRTInitializationType
- CONCRT/concurrency::join_type
- CONCRT/concurrency::message_status Enumeration
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
ms.openlocfilehash: e3a943ed52ce9653086203713bb98331f809314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372727"
---
# <a name="concurrency-namespace-enums"></a>concurrency, énumérations de l’espace de noms

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType (en)](#criticalregiontype)|[DynamicProgressFeedbackType (en)](#dynamicprogressfeedbacktype)|[PolitiqueElementKey](#policyelementkey)|
|[CalendrierType](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|
|[WinRTInitializationType](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status-enumeration"></a><a name="agent_status"></a>agent_status Énumération

États valides d'un `agent`.

```cpp
enum agent_status;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`agent_canceled`|`agent` annulé.|
|`agent_created`|Le `agent` a été créé, mais pas commencé.|
|`agent_done`|Le `agent` fini sans être annulé.|
|`agent_runnable`|Le `agent` a été commencé, `run` mais pas entré dans sa méthode.|
|`agent_started`|Le `agent` a commencé.|

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [Asynchrone Agents](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Spécifications

**En-tête:** concrt.h

## <a name="agents_eventtype-enumeration"></a><a name="agents_eventtype"></a>Agents_EventType Énumération

Types d'événements qui peuvent être tracés à l'aide des fonctionnalités de traçage offertes par la bibliothèque d'agents.

```cpp
enum Agents_EventType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Un type d’événement qui représente la création d’un objet|
|`AGENTS_EVENT_DESTROY`|Un type d’événement qui représente la suppression d’un objet|
|`AGENTS_EVENT_END`|Un type d’événement qui représente la conclusion d’un certain traitement|
|`AGENTS_EVENT_LINK`|Un type d’événement qui représente la liaison des blocs de messages|
|`AGENTS_EVENT_NAME`|Un type d’événement qui représente le nom d’un objet|
|`AGENTS_EVENT_SCHEDULE`|Un type d’événement qui représente la planification d’un processus|
|`AGENTS_EVENT_START`|Un type d’événement qui représente l’initiation d’un traitement|
|`AGENTS_EVENT_UNLINK`|Un type d’événement qui représente le non-lien des blocs de messages|

### <a name="requirements"></a>Spécifications

**En-tête:** concrt.h

## <a name="concrt_eventtype-enumeration"></a><a name="concrt_eventtype"></a>ConcRT_EventType Énumération

Types d'événements qui peuvent être tracés à l'aide des fonctionnalités de traçage offertes par le runtime d'accès concurrentiel.

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Un type d’événement qui représente l’acte d’une fixation à un planificateur.|
|`CONCRT_EVENT_BLOCK`|Un type d’événement qui représente l’acte d’un blocage de contexte.|
|`CONCRT_EVENT_DETACH`|Un type d’événement qui représente l’acte d’un détachement d’un planificateur.|
|`CONCRT_EVENT_END`|Un type d’événement qui marque le début d’une paire d’événements de départ/fin.|
|`CONCRT_EVENT_GENERIC`|Un type d’événement utilisé pour des événements divers.|
|`CONCRT_EVENT_IDLE`|Un type d’événement qui représente l’acte d’un contexte devenant inactif.|
|`CONCRT_EVENT_START`|Un type d’événement qui marque le début d’une paire d’événements de départ/fin.|
|`CONCRT_EVENT_UNBLOCK`|Un type d’événement qui représente l’acte de débloquer un contexte.|
|`CONCRT_EVENT_YIELD`|Un type d’événement qui représente l’acte d’un contexte qui donne.|

### <a name="requirements"></a>Spécifications

**En-tête:** concrt.h **Namespace:** concordance

## <a name="concrt_traceflags-enumeration"></a><a name="concrt_traceflags"></a>Concrt_TraceFlags Énumération

Indicateurs de suivi des types d'événements.

```cpp
enum Concrt_TraceFlags;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`AgentEventFlag`||
|`AllEventsFlag`||
|`ContextEventFlag`||
|`PPLEventFlag`||
|`ResourceManagerEventFlag`||
|`SchedulerEventFlag`||
|`VirtualProcessorEventFlag`||

### <a name="requirements"></a>Spécifications

**En-tête:** concrt.h

## <a name="criticalregiontype-enumeration"></a><a name="criticalregiontype"></a>Énumération critique De l’énumération de la dumération

Type de région critique dans lequel se trouve un contexte.

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`InsideCriticalRegion`|Indique que le contexte se situe à l’intérieur d’une région critique. À l’intérieur d’une région critique, des suspensions asynchrones sont cachées à l’horaire. Si une telle suspension se produit, le gestionnaire des ressources attendra que le fil devienne runnable et simplement le reprendre au lieu d’invoquer le planificateur à nouveau. Toutes les écluses prises à l’intérieur d’une telle région doivent être prises avec un soin extrême.|
|`InsideHyperCriticalRegion`|Indique que le contexte se trouve à l’intérieur d’une région hyper-critique. À l’intérieur d’une région hyper-critique, les suspensions synchrones et asynchrones sont cachées à l’horaire. Si une telle suspension ou blocage se produit, le gestionnaire des ressources attendra que le fil devienne runnable et simplement le reprendre au lieu d’invoquer le planificateur à nouveau. Les serrures prises à l’intérieur d’une telle région ne doivent jamais être partagées avec le code en cours d’exécution en dehors d’une telle région. Cela entraînera une impasse imprévisible.|
|`OutsideCriticalRegion`|Indique que le contexte se situe en dehors de toute région critique.|

### <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

## <a name="dynamicprogressfeedbacktype-enumeration"></a><a name="dynamicprogressfeedbacktype"></a>Répartition dynamiqueProgressFeedbackType

Utilisé par la stratégie `DynamicProgressFeedback` pour décrire si les ressources du planificateur sont rééquilibrées d'après les informations statistiques collectées auprès du planificateur ou uniquement en fonction des processeurs virtuels qui entrent dans l'état d'inactivité et en sortent via des appels aux méthodes `Activate` et `Deactivate` sur l'interface `IVirtualProcessorRoot`. Pour plus d’informations sur les politiques de planificateur disponibles, voir [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Le planificateur ne recueille pas d’informations sur les progrès. Le rééquilibrage se fait uniquement en fonction du niveau d’abonnement du fil matériel sous-jacent. Pour plus d’informations sur les niveaux d’abonnement, voir [IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).<br /><br /> Cette valeur est réservée à l’utilisation par le temps d’exécution.|
|`ProgressFeedbackEnabled`|Le planificateur recueille des informations sur les progrès et les transmet au gestionnaire des ressources. Le gestionnaire des ressources utilisera ces informations statistiques pour rééquilibrer les ressources au nom du planificateur en plus du niveau d’abonnement du fil matériel sous-jacent. Pour plus d’informations sur les niveaux d’abonnement, voir [IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).|

## <a name="join_type-enumeration"></a><a name="join_type"></a>join_type Énumération

Type d'un bloc de messagerie `join`.

```cpp
enum join_type;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`greedy`|Les `join` blocs de messagerie gourmands acceptent immédiatement un message lors de la propagation. C’est plus efficace, mais a la possibilité de verrouillage en direct, en fonction de la configuration du réseau.|
|`non_greedy`|Les blocs `join` de messagerie non gourmands reportent les messages et essaient de les consommer après que tous sont arrivés. Ceux-ci sont garantis pour fonctionner, mais plus lent.|

### <a name="requirements"></a>Spécifications

**En-tête :** agents.h

## <a name="message_status-enumeration"></a><a name="message_status"></a>message_status Énumération

Réponses valides à une offre d'objet `message` à un bloc.

```cpp
enum message_status;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`accepted`|La cible a accepté le message.|
|`declined`|La cible n’a pas accepté le message.|
|`missed`|La cible a essayé d’accepter le message, mais il n’était plus disponible.|
|`postponed`|La cible a reporté le message.|

### <a name="requirements"></a>Spécifications

**En-tête :** agents.h

## <a name="policyelementkey-enumeration"></a><a name="policyelementkey"></a>Énumération politiqueElementKey

Clés de stratégie qui décrivent certains aspects du comportement du planificateur. Chaque élément de stratégie est décrit par une paire clé-valeur. Pour de plus amples renseignements sur les politiques des planificateurs et leur impact sur les planificateurs, consultez [Task Scheduler](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`ContextPriority`|La priorité de thread système d’exploitation de chaque contexte dans le planificateur. Si cette clé est `INHERIT_THREAD_PRIORITY` définie à la valeur, les contextes du planificateur hériteront de la priorité du thread qui a créé le planificateur.<br /><br /> Valeurs valables : N’importe `SetThreadPriority` quelle des valeurs valides pour la fonction Windows et la valeur spéciale`INHERIT_THREAD_PRIORITY`<br /><br /> Valeur par défaut :`THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|La taille réservée de la pile de chaque contexte dans le planificateur en kilooctets.<br /><br /> Valeurs valables : intégreurs positifs<br /><br /> Valeur par `0`défaut : , indiquant que la valeur par défaut du processus pour la taille de la pile soit utilisée.|
|`DynamicProgressFeedback`|Détermine si les ressources du planificateur seront rééquilibrées en fonction des informations statistiques recueillies auprès du planificateur ou uniquement en fonction du niveau d’abonnement des threads matériels sous-jacents. Pour plus d’informations, voir [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype).<br /><br /> Valeurs valables : `DynamicProgressFeedbackType` Membre de l’énumération, soit `ProgressFeedbackEnabled``ProgressFeedbackDisabled`<br /><br /> Valeur par défaut :`ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Lorsque `SchedulingProtocol` la clé de stratégie `EnhanceScheduleGroupLocality`est définie à la valeur, cela spécifie le nombre maximum de contextes runnables autorisés à être mis en cache par processeur virtuel files d’attente locales. De tels contextes s’exécutent généralement dans l’ordre de dernière en première sortie (LIFO) sur le processeur virtuel qui les a fait devenir runnable. Notez que cette clé de `SchedulingProtocol` stratégie n’a `EnhanceForwardProgress`aucun sens lorsque la clé est définie à la valeur .<br /><br /> Valeurs valables : intégrants non négatifs<br /><br /> Valeur par défaut :`8`|
|`MaxConcurrency`|Le niveau maximum de concurrence souhaité par le planificateur. Le gestionnaire des ressources tentera d’allouer dans un premier temps ces nombreux processeurs virtuels. La valeur spéciale [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) indique que le niveau de concurrence souhaité est le même que le nombre de threads matériels sur la machine. Si la valeur `MinConcurrency` spécifiée est supérieure au nombre de `MaxConcurrency` threads `MaxExecutionResources`matériels `MaxConcurrency` sur la machine et `MinConcurrency`est spécifiée comme , la valeur pour est augmentée pour correspondre à ce qui est fixé pour .<br /><br /> Valeurs valables : intégrants positifs et valeur particulière`MaxExecutionResources`<br /><br /> Valeur par défaut :`MaxExecutionResources`|
|`MaxPolicyElementKey`|La clé maximale de l’élément de politique. Pas une clé d’élément valide.|
|`MinConcurrency`|Le niveau minimum de concurrence qui doit être fourni à l’planificateur par le gestionnaire des ressources. Le nombre de processeurs virtuels attribués à un planificateur ne sera jamais inférieur au minimum. La valeur spéciale [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) indique que le niveau minimum de concurrence est le même que le nombre de threads matériels sur la machine. Si la valeur `MaxConcurrency` spécifiée pour est inférieure au nombre `MinConcurrency` de threads matériels sur la machine et est spécifiée comme `MaxExecutionResources`, la valeur pour est abaissée pour `MinConcurrency` correspondre à ce qui est réglé pour `MaxConcurrency`.<br /><br /> Valeurs valables : intégrants non `MaxExecutionResources`négatifs et valeur spéciale . Notez que pour les polices de planificateurs utilisées pour la `0` construction des planificateurs de l’exécution de concurrency, la valeur est invalide.<br /><br /> Valeur par défaut :`1`|
|`SchedulerKind`|Le type de threads que le planificateur utilisera pour les contextes d’exécution sous-jacents. Pour plus d’informations, voir [SchedulerType](#schedulertype).<br /><br /> Valeurs valables : `SchedulerType` Membre de l’énumération, par exemple,`ThreadScheduler`<br /><br /> Valeur par `ThreadScheduler`défaut : . Cela se traduit par des threads Win32 sur tous les systèmes d’exploitation.|
|`SchedulingProtocol`|Décrit l’algorithme de planification qui sera utilisé par le planificateur. Pour plus d’informations, voir [SchedulingProtocolType](#schedulingprotocoltype).<br /><br /> Valeurs valables : `SchedulingProtocolType` Membre de l’énumération, soit `EnhanceScheduleGroupLocality``EnhanceForwardProgress`<br /><br /> Valeur par défaut :`EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Nombre provisoire de processeurs virtuels par thread matériel. Le facteur de sursubscription cible peut être augmenté par `MaxConcurrency` le gestionnaire de ressources, si nécessaire, pour satisfaire avec les fils matériels sur la machine.<br /><br /> Valeurs valables : intégreurs positifs<br /><br /> Valeur par défaut :`1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Spécifications

**En-tête:** concrt.h

## <a name="schedulertype-enumeration"></a><a name="schedulertype"></a>Énumération de schedulerType

Utilisé par la stratégie `SchedulerKind` pour décrire le type des threads que le planificateur doit utiliser pour les contextes d'exécution sous-jacents. Pour plus d’informations sur les politiques de planificateur disponibles, voir [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulerType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`ThreadScheduler`|Indique une demande explicite de threads Win32 réguliers.|
|`UmsThreadDefault`|Les threads schedulables en mode utilisateur (UMS) ne sont pas pris en charge dans le Concurrency Runtime dans Visual Studio 2013. L’utilisation `UmsThreadDefault` comme `SchedulerType` valeur de la stratégie n’entraînera pas d’erreur. Cependant, un planificateur créé avec cette stratégie par défaut à l’utilisation des threads Win32.|

### <a name="requirements"></a>Spécifications

**En-tête:** concrt.h

## <a name="schedulingprotocoltype-enumeration"></a><a name="schedulingprotocoltype"></a>SchedulingProtocolType Enumeration

Utilisé par la stratégie `SchedulingProtocol` pour décrire l'algorithme de planification utilisé pour le planificateur. Pour plus d’informations sur les politiques de planificateur disponibles, voir [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`EnhanceForwardProgress`|Le planificateur préfère faire du tournoi à la ronde à travers les groupes d’horaire après l’exécution de chaque tâche. Les contextes débloqués sont généralement programmés de la manière du premier en premier (FIFO). Les processeurs virtuels ne cachent pas de contextes débloqués.|
|`EnhanceScheduleGroupLocality`|Le planificateur préfère continuer à travailler sur les tâches au sein du groupe d’horaire actuel avant de passer à un autre groupe d’horaire. Les contextes débloqués sont mis en cache par processeur virtuel et sont généralement programmés de façon dernière en premier (LIFO) par le processeur virtuel qui les a débloqués.|

### <a name="requirements"></a>Spécifications

**En-tête:** concrt.h

## <a name="switchingproxystate-enumeration"></a><a name="switchingproxystate"></a>CommutationProxyState Énumération

Utilisé pour indiquer l'état d'un proxy de thread, quand il exécute un changement de contexte coopératif vers un proxy de thread différent.

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`Blocking`|Indique que le fil d’appel bloque en coopération et doit être exclusivement détenu par l’appelant jusqu’à ce qu’il soit exécuté à nouveau par la suite et qu’il effectue d’autres actions.|
|`Idle`|Indique que le fil d’appel n’est plus nécessaire par le planificateur et qu’il est retourné au gestionnaire des ressources. Le contexte qui a été envoyé n’est plus en mesure d’être utilisé par le gestionnaire des ressources.|
|`Nesting`|Indique que le fil d’appel niche un planificateur d’enfant et est nécessaire par l’appelant, afin de s’attacher à un planificateur différent.|

### <a name="remarks"></a>Notes

Un paramètre `SwitchingProxyState` de type est `IThreadProxy::SwitchTo` transmis à la méthode pour instruire le gestionnaire de ressources comment traiter le proxy de thread qui effectue l’appel.

Pour plus d’informations sur la façon dont ce type est utilisé, voir [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto).

## <a name="task_group_status-enumeration"></a><a name="task_group_status"></a>task_group_status Énumération

Décrit l'état d'exécution d'un objet `task_group` ou `structured_task_group`. Une valeur de ce type est retournée par de nombreuses méthodes qui attendent que les tâches planifiées pour un groupe de tâches se terminent.

```cpp
enum task_group_status;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`canceled`|L'objet `task_group` ou `structured_task_group` a été annulé. Une ou plusieurs tâches n’ont pas pu s’exécuter.|
|`completed`|Les tâches mises en file d’attente dans l’objet `task_group` ou `structured_task_group` sont terminées.|
|`not_complete`|Les tâches mises en file d’attente dans l’objet `task_group` ne sont pas terminées. Notez que cette valeur n'est actuellement pas retournée par le runtime d'accès concurrentiel.|

### <a name="requirements"></a>Spécifications

**En-tête:** pplinterface.h

## <a name="winrtinitializationtype-enumeration"></a><a name="winrtinitializationtype"></a>WinRTInitializationType Enumeration

Utilisé par la stratégie `WinRTInitialization` pour décrire si et comment le Windows Runtime est initialisé sur les threads de planificateur pour une application qui s'exécute sur des systèmes d'exploitation Windows 8 ou versions ultérieures. Pour plus d’informations sur les politiques de planificateur disponibles, voir [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`DoNotInitializeWinRT`|Lorsque l’application est exécutée sur les systèmes d’exploitation avec la version Windows 8 ou plus, les threads dans le planificateur ne sera pas initialiser le Windows Runtime .|
|`InitializeWinRTAsMTA`|Lorsque l’application est exécutée sur les systèmes d’exploitation avec la version Windows 8 ou plus, chaque thread dans le planificateur va initialiser le Windows Runtime et déclarer qu’il fait partie de l’appartement multithreaded.|

## <a name="requirements"></a>Spécifications

**En-tête:** concrt.h

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
