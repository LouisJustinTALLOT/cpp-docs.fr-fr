---
title: multitype_join, classe
ms.date: 11/04/2016
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
ms.openlocfilehash: 4214c43fa0d0ab8fdd29ed54738c19f72a07267a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138950"
---
# <a name="multitype_join-class"></a>multitype_join, classe

Un bloc de messagerie `multitype_join` est un bloc de messagerie à sources multiples et à cible unique qui combine des messages de types différents en provenance de chacune de ses sources et qui offre un tuple des messages combinés à ses cibles.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
`tuple` type de charge utile des messages joints et propagés par le bloc.

*_Jtype*<br/>
Type de `join` bloc, `greedy` ou `non_greedy`

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`type`|Alias de type pour `T`.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[multitype_join](#ctor)|Surchargé. Construit un bloc de messagerie `multitype_join` .|
|[Destructeur ~ multitype_join](#dtor)|Détruit le bloc de messagerie `multitype_join`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[valide](#accept)|Accepte un message qui a été proposé par ce bloc de `multitype_join`, en transférant la propriété à l’appelant.|
|[acquire_ref](#acquire_ref)|Acquiert un nombre de références sur ce bloc de messagerie `multitype_join` pour empêcher la suppression.|
|[Utiliser](#consume)|Consomme un message précédemment offert par le bloc de messagerie `multitype_join` et a été réservé par la cible, en transférant la propriété à l’appelant.|
|[link_target](#link_target)|Lie un bloc cible à ce `multitype_join` bloc de messagerie.|
|[release](#release)|Libère une réservation de message réussie précédente.|
|[release_ref](#release_ref)|Libère un nombre de références sur ce bloc de messagerie `multiple_join`.|
|[reserve](#reserve)|Réserve un message précédemment offert par ce `multitype_join` bloc de messagerie.|
|[unlink_target](#unlink_target)|Dissocie un bloc cible de cet `multitype_join` bloc de messagerie.|
|[unlink_targets](#unlink_targets)|Dissocie toutes les cibles de cette `multitype_join` bloc de messagerie. (Substitue [ISource :: unlink_targets](isource-class.md#unlink_targets).)|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="accept"></a>valide

Accepte un message qui a été proposé par ce bloc de `multitype_join`, en transférant la propriété à l’appelant.

```cpp
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` proposé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `accept`.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le message dont l’appelant est désormais propriétaire.

## <a name="acquire_ref"></a>acquire_ref

Acquiert un nombre de références sur ce bloc de messagerie `multitype_join` pour empêcher la suppression.

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un objet `ITarget` qui est lié à cette source pendant la méthode `link_target`.

## <a name="consume"></a>occuper

Consomme un message précédemment offert par le bloc de messagerie `multitype_join` et a été réservé par la cible, en transférant la propriété à l’appelant.

```cpp
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` réservé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `consume`.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet `message` dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

La méthode `consume` est semblable à `accept`, mais doit toujours être précédée d’un appel à `reserve` qui a retourné la **valeur true**.

## <a name="link_target"></a>link_target

Lie un bloc cible à ce `multitype_join` bloc de messagerie.

```cpp
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers un bloc `ITarget` à lier à ce bloc de messagerie `multitype_join`.

## <a name="ctor"></a>multitype_join

Construit un bloc de messagerie `multitype_join` .

```cpp
explicit multitype_join(
    T _Tuple);

multitype_join(
    Scheduler& _PScheduler,
    T _Tuple);

multitype_join(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

multitype_join(
    multitype_join&& _Join);
```

### <a name="parameters"></a>Paramètres

*_Tuple*<br/>
`tuple` de sources pour ce bloc de messagerie `multitype_join` .

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `multitype_join` est planifiée.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `multitype_join` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

*_Join*<br/>
Bloc de messagerie `multitype_join` à partir duquel la copie est effectuée. Notez que l’objet d'origine est orphelin, ce qui en fait un constructeur de déplacement.

### <a name="remarks"></a>Notes

Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .

La construction du déplacement ne s’exécute pas en présence d’un verrou, ce qui signifie que c’est à l’utilisateur de s’assurer qu’il n’y a pas de tâches non activables en vol au moment du déplacement. Sinon, de nombreuses courses peuvent se produire, ce qui aboutit à des exceptions ou à un état incohérent.

## <a name="dtor"></a>~ multitype_join

Détruit le bloc de messagerie `multitype_join`.

```cpp
~multitype_join();
```

## <a name="release"></a>3/05

Libère une réservation de message réussie précédente.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` en cours de libération.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `release`.

## <a name="release_ref"></a>release_ref

Libère un nombre de références sur ce bloc de messagerie `multiple_join`.

```cpp
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un objet `ITarget` qui n’est pas lié à cette source. Le bloc source est autorisé à libérer toutes les ressources réservées pour le bloc cible.

## <a name="reserve"></a>réserver

Réserve un message précédemment offert par ce `multitype_join` bloc de messagerie.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` qui est réservé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `reserve`.

### <a name="return-value"></a>Valeur de retour

`true` si le message a été réservé avec succès, `false` dans le cas contraire. Les réservations peuvent échouer pour de nombreuses raisons, notamment : le message a déjà été réservé ou accepté par une autre cible, la source peut refuser des réservations, et ainsi de suite.

### <a name="remarks"></a>Notes

Une fois que vous avez appelé `reserve`, si elle est réussie, vous devez appeler `consume` ou `release` pour accepter ou abandonner la possession du message, respectivement.

## <a name="unlink_target"></a>unlink_target

Dissocie un bloc cible de cet `multitype_join` bloc de messagerie.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers un bloc `ITarget` à dissocier de ce `multitype_join` bloc de messagerie.

## <a name="unlink_targets"></a>unlink_targets

Dissocie toutes les cibles de cette `multitype_join` bloc de messagerie.

```cpp
virtual void unlink_targets();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[choice, classe](choice-class.md)<br/>
[join, classe](join-class.md)
