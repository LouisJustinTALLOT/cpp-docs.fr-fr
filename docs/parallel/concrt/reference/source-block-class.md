---
title: source_block, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4a184e0fee76f3aa5bb8f7729250c03b10b9dfc
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163489"
---
# <a name="sourceblock-class"></a>source_block, classe

La classe `source_block` est une classe de base abstraite pour les blocs sources uniquement. La classe fournit une fonctionnalité de gestion des liens de base ainsi que des vérifications d'erreurs courantes.

## <a name="syntax"></a>Syntaxe

```
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```

#### <a name="parameters"></a>Paramètres

*_TargetLinkRegistry*<br/>
Registre de lien à utiliser pour contenir les liens de la cible.

*_MessageProcessorType*<br/>
Type de processeur pour le traitement du message.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`target_iterator`|Itérateur à parcourir les cibles connectées.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[source_block](#ctor)|Construit un objet `source_block`.|
|[~ source_block, destructeur](#dtor)|Détruit le `source_block` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[accept](#accept)|Accepte un message qui a été proposé par ce `source_block` objet, en transférant la propriété à l’appelant.|
|[acquire_ref](#acquire_ref)|Acquiert un décompte de références sur ce `source_block` objet, pour empêcher la suppression.|
|[consommer](#consume)|Consomme un message précédemment proposé par ce `source_block` de l’objet et réservé avec succès par la cible, en transférant la propriété à l’appelant.|
|[link_target](#link_target)|Lie un bloc cible à ce `source_block` objet.|
|[release](#release)|Libère une réservation de message réussie précédente.|
|[release_ref](#release_ref)|Libère un décompte de références sur ce `source_block` objet.|
|[reserve](#reserve)|Réserve un message précédemment proposé par ce `source_block` objet.|
|[unlink_target](#unlink_target)|Dissocie un bloc cible de ce `source_block` objet.|
|[unlink_targets](#unlink_targets)|Dissocie tous les blocs de cibles à partir de ce `source_block` objet. (Substitue [ISource::unlink_targets](isource-class.md#unlink_targets).)|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[accept_message](#accept_message)|En cas de substitution dans une classe dérivée, accepte un message envoyé par la source. Blocs de messages doivent substituer cette méthode pour valider le `_MsgId` et retourner un message.|
|[async_send](#async_send)|Les files d’attente des messages de façon asynchrone et démarre une tâche de propagation, si cela n’a pas déjà été fait|
|[consume_message](#consume_message)|En cas de substitution dans une classe dérivée, consomme un message qui a été réservé précédemment.|
|[enable_batched_processing](#enable_batched_processing)|Active par lot de traitement pour ce bloc.|
|[initialize_source](#initialize_source)|Initialise le `message_propagator` dans cet `source_block`.|
|[link_target_notification](#link_target_notification)|Rappel qui notifie qu’une nouvelle cible a été liée à ce `source_block` objet.|
|[process_input_messages](#process_input_messages)|Traiter les messages d’entrée. Cela est utile uniquement pour les blocs propagateurs, qui dérivent de source_block|
|[propagate_output_messages](#propagate_output_messages)|Propager des messages aux cibles.|
|[propagate_to_any_targets](#propagate_to_any_targets)|En cas de substitution dans une classe dérivée, propage le message donné dans une ou toutes les cibles liées. Il s’agit de la routine de propagation principale pour les blocs de messages.|
|[release_message](#release_message)|En cas de substitution dans une classe dérivée, libère une réservation de message précédent.|
|[remove_targets](#remove_targets)|Supprime tous les liens de cible de ce bloc source. Cela doit être appelée à partir du destructeur.|
|[reserve_message](#reserve_message)|En cas de substitution dans une classe dérivée, réserve un message précédemment proposé par ce `source_block` objet.|
|[resume_propagation](#resume_propagation)|En cas de substitution dans une classe dérivée, reprend la propagation après qu’une réservation a été libérée.|
|[sync_send](#sync_send)|Mode synchrone les files d’attente des messages et démarre une tâche de propagation, si cela n’a pas déjà été fait.|
|[unlink_target_notification](#unlink_target_notification)|Un rappel qui informe qu’une cible a été dissociée à partir de ce `source_block` objet.|
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|Attend que toutes les propagations asynchrones soient terminées. Cette attente de rotation spécifique au propagateur est utilisée dans les destructeurs de blocs de messages pour vous assurer que toutes les propagations asynchrones ont le temps se termine avant de détruire le bloc.|

## <a name="remarks"></a>Notes

Blocs de messages doivent dériver de ce bloc pour tirer parti de la gestion de la liaison et de synchronisation fournies par cette classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

`source_block`

## <a name="requirements"></a>Configuration requise

**En-tête :** agents.h

**Espace de noms :** concurrency

##  <a name="accept"></a> Accepter

Accepte un message qui a été proposé par ce `source_block` objet, en transférant la propriété à l’appelant.

```
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de le proposé `message` objet.

*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `accept` (méthode).

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le `message` que l’appelant a désormais la propriété de l’objet.

### <a name="remarks"></a>Notes

La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le paramètre `_PTarget` est `NULL`.

Le `accept` méthode est appelée par une cible pendant qu’un message est offert par ce `ISource` bloc. Le pointeur de message retourné peut être différent de celui passé dans le `propagate` méthode de la `ITarget` bloquer, si cette source décide d’effectuer une copie du message.

##  <a name="accept_message"></a> accept_message

En cas de substitution dans une classe dérivée, accepte un message envoyé par la source. Blocs de messages doivent substituer cette méthode pour valider le `_MsgId` et retourner un message.

```
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
L’identité d’objet runtime le `message` objet.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le message dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

Pour transférer la propriété, le pointeur de message d’origine doit être retourné. Pour maintenir la propriété, une copie de la charge utile de message doit être effectuée et renvoyée.

##  <a name="acquire_ref"></a> acquire_ref

Acquiert un décompte de références sur ce `source_block` objet, pour empêcher la suppression.

```
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par un `ITarget` objet lié à cette source pendant le `link_target` (méthode).

##  <a name="async_send"></a> async_send

Les files d’attente des messages de façon asynchrone et démarre une tâche de propagation, si cela n’a pas déjà été fait

```
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Paramètres

*_Msg*<br/>
Un pointeur vers un `message` objet à envoyer de façon asynchrone.

##  <a name="consume"></a> consommer

Consomme un message précédemment proposé par ce `source_block` de l’objet et réservé avec succès par la cible, en transférant la propriété à l’appelant.

```
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de réservée `message` objet.

*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `consume` (méthode).

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le `message` que l’appelant a désormais la propriété de l’objet.

### <a name="remarks"></a>Notes

La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le paramètre `_PTarget` est `NULL`.

La méthode lève un [bad_target](bad-target-class.md) exception si le paramètre `_PTarget` ne représente pas la cible qui a appelé `reserve`.

Le `consume` méthode est similaire à `accept`, mais doit toujours être précédé par un appel à `reserve` qui retourné **true**.

##  <a name="consume_message"></a> consume_message

En cas de substitution dans une classe dérivée, consomme un message qui a été réservé précédemment.

```
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de la `message` de l’objet ayant été consommé.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le message dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

Semblable à `accept`, mais est toujours précédé par un appel à `reserve`.

##  <a name="enable_batched_processing"></a> enable_batched_processing

Active par lot de traitement pour ce bloc.

```
void enable_batched_processing();
```

##  <a name="initialize_source"></a> initialize_source

Initialise le `message_propagator` dans cet `source_block`.

```
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Paramètres

*_PScheduler*<br/>
Le planificateur à utiliser pour la planification des tâches.

*_PScheduleGroup*<br/>
Le groupe de planification à utiliser pour la planification des tâches.

##  <a name="link_target"></a> link_target

Lie un bloc cible à ce `source_block` objet.

```
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Un pointeur vers un `ITarget` à lier à ce bloc `source_block` objet.

### <a name="remarks"></a>Notes

La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le paramètre `_PTarget` est `NULL`.

##  <a name="link_target_notification"></a> link_target_notification

Rappel qui notifie qu’une nouvelle cible a été liée à ce `source_block` objet.

```
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```

##  <a name="process_input_messages"></a> process_input_messages

Traiter les messages d’entrée. Cela est utile uniquement pour les blocs propagateurs, qui dérivent de source_block

```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message doit être traité.

##  <a name="propagate_output_messages"></a> propagate_output_messages

Propager des messages aux cibles.

```
virtual void propagate_output_messages();
```

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

En cas de substitution dans une classe dérivée, propage le message donné dans une ou toutes les cibles liées. Il s’agit de la routine de propagation principale pour les blocs de messages.

```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message qui doit être propagée.

##  <a name="release"></a> Mise en production

Libère une réservation de message réussie précédente.

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de réservée `message` objet.

*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `release` (méthode).

### <a name="remarks"></a>Notes

La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le paramètre `_PTarget` est `NULL`.

La méthode lève un [bad_target](bad-target-class.md) exception si le paramètre `_PTarget` ne représente pas la cible qui a appelé `reserve`.

##  <a name="release_message"></a> release_message

En cas de substitution dans une classe dérivée, libère une réservation de message précédent.

```
virtual void release_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de la `message` de l’objet qui est libéré.

##  <a name="release_ref"></a> release_ref

Libère un décompte de références sur ce `source_block` objet.

```
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un `ITarget` objet dissocié de cette source. Le bloc source est autorisé à libérer les ressources réservées pour le bloc cible.

##  <a name="remove_targets"></a> remove_targets

Supprime tous les liens de cible de ce bloc source. Cela doit être appelée à partir du destructeur.

```
void remove_targets();
```

##  <a name="reserve"></a> réserver

Réserve un message précédemment proposé par ce `source_block` objet.

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de le proposé `message` objet.

*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `reserve` (méthode).

### <a name="return-value"></a>Valeur de retour

**true** si le message a été réservé avec succès, **false** dans le cas contraire. Les réservations peuvent échouer pour de nombreuses raisons, notamment : le message a été déjà réservé ou accepté par une autre cible, la source peut refuser des réservations et ainsi de suite.

### <a name="remarks"></a>Notes

La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le paramètre `_PTarget` est `NULL`.

Après avoir appelé `reserve`, si elle réussit, vous devez appeler `consume` ou `release` afin d’accepter ou renoncer à la possession du message, respectivement.

##  <a name="reserve_message"></a> reserve_message

En cas de substitution dans une classe dérivée, réserve un message précédemment proposé par ce `source_block` objet.

```
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de la `message` de l’objet en cours de réservation.

### <a name="return-value"></a>Valeur de retour

**true** si le message a été réservé avec succès, **false** dans le cas contraire.

### <a name="remarks"></a>Notes

Après avoir `reserve` est appelée, si elle retourne **true**, soit `consume` ou `release` doit être appelé pour accepter ou libérer la propriété du message.

##  <a name="resume_propagation"></a> resume_propagation

En cas de substitution dans une classe dérivée, reprend la propagation après qu’une réservation a été libérée.

```
virtual void resume_propagation() = 0;
```

##  <a name="ctor"></a> source_block

Construit un objet `source_block`.

```
source_block();
```

##  <a name="dtor"></a> ~ source_block

Détruit le `source_block` objet.

```
virtual ~source_block();
```

##  <a name="sync_send"></a> sync_send

Mode synchrone les files d’attente des messages et démarre une tâche de propagation, si cela n’a pas déjà été fait.

```
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Paramètres

*_Msg*<br/>
Un pointeur vers un `message` objet à envoyer de façon synchrone.

##  <a name="unlink_target"></a> unlink_target

Dissocie un bloc cible de ce `source_block` objet.

```
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Un pointeur vers un `ITarget` à dissocier de ce bloc `source_block` objet.

### <a name="remarks"></a>Notes

La méthode lève un [invalid_argument](../../../standard-library/invalid-argument-class.md) exception si le paramètre `_PTarget` est `NULL`.

##  <a name="unlink_target_notification"></a> unlink_target_notification

Un rappel qui informe qu’une cible a été dissociée à partir de ce `source_block` objet.

```
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Le `ITarget` bloc qui a été dissocié.

##  <a name="unlink_targets"></a> unlink_targets

Dissocie tous les blocs de cibles à partir de ce `source_block` objet.

```
virtual void unlink_targets();
```

##  <a name="wait_for_outstanding_async_sends"></a> wait_for_outstanding_async_sends

Attend que toutes les propagations asynchrones soient terminées. Cette attente de rotation spécifique au propagateur est utilisée dans les destructeurs de blocs de messages pour vous assurer que toutes les propagations asynchrones ont le temps se termine avant de détruire le bloc.

```
void wait_for_outstanding_async_sends();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[ISource, classe](isource-class.md)
