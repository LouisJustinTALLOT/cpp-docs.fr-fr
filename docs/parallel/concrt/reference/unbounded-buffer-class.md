---
description: 'En savoir plus sur : classe unbounded_buffer'
title: Classe unbounded_buffer
ms.date: 11/04/2016
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
ms.openlocfilehash: c9cd31209831dc915ae7a4aacaad5cddc0203176
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188103"
---
# <a name="unbounded_buffer-class"></a>Classe unbounded_buffer

Un bloc de messagerie `unbounded_buffer` est un `propagator_block` à cibles multiples, à sources multiples et ordonné, capable de stocker un nombre illimité de messages.

## <a name="syntax"></a>Syntaxe

```cpp
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

### <a name="parameters"></a>Paramètres

*_Type*<br/>
Type de charge utile des messages stockés et propagés par la mémoire tampon.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[unbounded_buffer](#ctor)|Surchargé. Construit un `unbounded_buffer` bloc de messagerie.|
|[Destructeur ~ unbounded_buffer](#dtor)|Détruit le `unbounded_buffer` bloc de messagerie.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[retrait](#dequeue)|Supprime un élément du `unbounded_buffer` bloc de messagerie.|
|[Enqueue](#enqueue)|Ajoute un élément au `unbounded_buffer` bloc de messagerie.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[accept_message](#accept_message)|Accepte un message qui a été proposé par ce `unbounded_buffer` bloc de messagerie, en transférant la propriété à l’appelant.|
|[consume_message](#consume_message)|Consomme un message précédemment offert par le `unbounded_buffer` bloc de messagerie et réservé par la cible, en transférant la propriété à l’appelant.|
|[link_target_notification](#link_target_notification)|Rappel qui signale qu’une nouvelle cible a été liée à ce `unbounded_buffer` bloc de messagerie.|
|[process_input_messages](#process_input_messages)|Place le `message` `_PMessage` dans ce `unbounded_buffer` bloc de messagerie et tente de l’offrir à toutes les cibles liées.|
|[propagate_message](#propagate_message)|Passe de façon asynchrone un message d’un `ISource` bloc à ce `unbounded_buffer` bloc de messagerie. Elle est appelée par la `propagate` méthode, quand elle est appelée par un bloc source.|
|[propagate_output_messages](#propagate_output_messages)|Place le `message` `_PMessage` dans ce `unbounded_buffer` bloc de messagerie et tente de l’offrir à toutes les cibles liées. (Substitue [source_block ::p ropagate_output_messages](source-block-class.md#propagate_output_messages).)|
|[release_message](#release_message)|Libère une réservation de message précédente. (Substitue [source_block :: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Réserve un message précédemment offert par ce `unbounded_buffer` bloc de messagerie. (Substitue [source_block :: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Reprend la propagation après la libération d’une réservation. (Substitue [source_block :: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Transmet de façon synchrone un message d’un `ISource` bloc à ce `unbounded_buffer` bloc de messagerie. Elle est appelée par la `send` méthode, quand elle est appelée par un bloc source.|
|[supports_anonymous_source](#supports_anonymous_source)|Substitue la `supports_anonymous_source` méthode pour indiquer que ce bloc peut accepter des messages qui lui sont offerts par une source qui n’est pas liée. (Substitue [ITarget :: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

Pour plus d’informations, consultez [blocs de messages asynchrones](../asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="accept_message"></a><a name="accept_message"></a> accept_message

Accepte un message qui a été proposé par ce `unbounded_buffer` bloc de messagerie, en transférant la propriété à l’appelant.

```cpp
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l’objet proposé `message` .

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `message` objet dont l’appelant est désormais propriétaire.

## <a name="consume_message"></a><a name="consume_message"></a> consume_message

Consomme un message précédemment offert par le `unbounded_buffer` bloc de messagerie et réservé par la cible, en transférant la propriété à l’appelant.

```cpp
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l' `message` objet consommé.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `message` objet dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

Semblable à `accept` , mais est toujours précédé d’un appel à `reserve` .

## <a name="dequeue"></a><a name="dequeue"></a> retrait

Supprime un élément du `unbounded_buffer` bloc de messagerie.

```cpp
_Type dequeue();
```

### <a name="return-value"></a>Valeur renvoyée

Charge utile du message supprimé de `unbounded_buffer` .

## <a name="enqueue"></a><a name="enqueue"></a> Enqueue

Ajoute un élément au `unbounded_buffer` bloc de messagerie.

```cpp
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>Paramètres

