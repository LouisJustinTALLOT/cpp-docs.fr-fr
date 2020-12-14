---
description: 'En savoir plus sur : classe Timer'
title: Classe timer
ms.date: 11/04/2016
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
ms.openlocfilehash: 460185f61be0dd33fe11dfa0f94e2147893089d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188168"
---
# <a name="timer-class"></a>Classe timer

Un bloc de messagerie `timer` est un `source_block` à cible unique, capable d'envoyer un message à sa cible après un délai spécifié ou à intervalles spécifiques.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de charge utile des messages de sortie de ce bloc.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[minute](#ctor)|Surchargé. Construit un `timer` bloc de messagerie qui activera un message donné après un intervalle spécifié.|
|[~ Timer, destructeur](#dtor)|Détruit un `timer` bloc de messagerie.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[pause](#pause)|Arrête le `timer` bloc de messagerie. S’il s’agit d’un `timer` bloc de messagerie répétitif, il peut être redémarré avec un `start()` appel ultérieur. Pour les minuteurs qui ne se répètent pas, cela a le même effet qu’un `stop` appel.|
|[start](#start)|Démarre le `timer` bloc de messagerie. Nombre de millisecondes spécifié après l’appel de, la valeur spécifiée est propagée en aval en tant que `message` .|
|[stop](#stop)|Arrête le `timer` bloc de messagerie.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[accept_message](#accept_message)|Accepte un message qui a été proposé par ce `timer` bloc de messagerie, en transférant la propriété à l’appelant.|
|[consume_message](#consume_message)|Consomme un message précédemment offert par le `timer` et réservé par la cible, en transférant la propriété à l’appelant.|
|[link_target_notification](#link_target_notification)|Rappel qui signale qu’une nouvelle cible a été liée à ce `timer` bloc de messagerie.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Tente d’offrir le message produit par le `timer` bloc à toutes les cibles liées.|
|[release_message](#release_message)|Libère une réservation de message précédente. (Substitue [source_block :: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Réserve un message précédemment offert par ce `timer` bloc de messagerie. (Substitue [source_block :: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Reprend la propagation après la libération d’une réservation. (Substitue [source_block :: resume_propagation](source-block-class.md#resume_propagation).)|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

[source_block](source-block-class.md)

`timer`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="accept_message"></a><a name="accept_message"></a> accept_message

Accepte un message qui a été proposé par ce `timer` bloc de messagerie, en transférant la propriété à l’appelant.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l’objet proposé `message` .

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `message` objet dont l’appelant est désormais propriétaire.

## <a name="consume_message"></a><a name="consume_message"></a> consume_message

Consomme un message précédemment offert par le `timer` et réservé par la cible, en transférant la propriété à l’appelant.

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l' `message` objet consommé.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `message` objet dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

Semblable à `accept` , mais est toujours précédé d’un appel à `reserve` .

## <a name="link_target_notification"></a><a name="link_target_notification"></a> link_target_notification

Rappel qui signale qu’une nouvelle cible a été liée à ce `timer` bloc de messagerie.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers la cible nouvellement liée.

## <a name="pause"></a><a name="pause"></a> suspen

Arrête le `timer` bloc de messagerie. S’il s’agit d’un `timer` bloc de messagerie répétitif, il peut être redémarré avec un `start()` appel ultérieur. Pour les minuteurs qui ne se répètent pas, cela a le même effet qu’un `stop` appel.

```cpp
void pause();
```

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a> propagate_to_any_targets

Tente d’offrir le message produit par le `timer` bloc à toutes les cibles liées.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
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

Réserve un message précédemment offert par ce `timer` bloc de messagerie.

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

## <a name="start"></a><a name="start"></a> activer

Démarre le `timer` bloc de messagerie. Nombre de millisecondes spécifié après l’appel de, la valeur spécifiée est propagée en aval en tant que `message` .

```cpp
void start();
```

## <a name="stop"></a><a name="stop"></a> erreur

Arrête le `timer` bloc de messagerie.

```cpp
void stop();
```

## <a name="timer"></a><a name="ctor"></a> minute

Construit un `timer` bloc de messagerie qui activera un message donné après un intervalle spécifié.

```cpp
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```

### <a name="parameters"></a>Paramètres

*_Ms*<br/>
Nombre de millisecondes qui doivent s’écouler après l’appel de Start pour que le message spécifié soit propagé en aval.

*value*<br/>
Valeur qui sera propagée en aval lorsque la minuterie s’écoulera.

*_PTarget*<br/>
Cible vers laquelle la minuterie propage son message.

*_Repeating*<br/>
Si la valeur est true, indique que la minuterie se déclenchera périodiquement toutes les `_Ms` millisecondes.

*_Scheduler*<br/>
L' `Scheduler` objet dans lequel la tâche de propagation du `timer` bloc de messagerie est planifiée est planifié.

*_ScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `timer` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="remarks"></a>Notes

Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_Scheduler` ou `_ScheduleGroup` .

## <a name="timer"></a><a name="dtor"></a> ~ minuterie

Détruit un `timer` bloc de messagerie.

```cpp
~timer();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
