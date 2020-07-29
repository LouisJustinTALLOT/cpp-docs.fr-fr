---
title: ITarget, classe
ms.date: 11/04/2016
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
ms.openlocfilehash: 39aebd9d82f098225c1275ac6f43d64fc1ce3ba8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231713"
---
# <a name="itarget-class"></a>ITarget, classe

La classe `ITarget` est l'interface de tous les blocs cibles. Les blocs cibles consomment les messages qui leur sont offerts par les blocs `ISource`.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class ITarget;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données de la charge utile dans les messages acceptés par le bloc cible.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`filter_method`|Signature de toute méthode utilisée par le bloc qui retourne une **`bool`** valeur pour déterminer si un message proposé doit être accepté.|
|`type`|Alias de type pour `T` .|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[~ ITarget, destructeur](#dtor)|Détruit l' `ITarget` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[propager](#propagate)|En cas de substitution dans une classe dérivée, passe de façon asynchrone un message d’un bloc source à ce bloc cible.|
|[envoyer](#send)|En cas de substitution dans une classe dérivée, passe de façon synchrone un message au bloc cible.|
|[supports_anonymous_source](#supports_anonymous_source)|En cas de substitution dans une classe dérivée, retourne la valeur true ou false selon que le bloc de message accepte ou non les messages offerts par une source qui n’est pas liée à celui-ci. Si la méthode substituée retourne **`true`** , la cible ne peut pas reporter un message proposé, car la consommation d’un message différé à un moment ultérieur nécessite que la source soit identifiée dans son registre de liens source.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[link_source](#link_source)|En cas de substitution dans une classe dérivée, lie un bloc source spécifié à ce `ITarget` bloc.|
|[unlink_source](#unlink_source)|En cas de substitution dans une classe dérivée, dissocie un bloc source spécifié de ce `ITarget` bloc.|
|[unlink_sources](#unlink_sources)|En cas de substitution dans une classe dérivée, dissocie tous les blocs sources de ce `ITarget` bloc.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ITarget`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="itarget"></a><a name="dtor"></a>~ ITarget

Détruit l' `ITarget` objet.

```cpp
virtual ~ITarget();
```

## <a name="link_source"></a><a name="link_source"></a>link_source

En cas de substitution dans une classe dérivée, lie un bloc source spécifié à ce `ITarget` bloc.

```cpp
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Paramètres

*_PSource*<br/>
`ISource`Bloc lié à ce `ITarget` bloc.

### <a name="remarks"></a>Notes

Cette fonction ne doit pas être appelée directement sur un `ITarget` bloc. Les blocs doivent être connectés ensemble à l’aide de la `link_target` méthode sur `ISource` les blocs, qui appellera la `link_source` méthode sur la cible correspondante.

## <a name="propagate"></a><a name="propagate"></a>propager

En cas de substitution dans une classe dérivée, passe de façon asynchrone un message d’un bloc source à ce bloc cible.

```cpp
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui offre le message.

### <a name="return-value"></a>Valeur de retour

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le `_PMessage` `_PSource` paramètre ou a la valeur `NULL` .

## <a name="send"></a><a name="send"></a>Envoyer

En cas de substitution dans une classe dérivée, passe de façon synchrone un message au bloc cible.

```cpp
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers l'objet `message`.

*_PSource*<br/>
Pointeur vers le bloc source qui offre le message.

### <a name="return-value"></a>Valeur de retour

Une [message_status](concurrency-namespace-enums.md) indication de ce que la cible A décidé de faire avec le message.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) si le `_PMessage` `_PSource` paramètre ou a la valeur `NULL` .

L’utilisation `send` de la méthode en dehors de l’initiation du message et de la propagation des messages au sein d’un réseau est dangereuse et peut entraîner un interblocage.

Lorsque `send` retourne, le message a déjà été accepté, puis transféré dans le bloc cible, ou il a été refusé par la cible.

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a>supports_anonymous_source

En cas de substitution dans une classe dérivée, retourne la valeur true ou false selon que le bloc de message accepte ou non les messages offerts par une source qui n’est pas liée à celui-ci. Si la méthode substituée retourne **`true`** , la cible ne peut pas reporter un message proposé, car la consommation d’un message différé à un moment ultérieur nécessite que la source soit identifiée dans son registre de liaisons de l’alimentation.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si le bloc peut accepter le message d’une source qui n’est pas liée à celui-ci dans le **`false`** cas contraire.

## <a name="unlink_source"></a><a name="unlink_source"></a>unlink_source

En cas de substitution dans une classe dérivée, dissocie un bloc source spécifié de ce `ITarget` bloc.

```cpp
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Paramètres

*_PSource*<br/>
`ISource`Bloc en cours de dissociation de ce `ITarget` bloc.

### <a name="remarks"></a>Notes

Cette fonction ne doit pas être appelée directement sur un `ITarget` bloc. Les blocs doivent être déconnectés à l’aide des `unlink_target` `unlink_targets` méthodes ou sur des `ISource` blocs, qui appellera la `unlink_source` méthode sur la cible correspondante.

## <a name="unlink_sources"></a><a name="unlink_sources"></a>unlink_sources

En cas de substitution dans une classe dérivée, dissocie tous les blocs sources de ce `ITarget` bloc.

```cpp
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[ISource (classe)](isource-class.md)
