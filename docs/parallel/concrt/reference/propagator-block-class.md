---
description: 'En savoir plus sur : classe propagator_block'
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
ms.openlocfilehash: 4dd006829e01f663be20be76a2cc2e0364ef7b38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115246"
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

|Nom|Description|
|----------|-----------------|
|`source_iterator`|Type de l’itérateur pour le `source_link_manager` pour ce `propagator_block` .|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[propagator_block](#ctor)|Construit un objet `propagator_block`.|
|[Destructeur ~ propagator_block](#dtor)|Détruit un objet `propagator_block` .|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[propager](#propagate)|Passe de façon asynchrone un message d’un bloc source à ce bloc cible.|
|[envoyer](#send)|Initialise de façon synchrone un message dans ce bloc. Appelée par un `ISource` bloc. Lorsque cette fonction est terminée, le message est déjà propagé dans le bloc.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[decline_incoming_messages](#decline_incoming_messages)|Indique au bloc que les nouveaux messages doivent être refusés.|
|[initialize_source_and_target](#initialize_source_and_target)|Initialise l’objet de base. Plus précisément, l' `message_processor` objet doit être initialisé.|
|[link_source](#link_source)|Lie un bloc source spécifié à cet `propagator_block` objet.|
|[process_input_messages](#process_input_messages)|Traiter les messages d’entrée. Cela est utile uniquement pour les blocs de propagation, qui dérivent de source_block (substitutions [source_block ::p rocess_input_messages](source-block-class.md#process_input_messages).)|
|[propagate_message](#propagate_message)|En cas de substitution dans une classe dérivée, cette méthode passe de façon asynchrone un message d’un `ISource` bloc à cet `propagator_block` objet. Elle est appelée par la `propagate` méthode, quand elle est appelée par un bloc source.|
|[register_filter](#register_filter)|Inscrit une méthode de filtre qui sera appelée sur chaque message reçu.|
|[remove_network_links](#remove_network_links)|Supprime tous les liens réseau source et cible de cet `propagator_block` objet.|
|[send_message](#send_message)|En cas de substitution dans une classe dérivée, cette méthode passe de façon synchrone un message d’un `ISource` bloc à cet `propagator_block` objet. Elle est appelée par la `send` méthode, quand elle est appelée par un bloc source.|
|[unlink_source](#unlink_source)|Dissocie un bloc source spécifié de cet `propagator_block` objet.|
|[unlink_sources](#unlink_sources)|Dissocie tous les blocs sources de cet `propagator_block` objet. (Substitue [ITarget :: unlink_sources](itarget-class.md#unlink_sources).)|

## <a name="remarks"></a>Notes

Pour éviter l’héritage multiple, la `propagator_block` classe hérite de la classe et de la `source_block` `ITarget` classe abstraite. La plupart des fonctionnalités de la `target_block` classe sont répliquées ici.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

`propagator_block`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="decline_incoming_messages"></a><a name="decline_incoming_messages"></a> decline_incoming_messages

Indique au bloc que les nouveaux messages doivent être refusés.

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par le destructeur pour s’assurer que les nouveaux messages sont refusés pendant que la destruction est en cours.

## <a name="initialize_source_and_target"></a><a name="initialize_source_and_target"></a> initialize_source_and_target

Initialise l’objet de base. Plus précisément, l' `message_processor` objet doit être initialisé.

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

## <a name="link_source"></a><a name="link_source"></a> link_source

Lie un bloc source spécifié à cet `propagator_block` objet.

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PSource*<br/>
Pointeur vers le `ISource` bloc qui doit être lié.

## <a name="process_input_messages"></a><a name="process_input_messages"></a> process_input_messages

Traiter les messages d’entrée. Cela est utile uniquement pour les blocs de propagation, qui dérivent de source_block

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message qui doit être traité.

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

La `propagate` méthode est appelée sur un bloc cible par un bloc source lié. Il met en file d’attente une tâche asynchrone pour gérer le message, si celle-ci n’est pas déjà en file d’attente ou en cours d’exécution.

La méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le `_PMessage` `_PSource` paramètre ou a la valeur `NULL` .

## <a name="propagate_message"></a><a name="propagate_message"></a> propagate_message

En cas de substitution dans une classe dérivée, cette méthode passe de façon asynchrone un message d’un `ISource` bloc à cet `propagator_block` objet. Elle est appelée par la `propagate` méthode, quand elle est appelée par un bloc source.

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

## <a name="propagator_block"></a><a name="ctor"></a> propagator_block

Construit un objet `propagator_block`.

```cpp
propagator_block();
```

## <a name="propagator_block"></a><a name="dtor"></a> ~ propagator_block

Détruit un objet `propagator_block` .

```cpp
virtual ~propagator_block();
```

## <a name="register_filter"></a><a name="register_filter"></a> register_filter

Inscrit une méthode de filtre qui sera appelée sur chaque message reçu.

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Paramètres

*_Filter*<br/>
Méthode de filtre.

## <a name="remove_network_links"></a><a name="remove_network_links"></a> remove_network_links

Supprime tous les liens réseau source et cible de cet `propagator_block` objet.

```cpp
void remove_network_links();
```

## <a name="send"></a><a name="send"></a> Envoyer

Initialise de façon synchrone un message dans ce bloc. Appelée par un `ISource` bloc. Lorsque cette fonction est terminée, le message est déjà propagé dans le bloc.

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

Cette méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le `_PMessage` `_PSource` paramètre ou a la valeur `NULL` .

## <a name="send_message"></a><a name="send_message"></a> send_message

En cas de substitution dans une classe dérivée, cette méthode passe de façon synchrone un message d’un `ISource` bloc à cet `propagator_block` objet. Elle est appelée par la `send` méthode, quand elle est appelée par un bloc source.

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Valeur renvoyée

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

### <a name="remarks"></a>Notes

Par défaut, ce bloc retourne, `declined` sauf s’il est substitué par une classe dérivée.

## <a name="unlink_source"></a><a name="unlink_source"></a> unlink_source

Dissocie un bloc source spécifié de cet `propagator_block` objet.

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PSource*<br/>
Pointeur vers le `ISource` bloc qui doit être dissocié.

## <a name="unlink_sources"></a><a name="unlink_sources"></a> unlink_sources

Dissocie tous les blocs sources de cet `propagator_block` objet.

```cpp
virtual void unlink_sources();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe source_block](source-block-class.md)<br/>
[ITarget, classe](itarget-class.md)
