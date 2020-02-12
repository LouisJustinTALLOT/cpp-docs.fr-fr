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
ms.openlocfilehash: ea9ca799f36cac0d843a578eb7cef9c1e9c5cda6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138781"
---
# <a name="ordered_message_processor-class"></a>ordered_message_processor, classe

Un `ordered_message_processor` est un `message_processor` qui permet aux blocs de messages de traiter les messages dans l'ordre de leur réception.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class ordered_message_processor : public message_processor<T>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de charge utile des messages gérés par le processeur.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`type`|Alias de type pour `T`.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[ordered_message_processor](#ctor)|Construit un objet `ordered_message_processor`.|
|[Destructeur ~ ordered_message_processor](#dtor)|Détruit l’objet `ordered_message_processor`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[async_send](#async_send)|Met en file d’attente de manière asynchrone les messages et démarre une tâche de traitement, si ce n’est déjà fait. (Substitue [message_processor :: async_send](message-processor-class.md#async_send).)|
|[initialiser](#initialize)|Initialise l’objet `ordered_message_processor` avec la fonction de rappel, le planificateur et le groupe de planification appropriés.|
|[initialize_batched_processing](#initialize_batched_processing)|Initialiser le traitement des messages par lots|
|[sync_send](#sync_send)|Met en file d’attente de manière synchrone les messages et démarre une tâche de traitement, si ce n’est déjà fait. (Substitue [message_processor :: sync_send](message-processor-class.md#sync_send).)|
|[qu'](#wait)|Attente de spin spécifique au processeur, utilisée dans les destructeurs de blocs de messages pour s’assurer que toutes les tâches de traitement asynchrones ont le temps de se terminer avant de détruire le bloc. (Substitue [message_processor :: wait](message-processor-class.md#wait).)|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|Fonction de traitement appelée de manière asynchrone. Il met en file d’attente les messages et commence à les traiter. (Substitue [message_processor ::p rocess_incoming_message](message-processor-class.md#process_incoming_message).)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[message_processor](message-processor-class.md)

`ordered_message_processor`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="async_send"></a>async_send

Met en file d’attente de manière asynchrone les messages et démarre une tâche de traitement, si ce n’est déjà fait.

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>Paramètres

*_Msg*<br/>
Pointeur vers un message.

## <a name="initialize"></a>initialiser

Initialise l’objet `ordered_message_processor` avec la fonction de rappel, le planificateur et le groupe de planification appropriés.

```cpp
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```

### <a name="parameters"></a>Paramètres

*_PScheduler*<br/>
Pointeur vers le planificateur à utiliser pour planifier des tâches légères.

*_PScheduleGroup*<br/>
Pointeur vers le groupe de planification à utiliser pour planifier des tâches légères.

*_Handler*<br/>
Functor de gestionnaire appelé pendant le rappel.

## <a name="initialize_batched_processing"></a>initialize_batched_processing

Initialiser le traitement des messages par lots

```cpp
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```

### <a name="parameters"></a>Paramètres

*_Processor*<br/>
Functor de processeur appelé pendant le rappel.

*_Propagator*<br/>
Functor de propagateur appelé pendant le rappel.

## <a name="ctor"></a>ordered_message_processor

Construit un objet `ordered_message_processor`.

```cpp
ordered_message_processor();
```

### <a name="remarks"></a>Notes

Cette `ordered_message_processor` ne planifie pas de gestionnaires asynchrones ou synchrones tant que la fonction `initialize` n’est pas appelée.

## <a name="dtor"></a>~ ordered_message_processor

Détruit l’objet `ordered_message_processor`.

```cpp
virtual ~ordered_message_processor();
```

### <a name="remarks"></a>Notes

Attend toutes les opérations asynchrones en suspens avant de détruire le processeur.

## <a name="process_incoming_message"></a>process_incoming_message

Fonction de traitement appelée de manière asynchrone. Il met en file d’attente les messages et commence à les traiter.

```cpp
virtual void process_incoming_message();
```

## <a name="sync_send"></a>sync_send

Met en file d’attente de manière synchrone les messages et démarre une tâche de traitement, si ce n’est déjà fait.

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>Paramètres

*_Msg*<br/>
Pointeur vers un message.

## <a name="wait"></a>qu'

Attente de spin spécifique au processeur, utilisée dans les destructeurs de blocs de messages pour s’assurer que toutes les tâches de traitement asynchrones ont le temps de se terminer avant de détruire le bloc.

```cpp
virtual void wait();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
