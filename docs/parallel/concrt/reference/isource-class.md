---
description: 'En savoir plus sur : classe ISource'
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
ms.openlocfilehash: 86a55c9ca056c0aebb98e00c12518293b316bcb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334440"
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

|Nom|Description|
|----------|-----------------|
|`source_type`|Alias de type pour `T` .|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[~, Destructeur de ISource](#dtor)|Détruit l' `ISource` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[valide](#accept)|En cas de substitution dans une classe dérivée, accepte un message qui a été proposé par ce `ISource` bloc, en transférant la propriété à l’appelant.|
|[acquire_ref](#acquire_ref)|En cas de substitution dans une classe dérivée, acquiert un décompte de références sur ce `ISource` bloc pour empêcher la suppression.|
|[occuper](#consume)|En cas de substitution dans une classe dérivée, consomme un message précédemment offert par ce `ISource` bloc et correctement réservé par la cible, en transférant la propriété à l’appelant.|
|[link_target](#link_target)|En cas de substitution dans une classe dérivée, lie un bloc cible à ce `ISource` bloc.|
|[3/05](#release)|En cas de substitution dans une classe dérivée, libère une réservation de message réussie précédente.|
|[release_ref](#release_ref)|En cas de substitution dans une classe dérivée, libère un décompte de références sur ce `ISource` bloc.|
|[reserve](#reserve)|En cas de substitution dans une classe dérivée, réserve un message précédemment offert par ce `ISource` bloc.|
|[unlink_target](#unlink_target)|En cas de substitution dans une classe dérivée, dissocie un bloc cible de ce `ISource` bloc, s’il est trouvé précédemment lié.|
|[unlink_targets](#unlink_targets)|En cas de substitution dans une classe dérivée, dissocie tous les blocs cibles de ce `ISource` bloc.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ISource`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="accept"></a><a name="accept"></a> valide

En cas de substitution dans une classe dérivée, accepte un message qui a été proposé par ce `ISource` bloc, en transférant la propriété à l’appelant.

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l’objet proposé `message` .

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la `accept` méthode.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le message dont l’appelant est désormais propriétaire.

### <a name="remarks"></a>Notes

La `accept` méthode est appelée par une cible lorsqu’un message est proposé par ce `ISource` bloc. Le pointeur de message retourné peut être différent de celui passé dans la `propagate` méthode du `ITarget` bloc, si cette source décide d’effectuer une copie du message.

## <a name="acquire_ref"></a><a name="acquire_ref"></a> acquire_ref

En cas de substitution dans une classe dérivée, acquiert un décompte de références sur ce `ISource` bloc pour empêcher la suppression.

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un `ITarget` objet qui est lié à cette source au cours de la `link_target` méthode.

## <a name="consume"></a><a name="consume"></a> occuper

En cas de substitution dans une classe dérivée, consomme un message précédemment offert par ce `ISource` bloc et correctement réservé par la cible, en transférant la propriété à l’appelant.

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
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

## <a name="isource"></a><a name="dtor"></a> ~ ISource

Détruit l' `ISource` objet.

```cpp
virtual ~ISource();
```

## <a name="link_target"></a><a name="link_target"></a> link_target

En cas de substitution dans une classe dérivée, lie un bloc cible à ce `ISource` bloc.

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui est lié à ce `ISource` bloc.

## <a name="release"></a><a name="release"></a> 3/05

En cas de substitution dans une classe dérivée, libère une réservation de message réussie précédente.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l’objet réservé `message` .

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la `release` méthode.

## <a name="release_ref"></a><a name="release_ref"></a> release_ref

En cas de substitution dans une classe dérivée, libère un décompte de références sur ce `ISource` bloc.

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un `ITarget` objet qui n’est pas lié à cette source. Le bloc source est autorisé à libérer toutes les ressources réservées pour le bloc cible.

## <a name="reserve"></a><a name="reserve"></a> réserver

En cas de substitution dans une classe dérivée, réserve un message précédemment offert par ce `ISource` bloc.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l’objet proposé `message` .

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la `reserve` méthode.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le message a été réservé avec succès ; **`false`** sinon,. Les réservations peuvent échouer pour de nombreuses raisons, notamment : le message a déjà été réservé ou accepté par une autre cible, la source peut refuser des réservations, et ainsi de suite.

### <a name="remarks"></a>Notes

Après avoir appelé `reserve` , en cas de tentative réussie, vous devez appeler `consume` ou `release` pour accepter ou abandonner la détention du message, respectivement.

## <a name="unlink_target"></a><a name="unlink_target"></a> unlink_target

En cas de substitution dans une classe dérivée, dissocie un bloc cible de ce `ISource` bloc, s’il est trouvé précédemment lié.

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui est dissocié de ce `ISource` bloc.

## <a name="unlink_targets"></a><a name="unlink_targets"></a> unlink_targets

En cas de substitution dans une classe dérivée, dissocie tous les blocs cibles de ce `ISource` bloc.

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[ITarget, classe](itarget-class.md)
