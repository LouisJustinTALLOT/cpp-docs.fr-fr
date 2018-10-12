---
title: multitype_join, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e8a06068d7a9bec4fd828941da409780eeed457
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163659"
---
# <a name="multitypejoin-class"></a>multitype_join, classe

Un bloc de messagerie `multitype_join` est un bloc de messagerie à sources multiples et à cible unique qui combine des messages de types différents en provenance de chacune de ses sources et qui offre un tuple des messages combinés à ses cibles.

## <a name="syntax"></a>Syntaxe

```
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le `tuple` type de charge utile des messages joints et propagés par le bloc.

*_Jtype*<br/>
Le genre de `join` bloc est `greedy` ou `non_greedy`

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`type`|Alias de type pour `T`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[multitype_join](#ctor)|Surchargé. Construit un bloc de messagerie `multitype_join` .|
|[~ multitype_join, destructeur](#dtor)|Détruit le `multitype_join` bloc de messagerie.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[accept](#accept)|Accepte un message qui a été proposé par ce `multitype_join` bloc, en transférant la propriété à l’appelant.|
|[acquire_ref](#acquire_ref)|Acquiert un décompte de références sur ce `multitype_join` bloc de messagerie, pour empêcher la suppression.|
|[consommer](#consume)|Consomme un message précédemment proposé par le `multitype_join` bloc de messagerie et réservé avec succès par la cible, en transférant la propriété à l’appelant.|
|[link_target](#link_target)|Lie un bloc cible à ce `multitype_join` bloc de messagerie.|
|[release](#release)|Libère une réservation de message réussie précédente.|
|[release_ref](#release_ref)|Libère un décompte de références sur ce `multiple_join` bloc de messagerie.|
|[reserve](#reserve)|Réserve un message précédemment proposé par ce `multitype_join` bloc de messagerie.|
|[unlink_target](#unlink_target)|Dissocie un bloc cible de ce `multitype_join` bloc de messagerie.|
|[unlink_targets](#unlink_targets)|Dissocie toutes les cibles à partir de ce `multitype_join` bloc de messagerie. (Substitue [ISource::unlink_targets](isource-class.md#unlink_targets).)|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [des blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>Configuration requise

**En-tête :** agents.h

**Espace de noms :** concurrency

##  <a name="accept"></a> Accepter

Accepte un message qui a été proposé par ce `multitype_join` bloc, en transférant la propriété à l’appelant.

```
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de le proposé `message` objet.

*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `accept` (méthode).

### <a name="return-value"></a>Valeur de retour

Pointeur vers le message dont l’appelant est désormais propriétaire.

##  <a name="acquire_ref"></a> acquire_ref

Acquiert un décompte de références sur ce `multitype_join` bloc de messagerie, pour empêcher la suppression.

```
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un `ITarget` objet lié à cette source pendant le `link_target` (méthode).

##  <a name="consume"></a> consommer

Consomme un message précédemment proposé par le `multitype_join` bloc de messagerie et réservé avec succès par la cible, en transférant la propriété à l’appelant.

```
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de réservée `message` objet.

*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `consume` (méthode).

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le `message` que l’appelant a désormais la propriété de l’objet.

### <a name="remarks"></a>Notes

Le `consume` méthode est similaire à `accept`, mais doit toujours être précédé par un appel à `reserve` qui retourné **true**.

##  <a name="link_target"></a> link_target

Lie un bloc cible à ce `multitype_join` bloc de messagerie.

```
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Un pointeur vers un `ITarget` à lier à ce bloc `multitype_join` bloc de messagerie.

##  <a name="ctor"></a> multitype_join

Construit un bloc de messagerie `multitype_join` .

```
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

*_Joindre les*<br/>
Bloc de messagerie `multitype_join` à partir duquel la copie est effectuée. Notez que l’objet d'origine est orphelin, ce qui en fait un constructeur de déplacement.

### <a name="remarks"></a>Notes

Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .

La construction du déplacement ne s’exécute pas en présence d’un verrou, ce qui signifie que c’est à l’utilisateur de s’assurer qu’il n’y a pas de tâches non activables en vol au moment du déplacement. Sinon, de nombreuses courses peuvent se produire, ce qui aboutit à des exceptions ou à un état incohérent.

##  <a name="dtor"></a> ~multitype_join

Détruit le `multitype_join` bloc de messagerie.

```
~multitype_join();
```

##  <a name="release"></a> Mise en production

Libère une réservation de message réussie précédente.

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de la `message` de l’objet qui est libéré.

*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `release` (méthode).

##  <a name="release_ref"></a> release_ref

Libère un décompte de références sur ce `multiple_join` bloc de messagerie.

```
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un `ITarget` objet dissocié de cette source. Le bloc source est autorisé à libérer les ressources réservées pour le bloc cible.

##  <a name="reserve"></a> réserver

Réserve un message précédemment proposé par ce `multitype_join` bloc de messagerie.

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de la `message` de l’objet en cours de réservation.

*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `reserve` (méthode).

### <a name="return-value"></a>Valeur de retour

`true` Si le message a été réservé avec succès, `false` dans le cas contraire. Les réservations peuvent échouer pour de nombreuses raisons, notamment : le message a été déjà réservé ou accepté par une autre cible, la source peut refuser des réservations et ainsi de suite.

### <a name="remarks"></a>Notes

Après avoir appelé `reserve`, si elle réussit, vous devez appeler `consume` ou `release` afin d’accepter ou renoncer à la possession du message, respectivement.

##  <a name="unlink_target"></a> unlink_target

Dissocie un bloc cible de ce `multitype_join` bloc de messagerie.

```
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Un pointeur vers un `ITarget` à dissocier de ce bloc `multitype_join` bloc de messagerie.

##  <a name="unlink_targets"></a> unlink_targets

Dissocie toutes les cibles à partir de ce `multitype_join` bloc de messagerie.

```
virtual void unlink_targets();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[choice, classe](choice-class.md)<br/>
[join, classe](join-class.md)
