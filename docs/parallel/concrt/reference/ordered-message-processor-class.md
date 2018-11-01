---
title: ordered_message_processor, classe
ms.date: 11/04/2016
f1_keywords:
- ordered_message_processor
- AGENTS/concurrency::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::async_send
- AGENTS/concurrency::ordered_message_processor::initialize
- AGENTS/concurrency::ordered_message_processor::initialize_batched_processing
- AGENTS/concurrency::ordered_message_processor::sync_send
- AGENTS/concurrency::ordered_message_processor::wait
- AGENTS/concurrency::ordered_message_processor::process_incoming_message
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
ms.openlocfilehash: c6e09ff862f0725cc508e3e390dbfa3cc12f7daa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545962"
---
# <a name="orderedmessageprocessor-class"></a>ordered_message_processor, classe

Un `ordered_message_processor` est un `message_processor` qui permet aux blocs de messages de traiter les messages dans l'ordre de leur réception.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ordered_message_processor : public message_processor<T>;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de charge utile des messages traités par le processeur.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`type`|Alias de type pour `T`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[ordered_message_processor](#ctor)|Construit un objet `ordered_message_processor`.|
|[~ ordered_message_processor, destructeur](#dtor)|Détruit le `ordered_message_processor` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[async_send](#async_send)|Les files d’attente des messages et démarre une tâche de traitement, si cela n’a pas déjà été fait de façon asynchrone. (Substitue [message_processor::async_send](message-processor-class.md#async_send).)|
|[initialiser](#initialize)|Initialise le `ordered_message_processor` objet avec le groupe de fonction, le planificateur et planification de rappel appropriées.|
|[initialize_batched_processing](#initialize_batched_processing)|Initialiser le traitement des messages par lot|
|[sync_send](#sync_send)|Mode synchrone les files d’attente des messages et démarre une tâche de traitement, si cela n’a pas déjà été fait. (Substitue [message_processor::sync_send](message-processor-class.md#sync_send).)|
|[attente](#wait)|Attente de rotation spécifique au processeur utilisée dans les destructeurs de blocs de messages pour vous assurer que toutes les tâches de traitement asynchrone ont le temps se termine avant de détruire le bloc. (Substitue [message_processor::wait](message-processor-class.md#wait).)|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|La fonction de traitement qui est appelée de façon asynchrone. Il enlève les messages et commence à les traiter. (Substitue [message_processor::process_incoming_message](message-processor-class.md#process_incoming_message).)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[message_processor](message-processor-class.md)

`ordered_message_processor`

## <a name="requirements"></a>Configuration requise

**En-tête :** agents.h

**Espace de noms :** concurrency

##  <a name="async_send"></a> async_send

Les files d’attente des messages et démarre une tâche de traitement, si cela n’a pas déjà été fait de façon asynchrone.

```
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>Paramètres

*_Msg*<br/>
Pointeur vers un message.

##  <a name="initialize"></a> initialiser

Initialise le `ordered_message_processor` objet avec le groupe de fonction, le planificateur et planification de rappel appropriées.

```
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```

### <a name="parameters"></a>Paramètres

*_PScheduler*<br/>
Pointeur vers le planificateur à utiliser pour la planification des tâches légères.

*_PScheduleGroup*<br/>
Pointeur vers le groupe de planification à utiliser pour la planification des tâches légères.

*_Handler*<br/>
Le functor de gestionnaire appelé pendant le rappel.

##  <a name="initialize_batched_processing"></a> initialize_batched_processing

Initialiser le traitement des messages par lot

```
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```

### <a name="parameters"></a>Paramètres

*_Processor*<br/>
Le functor processeur appelé pendant le rappel.

*_Propagator*<br/>
Le functor propagateur appelé pendant le rappel.

##  <a name="ctor"></a> ordered_message_processor

Construit un objet `ordered_message_processor`.

```
ordered_message_processor();
```

### <a name="remarks"></a>Notes

Cela `ordered_message_processor` ne programmons pas de gestionnaires asynchrones ou synchrones jusqu'à ce que le `initialize` fonction est appelée.

##  <a name="dtor"></a> ~ordered_message_processor

Détruit le `ordered_message_processor` objet.

```
virtual ~ordered_message_processor();
```

### <a name="remarks"></a>Notes

Attend que toutes les opérations asynchrones en attente avant de détruire le processeur.

##  <a name="process_incoming_message"></a> process_incoming_message

La fonction de traitement qui est appelée de façon asynchrone. Il enlève les messages et commence à les traiter.

```
virtual void process_incoming_message();
```

##  <a name="sync_send"></a> sync_send

Mode synchrone les files d’attente des messages et démarre une tâche de traitement, si cela n’a pas déjà été fait.

```
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>Paramètres

*_Msg*<br/>
Pointeur vers un message.

##  <a name="wait"></a> attente

Attente de rotation spécifique au processeur utilisée dans les destructeurs de blocs de messages pour vous assurer que toutes les tâches de traitement asynchrone ont le temps se termine avant de détruire le bloc.

```
virtual void wait();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
