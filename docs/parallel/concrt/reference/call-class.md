---
title: call, classe
ms.date: 11/04/2016
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
helpviewer_keywords:
- call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
ms.openlocfilehash: 445e368ced9d9c8faf30351ecaeecc4e1b8a59f2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142835"
---
# <a name="call-class"></a>call, classe

Un bloc de messagerie `call` est un `target_block` ordonné à plusieurs sources qui appelle une fonction spécifiée lors de la réception d'un message.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de charge utile des messages propagés à ce bloc.

*_FunctorType*<br/>
Signature des fonctions que ce bloc peut accepter.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[invoqu](#ctor)|Surchargé. Construit un bloc de messagerie `call` .|
|[~ Call, destructeur](#dtor)|Détruit le bloc de messagerie `call`.|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[process_input_messages](#process_input_messages)|Exécute la fonction d’appel sur les messages d’entrée.|
|[process_message](#process_message)|Traite un message qui a été accepté par ce `call` bloc de messagerie.|
|[propagate_message](#propagate_message)|Passe de façon asynchrone un message d’un bloc de `ISource` à ce `call` bloc de messagerie. Elle est appelée par la méthode `propagate`, quand elle est appelée par un bloc source.|
|[send_message](#send_message)|Transmet de façon synchrone un message d’un bloc de `ISource` à ce `call` bloc de messagerie. Elle est appelée par la méthode `send`, quand elle est appelée par un bloc source.|
|[supports_anonymous_source](#supports_anonymous_source)|Substitue la méthode `supports_anonymous_source` pour indiquer que ce bloc peut accepter des messages qui lui sont offerts par une source qui n’est pas liée. (Substitue [ITarget :: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ITarget](itarget-class.md)

[target_block](target-block-class.md)

`call`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="ctor"></a>invoqu

Construit un bloc de messagerie `call` .

```cpp
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Paramètres

*_Func*<br/>
Fonction qui sera appelée pour chaque message accepté.

*_Filter*<br/>
Fonction de filtre qui détermine si les messages offerts doivent être acceptés.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `call` est planifiée.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `call` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

### <a name="remarks"></a>Notes

Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .

Le type `_Call_method` est un functor avec la signature `void (T const &)` qui est appelé par ce `call` bloc de messagerie pour traiter un message.

Le type `filter_method` est un functor avec la signature `bool (T const &)` qui est appelé par ce `call` bloc de messagerie pour déterminer s’il doit ou non accepter un message proposé.

## <a name="dtor"></a>~ appeler

Détruit le bloc de messagerie `call`.

```cpp
~call();
```

## <a name="process_input_messages"></a>process_input_messages

Exécute la fonction d’appel sur les messages d’entrée.

```cpp
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message qui doit être géré.

## <a name="process_message"></a>process_message

Traite un message qui a été accepté par ce `call` bloc de messagerie.

```cpp
virtual void process_message(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Paramètres

*_PMessage*<br/>
Pointeur vers le message qui doit être géré.

## <a name="propagate_message"></a>propagate_message

Passe de façon asynchrone un message d’un bloc de `ISource` à ce `call` bloc de messagerie. Elle est appelée par la méthode `propagate`, quand elle est appelée par un bloc source.

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

## <a name="send_message"></a>send_message

Transmet de façon synchrone un message d’un bloc de `ISource` à ce `call` bloc de messagerie. Elle est appelée par la méthode `send`, quand elle est appelée par un bloc source.

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

## <a name="supports_anonymous_source"></a>supports_anonymous_source

Substitue la méthode `supports_anonymous_source` pour indiquer que ce bloc peut accepter des messages qui lui sont offerts par une source qui n’est pas liée.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Valeur de retour

**true** car le bloc n’ajourne pas les messages offerts.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[transformer, classe](transformer-class.md)
