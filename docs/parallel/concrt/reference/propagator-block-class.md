---
title: propagator_block, classe
ms.date: 11/04/2016
f1_keywords:
- propagator_block
- AGENTS/concurrency::propagator_block
- AGENTS/concurrency::propagator_block::propagator_block
- AGENTS/concurrency::propagator_block::propagate
- AGENTS/concurrency::propagator_block::send
- AGENTS/concurrency::propagator_block::decline_incoming_messages
- AGENTS/concurrency::propagator_block::initialize_source_and_target
- AGENTS/concurrency::propagator_block::link_source
- AGENTS/concurrency::propagator_block::process_input_messages
- AGENTS/concurrency::propagator_block::propagate_message
- AGENTS/concurrency::propagator_block::register_filter
- AGENTS/concurrency::propagator_block::remove_network_links
- AGENTS/concurrency::propagator_block::send_message
- AGENTS/concurrency::propagator_block::unlink_source
- AGENTS/concurrency::propagator_block::unlink_sources
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
ms.openlocfilehash: 340af181669cbbf4c5ba910aa3ee862bd40ba27f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138738"
---
# <a name="propagator_block-class"></a>propagator_block, classe

La classe `propagator_block` est une classe de base abstraite pour les blocs de messages qui sont à la fois une source et une cible. Elle combine les fonctionnalités des classes `source_block` et `target_block`.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>Paramètres

*_TargetLinkRegistry*<br/>
Registre de liens à utiliser pour conserver les liens cibles.

*_SourceLinkRegistry*<br/>
Registre de liens à utiliser pour conserver les liens source.

