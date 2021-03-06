---
description: 'En savoir plus sur : classe transformer'
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
ms.openlocfilehash: 34d937d1be1c3907ea75d0345bb52bcf359d4f34
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188129"
---
# <a name="transformer-class"></a>Classe transformer

Un bloc de messagerie `transformer` est un `propagator_block` à cible unique, à sources multiples et classé qui peut accepter des messages d'un type et est capable de stocker un nombre illimité de messages d'un type différent.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

### <a name="parameters"></a>Paramètres

*_Input*<br/>
Type de charge utile des messages acceptés par la mémoire tampon.

*_Output*<br/>
Type de charge utile des messages stockés et propagés par la mémoire tampon.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[transformer](#ctor)|Surchargé. Construit un bloc de messagerie `transformer` .|
|[~ transformer, destructeur](#dtor)|Détruit le `transformer` bloc de messagerie.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[accept_message](#accept_message)|Accepte un message qui a été proposé par ce `transformer` bloc de messagerie, en transférant la propriété à l’appelant.|
|[consume_message](#consume_message)|Consomme un message précédemment offert par le `transformer` et réservé par la cible, en transférant la propriété à l’appelant.|
|[link_target_notification](#link_target_notification)|Rappel qui signale qu’une nouvelle cible a été liée à ce `transformer` bloc de messagerie.|
|[propagate_message](#propagate_message)|Passe de façon asynchrone un message d’un `ISource` bloc à ce `transformer` bloc de messagerie. Elle est appelée par la `propagate` méthode, quand elle est appelée par un bloc source.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Exécute la fonction transformateur sur les messages d’entrée.|
|[release_message](#release_message)|Libère une réservation de message précédente. (Substitue [source_block :: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Réserve un message précédemment offert par ce `transformer` bloc de messagerie. (Substitue [source_block :: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Reprend la propagation après la libération d’une réservation. (Substitue [source_block :: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Transmet de façon synchrone un message d’un `ISource` bloc à ce `transformer` bloc de messagerie. Elle est appelée par la `send` méthode, quand elle est appelée par un bloc source.|
|[supports_anonymous_source](#supports_anonymous_source)|Substitue la `supports_anonymous_source` méthode pour indiquer que ce bloc peut accepter des messages qui lui sont offerts par une source qui n’est pas liée. (Substitue [ITarget :: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`transformer`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="accept_message"></a><a name="accept_message"></a> accept_message

Accepte un message qui a été proposé par ce `transformer` bloc de messagerie, en transférant la propriété à l’appelant.

```cpp
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l’objet proposé `message` .

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `message` objet dont l’appelant est désormais propriétaire.

## <a name="consume_message"></a><a name="consume_message"></a> consume_message

Consomme un message précédemment offert par le `transformer` et réservé par la cible, en transférant la propriété à l’appelant.

```cpp
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l' `message` objet consommé.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `message` objet dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

Semblable à `accept` , mais est toujours précédé d’un appel à `reserve` .

## <a name="link_target_notification"></a><a name="link_target_notification"></a> link_target_notification

Rappel qui signale qu’une nouvelle cible a été liée à ce `transformer` bloc de messagerie.

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

## <a name="propagate_message"></a><a name="propagate_message"></a> propagate_message

Passe de façon asynchrone un message d’un `ISource` bloc à ce `transformer` bloc de messagerie. Elle est appelée par la `propagate` méthode, quand elle est appelée par un bloc source.

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui offre le message.

### <a name="return-value"></a>Valeur renvoyée

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a> propagate_to_any_targets

Exécute la fonction transformateur sur les messages d’entrée.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
```

## <a name="release_message"></a><a name="release_message"></a> release_message

Libère une réservation de message précédente.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l' `message` objet en cours de libération.

## <a name="reserve_message"></a><a name="reserve_message"></a> reserve_message

Réserve un message précédemment offert par ce `transformer` bloc de messagerie.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l' `message` objet qui est réservé.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le message a été réservé avec succès ; **`false`** sinon,.

### <a name="remarks"></a>Notes

Après `reserve` l’appel de, s’il retourne **`true`** , `consume` ou `release` doit être appelé pour accepter ou libérer la propriété du message.

## <a name="resume_propagation"></a><a name="resume_propagation"></a> resume_propagation

Reprend la propagation après la libération d’une réservation.

```cpp
virtual void resume_propagation();
```

## <a name="send_message"></a><a name="send_message"></a> send_message

Transmet de façon synchrone un message d’un `ISource` bloc à ce `transformer` bloc de messagerie. Elle est appelée par la `send` méthode, quand elle est appelée par un bloc source.

```cpp
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui offre le message.

### <a name="return-value"></a>Valeur renvoyée

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a> supports_anonymous_source

Substitue la `supports_anonymous_source` méthode pour indiquer que ce bloc peut accepter des messages qui lui sont offerts par une source qui n’est pas liée.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** parce que le bloc n’ajourne pas les messages offerts.

## <a name="transformer"></a><a name="ctor"></a> transformer

Construit un bloc de messagerie `transformer` .

```cpp
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
Fonction qui sera appelée pour chaque message accepté.

*_PTarget*<br/>
Pointeur vers un bloc cible à lier au transformateur.

*_Filter*<br/>
Fonction de filtre qui détermine si les messages offerts doivent être acceptés.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `transformer` est planifiée.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `transformer` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="remarks"></a>Notes

Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .

Le type `_Transform_method` est un functor avec la signature `_Output (_Input const &)` qui est appelé par ce `transformer` bloc de messagerie pour traiter un message.

Le type `filter_method` est un functor avec la signature `bool (_Input const &)` qui est appelé par ce `transformer` bloc de messagerie pour déterminer s’il doit ou non accepter un message proposé.

## <a name="transformer"></a><a name="dtor"></a> ~ transformateur

Détruit le `transformer` bloc de messagerie.

```cpp
~transformer();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Call (classe)](call-class.md)
