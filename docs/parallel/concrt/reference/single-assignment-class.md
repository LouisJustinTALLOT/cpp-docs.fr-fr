---
title: single_assignment, classe
ms.date: 11/04/2016
f1_keywords:
- single_assignment
- AGENTS/concurrency::single_assignment
- AGENTS/concurrency::single_assignment::single_assignment
- AGENTS/concurrency::single_assignment::has_value
- AGENTS/concurrency::single_assignment::value
- AGENTS/concurrency::single_assignment::accept_message
- AGENTS/concurrency::single_assignment::consume_message
- AGENTS/concurrency::single_assignment::link_target_notification
- AGENTS/concurrency::single_assignment::propagate_message
- AGENTS/concurrency::single_assignment::propagate_to_any_targets
- AGENTS/concurrency::single_assignment::release_message
- AGENTS/concurrency::single_assignment::reserve_message
- AGENTS/concurrency::single_assignment::resume_propagation
- AGENTS/concurrency::single_assignment::send_message
helpviewer_keywords:
- single_assignment class
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
ms.openlocfilehash: 0d302f4f7f85737d9c3b2368e3ae04d88bc1a370
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142740"
---
# <a name="single_assignment-class"></a>single_assignment, classe

Un bloc de messagerie `single_assignment` est un `propagator_block` à cibles multiples, à sources multiples et ordonné, capable de stocker un `message` unique écrit une seule fois.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de charge utile du message stocké et propagé par la mémoire tampon.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[single_assignment](#ctor)|Surchargé. Construit un bloc de messagerie `single_assignment` .|
|[Destructeur ~ single_assignment](#dtor)|Détruit le bloc de messagerie `single_assignment`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[has_value](#has_value)|Vérifie si ce `single_assignment` bloc de messagerie a déjà été initialisé avec une valeur.|
|[value](#value)|Obtient une référence à la charge utile actuelle du message stocké dans le bloc de messagerie `single_assignment`.|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[accept_message](#accept_message)|Accepte un message qui a été proposé par ce bloc de messagerie `single_assignment`, en retournant une copie du message à l’appelant.|
|[consume_message](#consume_message)|Consomme un message précédemment offert par le `single_assignment` et réservé par la cible, en retournant une copie du message à l’appelant.|
|[link_target_notification](#link_target_notification)|Rappel qui signale qu’une nouvelle cible a été liée à ce `single_assignment` bloc de messagerie.|
|[propagate_message](#propagate_message)|Passe de façon asynchrone un message d’un bloc de `ISource` à ce `single_assignment` bloc de messagerie. Elle est appelée par la méthode `propagate`, quand elle est appelée par un bloc source.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Place le `message _PMessage` dans ce bloc de messagerie `single_assignment` et l’offre à toutes les cibles liées.|
|[release_message](#release_message)|Libère une réservation de message précédente. (Substitue [source_block :: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Réserve un message précédemment offert par ce `single_assignment` bloc de messagerie. (Substitue [source_block :: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Reprend la propagation après la libération d’une réservation. (Substitue [source_block :: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Transmet de façon synchrone un message d’un bloc de `ISource` à ce `single_assignment` bloc de messagerie. Elle est appelée par la méthode `send`, quand elle est appelée par un bloc source.|

## <a name="remarks"></a>Notes

Un bloc de messagerie `single_assignment` propage les copies de son message à chaque cible.

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`single_assignment`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="accept_message"></a>accept_message

Accepte un message qui a été proposé par ce bloc de messagerie `single_assignment`, en retournant une copie du message à l’appelant.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` proposé.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet `message` dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

Le bloc de messagerie `single_assignment` retourne des copies du message à ses cibles, au lieu de transférer la propriété du message actuellement détenu.

## <a name="consume_message"></a>consume_message

Consomme un message précédemment offert par le `single_assignment` et réservé par la cible, en retournant une copie du message à l’appelant.

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` qui est consommé.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet `message` dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

Semblable à `accept`, mais est toujours précédé d’un appel à `reserve`.

## <a name="has_value"></a>has_value

Vérifie si ce `single_assignment` bloc de messagerie a déjà été initialisé avec une valeur.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le bloc a reçu une valeur, **false** dans le cas contraire.

## <a name="link_target_notification"></a>link_target_notification

Rappel qui signale qu’une nouvelle cible a été liée à ce `single_assignment` bloc de messagerie.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers la cible nouvellement liée.

## <a name="propagate_message"></a>propagate_message

Passe de façon asynchrone un message d’un bloc de `ISource` à ce `single_assignment` bloc de messagerie. Elle est appelée par la méthode `propagate`, quand elle est appelée par un bloc source.

```cpp
virtual message_status propagate_message(
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

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

Place le `message` `_PMessage` dans ce bloc de messagerie `single_assignment` et l’offre à toutes les cibles liées.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers une `message` que ce `single_assignment` bloc de messagerie a pris possession de.

## <a name="release_message"></a>release_message

Libère une réservation de message précédente.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` en cours de libération.

## <a name="reserve_message"></a>reserve_message

Réserve un message précédemment offert par ce `single_assignment` bloc de messagerie.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` qui est réservé.

### <a name="return-value"></a>Valeur de retour

**true** si le message a été réservé, **false** dans le cas contraire.

### <a name="remarks"></a>Notes

Une fois `reserve` appelée, si elle retourne la **valeur true**, `consume` ou `release` doit être appelé pour accepter ou libérer la propriété du message.

## <a name="resume_propagation"></a>resume_propagation

Reprend la propagation après la libération d’une réservation.

```cpp
virtual void resume_propagation();
```

## <a name="send_message"></a>send_message

Transmet de façon synchrone un message d’un bloc de `ISource` à ce `single_assignment` bloc de messagerie. Elle est appelée par la méthode `send`, quand elle est appelée par un bloc source.

```cpp
virtual message_status send_message(
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

## <a name="ctor"></a>single_assignment

Construit un bloc de messagerie `single_assignment` .

```cpp
single_assignment();

single_assignment(
    filter_method const& _Filter);

single_assignment(
    Scheduler& _PScheduler);

single_assignment(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

single_assignment(
    ScheduleGroup& _PScheduleGroup);

single_assignment(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Paramètres

*_Filter*<br/>
Fonction de filtre qui détermine si les messages offerts doivent être acceptés.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `single_assignment` est planifiée.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `single_assignment` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="remarks"></a>Notes

Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .

Le type `filter_method` est un functor avec la signature `bool (T const &)` qui est appelé par ce `single_assignment` bloc de messagerie pour déterminer s’il doit ou non accepter un message proposé.

## <a name="dtor"></a>~ single_assignment

Détruit le bloc de messagerie `single_assignment`.

```cpp
~single_assignment();
```

## <a name="value"></a>ajoutée

Obtient une référence à la charge utile actuelle du message stocké dans le bloc de messagerie `single_assignment`.

```cpp
T const& value();
```

### <a name="return-value"></a>Valeur de retour

Charge utile du message stocké.

### <a name="remarks"></a>Notes

Cette méthode attend jusqu’à ce qu’un message arrive si aucun message n’est actuellement stocké dans le bloc de messagerie `single_assignment`.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[overwrite_buffer, classe](overwrite-buffer-class.md)<br/>
[Classe unbounded_buffer](unbounded-buffer-class.md)
