---
title: source_block, classe
ms.date: 11/04/2016
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
ms.openlocfilehash: 3a0d69bc2e2904b1dcf37a7e9891d95bd869a610
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417081"
---
# <a name="source_block-class"></a>source_block, classe

La classe `source_block` est une classe de base abstraite pour les blocs sources uniquement. La classe fournit une fonctionnalité de gestion des liens de base ainsi que des vérifications d'erreurs courantes.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```

### <a name="parameters"></a>Paramètres

*_TargetLinkRegistry*<br/>
Registre de liaison à utiliser pour conserver les liens cibles.

*_MessageProcessorType*<br/>
Type de processeur pour le traitement des messages.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`target_iterator`|Itérateur pour parcourir les cibles connectées.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[source_block](#ctor)|Construit un objet `source_block`.|
|[Destructeur ~ source_block](#dtor)|Détruit l’objet `source_block`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[valide](#accept)|Accepte un message qui a été proposé par cet objet `source_block`, en transférant la propriété à l’appelant.|
|[acquire_ref](#acquire_ref)|Acquiert un décompte de références sur cet objet `source_block` pour empêcher la suppression.|
|[Utiliser](#consume)|Consomme un message précédemment offert par cet objet `source_block` et correctement réservé par la cible, en transférant la propriété à l’appelant.|
|[link_target](#link_target)|Lie un bloc cible à cet objet `source_block`.|
|[release](#release)|Libère une réservation de message réussie précédente.|
|[release_ref](#release_ref)|Libère un décompte de références sur cet objet `source_block`.|
|[reserve](#reserve)|Réserve un message précédemment offert par cet objet `source_block`.|
|[unlink_target](#unlink_target)|Dissocie un bloc cible de cet objet `source_block`.|
|[unlink_targets](#unlink_targets)|Dissocie tous les blocs cibles de cet objet `source_block`. (Substitue [ISource :: unlink_targets](isource-class.md#unlink_targets).)|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[accept_message](#accept_message)|En cas de substitution dans une classe dérivée, accepte un message proposé par la source. Les blocs de messages doivent remplacer cette méthode pour valider le `_MsgId` et retourner un message.|
|[async_send](#async_send)|Met en file d’attente de manière asynchrone les messages et démarre une tâche de propagation, si ce n’est déjà fait|
|[consume_message](#consume_message)|En cas de substitution dans une classe dérivée, consomme un message qui a été précédemment réservé.|
|[enable_batched_processing](#enable_batched_processing)|Active le traitement par lots pour ce bloc.|
|[initialize_source](#initialize_source)|Initialise le `message_propagator` dans ce `source_block`.|
|[link_target_notification](#link_target_notification)|Rappel qui signale qu’une nouvelle cible a été liée à cet objet `source_block`.|
|[process_input_messages](#process_input_messages)|Traiter les messages d’entrée. Cela est utile uniquement pour les blocs de propagation, qui dérivent de source_block|
|[propagate_output_messages](#propagate_output_messages)|Propager les messages aux cibles.|
|[propagate_to_any_targets](#propagate_to_any_targets)|En cas de substitution dans une classe dérivée, propage le message donné à tout ou partie des cibles liées. Il s’agit de la routine de propagation principale pour les blocs de message.|
|[release_message](#release_message)|En cas de substitution dans une classe dérivée, libère une réservation de message précédente.|
|[remove_targets](#remove_targets)|Supprime tous les liens cibles pour ce bloc source. Cette méthode doit être appelée à partir du destructeur.|
|[reserve_message](#reserve_message)|En cas de substitution dans une classe dérivée, réserve un message précédemment offert par cet objet `source_block`.|
|[resume_propagation](#resume_propagation)|En cas de substitution dans une classe dérivée, reprend la propagation après la libération d’une réservation.|
|[sync_send](#sync_send)|Met en file d’attente de manière synchrone les messages et démarre une tâche de propagation, si ce n’est déjà fait.|
|[unlink_target_notification](#unlink_target_notification)|Rappel qui notifie la dissociation d’une cible de cet objet `source_block`.|
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|Attend la fin de toutes les propagations asynchrones. Cette attente de rotation spécifique au propagateur est utilisée dans les destructeurs de blocs de message pour s’assurer que toutes les propagations asynchrones ont le temps de se terminer avant de détruire le bloc.|

## <a name="remarks"></a>Notes

Les blocs de messages doivent dériver de ce bloc pour tirer parti de la gestion et de la synchronisation des liens fournis par cette classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[ISource](isource-class.md)

`source_block`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="accept"></a>valide

Accepte un message qui a été proposé par cet objet `source_block`, en transférant la propriété à l’appelant.

```cpp
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` proposé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `accept`.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet `message` dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le paramètre `_PTarget` est `NULL`.

La méthode `accept` est appelée par une cible lorsqu’un message est proposé par ce bloc de `ISource`. Le pointeur de message retourné peut être différent de celui passé dans la méthode `propagate` du bloc `ITarget`, si cette source décide d’effectuer une copie du message.

## <a name="accept_message"></a>accept_message

En cas de substitution dans une classe dérivée, accepte un message proposé par la source. Les blocs de messages doivent remplacer cette méthode pour valider le `_MsgId` et retourner un message.

```cpp
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Identité de l’objet d’exécution de l’objet `message`.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le message dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

Pour transférer la propriété, le pointeur de message d’origine doit être retourné. Pour maintenir la propriété, une copie de la charge utile de message doit être effectuée et retournée.

## <a name="acquire_ref"></a>acquire_ref

Acquiert un décompte de références sur cet objet `source_block` pour empêcher la suppression.

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par un objet `ITarget` qui est lié à cette source pendant la méthode `link_target`.

## <a name="async_send"></a>async_send

Met en file d’attente de manière asynchrone les messages et démarre une tâche de propagation, si ce n’est déjà fait

```cpp
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Paramètres

*_Msg*<br/>
Pointeur vers un objet `message` à envoyer de façon asynchrone.

## <a name="consume"></a>occuper

Consomme un message précédemment offert par cet objet `source_block` et correctement réservé par la cible, en transférant la propriété à l’appelant.

```cpp
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` réservé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `consume`.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet `message` dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le paramètre `_PTarget` est `NULL`.

La méthode lève une exception [bad_target](bad-target-class.md) si le paramètre `_PTarget` ne représente pas la cible qui a appelé `reserve`.

La méthode `consume` est semblable à `accept`, mais doit toujours être précédée d’un appel à `reserve` qui a retourné la **valeur true**.

## <a name="consume_message"></a>consume_message

En cas de substitution dans une classe dérivée, consomme un message qui a été précédemment réservé.

```cpp
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` qui est consommé.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le message dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

Semblable à `accept`, mais est toujours précédé d’un appel à `reserve`.

## <a name="enable_batched_processing"></a>enable_batched_processing

Active le traitement par lots pour ce bloc.

```cpp
void enable_batched_processing();
```

## <a name="initialize_source"></a>initialize_source

Initialise le `message_propagator` dans ce `source_block`.

```cpp
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Paramètres

*_PScheduler*<br/>
Planificateur à utiliser pour planifier les tâches.

*_PScheduleGroup*<br/>
Groupe de planification à utiliser pour planifier les tâches.

## <a name="link_target"></a>link_target

Lie un bloc cible à cet objet `source_block`.

```cpp
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers un bloc `ITarget` à lier à cet objet `source_block`.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le paramètre `_PTarget` est `NULL`.

## <a name="link_target_notification"></a>link_target_notification

Rappel qui signale qu’une nouvelle cible a été liée à cet objet `source_block`.

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```

## <a name="process_input_messages"></a>process_input_messages

Traiter les messages d’entrée. Cela est utile uniquement pour les blocs de propagation, qui dérivent de source_block

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message qui doit être traité.

## <a name="propagate_output_messages"></a>propagate_output_messages

Propager les messages aux cibles.

```cpp
virtual void propagate_output_messages();
```

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

En cas de substitution dans une classe dérivée, propage le message donné à tout ou partie des cibles liées. Il s’agit de la routine de propagation principale pour les blocs de message.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message qui doit être propagé.

## <a name="release"></a>3/05

Libère une réservation de message réussie précédente.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` réservé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `release`.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le paramètre `_PTarget` est `NULL`.

La méthode lève une exception [bad_target](bad-target-class.md) si le paramètre `_PTarget` ne représente pas la cible qui a appelé `reserve`.

## <a name="release_message"></a>release_message

En cas de substitution dans une classe dérivée, libère une réservation de message précédente.

```cpp
virtual void release_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` en cours de libération.

## <a name="release_ref"></a>release_ref

Libère un décompte de références sur cet objet `source_block`.

```cpp
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un objet `ITarget` qui n’est pas lié à cette source. Le bloc source est autorisé à libérer toutes les ressources réservées pour le bloc cible.

## <a name="remove_targets"></a>remove_targets

Supprime tous les liens cibles pour ce bloc source. Cette méthode doit être appelée à partir du destructeur.

```cpp
void remove_targets();
```

## <a name="reserve"></a>réserver

Réserve un message précédemment offert par cet objet `source_block`.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` proposé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `reserve`.

### <a name="return-value"></a>Valeur de retour

**true** si le message a été réservé, **false** dans le cas contraire. Les réservations peuvent échouer pour de nombreuses raisons, notamment : le message a déjà été réservé ou accepté par une autre cible, la source peut refuser des réservations, et ainsi de suite.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le paramètre `_PTarget` est `NULL`.

Une fois que vous avez appelé `reserve`, si elle est réussie, vous devez appeler `consume` ou `release` pour accepter ou abandonner la possession du message, respectivement.

## <a name="reserve_message"></a>reserve_message

En cas de substitution dans une classe dérivée, réserve un message précédemment offert par cet objet `source_block`.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` qui est réservé.

### <a name="return-value"></a>Valeur de retour

**true** si le message a été réservé, **false** dans le cas contraire.

### <a name="remarks"></a>Notes

Une fois `reserve` appelée, si elle retourne la **valeur true**, `consume` ou `release` doit être appelé pour accepter ou libérer la propriété du message.

## <a name="resume_propagation"></a>resume_propagation

En cas de substitution dans une classe dérivée, reprend la propagation après la libération d’une réservation.

```cpp
virtual void resume_propagation() = 0;
```

## <a name="ctor"></a>source_block

Construit un objet `source_block`.

```cpp
source_block();
```

## <a name="dtor"></a>~ source_block

Détruit l’objet `source_block`.

```cpp
virtual ~source_block();
```

## <a name="sync_send"></a>sync_send

Met en file d’attente de manière synchrone les messages et démarre une tâche de propagation, si ce n’est déjà fait.

```cpp
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Paramètres

*_Msg*<br/>
Pointeur vers un objet `message` à envoyer de façon synchrone.

## <a name="unlink_target"></a>unlink_target

Dissocie un bloc cible de cet objet `source_block`.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers un bloc `ITarget` à dissocier de cet objet `source_block`.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le paramètre `_PTarget` est `NULL`.

## <a name="unlink_target_notification"></a>unlink_target_notification

Rappel qui notifie la dissociation d’une cible de cet objet `source_block`.

```cpp
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Bloc `ITarget` qui n’a pas été lié.

## <a name="unlink_targets"></a>unlink_targets

Dissocie tous les blocs cibles de cet objet `source_block`.

```cpp
virtual void unlink_targets();
```

## <a name="wait_for_outstanding_async_sends"></a>wait_for_outstanding_async_sends

Attend la fin de toutes les propagations asynchrones. Cette attente de rotation spécifique au propagateur est utilisée dans les destructeurs de blocs de message pour s’assurer que toutes les propagations asynchrones ont le temps de se terminer avant de détruire le bloc.

```cpp
void wait_for_outstanding_async_sends();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[ISource, classe](isource-class.md)