*_MessageProcessorType*<br/>
Type de processeur pour le traitement des messages.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`source_iterator`|Type de l’itérateur pour le `source_link_manager` pour ce `propagator_block`.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[propagator_block](#ctor)|Construit un objet `propagator_block`.|
|[Destructeur ~ propagator_block](#dtor)|Détruit un objet `propagator_block`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[propager](#propagate)|Passe de façon asynchrone un message d’un bloc source à ce bloc cible.|
|[send](#send)|Initialise de façon synchrone un message dans ce bloc. Appelée par un bloc `ISource`. Lorsque cette fonction est terminée, le message est déjà propagé dans le bloc.|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[decline_incoming_messages](#decline_incoming_messages)|Indique au bloc que les nouveaux messages doivent être refusés.|
|[initialize_source_and_target](#initialize_source_and_target)|Initialise l’objet de base. Plus précisément, l’objet `message_processor` doit être initialisé.|
|[link_source](#link_source)|Lie un bloc source spécifié à cet objet `propagator_block`.|
|[process_input_messages](#process_input_messages)|Traiter les messages d’entrée. Cela est utile uniquement pour les blocs de propagation, qui dérivent de source_block (substitutions [source_block ::p rocess_input_messages](source-block-class.md#process_input_messages).)|
|[propagate_message](#propagate_message)|En cas de substitution dans une classe dérivée, cette méthode passe de façon asynchrone un message d’un bloc de `ISource` à cet objet `propagator_block`. Elle est appelée par la méthode `propagate`, quand elle est appelée par un bloc source.|
|[register_filter](#register_filter)|Inscrit une méthode de filtre qui sera appelée sur chaque message reçu.|
|[remove_network_links](#remove_network_links)|Supprime tous les liens réseau source et cible de cet objet `propagator_block`.|
|[send_message](#send_message)|En cas de substitution dans une classe dérivée, cette méthode passe de façon synchrone un message d’un bloc de `ISource` à cet objet `propagator_block`. Elle est appelée par la méthode `send`, quand elle est appelée par un bloc source.|
|[unlink_source](#unlink_source)|Dissocie un bloc source spécifié de cet objet `propagator_block`.|
|[unlink_sources](#unlink_sources)|Dissocie tous les blocs sources de cet objet `propagator_block`. (Substitue [ITarget :: unlink_sources](itarget-class.md#unlink_sources).)|

## <a name="remarks"></a>Notes

Pour éviter l’héritage multiple, la classe `propagator_block` hérite de la classe `source_block` et `ITarget` classe abstraite. La plupart des fonctionnalités de la classe `target_block` sont répliquées ici.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

`propagator_block`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="decline_incoming_messages"></a>decline_incoming_messages

Indique au bloc que les nouveaux messages doivent être refusés.

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par le destructeur pour s’assurer que les nouveaux messages sont refusés pendant que la destruction est en cours.

## <a name="initialize_source_and_target"></a>initialize_source_and_target

Initialise l’objet de base. Plus précisément, l’objet `message_processor` doit être initialisé.

```cpp
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Paramètres

*_PScheduler*<br/>
Planificateur à utiliser pour planifier les tâches.

*_PScheduleGroup*<br/>
Groupe de planification à utiliser pour planifier les tâches.

## <a name="link_source"></a>link_source

Lie un bloc source spécifié à cet objet `propagator_block`.

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PSource*<br/>
Pointeur vers le bloc `ISource` qui doit être lié.

## <a name="process_input_messages"></a>process_input_messages

Traiter les messages d’entrée. Cela est utile uniquement pour les blocs de propagation, qui dérivent de source_block

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message qui doit être traité.

## <a name="propagate"></a>propager

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

### <a name="return-value"></a>Valeur de retour

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

### <a name="remarks"></a>Notes

La méthode `propagate` est appelée sur un bloc cible par un bloc source lié. Il met en file d’attente une tâche asynchrone pour gérer le message, si celle-ci n’est pas déjà en file d’attente ou en cours d’exécution.

La méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le paramètre `_PMessage` ou `_PSource` est `NULL`.

## <a name="propagate_message"></a>propagate_message

En cas de substitution dans une classe dérivée, cette méthode passe de façon asynchrone un message d’un bloc de `ISource` à cet objet `propagator_block`. Elle est appelée par la méthode `propagate`, quand elle est appelée par un bloc source.

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

### <a name="return-value"></a>Valeur de retour

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

## <a name="ctor"></a>propagator_block

Construit un objet `propagator_block`.

```cpp
propagator_block();
```

## <a name="dtor"></a>~ propagator_block

Détruit un objet `propagator_block`.

```cpp
virtual ~propagator_block();
```

## <a name="register_filter"></a>register_filter

Inscrit une méthode de filtre qui sera appelée sur chaque message reçu.

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Paramètres

*_Filter*<br/>
Méthode de filtre.

## <a name="remove_network_links"></a>remove_network_links

Supprime tous les liens réseau source et cible de cet objet `propagator_block`.

```cpp
void remove_network_links();
```

## <a name="send"></a>Envoyer

Initialise de façon synchrone un message dans ce bloc. Appelée par un bloc `ISource`. Lorsque cette fonction est terminée, le message est déjà propagé dans le bloc.

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

### <a name="return-value"></a>Valeur de retour

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

### <a name="remarks"></a>Notes

Cette méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le paramètre `_PMessage` ou `_PSource` est `NULL`.

## <a name="send_message"></a>send_message

En cas de substitution dans une classe dérivée, cette méthode passe de façon synchrone un message d’un bloc de `ISource` à cet objet `propagator_block`. Elle est appelée par la méthode `send`, quand elle est appelée par un bloc source.

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Valeur de retour

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

### <a name="remarks"></a>Notes

Par défaut, ce bloc retourne `declined` sauf si elle est substituée par une classe dérivée.

## <a name="unlink_source"></a>unlink_source

Dissocie un bloc source spécifié de cet objet `propagator_block`.

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PSource*<br/>
Pointeur vers le bloc `ISource` qui doit être dissocié.

## <a name="unlink_sources"></a>unlink_sources

Dissocie tous les blocs sources de cet objet `propagator_block`.

```cpp
virtual void unlink_sources();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[source_block, classe](source-block-class.md)<br/>
[ITarget, classe](itarget-class.md)
