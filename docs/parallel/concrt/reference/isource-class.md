---
title: ISource, classe
ms.date: 11/04/2016
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
ms.openlocfilehash: a9ef9990db6376536f2f2a15c053b3b1d4ed12cf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139316"
---
# <a name="isource-class"></a>ISource, classe

La classe `ISource` est l'interface de tous les blocs sources. Les blocs sources propagent les messages aux blocs `ITarget`.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class ISource;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données de la charge utile dans les messages produits par le bloc source.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`source_type`|Alias de type pour `T`.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[~, Destructeur de ISource](#dtor)|Détruit l’objet `ISource`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[valide](#accept)|En cas de substitution dans une classe dérivée, accepte un message qui a été proposé par ce bloc `ISource`, en transférant la propriété à l’appelant.|
|[acquire_ref](#acquire_ref)|En cas de substitution dans une classe dérivée, acquiert un nombre de références sur ce bloc de `ISource` pour empêcher la suppression.|
|[Utiliser](#consume)|En cas de substitution dans une classe dérivée, consomme un message précédemment offert par ce `ISource` bloc et correctement réservé par la cible, en transférant la propriété à l’appelant.|
|[link_target](#link_target)|En cas de substitution dans une classe dérivée, lie un bloc cible à ce `ISource` bloc.|
|[release](#release)|En cas de substitution dans une classe dérivée, libère une réservation de message réussie précédente.|
|[release_ref](#release_ref)|En cas de substitution dans une classe dérivée, libère un nombre de références sur ce bloc de `ISource`.|
|[reserve](#reserve)|En cas de substitution dans une classe dérivée, réserve un message précédemment offert par ce bloc de `ISource`.|
|[unlink_target](#unlink_target)|En cas de substitution dans une classe dérivée, dissocie un bloc cible de ce bloc de `ISource`, s’il est trouvé précédemment lié.|
|[unlink_targets](#unlink_targets)|En cas de substitution dans une classe dérivée, dissocie tous les blocs cibles de ce bloc de `ISource`.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ISource`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="accept"></a>valide

En cas de substitution dans une classe dérivée, accepte un message qui a été proposé par ce bloc `ISource`, en transférant la propriété à l’appelant.

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` proposé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `accept`.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le message dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

La méthode `accept` est appelée par une cible lorsqu’un message est proposé par ce bloc de `ISource`. Le pointeur de message retourné peut être différent de celui passé dans la méthode `propagate` du bloc `ITarget`, si cette source décide d’effectuer une copie du message.

## <a name="acquire_ref"></a>acquire_ref

En cas de substitution dans une classe dérivée, acquiert un nombre de références sur ce bloc de `ISource` pour empêcher la suppression.

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un objet `ITarget` qui est lié à cette source pendant la méthode `link_target`.

## <a name="consume"></a>occuper

En cas de substitution dans une classe dérivée, consomme un message précédemment offert par ce `ISource` bloc et correctement réservé par la cible, en transférant la propriété à l’appelant.

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
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

## <a name="dtor"></a>~ ISource

Détruit l’objet `ISource`.

```cpp
virtual ~ISource();
```

## <a name="link_target"></a>link_target

En cas de substitution dans une classe dérivée, lie un bloc cible à ce `ISource` bloc.

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui est lié à ce bloc de `ISource`.

## <a name="release"></a>3/05

En cas de substitution dans une classe dérivée, libère une réservation de message réussie précédente.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` réservé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `release`.

## <a name="release_ref"></a>release_ref

En cas de substitution dans une classe dérivée, libère un nombre de références sur ce bloc de `ISource`.

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un objet `ITarget` qui n’est pas lié à cette source. Le bloc source est autorisé à libérer toutes les ressources réservées pour le bloc cible.

## <a name="reserve"></a>réserver

En cas de substitution dans une classe dérivée, réserve un message précédemment offert par ce bloc de `ISource`.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` proposé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `reserve`.

### <a name="return-value"></a>Valeur de retour

**true** si le message a été réservé, **false** dans le cas contraire. Les réservations peuvent échouer pour de nombreuses raisons, notamment : le message a déjà été réservé ou accepté par une autre cible, la source peut refuser des réservations, et ainsi de suite.

### <a name="remarks"></a>Notes

Une fois que vous avez appelé `reserve`, si elle est réussie, vous devez appeler `consume` ou `release` pour accepter ou abandonner la possession du message, respectivement.

## <a name="unlink_target"></a>unlink_target

En cas de substitution dans une classe dérivée, dissocie un bloc cible de ce bloc de `ISource`, s’il est trouvé précédemment lié.

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui est dissocié de ce bloc de `ISource`.

## <a name="unlink_targets"></a>unlink_targets

En cas de substitution dans une classe dérivée, dissocie tous les blocs cibles de ce bloc de `ISource`.

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[ITarget, classe](itarget-class.md)
