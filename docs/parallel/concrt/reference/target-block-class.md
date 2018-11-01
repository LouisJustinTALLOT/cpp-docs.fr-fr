---
title: target_block, classe
ms.date: 11/04/2016
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
ms.openlocfilehash: cb8880b66ebeef12018ef7449c9c383b99ec396c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656886"
---
# <a name="targetblock-class"></a>target_block, classe

La classe `target_block` est une classe de base abstraite qui fournit une fonctionnalité de gestion des liens de base et une vérification des erreurs pour les blocs cibles uniquement.

## <a name="syntax"></a>Syntaxe

```
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

#### <a name="parameters"></a>Paramètres

*_SourceLinkRegistry*<br/>
Le Registre de lien à utiliser pour contenir les liens de la source.

*_MessageProcessorType*<br/>
Le type de processeur pour le traitement du message.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`source_iterator`|Le type de l’itérateur pour le `source_link_manager` pour ce `target_block` objet.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[target_block](#ctor)|Construit un objet `target_block`.|
|[~ target_block, destructeur](#dtor)|Détruit le `target_block` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[propager](#propagate)|Passe de façon asynchrone un message à partir d’un bloc source à ce bloc cible.|
|[send](#send)|Passe de façon synchrone un message à partir d’un bloc source à ce bloc cible.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[async_send](#async_send)|Envoie un message pour le traitement de façon asynchrone.|
|[decline_incoming_messages](#decline_incoming_messages)|Indique au bloc que les nouveaux messages doivent être refusées.|
|[enable_batched_processing](#enable_batched_processing)|Active par lot de traitement pour ce bloc.|
|[initialize_target](#initialize_target)|Initialise l’objet de base. Plus précisément, le `message_processor` objet doit être initialisé.|
|[link_source](#link_source)|Lie un bloc source spécifié à ce `target_block` objet.|
|[process_input_messages](#process_input_messages)|Traite les messages sont reçus en tant qu’entrées.|
|[process_message](#process_message)|En cas de substitution dans une classe dérivée, traite un message qui a été accepté par ce `target_block` objet.|
|[propagate_message](#propagate_message)|En cas de substitution dans une classe dérivée, cette méthode passe de façon asynchrone un message à partir d’un `ISource` à ce bloc `target_block` objet. Elle est appelée par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.|
|[register_filter](#register_filter)|Enregistre une méthode de filtre qui sera appelée sur chaque message reçu.|
|[remove_sources](#remove_sources)|Dissocie toutes les sources après avoir attendu pour les opérations d’envoi asynchrone en attente se termine.|
|[send_message](#send_message)|En cas de substitution dans une classe dérivée, cette méthode passe de façon synchrone un message à partir d’un `ISource` à ce bloc `target_block` objet. Elle est appelée par le `send` (méthode), lorsqu’elle est appelée par un bloc source.|
|[sync_send](#sync_send)|Envoyer un message pour le traitement de façon synchrone.|
|[unlink_source](#unlink_source)|Dissocie un bloc source spécifié à partir de ce `target_block` objet.|
|[unlink_sources](#unlink_sources)|Dissocie tous les blocs de code source à partir de ce `target_block` objet. (Substitue [ITarget::unlink_sources](itarget-class.md#unlink_sources).)|
|[wait_for_async_sends](#wait_for_async_sends)|Attend que toutes les propagations asynchrones soient terminées.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ITarget](itarget-class.md)

`target_block`

## <a name="requirements"></a>Configuration requise

**En-tête :** agents.h

**Espace de noms :** concurrency

##  <a name="async_send"></a> async_send

Envoie un message pour le traitement de façon asynchrone.

```
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message envoyé.

##  <a name="decline_incoming_messages"></a> decline_incoming_messages

Indique au bloc que les nouveaux messages doivent être refusées.

```
void decline_incoming_messages();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par le destructeur pour vous assurer que les nouveaux messages sont refusés pendant que la destruction est en cours d’exécution.

##  <a name="enable_batched_processing"></a> enable_batched_processing

Active par lot de traitement pour ce bloc.

```
void enable_batched_processing();
```

##  <a name="initialize_target"></a> initialize_target

Initialise l’objet de base. Plus précisément, le `message_processor` objet doit être initialisé.

```
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Paramètres

*_PScheduler*<br/>
Le planificateur à utiliser pour la planification des tâches.

*_PScheduleGroup*<br/>
Le groupe de planification à utiliser pour la planification des tâches.

##  <a name="link_source"></a> link_source

Lie un bloc source spécifié à ce `target_block` objet.

