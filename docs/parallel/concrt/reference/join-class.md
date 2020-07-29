---
title: join, classe
ms.date: 11/04/2016
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
ms.openlocfilehash: c65eed8abafe424fa27c5b9a72d3c73b7127b68e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219584"
---
# <a name="join-class"></a>join, classe

Un bloc de messagerie `join` est un `propagator_block` à cible unique, à sources multiples et ordonné qui combine des messages de type `T` en provenance de chacune de ses sources.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de charge utile des messages joints et propagés par le bloc.

*_Jtype*<br/>
Type de `join` bloc qui est, `greedy` ou`non_greedy`

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[join](#ctor)|Surchargé. Construit un bloc de messagerie `join` .|
|[~, destructeur de jointure](#dtor)|Détruit le `join` bloc.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[accept_message](#accept_message)|Accepte un message qui a été proposé par ce `join` bloc de messagerie, en transférant la propriété à l’appelant.|
|[consume_message](#consume_message)|Consomme un message précédemment offert par le `join` bloc de messagerie et réservé par la cible, en transférant la propriété à l’appelant.|
|[link_target_notification](#link_target_notification)|Rappel qui signale qu’une nouvelle cible a été liée à ce `join` bloc de messagerie.|
|[propagate_message](#propagate_message)|Passe de façon asynchrone un message d’un `ISource` bloc à ce `join` bloc de messagerie. Elle est appelée par la `propagate` méthode, quand elle est appelée par un bloc source.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Construit un message de sortie contenant un message d’entrée à partir de chaque source lorsqu’il a tous propagé un message. Envoie ce message de sortie à chacune de ses cibles.|
|[release_message](#release_message)|Libère une réservation de message précédente. (Substitue [source_block :: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Réserve un message précédemment offert par ce `join` bloc de messagerie. (Substitue [source_block :: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Reprend la propagation après la libération d’une réservation. (Substitue [source_block :: resume_propagation](source-block-class.md#resume_propagation).)|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`join`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

Accepte un message qui a été proposé par ce `join` bloc de messagerie, en transférant la propriété à l’appelant.

```cpp
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l’objet proposé `message` .

### <a name="return-value"></a>Valeur de retour

Pointeur vers l' `message` objet dont l’appelant est désormais propriétaire.

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

Consomme un message précédemment offert par le `join` bloc de messagerie et réservé par la cible, en transférant la propriété à l’appelant.

```cpp
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l' `message` objet consommé.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l' `message` objet dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

Semblable à `accept` , mais est toujours précédé d’un appel à `reserve` .

## <a name="join"></a><a name="ctor"></a>réflexive

Construit un bloc de messagerie `join` .

```cpp
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Paramètres

*_NumInputs*<br/>
Nombre d’entrées autorisées dans ce `join` bloc.

*_Filter*<br/>
Fonction de filtre qui détermine si les messages offerts doivent être acceptés.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `join` est planifiée.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `join` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="remarks"></a>Notes

Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .

Le type `filter_method` est un functor avec la signature `bool (T const &)` qui est appelé par ce `join` bloc de messagerie pour déterminer s’il doit ou non accepter un message proposé.

## <a name="join"></a><a name="dtor"></a>~ joindre

Détruit le `join` bloc.

```cpp
~join();
```

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

Rappel qui signale qu’une nouvelle cible a été liée à ce `join` bloc de messagerie.

```cpp
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

Passe de façon asynchrone un message d’un `ISource` bloc à ce `join` bloc de messagerie. Elle est appelée par la `propagate` méthode, quand elle est appelée par un bloc source.

```cpp
message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui offre le message.

### <a name="return-value"></a>Valeur de retour

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

Construit un message de sortie contenant un message d’entrée à partir de chaque source lorsqu’il a tous propagé un message. Envoie ce message de sortie à chacune de ses cibles.

```cpp
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```

## <a name="release_message"></a><a name="release_message"></a>release_message

Libère une réservation de message précédente.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l' `message` objet en cours de libération.

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

Réserve un message précédemment offert par ce `join` bloc de messagerie.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l’objet proposé `message` .

### <a name="return-value"></a>Valeur de retour

**`true`** Si le message a été réservé avec succès ; **`false`** sinon,.

### <a name="remarks"></a>Notes

Après `reserve` l’appel de, s’il retourne **`true`** , `consume` ou `release` doit être appelé pour accepter ou libérer la propriété du message.

## <a name="resume_propagation"></a><a name="resume_propagation"></a>resume_propagation

Reprend la propagation après la libération d’une réservation.

```cpp
virtual void resume_propagation();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe Choice](choice-class.md)<br/>
[Classe multitype_join](multitype-join-class.md)
