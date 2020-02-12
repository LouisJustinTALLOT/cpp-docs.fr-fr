---
title: choice, classe
ms.date: 11/04/2016
f1_keywords:
- choice
- AGENTS/concurrency::choice
- AGENTS/concurrency::choice::choice
- AGENTS/concurrency::choice::accept
- AGENTS/concurrency::choice::acquire_ref
- AGENTS/concurrency::choice::consume
- AGENTS/concurrency::choice::has_value
- AGENTS/concurrency::choice::index
- AGENTS/concurrency::choice::link_target
- AGENTS/concurrency::choice::release
- AGENTS/concurrency::choice::release_ref
- AGENTS/concurrency::choice::reserve
- AGENTS/concurrency::choice::unlink_target
- AGENTS/concurrency::choice::unlink_targets
- AGENTS/concurrency::choice::value
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
ms.openlocfilehash: 3e718d0d34580d3bf2f13937159e431134631218
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142214"
---
# <a name="choice-class"></a>choice, classe

Un bloc de messagerie `choice` est un bloc à plusieurs sources et à cible unique qui représente une interaction de flux de contrôle avec un jeu de sources. Le bloc choice attend que l'une des multiples sources produise un message et propage l'index de la source qui a généré le message.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    class T
>
class choice: public ISource<size_t>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type basé sur `tuple`représentant les charges utiles des sources d’entrée.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`type`|Alias de type pour `T`.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[sélectionnée](#ctor)|Surchargé. Construit un bloc de messagerie `choice` .|
|[Destructeur ~ Choice](#dtor)|Détruit le bloc de messagerie `choice`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[valide](#accept)|Accepte un message qui a été proposé par ce bloc de `choice`, en transférant la propriété à l’appelant.|
|[acquire_ref](#acquire_ref)|Acquiert un nombre de références sur ce bloc de messagerie `choice` pour empêcher la suppression.|
|[Utiliser](#consume)|Consomme un message précédemment offert par ce `choice` bloc de messagerie et correctement réservé par la cible, en transférant la propriété à l’appelant.|
|[has_value](#has_value)|Vérifie si ce `choice` bloc de messagerie a déjà été initialisé avec une valeur.|
|[index](#index)|Retourne un index dans le `tuple` représentant l’élément sélectionné par le bloc de messagerie `choice`.|
|[link_target](#link_target)|Lie un bloc cible à ce `choice` bloc de messagerie.|
|[release](#release)|Libère une réservation de message réussie précédente.|
|[release_ref](#release_ref)|Libère un nombre de références sur ce bloc de messagerie `choice`.|
|[reserve](#reserve)|Réserve un message précédemment offert par ce `choice` bloc de messagerie.|
|[unlink_target](#unlink_target)|Dissocie un bloc cible de cet `choice` bloc de messagerie.|
|[unlink_targets](#unlink_targets)|Dissocie toutes les cibles de cette `choice` bloc de messagerie. (Substitue [ISource :: unlink_targets](isource-class.md#unlink_targets).)|
|[value](#value)|Obtient le message dont l’index a été sélectionné par le bloc de messagerie `choice`.|

## <a name="remarks"></a>Notes

Le bloc Choice garantit qu’un seul des messages entrants est consommé.

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="accept"></a>valide

Accepte un message qui a été proposé par ce bloc de `choice`, en transférant la propriété à l’appelant.

```cpp
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` proposé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `accept`.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le message dont l’appelant est désormais propriétaire.

## <a name="acquire_ref"></a>acquire_ref

Acquiert un nombre de références sur ce bloc de messagerie `choice` pour empêcher la suppression.

```cpp
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un objet `ITarget` qui est lié à cette source pendant la méthode `link_target`.

## <a name="ctor"></a>sélectionnée

Construit un bloc de messagerie `choice` .

```cpp
explicit choice(
    T _Tuple);

choice(
    Scheduler& _PScheduler,
    T _Tuple);

choice(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

choice(
    choice&& _Choice);
```

### <a name="parameters"></a>Paramètres

*_Tuple*<br/>
`tuple` de sources pour choice.

*_PScheduler*<br/>
Objet `Scheduler` dans lequel la tâche de propagation du bloc de messagerie `choice` est planifiée.

*_PScheduleGroup*<br/>
Objet `ScheduleGroup` dans lequel la tâche de propagation du bloc de messagerie `choice` est planifiée. L’objet `Scheduler` utilisé est suggéré par le groupe de planification.

*_Choice*<br/>
Bloc de messagerie `choice` à partir duquel la copie est effectuée. Notez que l’objet d'origine est orphelin, ce qui en fait un constructeur de déplacement.

### <a name="remarks"></a>Notes

Le runtime utilise le planificateur par défaut si vous ne spécifiez pas les paramètres `_PScheduler` ou `_PScheduleGroup` .

La construction du déplacement ne s’exécute pas en présence d’un verrou, ce qui signifie que c’est à l’utilisateur de s’assurer qu’il n’y a pas de tâches non activables en vol au moment du déplacement. Sinon, de nombreuses courses peuvent se produire, ce qui aboutit à des exceptions ou à un état incohérent.

## <a name="dtor"></a>~ choix

Détruit le bloc de messagerie `choice`.

```cpp
~choice();
```

## <a name="consume"></a>occuper

Consomme un message précédemment offert par ce `choice` bloc de messagerie et correctement réservé par la cible, en transférant la propriété à l’appelant.

```cpp
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
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

## <a name="has_value"></a>has_value

Vérifie si ce `choice` bloc de messagerie a déjà été initialisé avec une valeur.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le bloc a reçu une valeur, **false** dans le cas contraire.

## <a name="index"></a>évaluer

Retourne un index dans le `tuple` représentant l’élément sélectionné par le bloc de messagerie `choice`.

```cpp
size_t index();
```

### <a name="return-value"></a>Valeur de retour

Index du message.

### <a name="remarks"></a>Notes

La charge utile de message peut être extraite à l’aide de la méthode `get`.

## <a name="link_target"></a>link_target

Lie un bloc cible à ce `choice` bloc de messagerie.

```cpp
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers un bloc `ITarget` à lier à ce bloc de messagerie `choice`.

## <a name="release"></a>3/05

Libère une réservation de message réussie précédente.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` en cours de libération.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `release`.

## <a name="release_ref"></a>release_ref

Libère un nombre de références sur ce bloc de messagerie `choice`.

```cpp
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un objet `ITarget` qui n’est pas lié à cette source. Le bloc source est autorisé à libérer toutes les ressources réservées pour le bloc cible.

## <a name="reserve"></a>réserver

Réserve un message précédemment offert par ce `choice` bloc de messagerie.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity` de l’objet `message` qui est réservé.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la méthode `reserve`.

### <a name="return-value"></a>Valeur de retour

**true** si le message a été réservé, **false** dans le cas contraire. Les réservations peuvent échouer pour de nombreuses raisons, notamment : le message a déjà été réservé ou accepté par une autre cible, la source peut refuser des réservations, et ainsi de suite.

### <a name="remarks"></a>Notes

Une fois que vous avez appelé `reserve`, si elle est réussie, vous devez appeler `consume` ou `release` pour accepter ou abandonner la possession du message, respectivement.

## <a name="unlink_target"></a>unlink_target

Dissocie un bloc cible de cet `choice` bloc de messagerie.

```cpp
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers un bloc `ITarget` à dissocier de ce `choice` bloc de messagerie.

## <a name="unlink_targets"></a>unlink_targets

Dissocie toutes les cibles de cette `choice` bloc de messagerie.

```cpp
virtual void unlink_targets();
```

### <a name="remarks"></a>Notes

Cette méthode n’a pas besoin d’être appelée à partir du destructeur, car le destructeur du bloc `single_assignment` interne se dissocie correctement.

## <a name="value"></a>ajoutée

Obtient le message dont l’index a été sélectionné par le bloc de messagerie `choice`.

```cpp
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>Paramètres

*_Payload_type*<br/>
Type de la charge utile de message.

### <a name="return-value"></a>Valeur de retour

Charge de travail du message.

### <a name="remarks"></a>Notes

Étant donné qu’un bloc de messagerie `choice` peut prendre des entrées avec différents types de charge utile, vous devez spécifier le type de la charge utile au point de récupération. Vous pouvez déterminer le type en fonction du résultat de la méthode `index`.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[join, classe](join-class.md)<br/>
[single_assignment, classe](single-assignment-class.md)