```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PSource*<br/>
Un pointeur vers le `ISource` bloc qui doit être liée.

### <a name="remarks"></a>Notes

Cette fonction ne doit pas être appelée directement sur un `target_block` objet. Les blocs doivent être connectés à l’aide de la `link_target` méthode sur `ISource` blocs, qui appelleront le `link_source` méthode sur la cible correspondante.

##  <a name="process_input_messages"></a> process_input_messages

Traite les messages sont reçus en tant qu’entrées.

```
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message doit être traité.

##  <a name="process_message"></a> process_message

En cas de substitution dans une classe dérivée, traite un message qui a été accepté par ce `target_block` objet.

```
virtual void process_message(message<_Source_type> *);
```

##  <a name="propagate"></a> propager

Passe de façon asynchrone un message à partir d’un bloc source à ce bloc cible.

```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui transmet le message.

### <a name="return-value"></a>Valeur de retour

Un [message_status](concurrency-namespace-enums.md) indication de ce que la cible a décidé de faire avec le message.

### <a name="remarks"></a>Notes

La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le `_PMessage` ou `_PSource` paramètre est `NULL`.

##  <a name="propagate_message"></a> propagate_message

En cas de substitution dans une classe dérivée, cette méthode passe de façon asynchrone un message à partir d’un `ISource` à ce bloc `target_block` objet. Elle est appelée par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.

```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui transmet le message.

### <a name="return-value"></a>Valeur de retour

Un [message_status](concurrency-namespace-enums.md) indication de ce que la cible a décidé de faire avec le message.

##  <a name="register_filter"></a> register_filter

Enregistre une méthode de filtre qui sera appelée sur chaque message reçu.

```
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Paramètres

*_Filtre*<br/>
La méthode de filtrage.

##  <a name="remove_sources"></a> remove_sources

Dissocie toutes les sources après avoir attendu pour les opérations d’envoi asynchrone en attente se termine.

```
void remove_sources();
```

### <a name="remarks"></a>Notes

Tous les blocs cibles doivent appeler cette routine pour supprimer les sources dans leur destructeur.

##  <a name="send"></a> Envoyer

Passe de façon synchrone un message à partir d’un bloc source à ce bloc cible.

```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui transmet le message.

### <a name="return-value"></a>Valeur de retour

Un [message_status](concurrency-namespace-enums.md) indication de ce que la cible a décidé de faire avec le message.

### <a name="remarks"></a>Notes

La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le `_PMessage` ou `_PSource` paramètre est `NULL`.

À l’aide de la `send` méthode en dehors de l’émission de messages et pour propager des messages au sein d’un réseau est dangereux et peut provoquer un interblocage.

Lorsque `send` est retournée, le message a déjà été accepté et transféré dans le bloc cible, ou il a été refusé par la cible.

##  <a name="send_message"></a> send_message

En cas de substitution dans une classe dérivée, cette méthode passe de façon synchrone un message à partir d’un `ISource` à ce bloc `target_block` objet. Elle est appelée par le `send` (méthode), lorsqu’elle est appelée par un bloc source.

```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Valeur de retour

Un [message_status](concurrency-namespace-enums.md) indication de ce que la cible a décidé de faire avec le message.

### <a name="remarks"></a>Notes

Par défaut, ce bloc retourne `declined` sauf substitution par une classe dérivée.

##  <a name="sync_send"></a> sync_send

Envoyer un message pour le traitement de façon synchrone.

```
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message envoyé.

##  <a name="ctor"></a> target_block

Construit un objet `target_block`.

```
target_block();
```

##  <a name="dtor"></a> ~target_block

Détruit le `target_block` objet.

```
virtual ~target_block();
```

##  <a name="unlink_source"></a> unlink_source

Dissocie un bloc source spécifié à partir de ce `target_block` objet.

```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PSource*<br/>
Un pointeur vers le `ISource` bloc qui doit être dissocié.

##  <a name="unlink_sources"></a> unlink_sources

Dissocie tous les blocs de code source à partir de ce `target_block` objet.

```
virtual void unlink_sources();
```

##  <a name="wait_for_async_sends"></a> wait_for_async_sends

Attend que toutes les propagations asynchrones soient terminées.

```
void wait_for_async_sends();
```

### <a name="remarks"></a>Notes

Cette méthode est utilisée par les destructeurs de bloc de message pour vous assurer que toutes les opérations asynchrones ont eu le temps de terminer avant de détruire le bloc.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[ITarget, classe](itarget-class.md)