*_Item*<br/>
Élément à ajouter.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément a été accepté ; **`false`** sinon,.

## <a name="link_target_notification"></a><a name="link_target_notification"></a> link_target_notification

Rappel qui signale qu’une nouvelle cible a été liée à ce `unbounded_buffer` bloc de messagerie.

```cpp
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers la cible nouvellement liée.

## <a name="propagate_message"></a><a name="propagate_message"></a> propagate_message

Passe de façon asynchrone un message d’un `ISource` bloc à ce `unbounded_buffer` bloc de messagerie. Elle est appelée par la `propagate` méthode, quand elle est appelée par un bloc source.

```cpp
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui offre le message.

### <a name="return-value"></a>Valeur renvoyée

Une [message_status](concurrency-namespace-enums.md#message_status) indication de ce que la cible A décidé de faire avec le message.

## <a name="propagate_output_messages"></a><a name="propagate_output_messages"></a> propagate_output_messages

Place le `message` `_PMessage` dans ce `unbounded_buffer` bloc de messagerie et tente de l’offrir à toutes les cibles liées.

```cpp
virtual void propagate_output_messages();
```

### <a name="remarks"></a>Notes

Si un autre message est déjà en avance dans le `unbounded_buffer` , la propagation aux cibles liées n’a pas lieu tant que les messages précédents n’ont pas été acceptés ou consommés. La première cible liée est correctement `accept` ou `consume` le message est propriétaire, et aucune autre cible ne peut alors recevoir le message.

## <a name="process_input_messages"></a><a name="process_input_messages"></a> process_input_messages

Place le `message` `_PMessage` dans ce `unbounded_buffer` bloc de messagerie et tente de l’offrir à toutes les cibles liées.

```cpp
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message qui doit être traité.

## <a name="release_message"></a><a name="release_message"></a> release_message

Libère une réservation de message précédente.

```cpp
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l' `message` objet en cours de libération.

## <a name="reserve_message"></a><a name="reserve_message"></a> reserve_message

Réserve un message précédemment offert par ce `unbounded_buffer` bloc de messagerie.

```cpp
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
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

Transmet de façon synchrone un message d’un `ISource` bloc à ce `unbounded_buffer` bloc de messagerie. Elle est appelée par la `send` méthode, quand elle est appelée par un bloc source.

```cpp
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui offre le message.

### <a name="return-value"></a>Valeur renvoyée

Une [message_status](concurrency-namespace-enums.md#message_status) indication de ce que la cible A décidé de faire avec le message.

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a> supports_anonymous_source

Substitue la `supports_anonymous_source` méthode pour indiquer que ce bloc peut accepter des messages qui lui sont offerts par une source qui n’est pas liée.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** parce que le bloc n’ajourne pas les messages offerts.

## <a name="unbounded_buffer"></a><a name="ctor"></a> unbounded_buffer

Construit un `unbounded_buffer` bloc de messagerie.

```cpp
unbounded_buffer();

unbounded_buffer(
   filter_method const&                 _Filter
);

unbounded_buffer(
   Scheduler&                 _PScheduler
);

unbounded_buffer(
   Scheduler&                 _PScheduler,
   filter_method const&                 _Filter
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup,
   filter_method const&                 _Filter
);
```

### <a name="parameters"></a>Paramètres

*_Filter*<br/>
Fonction de filtre qui détermine si les messages offerts doivent être acceptés.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `unbounded_buffer` est planifiée.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `unbounded_buffer` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="remarks"></a>Notes

Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .

Le type `filter_method` est un functor avec la signature `bool (_Type const &)` qui est appelé par ce `unbounded_buffer` bloc de messagerie pour déterminer s’il doit ou non accepter un message proposé.

## <a name="unbounded_buffer"></a><a name="dtor"></a> ~ unbounded_buffer

Détruit le `unbounded_buffer` bloc de messagerie.

```cpp
~unbounded_buffer();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe overwrite_buffer](overwrite-buffer-class.md)<br/>
[Classe single_assignment](single-assignment-class.md)
