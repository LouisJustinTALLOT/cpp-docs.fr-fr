---
title: énumérations d’espace de noms d’accès concurrentiel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69b11a78d1be76895b9687d1423df74c51fe3d39
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416693"
---
# <a name="concurrency-namespace-enums"></a>énumérations d’espace de noms d’accès concurrentiel

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[PolicyElementKey](#policyelementkey)|
|[SchedulerType](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|
|[WinRTInitializationType](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

##  <a name="agent_status"></a>  agent_status, énumération

États valides d'un `agent`.

```
enum agent_status;
```
### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`agent_canceled`|`agent` a été annulé.|
|`agent_created`|Le `agent` a été créé mais n’a ne pas démarré.|
|`agent_done`|Le `agent` terminé sans avoir été annulé.|
|`agent_runnable`|Le `agent` a été démarré, mais n’avez ne pas entré son `run` (méthode).|
|`agent_started`|Le `agent` a démarré.|

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Agents asynchrones](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

##  <a name="agents_eventtype"></a>  Agents_eventtype, énumération

Types d'événements qui peuvent être tracés à l'aide des fonctionnalités de traçage offertes par la bibliothèque d'agents.

```
enum Agents_EventType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Un type d’événement qui représente la création d’un objet|
|`AGENTS_EVENT_DESTROY`|Un type d’événement qui représente la suppression d’un objet|
|`AGENTS_EVENT_END`|Traitement d’un type d’événement qui représente la fin de certaines|
|`AGENTS_EVENT_LINK`|Un type d’événement qui représente la liaison des blocs de messages|
|`AGENTS_EVENT_NAME`|Un type d’événement qui représente le nom d’un objet|
|`AGENTS_EVENT_SCHEDULE`|Un type d’événement qui représente la planification d’un processus|
|`AGENTS_EVENT_START`|Traitement d’un type d’événement qui représente l’ouverture de certains|
|`AGENTS_EVENT_UNLINK`|Un type d’événement qui représente la dissociation de blocs de messages|

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

##  <a name="concrt_eventtype"></a>  ConcRT_EventType, énumération

Types d'événements qui peuvent être tracés à l'aide des fonctionnalités de traçage offertes par le runtime d'accès concurrentiel.

```
enum ConcRT_EventType;
```
### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Un type d’événement qui représente l’opération d’attachement à un planificateur.|
|`CONCRT_EVENT_BLOCK`|Un type d’événement qui représente l’action consistant à un blocage de contexte.|
|`CONCRT_EVENT_DETACH`|Un type d’événement qui représente l’opération de détachement d’un planificateur.|
|`CONCRT_EVENT_END`|Un type d’événement qui marque le début d’une paire d’événements de début et de fin.|
|`CONCRT_EVENT_GENERIC`|Un type d’événement utilisé pour divers événements.|
|`CONCRT_EVENT_IDLE`|Un type d’événement qui représente l’opération d’un contexte de devenir inactives.|
|`CONCRT_EVENT_START`|Un type d’événement qui marque le début d’une paire d’événements de début et de fin.|
|`CONCRT_EVENT_UNBLOCK`|Un type d’événement qui représente l’opération de déverrouillage d’un contexte.|
|`CONCRT_EVENT_YIELD`|Un type d’événement qui représente l’action consistant à un contexte produisant.|

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h **Namespace :** accès concurrentiel

##  <a name="concrt_traceflags"></a>  Concrt_traceflags, énumération

Indicateurs de suivi des types d'événements.

```
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

**En-tête :** concrt.h

##  <a name="criticalregiontype"></a>  CriticalRegionType, énumération

Type de région critique dans lequel se trouve un contexte.

```
enum CriticalRegionType;
```
### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`InsideCriticalRegion`|Indique que le contexte est à l’intérieur d’une zone critique. À l’intérieur d’une zone critique, asynchrones suspensions sont masquées dans le planificateur. Une telle suspension opportun, le Gestionnaire de ressources attendra que le thread soit exécutable, et il suffit de le reprendre au lieu d’appeler de nouveau le planificateur. Les verrous appliqués dans une région de ce type doivent être prises avec une extrême prudence.|
|`InsideHyperCriticalRegion`|Indique que le contexte est à l’intérieur d’une zone hyper critique. À l’intérieur d’une zone hyper critique, suspensions synchrones et asynchrones sont masquées dans le planificateur. Si un tel arrêt ou blocage se produisent, le Gestionnaire de ressources attendra que le thread soit exécutable, et il suffit de le reprendre au lieu d’appeler de nouveau le planificateur. Les verrous d’une région de ce type ne doivent jamais être partagés avec du code exécuté en dehors de ces régions. Cela provoque un interblocage imprévisible.|
|`OutsideCriticalRegion`|Indique que le contexte est en dehors de n’importe quelle région critique.|

### <a name="requirements"></a>Configuration requise

**En-tête :** concrtrm.h

##  <a name="dynamicprogressfeedbacktype"></a>  DynamicProgressFeedbackType, énumération

Utilisé par la stratégie `DynamicProgressFeedback` pour décrire si les ressources du planificateur sont rééquilibrées d'après les informations statistiques collectées auprès du planificateur ou uniquement en fonction des processeurs virtuels qui entrent dans l'état d'inactivité et en sortent via des appels aux méthodes `Activate` et `Deactivate` sur l'interface `IVirtualProcessorRoot`. Pour plus d’informations sur les stratégies de planificateur disponibles, consultez [PolicyElementKey](concurrency-namespace-enums.md).

```
enum DynamicProgressFeedbackType;
```
### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Le planificateur ne collecte pas les informations de progression. Rééquilibrage est basé uniquement sur le niveau d’abonnement du thread matériel sous-jacent. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).<br /><br /> Cette valeur est réservée pour une utilisation par le runtime.|
|`ProgressFeedbackEnabled`|Le planificateur rassemble des informations de progression et les transmet au Gestionnaire de ressources. Le Gestionnaire de ressources utilisera ces informations statistiques pour rééquilibrer les ressources pour le compte du planificateur en plus du niveau d’abonnement du thread matériel sous-jacent. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).|
##  <a name="join_type"></a>  join_type, énumération

Type d'un bloc de messagerie `join`.

```
enum join_type;
```
### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`greedy`|Gourmand `join` les blocs de messagerie acceptent immédiatement un message lors de la propagation. Cela est plus efficace, mais avec le risque de verrou vivant, selon la configuration du réseau.|
|`non_greedy`|Non gourmand `join` les blocs de messagerie reporter des messages et essaye de les consommer après leur arrivée. Ceux-ci sont assurés de fonctionner, mais plus lentement.|

### <a name="requirements"></a>Configuration requise

**En-tête :** agents.h

##  <a name="message_status"></a>  message_status, énumération

Réponses valides à une offre d'objet `message` à un bloc.

```
enum message_status;
```
### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`accepted`|La cible a accepté le message.|
|`declined`|La cible n’a pas accepté le message.|
|`missed`|La cible a essayé d’accepter le message, mais il n’était plus disponible.|
|`postponed`|La cible a différé le message.|

### <a name="requirements"></a>Configuration requise

**En-tête :** agents.h

##  <a name="policyelementkey"></a>  PolicyElementKey, énumération

Clés de stratégie qui décrivent certains aspects du comportement du planificateur. Chaque élément de stratégie est décrit par une paire clé-valeur. Pour plus d’informations sur les stratégies de planificateur et leur impact sur les planificateurs, consultez [Planificateur de tâches](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```
enum PolicyElementKey;
```
### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`ContextPriority`|La priorité de thread de système d’exploitation de chaque contexte dans le planificateur. Si cette clé est définie à la valeur `INHERIT_THREAD_PRIORITY` les contextes dans le planificateur hériteront de la priorité du thread qui a créé le planificateur.<br /><br /> Valeurs valides : les valeurs valides pour le Windows `SetThreadPriority` fonction et la valeur spéciale `INHERIT_THREAD_PRIORITY`<br /><br /> Valeur par défaut : `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|La taille de pile réservée de chaque contexte dans le planificateur en kilo-octets.<br /><br /> Valeurs valides : entiers positifs<br /><br /> Valeur par défaut : `0`, indiquant que la valeur du processus par défaut pour la taille de la pile être utilisé.|
|`DynamicProgressFeedback`|Détermine si les ressources pour le planificateur sont rééquilibrées d’après les informations statistiques recueillies auprès du planificateur ou uniquement en fonction du niveau d’abonnement des threads matériels sous-jacents. Pour plus d’informations, consultez [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype).<br /><br /> Valeurs valides : un membre de la `DynamicProgressFeedbackType` énumération, soit `ProgressFeedbackEnabled` ou `ProgressFeedbackDisabled`<br /><br /> Valeur par défaut : `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Lorsque le `SchedulingProtocol` clé de la stratégie est définie sur la valeur `EnhanceScheduleGroupLocality`, cela spécifie le nombre maximal de contextes exécutables pouvant être mis en cache par les files d’attente locales du processeur virtuel. Ces contextes seront exécutent généralement par ordre dernier-in-first-out (LIFO) sur le processeur virtuel qui les a soit exécutable. Notez que cette clé de stratégie n’a aucune signification lorsque la `SchedulingProtocol` clé est définie à la valeur `EnhanceForwardProgress`.<br /><br /> Valeurs valides : entiers Non négatifs<br /><br /> Valeur par défaut : `8`|
|`MaxConcurrency`|L’accès concurrentiel maximal niveau désiré par le planificateur. Le Gestionnaire de ressources tentera d’initialement allouer ce nombre de processeurs virtuels. La valeur spéciale [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) indique que le niveau d’accès concurrentiel souhaité est identique au nombre de threads matériels sur l’ordinateur. Si la valeur spécifiée pour `MinConcurrency` est supérieur au nombre de threads matériels sur l’ordinateur et `MaxConcurrency` est spécifié en tant que `MaxExecutionResources`, la valeur de `MaxConcurrency` est déclenché pour correspondre à celle définie pour `MinConcurrency`.<br /><br /> Valeurs valides : entiers positifs et la valeur spéciale `MaxExecutionResources`<br /><br /> Valeur par défaut : `MaxExecutionResources`|
|`MaxPolicyElementKey`|La clé d’élément maximale des stratégies. Clé d’élément valide.|
|`MinConcurrency`|Le niveau de concurrence minimal qui doit être fourni au planificateur par le Gestionnaire de ressources. Le nombre de processeurs virtuels assigné à un planificateur n’ira jamais inférieur au minimum. La valeur spéciale [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) indique que le niveau de concurrence minimal est identique au nombre de threads matériels sur l’ordinateur. Si la valeur spécifiée pour `MaxConcurrency` est inférieur au nombre de threads matériels sur l’ordinateur et `MinConcurrency` est spécifié en tant que `MaxExecutionResources`, la valeur de `MinConcurrency` est réduite pour correspondre à celle définie pour `MaxConcurrency`.<br /><br /> Valeurs valides : entiers Non négatifs et la valeur spéciale `MaxExecutionResources`. Notez que pour les stratégies de planificateur utilisés pour la construction de planificateurs de Runtime d’accès concurrentiel, la valeur `0` n’est pas valide.<br /><br /> Valeur par défaut : `1`|
|`SchedulerKind`|Le type de threads que le planificateur utilisera pour les contextes d’exécution sous-jacents. Pour plus d’informations, consultez [SchedulerType](#schedulertype).<br /><br /> Valeurs valides : un membre de la `SchedulerType` énumération, par exemple, `ThreadScheduler`<br /><br /> Valeur par défaut : `ThreadScheduler`. Cela se traduit par les threads Win32 sur tous les systèmes d’exploitation.|
|`SchedulingProtocol`|Décrit l’algorithme de planification qui sera utilisé par le planificateur. Pour plus d’informations, consultez [SchedulingProtocolType](#schedulingprotocoltype).<br /><br /> Valeurs valides : un membre de la `SchedulingProtocolType` énumération, soit `EnhanceScheduleGroupLocality` ou `EnhanceForwardProgress`<br /><br /> Valeur par défaut : `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Nombre provisoire de processeurs virtuels par thread matériel. Le facteur de surabonnement cible peut être augmenté par le Gestionnaire de ressources, si nécessaire, pour satisfaire `MaxConcurrency` avec les threads matériels sur l’ordinateur.<br /><br /> Valeurs valides : entiers positifs<br /><br /> Valeur par défaut : `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

##  <a name="schedulertype"></a>  SchedulerType, énumération

Utilisé par la stratégie `SchedulerKind` pour décrire le type des threads que le planificateur doit utiliser pour les contextes d'exécution sous-jacents. Pour plus d’informations sur les stratégies de planificateur disponibles, consultez [PolicyElementKey](concurrency-namespace-enums.md).

```
enum SchedulerType;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`ThreadScheduler`|Indique une requête explicite de threads Win32 normaux.|
|`UmsThreadDefault`|En mode utilisateur planifiables threads UMS ne sont pas pris en charge dans le Runtime d’accès concurrentiel dans Visual Studio 2013. À l’aide de `UmsThreadDefault` en tant que valeur pour le `SchedulerType` stratégie n’entraîne pas une erreur. Toutefois, un planificateur créé avec cette stratégie par défaut à l’aide de threads Win32.|

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

##  <a name="schedulingprotocoltype"></a>  SchedulingProtocolType, énumération

Utilisé par la stratégie `SchedulingProtocol` pour décrire l'algorithme de planification utilisé pour le planificateur. Pour plus d’informations sur les stratégies de planificateur disponibles, consultez [PolicyElementKey](concurrency-namespace-enums.md).

```
enum SchedulingProtocolType;
```
### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`EnhanceForwardProgress`|Le planificateur préfère alterner les groupes de planification après l’exécution de chaque tâche. Contextes non bloqués sont généralement planifiées de manière in-first-out (FIFO). Processeurs virtuels ne mettent pas en cache les contextes non bloqués.|
|`EnhanceScheduleGroupLocality`|Le planificateur préfère continuer à travailler sur les tâches au sein du groupe de planification actuel avant de passer à un autre groupe de planification. Contextes non bloqués sont mis en cache par processeur virtuel et sont généralement planifiées de manière last-in-first-out (LIFO) par le processeur virtuel qui les débloqué.|

### <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

##  <a name="switchingproxystate"></a>  SwitchingProxyState, énumération

Utilisé pour indiquer l'état d'un proxy de thread, quand il exécute un changement de contexte coopératif vers un proxy de thread différent.

```
enum SwitchingProxyState;
```
### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`Blocking`|Indique que le thread appelant effectue un blocage coopératif et doit être possédé exclusivement par l’appelant jusqu'à ce que par la suite en cours d’exécution à nouveau et effectue d’autres actions.|
|`Idle`|Indique que le thread appelant n’est plus nécessaire par le planificateur et est retourné au Gestionnaire de ressources. Le contexte a été distribué n’est plus en mesure d’être utilisées par le Gestionnaire de ressources.|
|`Nesting`|Indique que le thread appelant est de l’imbrication d’un planificateur enfant et qu’il est nécessaire par l’appelant, pour pouvoir attacher à un autre planificateur.|

### <a name="remarks"></a>Notes

Un paramètre de type `SwitchingProxyState` est transmise à la méthode `IThreadProxy::SwitchTo` pour indiquer au Gestionnaire de ressources comment traiter le proxy de thread qui effectue l’appel.

Pour plus d’informations sur l’utilisation de ce type, consultez [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto).

##  <a name="task_group_status"></a>  task_group_status, énumération

Décrit l'état d'exécution d'un objet `task_group` ou `structured_task_group`. Une valeur de ce type est retournée par de nombreuses méthodes qui attendent que les tâches planifiées pour un groupe de tâches se terminent.

```
enum task_group_status;
```
### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`canceled`|L'objet `task_group` ou `structured_task_group` a été annulé. Une ou plusieurs tâches n’ont pas pu s’exécuter.|
|`completed`|Les tâches mises en file d'attente dans l'objet `task_group` ou `structured_task_group` sont terminées.|
|`not_complete`|Les tâches mises en file d'attente dans l'objet `task_group` ne sont pas terminées. Notez que cette valeur n'est actuellement pas retournée par le runtime d'accès concurrentiel.|

### <a name="requirements"></a>Configuration requise

**En-tête :** pplinterface.h

##  <a name="winrtinitializationtype"></a>  Winrtinitializationtype, énumération

Utilisé par la stratégie `WinRTInitialization` pour décrire si et comment le Windows Runtime est initialisé sur les threads de planificateur pour une application qui s'exécute sur des systèmes d'exploitation Windows 8 ou versions ultérieures. Pour plus d’informations sur les stratégies de planificateur disponibles, consultez [PolicyElementKey](concurrency-namespace-enums.md).

```
enum WinRTInitializationType;
```
### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`DoNotInitializeWinRT`|Lorsque l’application est exécutée sur les systèmes d’exploitation avec la version Windows 8 ou une version ultérieure, les threads dans le planificateur ne sera pas initialiser le Runtime de Windows.|
|`InitializeWinRTAsMTA`|Lorsque l’application est exécutée sur les systèmes d’exploitation avec la version Windows 8 ou une version ultérieure, chaque thread dans le planificateur s’initialiser le Runtime Windows et de le déclarer qu’il fait partie de la cloison multithread.|

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
