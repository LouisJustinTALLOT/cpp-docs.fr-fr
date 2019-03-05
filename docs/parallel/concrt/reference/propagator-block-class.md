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
ms.openlocfilehash: 7f466ad8f474ddb73d2235d9999c3dbeae627672
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272943"
---
# <a name="propagatorblock-class"></a>propagator_block, classe

La classe `propagator_block` est une classe de base abstraite pour les blocs de messages qui sont à la fois une source et une cible. Elle combine les fonctionnalités des classes `source_block` et `target_block`.

## <a name="syntax"></a>Syntaxe

```
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

#### <a name="parameters"></a>Paramètres

*_TargetLinkRegistry*<br/>
Le Registre de lien à utiliser pour contenir les liens de la cible.

*_SourceLinkRegistry*<br/>
Le Registre de lien à utiliser pour contenir les liens de la source.

*_MessageProcessorType*<br/>
Le type de processeur pour le traitement du message.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`source_iterator`|Le type de l’itérateur pour le `source_link_manager` pour ce `propagator_block`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[propagator_block](#ctor)|Construit un objet `propagator_block`.|
|[~ propagator_block, destructeur](#dtor)|Détruit un objet `propagator_block`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[propagate](#propagate)|Passe de façon asynchrone un message à partir d’un bloc source à ce bloc cible.|
|[send](#send)|Démarre de façon synchrone un message à ce bloc. Appelé par un `ISource` bloc. Lorsque cette fonction est terminée, le message est déjà propagé dans le bloc.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[decline_incoming_messages](#decline_incoming_messages)|Indique au bloc que les nouveaux messages doivent être refusées.|
|[initialize_source_and_target](#initialize_source_and_target)|Initialise l’objet de base. Plus précisément, le `message_processor` objet doit être initialisé.|
|[link_source](#link_source)|Lie un bloc source spécifié à ce `propagator_block` objet.|
|[process_input_messages](#process_input_messages)|Traiter les messages d’entrée. Cela est utile uniquement pour les blocs propagateurs, qui dérivent de source_block (remplace [source_block::process_input_messages](source-block-class.md#process_input_messages).)|
|[propagate_message](#propagate_message)|En cas de substitution dans une classe dérivée, cette méthode passe de façon asynchrone un message à partir d’un `ISource` à ce bloc `propagator_block` objet. Elle est appelée par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.|
|[register_filter](#register_filter)|Enregistre une méthode de filtre qui sera appelée sur chaque message reçu.|
|[remove_network_links](#remove_network_links)|Supprime tous les liens de réseau source et cible de ce `propagator_block` objet.|
|[send_message](#send_message)|En cas de substitution dans une classe dérivée, cette méthode passe de façon synchrone un message à partir d’un `ISource` à ce bloc `propagator_block` objet. Elle est appelée par le `send` (méthode), lorsqu’elle est appelée par un bloc source.|
|[unlink_source](#unlink_source)|Dissocie un bloc source spécifié à partir de ce `propagator_block` objet.|
|[unlink_sources](#unlink_sources)|Dissocie tous les blocs de code source à partir de ce `propagator_block` objet. (Substitue [ITarget::unlink_sources](itarget-class.md#unlink_sources).)|

## <a name="remarks"></a>Notes

Pour éviter l’héritage multiple, la `propagator_block` classe hérite de la `source_block` classe et `ITarget` classe abstraite. La plupart des fonctionnalités dans le `target_block` classe est répliquée ici.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

`propagator_block`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

##  <a name="decline_incoming_messages"></a> decline_incoming_messages

Indique au bloc que les nouveaux messages doivent être refusées.

```
void decline_incoming_messages();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par le destructeur pour vous assurer que les nouveaux messages sont refusés pendant que la destruction est en cours d’exécution.

##  <a name="initialize_source_and_target"></a> initialize_source_and_target

Initialise l’objet de base. Plus précisément, le `message_processor` objet doit être initialisé.

```
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Paramètres

*_PScheduler*<br/>
Le planificateur à utiliser pour la planification des tâches.

*_PScheduleGroup*<br/>
Le groupe de planification à utiliser pour la planification des tâches.

##  <a name="link_source"></a> link_source

Lie un bloc source spécifié à ce `propagator_block` objet.

```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PSource*<br/>
Un pointeur vers le `ISource` bloc qui doit être liée.

##  <a name="process_input_messages"></a> process_input_messages

Traiter les messages d’entrée. Cela est utile uniquement pour les blocs propagateurs, qui dérivent de source_block

```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message doit être traité.

##  <a name="propagate"></a> propagate

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

Le `propagate` méthode est appelée sur un bloc cible par un bloc source lié. Il place file d’attente une tâche asynchrone pour gérer le message, si un n’est pas déjà en attente ou de l’exécution.

La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le `_PMessage` ou `_PSource` paramètre est `NULL`.

##  <a name="propagate_message"></a> propagate_message

En cas de substitution dans une classe dérivée, cette méthode passe de façon asynchrone un message à partir d’un `ISource` à ce bloc `propagator_block` objet. Elle est appelée par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.

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

##  <a name="ctor"></a> propagator_block

Construit un objet `propagator_block`.

```
propagator_block();
```

##  <a name="dtor"></a> ~propagator_block

Détruit un objet `propagator_block`.

```
virtual ~propagator_block();
```

##  <a name="register_filter"></a> register_filter

Enregistre une méthode de filtre qui sera appelée sur chaque message reçu.

```
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Paramètres

*_Filter*<br/>
La méthode de filtrage.

##  <a name="remove_network_links"></a> remove_network_links

Supprime tous les liens de réseau source et cible de ce `propagator_block` objet.

```
void remove_network_links();
```

##  <a name="send"></a> Envoyer

Démarre de façon synchrone un message à ce bloc. Appelé par un `ISource` bloc. Lorsque cette fonction est terminée, le message est déjà propagé dans le bloc.

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

Cette méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le `_PMessage` ou `_PSource` paramètre est `NULL`.

##  <a name="send_message"></a> send_message

En cas de substitution dans une classe dérivée, cette méthode passe de façon synchrone un message à partir d’un `ISource` à ce bloc `propagator_block` objet. Elle est appelée par le `send` (méthode), lorsqu’elle est appelée par un bloc source.

```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Valeur de retour

Un [message_status](concurrency-namespace-enums.md) indication de ce que la cible a décidé de faire avec le message.

### <a name="remarks"></a>Notes

Par défaut, ce bloc retourne `declined` sauf substitution par une classe dérivée.

##  <a name="unlink_source"></a> unlink_source

Dissocie un bloc source spécifié à partir de ce `propagator_block` objet.

```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PSource*<br/>
Un pointeur vers le `ISource` bloc qui doit être dissocié.

##  <a name="unlink_sources"></a> unlink_sources

Dissocie tous les blocs de code source à partir de ce `propagator_block` objet.

```
virtual void unlink_sources();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[source_block, classe](source-block-class.md)<br/>
[ITarget, classe](itarget-class.md)
