---
description: 'En savoir plus sur : classe target_block'
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
ms.openlocfilehash: 0860ff7b185eef997d7c76f61d67ad10056ca9cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188415"
---
# <a name="target_block-class"></a>target_block, classe

La classe `target_block` est une classe de base abstraite qui fournit une fonctionnalité de gestion des liens de base et une vérification des erreurs pour les blocs cibles uniquement.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>Paramètres

*_SourceLinkRegistry*<br/>
Registre de liens à utiliser pour conserver les liens source.

*_MessageProcessorType*<br/>
Type de processeur pour le traitement des messages.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`source_iterator`|Type de l’itérateur pour `source_link_manager` pour cet `target_block` objet.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[target_block](#ctor)|Construit un objet `target_block`.|
|[Destructeur ~ target_block](#dtor)|Détruit l' `target_block` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[propager](#propagate)|Passe de façon asynchrone un message d’un bloc source à ce bloc cible.|
|[envoyer](#send)|Passe de façon synchrone un message d’un bloc source à ce bloc cible.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[async_send](#async_send)|Envoie de façon asynchrone un message pour traitement.|
|[decline_incoming_messages](#decline_incoming_messages)|Indique au bloc que les nouveaux messages doivent être refusés.|
|[enable_batched_processing](#enable_batched_processing)|Active le traitement par lots pour ce bloc.|
|[initialize_target](#initialize_target)|Initialise l’objet de base. Plus précisément, l' `message_processor` objet doit être initialisé.|
|[link_source](#link_source)|Lie un bloc source spécifié à cet `target_block` objet.|
|[process_input_messages](#process_input_messages)|Traite les messages reçus en tant qu’entrées.|
|[process_message](#process_message)|En cas de substitution dans une classe dérivée, traite un message qui a été accepté par cet `target_block` objet.|
|[propagate_message](#propagate_message)|En cas de substitution dans une classe dérivée, cette méthode passe de façon asynchrone un message d’un `ISource` bloc à cet `target_block` objet. Elle est appelée par la `propagate` méthode, quand elle est appelée par un bloc source.|
|[register_filter](#register_filter)|Inscrit une méthode de filtre qui sera appelée à chaque message reçu.|
|[remove_sources](#remove_sources)|Dissocie toutes les sources après avoir attendu la fin des opérations d’envoi asynchrones en suspens.|
|[send_message](#send_message)|En cas de substitution dans une classe dérivée, cette méthode passe de façon synchrone un message d’un `ISource` bloc à cet `target_block` objet. Elle est appelée par la `send` méthode, quand elle est appelée par un bloc source.|
|[sync_send](#sync_send)|Envoie de façon synchrone un message pour traitement.|
|[unlink_source](#unlink_source)|Dissocie un bloc source spécifié de cet `target_block` objet.|
|[unlink_sources](#unlink_sources)|Dissocie tous les blocs sources de cet `target_block` objet. (Substitue [ITarget :: unlink_sources](itarget-class.md#unlink_sources).)|
|[wait_for_async_sends](#wait_for_async_sends)|Attend la fin de toutes les propagations asynchrones.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ITarget](itarget-class.md)

`target_block`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="async_send"></a><a name="async_send"></a> async_send

Envoie de façon asynchrone un message pour traitement.

```cpp
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message envoyé.

## <a name="decline_incoming_messages"></a><a name="decline_incoming_messages"></a> decline_incoming_messages

Indique au bloc que les nouveaux messages doivent être refusés.

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par le destructeur pour s’assurer que les nouveaux messages sont refusés pendant que la destruction est en cours.

## <a name="enable_batched_processing"></a><a name="enable_batched_processing"></a> enable_batched_processing

Active le traitement par lots pour ce bloc.

```cpp
void enable_batched_processing();
```

## <a name="initialize_target"></a><a name="initialize_target"></a> initialize_target

Initialise l’objet de base. Plus précisément, l' `message_processor` objet doit être initialisé.

```cpp
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Paramètres

*_PScheduler*<br/>
Planificateur à utiliser pour planifier les tâches.

*_PScheduleGroup*<br/>
Groupe de planification à utiliser pour planifier les tâches.

## <a name="link_source"></a><a name="link_source"></a> link_source

Lie un bloc source spécifié à cet `target_block` objet.

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PSource*<br/>
Pointeur vers le `ISource` bloc qui doit être lié.

### <a name="remarks"></a>Notes

Cette fonction ne doit pas être appelée directement sur un `target_block` objet. Les blocs doivent être connectés ensemble à l’aide de la `link_target` méthode sur `ISource` les blocs, qui appellera la `link_source` méthode sur la cible correspondante.

## <a name="process_input_messages"></a><a name="process_input_messages"></a> process_input_messages

Traite les messages reçus en tant qu’entrées.

```cpp
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message qui doit être traité.

## <a name="process_message"></a><a name="process_message"></a> process_message

En cas de substitution dans une classe dérivée, traite un message qui a été accepté par cet `target_block` objet.

```cpp
virtual void process_message(message<_Source_type> *);
```

## <a name="propagate"></a><a name="propagate"></a> propager

Passe de façon asynchrone un message d’un bloc source à ce bloc cible.

```cpp
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui offre le message.

### <a name="return-value"></a>Valeur renvoyée

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le `_PMessage` `_PSource` paramètre ou a la valeur `NULL` .

## <a name="propagate_message"></a><a name="propagate_message"></a> propagate_message

En cas de substitution dans une classe dérivée, cette méthode passe de façon asynchrone un message d’un `ISource` bloc à cet `target_block` objet. Elle est appelée par la `propagate` méthode, quand elle est appelée par un bloc source.

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui offre le message.

### <a name="return-value"></a>Valeur renvoyée

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

## <a name="register_filter"></a><a name="register_filter"></a> register_filter

Inscrit une méthode de filtre qui sera appelée à chaque message reçu.

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Paramètres

*_Filter*<br/>
Méthode de filtre.

## <a name="remove_sources"></a><a name="remove_sources"></a> remove_sources

Dissocie toutes les sources après avoir attendu la fin des opérations d’envoi asynchrones en suspens.

```cpp
void remove_sources();
```

### <a name="remarks"></a>Notes

Tous les blocs cibles doivent appeler cette routine pour supprimer les sources dans leur destructeur.

## <a name="send"></a><a name="send"></a> Envoyer

Passe de façon synchrone un message d’un bloc source à ce bloc cible.

```cpp
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui offre le message.

### <a name="return-value"></a>Valeur renvoyée

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le `_PMessage` `_PSource` paramètre ou a la valeur `NULL` .

L’utilisation `send` de la méthode en dehors de l’initiation du message et de la propagation des messages au sein d’un réseau est dangereuse et peut entraîner un interblocage.

Lorsque `send` retourne, le message a déjà été accepté, puis transféré dans le bloc cible, ou il a été refusé par la cible.

## <a name="send_message"></a><a name="send_message"></a> send_message

En cas de substitution dans une classe dérivée, cette méthode passe de façon synchrone un message d’un `ISource` bloc à cet `target_block` objet. Elle est appelée par la `send` méthode, quand elle est appelée par un bloc source.

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Valeur renvoyée

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

### <a name="remarks"></a>Notes

Par défaut, ce bloc retourne, `declined` sauf s’il est substitué par une classe dérivée.

## <a name="sync_send"></a><a name="sync_send"></a> sync_send

Envoie de façon synchrone un message pour traitement.

```cpp
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message envoyé.

## <a name="target_block"></a><a name="ctor"></a> target_block

Construit un objet `target_block`.

```cpp
target_block();
```

## <a name="target_block"></a><a name="dtor"></a> ~ target_block

Détruit l' `target_block` objet.

```cpp
virtual ~target_block();
```

## <a name="unlink_source"></a><a name="unlink_source"></a> unlink_source

Dissocie un bloc source spécifié de cet `target_block` objet.

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PSource*<br/>
Pointeur vers le `ISource` bloc qui doit être dissocié.

## <a name="unlink_sources"></a><a name="unlink_sources"></a> unlink_sources

Dissocie tous les blocs sources de cet `target_block` objet.

```cpp
virtual void unlink_sources();
```

## <a name="wait_for_async_sends"></a><a name="wait_for_async_sends"></a> wait_for_async_sends

Attend la fin de toutes les propagations asynchrones.

```cpp
void wait_for_async_sends();
```

### <a name="remarks"></a>Notes

Cette méthode est utilisée par les destructeurs de bloc de message pour s’assurer que toutes les opérations asynchrones ont eu le temps de se terminer avant de détruire le bloc.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[ITarget, classe](itarget-class.md)
