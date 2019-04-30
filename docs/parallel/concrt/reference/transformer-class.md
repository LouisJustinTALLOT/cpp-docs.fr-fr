---
title: Classe transformer
ms.date: 11/04/2016
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
ms.openlocfilehash: c07017539bc0125e9e8c27e208480a50ccc7a719
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408067"
---
# <a name="transformer-class"></a>Classe transformer

Un bloc de messagerie `transformer` est un `propagator_block` à cible unique, à sources multiples et classé qui peut accepter des messages d'un type et est capable de stocker un nombre illimité de messages d'un type différent.

## <a name="syntax"></a>Syntaxe

```
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

#### <a name="parameters"></a>Paramètres

*_Input*<br/>
Type de charge utile des messages acceptés par la mémoire tampon.

*_Output*<br/>
Type de charge utile des messages stockés et propagée à la mémoire tampon.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[transformer](#ctor)|Surchargé. Construit un bloc de messagerie `transformer` .|
|[~ transformer, destructeur](#dtor)|Détruit le `transformer` bloc de messagerie.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[accept_message](#accept_message)|Accepte un message qui a été proposé par ce `transformer` bloc de messagerie, transfert de propriété à l’appelant.|
|[consume_message](#consume_message)|Consomme un message précédemment proposé par le `transformer` et réservé par la cible, en transférant la propriété à l’appelant.|
|[link_target_notification](#link_target_notification)|Rappel qui notifie qu’une nouvelle cible a été liée à ce `transformer` bloc de messagerie.|
|[propagate_message](#propagate_message)|Passe de façon asynchrone un message à partir d’un `ISource` à ce bloc `transformer` bloc de messagerie. Elle est appelée par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Exécute la fonction de transformateur sur les messages d’entrée.|
|[release_message](#release_message)|Libère une réservation de message précédent. (Substitue [source_block::release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Réserve un message précédemment proposé par ce `transformer` bloc de messagerie. (Substitue [source_block::reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Reprend la propagation après qu’une réservation a été libérée. (Substitue [source_block::resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Passe de façon synchrone un message à partir d’un `ISource` à ce bloc `transformer` bloc de messagerie. Elle est appelée par le `send` (méthode), lorsqu’elle est appelée par un bloc source.|
|[supports_anonymous_source](#supports_anonymous_source)|Remplace le `supports_anonymous_source` méthode pour indiquer que ce bloc peut accepter des messages offerts par une source qui n’est pas liée. (Substitue [ITarget::supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [des blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`transformer`

## <a name="requirements"></a>Configuration requise

**En-tête :** agents.h

**Espace de noms :** concurrency

##  <a name="accept_message"></a> accept_message

Accepte un message qui a été proposé par ce `transformer` bloc de messagerie, transfert de propriété à l’appelant.

```
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de le proposé `message` objet.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le `message` que l’appelant a désormais la propriété de l’objet.

##  <a name="consume_message"></a> consume_message

Consomme un message précédemment proposé par le `transformer` et réservé par la cible, en transférant la propriété à l’appelant.

```
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de la `message` de l’objet ayant été consommé.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le `message` que l’appelant a désormais la propriété de l’objet.

### <a name="remarks"></a>Notes

Semblable à `accept`, mais est toujours précédé par un appel à `reserve`.

##  <a name="link_target_notification"></a> link_target_notification

Rappel qui notifie qu’une nouvelle cible a été liée à ce `transformer` bloc de messagerie.

```
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

##  <a name="propagate_message"></a> propagate_message

Passe de façon asynchrone un message à partir d’un `ISource` à ce bloc `transformer` bloc de messagerie. Elle est appelée par le `propagate` (méthode), lorsqu’elle est appelée par un bloc source.

```
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui transmet le message.

### <a name="return-value"></a>Valeur de retour

Un [message_status](concurrency-namespace-enums.md) indication de ce que la cible a décidé de faire avec le message.

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

Exécute la fonction de transformateur sur les messages d’entrée.

```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
```

##  <a name="release_message"></a> release_message

Libère une réservation de message précédent.

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de la `message` de l’objet qui est libéré.

##  <a name="reserve_message"></a> reserve_message

Réserve un message précédemment proposé par ce `transformer` bloc de messagerie.

```
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de la `message` de l’objet en cours de réservation.

### <a name="return-value"></a>Valeur de retour

**true** si le message a été réservé avec succès, **false** dans le cas contraire.

### <a name="remarks"></a>Notes

Après avoir `reserve` est appelée, si elle retourne **true**, soit `consume` ou `release` doit être appelé pour accepter ou libérer la propriété du message.

##  <a name="resume_propagation"></a> resume_propagation

Reprend la propagation après qu’une réservation a été libérée.

```
virtual void resume_propagation();
```

##  <a name="send_message"></a> send_message

Passe de façon synchrone un message à partir d’un `ISource` à ce bloc `transformer` bloc de messagerie. Elle est appelée par le `send` (méthode), lorsqu’elle est appelée par un bloc source.

```
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui transmet le message.

### <a name="return-value"></a>Valeur de retour

Un [message_status](concurrency-namespace-enums.md) indication de ce que la cible a décidé de faire avec le message.

##  <a name="supports_anonymous_source"></a> supports_anonymous_source

Remplace le `supports_anonymous_source` méthode pour indiquer que ce bloc peut accepter des messages offerts par une source qui n’est pas liée.

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Valeur de retour

**true** , car le bloc de ne pas reporter des messages proposés.

##  <a name="ctor"></a> transformateur

Construit un bloc de messagerie `transformer` .

```
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Paramètres

*_Func*<br/>
Une fonction qui sera appelée pour chaque message accepté.

*_PTarget*<br/>
Pointeur vers un bloc cible à lier avec le transformateur.

*_Filter*<br/>
Une fonction de filtre qui détermine si les messages transmis doivent être acceptés.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `transformer` est planifiée.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `transformer` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="remarks"></a>Notes

Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .

Le type `_Transform_method` est un functor avec la signature `_Output (_Input const &)` qui est appelé par ce `transformer` bloc de messagerie pour traiter un message.

Le type `filter_method` est un functor avec la signature `bool (_Input const &)` qui est appelé par ce `transformer` bloc de messagerie pour déterminer s’il doit accepter un message proposé.

##  <a name="dtor"></a> ~transformer

Détruit le `transformer` bloc de messagerie.

```
~transformer();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[call, classe](call-class.md)
