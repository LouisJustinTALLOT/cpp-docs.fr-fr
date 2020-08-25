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
ms.openlocfilehash: 8b9aec0a3464b921ca80f731ac4a3c26e72ef34e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832241"
---
# <a name="concurrency-namespace-enums"></a>concurrency, énumérations de l’espace de noms

:::row:::
   :::column span="":::
      [`agent_status`](#agent_status)\
      [`Agents_EventType`](#agents_eventtype)\
      [`ConcRT_EventType`](#concrt_eventtype)\
      [`Concrt_TraceFlags`](#concrt_traceflags)\
      [`CriticalRegionType`](#criticalregiontype)
   :::column-end:::
   :::column span="":::
      [`DynamicProgressFeedbackType`](#dynamicprogressfeedbacktype)\
      [`join_type`](#join_type)\
      [`message_status`](#message_status)\
      [`PolicyElementKey`](#policyelementkey)\
      [`SchedulerType`](#schedulertype)
   :::column-end:::
   :::column span="":::
      [`SchedulingProtocolType`](#schedulingprotocoltype)\
      [`SwitchingProxyState`](#switchingproxystate)\
      [`task_group_status`](#task_group_status)\
      [`WinRTInitializationType`](#winrtinitializationtype)
   :::column-end:::
:::row-end:::

## <a name="agent_status-enumeration"></a><a name="agent_status"></a> Énumération agent_status

États valides d'un `agent`.

```cpp
enum agent_status;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`agent_canceled`|`agent` a été annulé.|
|`agent_created`|`agent`A été créé mais n’a pas démarré.|
|`agent_done`|`agent`Terminé sans être annulé.|
|`agent_runnable`|`agent`A été démarré, mais n’est pas entré dans sa `run` méthode.|
|`agent_started`|`agent`A démarré.|

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [agents asynchrones](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt. h

## <a name="agents_eventtype-enumeration"></a><a name="agents_eventtype"></a> Énumération Agents_EventType

Types d'événements qui peuvent être tracés à l'aide des fonctionnalités de traçage offertes par la bibliothèque d'agents.

```cpp
enum Agents_EventType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Type d’événement qui représente la création d’un objet|
|`AGENTS_EVENT_DESTROY`|Type d’événement qui représente la suppression d’un objet|
|`AGENTS_EVENT_END`|Type d’événement qui représente la conclusion d’un traitement|
|`AGENTS_EVENT_LINK`|Type d’événement qui représente la liaison des blocs de messages|
|`AGENTS_EVENT_NAME`|Type d’événement qui représente le nom d’un objet|
|`AGENTS_EVENT_SCHEDULE`|Type d’événement qui représente la planification d’un processus|
|`AGENTS_EVENT_START`|Type d’événement qui représente l’initiation d’un traitement|
|`AGENTS_EVENT_UNLINK`|Type d’événement qui représente la dissociation des blocs de messages|

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt. h

## <a name="concrt_eventtype-enumeration"></a><a name="concrt_eventtype"></a> Énumération ConcRT_EventType

Types d'événements qui peuvent être tracés à l'aide des fonctionnalités de traçage offertes par le runtime d'accès concurrentiel.

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Type d’événement qui représente l’acte d’un attachement à un planificateur.|
|`CONCRT_EVENT_BLOCK`|Type d’événement qui représente l’acte d’un blocage de contexte.|
|`CONCRT_EVENT_DETACH`|Type d’événement qui représente l’acte d’un détachement d’un planificateur.|
|`CONCRT_EVENT_END`|Type d’événement qui marque le début d’une paire d’événements de début/fin.|
|`CONCRT_EVENT_GENERIC`|Type d’événement utilisé pour les divers événements.|
|`CONCRT_EVENT_IDLE`|Type d’événement qui représente l’action d’un contexte qui devient inactif.|
|`CONCRT_EVENT_START`|Type d’événement qui marque le début d’une paire d’événements de début/fin.|
|`CONCRT_EVENT_UNBLOCK`|Type d’événement qui représente l’acte de déblocage d’un contexte.|
|`CONCRT_EVENT_YIELD`|Type d’événement qui représente l’action d’un contexte produisant.|

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt. h **espace de noms :** accès concurrentiel

## <a name="concrt_traceflags-enumeration"></a><a name="concrt_traceflags"></a> Énumération Concrt_TraceFlags

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

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt. h

## <a name="criticalregiontype-enumeration"></a><a name="criticalregiontype"></a> Énumération CriticalRegionType,

Type de région critique dans lequel se trouve un contexte.

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`InsideCriticalRegion`|Indique que le contexte se trouve à l’intérieur d’une zone critique. Dans une région critique, les suspensions asynchrones sont masquées dans le planificateur. Si une telle suspension se produit, les Gestionnaire des ressources attendent que le thread devienne exécutable et le reprennent simplement au lieu d’appeler à nouveau le planificateur. Tous les verrous effectués dans une telle région doivent être pris en compte avec une extrême prudence.|
|`InsideHyperCriticalRegion`|Indique que le contexte se trouve à l’intérieur d’une région hyper-critique. Dans une région hyper-critique, les suspensions synchrones et asynchrones sont masquées dans le planificateur. En cas de suspension ou de blocage, le gestionnaire de ressources attend que le thread devienne exécutable et le reprenne simplement au lieu d’appeler à nouveau le planificateur. Les verrous effectués dans une telle région ne doivent jamais être partagés avec du code qui s’exécute en dehors d’une telle région. Cela entraîne un blocage imprévisible.|
|`OutsideCriticalRegion`|Indique que le contexte se trouve en dehors de toute région critique.|

### <a name="requirements"></a>Configuration requise

**En-tête :** concrtrm. h

## <a name="dynamicprogressfeedbacktype-enumeration"></a><a name="dynamicprogressfeedbacktype"></a> Énumération DynamicProgressFeedbackType,

Utilisé par la stratégie `DynamicProgressFeedback` pour décrire si les ressources du planificateur sont rééquilibrées d'après les informations statistiques collectées auprès du planificateur ou uniquement en fonction des processeurs virtuels qui entrent dans l'état d'inactivité et en sortent via des appels aux méthodes `Activate` et `Deactivate` sur l'interface `IVirtualProcessorRoot`. Pour plus d’informations sur les stratégies de planificateur disponibles, consultez [PolicyElementKey,](concurrency-namespace-enums.md).

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Le planificateur ne collecte pas d’informations de progression. Le rééquilibrage est effectué uniquement en fonction du niveau d’abonnement du thread matériel sous-jacent. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource :: CurrentSubscriptionLevel](IExecutionResource-structure.md).<br /><br /> Cette valeur est réservée à une utilisation par le Runtime.|
|`ProgressFeedbackEnabled`|Le planificateur recueille les informations de progression et les transmet au gestionnaire des ressources. Le gestionnaire des ressources utilisera ces informations statistiques pour rééquilibrer les ressources pour le compte du planificateur en plus du niveau d’abonnement du thread matériel sous-jacent. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource :: CurrentSubscriptionLevel](IExecutionResource-structure.md).|

## <a name="join_type-enumeration"></a><a name="join_type"></a> Énumération join_type

Type d'un bloc de messagerie `join`.

```cpp
enum join_type;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`greedy`|Les `join` blocs de messagerie gourmands acceptent immédiatement un message lors de la propagation. Cela est plus efficace, mais il est possible de verrouiller en direct, en fonction de la configuration du réseau.|
|`non_greedy`|Les blocs de messagerie non gourmands `join` ajournent les messages et les essaient et les consomment après leur arrivée. Ces opérations sont garanties, mais plus lentes.|

### <a name="requirements"></a>Configuration requise

**En-tête :** agents.h

## <a name="message_status-enumeration"></a><a name="message_status"></a> Énumération message_status

Réponses valides à une offre d'objet `message` à un bloc.

```cpp
enum message_status;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`accepted`|La cible a accepté le message.|
|`declined`|La cible n’a pas accepté le message.|
|`missed`|La cible a tenté d’accepter le message, mais elle n’était plus disponible.|
|`postponed`|La cible a différé le message.|

### <a name="requirements"></a>Configuration requise

**En-tête :** agents.h

## <a name="policyelementkey-enumeration"></a><a name="policyelementkey"></a> Énumération PolicyElementKey,

Clés de stratégie qui décrivent certains aspects du comportement du planificateur. Chaque élément de stratégie est décrit par une paire clé-valeur. Pour plus d’informations sur les stratégies de planificateur et leur impact sur les planificateurs, consultez [Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`ContextPriority`|Priorité de thread de système d’exploitation de chaque contexte dans le planificateur. Si cette clé est définie sur la valeur, `INHERIT_THREAD_PRIORITY` les contextes du planificateur hériteront de la priorité du thread qui a créé le planificateur.<br /><br /> Valeurs valides : l’une des valeurs valides pour la `SetThreadPriority` fonction Windows et la valeur spéciale `INHERIT_THREAD_PRIORITY`<br /><br /> Valeur par défaut : `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|Taille de pile réservée de chaque contexte dans le planificateur, en kilo-octets.<br /><br /> Valeurs valides : entiers positifs<br /><br /> Valeur par défaut : `0` , indiquant que la valeur par défaut du processus pour la taille de la pile doit être utilisée.|
|`DynamicProgressFeedback`|Détermine si les ressources pour le planificateur sont rééquilibrées en fonction des informations statistiques collectées à partir du planificateur ou uniquement en fonction du niveau d’abonnement des threads matériels sous-jacents. Pour plus d’informations, consultez [DynamicProgressFeedbackType,](#dynamicprogressfeedbacktype).<br /><br /> Valeurs valides : un membre de l' `DynamicProgressFeedbackType` énumération, `ProgressFeedbackEnabled` ou `ProgressFeedbackDisabled`<br /><br /> Valeur par défaut : `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Lorsque la `SchedulingProtocol` clé de stratégie est définie sur la valeur `EnhanceScheduleGroupLocality` , cela spécifie le nombre maximal de contextes exécutables autorisés à être mis en cache dans par les files d’attente locales du processeur virtuel. Ces contextes sont généralement exécutés dans l’ordre LIFO (dernier entré, premier sorti) sur le processeur virtuel qui les a entraînés à devenir exécutables. Notez que cette clé de stratégie n’a aucune signification lorsque la `SchedulingProtocol` clé est définie sur la valeur `EnhanceForwardProgress` .<br /><br /> Valeurs valides : entiers non négatifs<br /><br /> Valeur par défaut : `8`|
|`MaxConcurrency`|Niveau de concurrence maximal souhaité par le planificateur. Le gestionnaire de ressources essaiera d’allouer initialement ce nombre de processeurs virtuels. La valeur spéciale [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) indique que le niveau de concurrence souhaité est le même que le nombre de threads matériels sur l’ordinateur. Si la valeur spécifiée pour `MinConcurrency` est supérieure au nombre de threads matériels sur l’ordinateur et `MaxConcurrency` est spécifiée en tant que `MaxExecutionResources` , la valeur de `MaxConcurrency` est déclenchée pour correspondre à ce qui est défini pour `MinConcurrency` .<br /><br /> Valeurs valides : entiers positifs et la valeur spéciale `MaxExecutionResources`<br /><br /> Valeur par défaut : `MaxExecutionResources`|
|`MaxPolicyElementKey`|Clé d’élément de stratégie maximale. N’est pas une clé d’élément valide.|
|`MinConcurrency`|Niveau de concurrence minimal qui doit être fourni au planificateur par le gestionnaire des ressources. Le nombre de processeurs virtuels affectés à un planificateur ne passera jamais au-dessous de la valeur minimale. La valeur spéciale [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) indique que le niveau de concurrence minimal est le même que le nombre de threads matériels sur l’ordinateur. Si la valeur spécifiée pour `MaxConcurrency` est inférieure au nombre de threads matériels sur l’ordinateur et `MinConcurrency` est spécifiée en tant que `MaxExecutionResources` , la valeur de `MinConcurrency` est abaissée pour correspondre à ce qui est défini pour `MaxConcurrency` .<br /><br /> Valeurs valides : entiers non négatifs et la valeur spéciale `MaxExecutionResources` . Notez que pour les stratégies de planificateur utilisées pour la construction de runtime d’accès concurrentiel planificateurs, la valeur `0` n’est pas valide.<br /><br /> Valeur par défaut : `1`|
|`SchedulerKind`|Type de threads que le planificateur utilisera pour les contextes d’exécution sous-jacents. Pour plus d’informations, consultez [SchedulerType,](#schedulertype).<br /><br /> Valeurs valides : un membre de l' `SchedulerType` énumération, par exemple, `ThreadScheduler`<br /><br /> Valeur par défaut : `ThreadScheduler` . Cela se traduit par des threads Win32 sur tous les systèmes d’exploitation.|
|`SchedulingProtocol`|Décrit l’algorithme de planification qui sera utilisé par le planificateur. Pour plus d’informations, consultez [SchedulingProtocolType,](#schedulingprotocoltype).<br /><br /> Valeurs valides : un membre de l' `SchedulingProtocolType` énumération, `EnhanceScheduleGroupLocality` ou `EnhanceForwardProgress`<br /><br /> Valeur par défaut : `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Nombre provisoire de processeurs virtuels par thread matériel. Le facteur de surabonnement cible peut être augmenté par le Gestionnaire des ressources, si nécessaire, pour satisfaire `MaxConcurrency` les threads matériels sur l’ordinateur.<br /><br /> Valeurs valides : entiers positifs<br /><br /> Valeur par défaut : `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt. h

## <a name="schedulertype-enumeration"></a><a name="schedulertype"></a> Énumération SchedulerType,

Utilisé par la stratégie `SchedulerKind` pour décrire le type des threads que le planificateur doit utiliser pour les contextes d'exécution sous-jacents. Pour plus d’informations sur les stratégies de planificateur disponibles, consultez [PolicyElementKey,](concurrency-namespace-enums.md).

```cpp
enum SchedulerType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`ThreadScheduler`|Indique une demande explicite de threads Win32 normaux.|
|`UmsThreadDefault`|Les threads UMS (user-mode) ne sont pas pris en charge dans le runtime d’accès concurrentiel dans Visual Studio 2013. L’utilisation de `UmsThreadDefault` comme valeur pour la `SchedulerType` stratégie ne génère pas d’erreur. Toutefois, un planificateur créé avec cette stratégie utilisera par défaut les threads Win32.|

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt. h

## <a name="schedulingprotocoltype-enumeration"></a><a name="schedulingprotocoltype"></a> Énumération SchedulingProtocolType,

Utilisé par la stratégie `SchedulingProtocol` pour décrire l'algorithme de planification utilisé pour le planificateur. Pour plus d’informations sur les stratégies de planificateur disponibles, consultez [PolicyElementKey,](concurrency-namespace-enums.md).

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`EnhanceForwardProgress`|Le planificateur préfère effectuer un tourniquet (Round Robin) à travers les groupes de planification après l’exécution de chaque tâche. Les contextes débloqués sont généralement planifiés dans un mode FIFO (premier entré, premier sorti). Les processeurs virtuels ne cachent pas de contextes débloqués.|
|`EnhanceScheduleGroupLocality`|Le planificateur préfère continuer à travailler sur les tâches du groupe de planification actuel avant de passer à un autre groupe de planification. Les contextes débloqués sont mis en cache par processeur virtuel et sont généralement planifiés selon un mode dernier entré, premier sorti (LIFO) par le processeur virtuel qui les a débloqués.|

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt. h

## <a name="switchingproxystate-enumeration"></a><a name="switchingproxystate"></a> Énumération SwitchingProxyState

Utilisé pour indiquer l'état d'un proxy de thread, quand il exécute un changement de contexte coopératif vers un proxy de thread différent.

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`Blocking`|Indique que le thread appelant se bloque de façon coopérative et qu’il doit appartenir exclusivement à l’appelant jusqu’à ce qu’il s’exécute à nouveau et qu’il effectue une autre action.|
|`Idle`|Indique que le thread appelant n’est plus requis par le planificateur et est retourné au Gestionnaire des ressources. Le contexte qui était en cours de distribution ne peut plus être utilisé par le Gestionnaire des ressources.|
|`Nesting`|Indique que le thread appelant imbrique un planificateur enfant et qu’il est requis par l’appelant, afin de s’attacher à un planificateur différent.|

### <a name="remarks"></a>Notes

Un paramètre de type `SwitchingProxyState` est passé à la méthode `IThreadProxy::SwitchTo` pour indiquer au gestionnaire des ressources comment traiter le proxy de thread qui effectue l’appel.

Pour plus d’informations sur l’utilisation de ce type, consultez [IThreadProxy :: SwitchTo](ithreadproxy-structure.md#switchto).

## <a name="task_group_status-enumeration"></a><a name="task_group_status"></a> Énumération task_group_status

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

### <a name="requirements"></a>Configuration requise

**En-tête :** pplinterface. h

## <a name="winrtinitializationtype-enumeration"></a><a name="winrtinitializationtype"></a> Énumération Winrtinitializationtype,

Utilisé par la stratégie `WinRTInitialization` pour décrire si et comment le Windows Runtime est initialisé sur les threads de planificateur pour une application qui s'exécute sur des systèmes d'exploitation Windows 8 ou versions ultérieures. Pour plus d’informations sur les stratégies de planificateur disponibles, consultez [PolicyElementKey,](concurrency-namespace-enums.md).

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`DoNotInitializeWinRT`|Lorsque l’application est exécutée sur des systèmes d’exploitation avec la version Windows 8 ou une version ultérieure, les threads dans le planificateur n’initialisent pas le Windows Runtime.|
|`InitializeWinRTAsMTA`|Lorsque l’application est exécutée sur des systèmes d’exploitation dont la version est Windows 8 ou une version ultérieure, chaque thread dans le planificateur Initialise l’Windows Runtime et déclare qu’il fait partie du cloisonnement multithread.|

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt. h

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
