---
description: 'En savoir plus sur : classe multitype_join'
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
ms.openlocfilehash: ee4e3a282bc9fa410140fefb79f31ac5ed9463ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202117"
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
`tuple`Type de charge utile des messages joints et propagés par le bloc.

*_Jtype*<br/>
Type de `join` bloc qui est, `greedy` ou `non_greedy`

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`type`|Alias de type pour `T` .|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[multitype_join](#ctor)|Surchargé. Construit un bloc de messagerie `multitype_join` .|
|[Destructeur ~ multitype_join](#dtor)|Détruit le `multitype_join` bloc de messagerie.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[valide](#accept)|Accepte un message qui a été proposé par ce `multitype_join` bloc, en transférant la propriété à l’appelant.|
|[acquire_ref](#acquire_ref)|Acquiert un nombre de références sur ce `multitype_join` bloc de messagerie pour empêcher la suppression.|
|[occuper](#consume)|Utilise un message précédemment offert par le `multitype_join` bloc de messagerie et correctement réservé par la cible, en transférant la propriété à l’appelant.|
|[link_target](#link_target)|Lie un bloc cible à ce `multitype_join` bloc de messagerie.|
|[3/05](#release)|Libère une réservation de message réussie précédente.|
|[release_ref](#release_ref)|Libère un nombre de références sur ce `multiple_join` bloc de messagerie.|
|[reserve](#reserve)|Réserve un message précédemment offert par ce `multitype_join` bloc de messagerie.|
|[unlink_target](#unlink_target)|Dissocie un bloc cible de ce `multitype_join` bloc de messagerie.|
|[unlink_targets](#unlink_targets)|Dissocie toutes les cibles de ce `multitype_join` bloc de messagerie. (Substitue [ISource :: unlink_targets](isource-class.md#unlink_targets).)|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="accept"></a><a name="accept"></a> valide

Accepte un message qui a été proposé par ce `multitype_join` bloc, en transférant la propriété à l’appelant.

```cpp
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l’objet proposé `message` .

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la `accept` méthode.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le message dont l’appelant est désormais propriétaire.

## <a name="acquire_ref"></a><a name="acquire_ref"></a> acquire_ref

Acquiert un nombre de références sur ce `multitype_join` bloc de messagerie pour empêcher la suppression.

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un `ITarget` objet qui est lié à cette source au cours de la `link_target` méthode.

## <a name="consume"></a><a name="consume"></a> occuper

Utilise un message précédemment offert par le `multitype_join` bloc de messagerie et correctement réservé par la cible, en transférant la propriété à l’appelant.

```cpp
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l’objet réservé `message` .

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la `consume` méthode.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `message` objet dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

La `consume` méthode est semblable à `accept` , mais doit toujours être précédée d’un appel à `reserve` ce retourné **`true`** .

## <a name="link_target"></a><a name="link_target"></a> link_target

Lie un bloc cible à ce `multitype_join` bloc de messagerie.

```cpp
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers un `ITarget` bloc à lier à ce `multitype_join` bloc de messagerie.

## <a name="multitype_join"></a><a name="ctor"></a> multitype_join

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

## <a name="multitype_join"></a><a name="dtor"></a> ~ multitype_join

Détruit le `multitype_join` bloc de messagerie.

```cpp
~multitype_join();
```

## <a name="release"></a><a name="release"></a> 3/05

Libère une réservation de message réussie précédente.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l' `message` objet en cours de libération.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la `release` méthode.

## <a name="release_ref"></a><a name="release_ref"></a> release_ref

Libère un nombre de références sur ce `multiple_join` bloc de messagerie.

```cpp
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un `ITarget` objet qui n’est pas lié à cette source. Le bloc source est autorisé à libérer toutes les ressources réservées pour le bloc cible.

## <a name="reserve"></a><a name="reserve"></a> réserver

Réserve un message précédemment offert par ce `multitype_join` bloc de messagerie.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l' `message` objet qui est réservé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la `reserve` méthode.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le message a été réservé avec succès ; **`false`** sinon,. Les réservations peuvent échouer pour de nombreuses raisons, notamment : le message a déjà été réservé ou accepté par une autre cible, la source peut refuser des réservations, et ainsi de suite.

### <a name="remarks"></a>Notes

Après avoir appelé `reserve` , en cas de tentative réussie, vous devez appeler `consume` ou `release` pour accepter ou abandonner la détention du message, respectivement.

## <a name="unlink_target"></a><a name="unlink_target"></a> unlink_target

Dissocie un bloc cible de ce `multitype_join` bloc de messagerie.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers un `ITarget` bloc à dissocier de ce `multitype_join` bloc de messagerie.

## <a name="unlink_targets"></a><a name="unlink_targets"></a> unlink_targets

Dissocie toutes les cibles de ce `multitype_join` bloc de messagerie.

```cpp
virtual void unlink_targets();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe Choice](choice-class.md)<br/>
[Classe join](join-class.md)
