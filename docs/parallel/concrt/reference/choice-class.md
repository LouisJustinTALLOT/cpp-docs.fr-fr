---
description: 'En savoir plus sur : classe Choice'
title: Classe choice
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
ms.openlocfilehash: a7597a3bd530185e316cdc42ebbc4696162d498f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254467"
---
# <a name="choice-class"></a>Classe choice

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
`tuple`Type basé sur qui représente les charges utiles des sources d’entrée.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`type`|Alias de type pour `T` .|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[choice](#ctor)|Surchargé. Construit un bloc de messagerie `choice` .|
|[Destructeur ~ Choice](#dtor)|Détruit le `choice` bloc de messagerie.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[valide](#accept)|Accepte un message qui a été proposé par ce `choice` bloc, en transférant la propriété à l’appelant.|
|[acquire_ref](#acquire_ref)|Acquiert un nombre de références sur ce `choice` bloc de messagerie pour empêcher la suppression.|
|[occuper](#consume)|Utilise un message précédemment offert par ce `choice` bloc de messagerie et correctement réservé par la cible, en transférant la propriété à l’appelant.|
|[has_value](#has_value)|Vérifie si ce `choice` bloc de messagerie a déjà été initialisé avec une valeur.|
|[index](#index)|Retourne un index dans le `tuple` représentant l’élément sélectionné par le `choice` bloc de messagerie.|
|[link_target](#link_target)|Lie un bloc cible à ce `choice` bloc de messagerie.|
|[3/05](#release)|Libère une réservation de message réussie précédente.|
|[release_ref](#release_ref)|Libère un nombre de références sur ce `choice` bloc de messagerie.|
|[reserve](#reserve)|Réserve un message précédemment offert par ce `choice` bloc de messagerie.|
|[unlink_target](#unlink_target)|Dissocie un bloc cible de ce `choice` bloc de messagerie.|
|[unlink_targets](#unlink_targets)|Dissocie toutes les cibles de ce `choice` bloc de messagerie. (Substitue [ISource :: unlink_targets](isource-class.md#unlink_targets).)|
|[value](#value)|Obtient le message dont l’index a été sélectionné par le `choice` bloc de messagerie.|

## <a name="remarks"></a>Notes

Le bloc Choice garantit qu’un seul des messages entrants est consommé.

Pour plus d’informations, consultez [blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="accept"></a><a name="accept"></a> valide

Accepte un message qui a été proposé par ce `choice` bloc, en transférant la propriété à l’appelant.

```cpp
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l’objet proposé `message` .

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la `accept` méthode.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le message dont l’appelant est désormais propriétaire.

## <a name="acquire_ref"></a><a name="acquire_ref"></a> acquire_ref

Acquiert un nombre de références sur ce `choice` bloc de messagerie pour empêcher la suppression.

```cpp
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un `ITarget` objet qui est lié à cette source au cours de la `link_target` méthode.

## <a name="choice"></a><a name="ctor"></a> sélectionnée

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

## <a name="choice"></a><a name="dtor"></a> ~ choix

Détruit le `choice` bloc de messagerie.

```cpp
~choice();
```

## <a name="consume"></a><a name="consume"></a> occuper

Utilise un message précédemment offert par ce `choice` bloc de messagerie et correctement réservé par la cible, en transférant la propriété à l’appelant.

```cpp
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
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

## <a name="has_value"></a><a name="has_value"></a> has_value

Vérifie si ce `choice` bloc de messagerie a déjà été initialisé avec une valeur.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le bloc a reçu une valeur ; **`false`** sinon,.

## <a name="index"></a><a name="index"></a> évaluer

Retourne un index dans le `tuple` représentant l’élément sélectionné par le `choice` bloc de messagerie.

```cpp
size_t index();
```

### <a name="return-value"></a>Valeur renvoyée

Index du message.

### <a name="remarks"></a>Notes

La charge utile de message peut être extraite à l’aide de la `get` méthode.

## <a name="link_target"></a><a name="link_target"></a> link_target

Lie un bloc cible à ce `choice` bloc de messagerie.

```cpp
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers un `ITarget` bloc à lier à ce `choice` bloc de messagerie.

## <a name="release"></a><a name="release"></a> 3/05

Libère une réservation de message réussie précédente.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
`runtime_object_identity`De l' `message` objet en cours de libération.

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle la `release` méthode.

## <a name="release_ref"></a><a name="release_ref"></a> release_ref

Libère un nombre de références sur ce `choice` bloc de messagerie.

```cpp
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un `ITarget` objet qui n’est pas lié à cette source. Le bloc source est autorisé à libérer toutes les ressources réservées pour le bloc cible.

## <a name="reserve"></a><a name="reserve"></a> réserver

Réserve un message précédemment offert par ce `choice` bloc de messagerie.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
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

Dissocie un bloc cible de ce `choice` bloc de messagerie.

```cpp
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers un `ITarget` bloc à dissocier de ce `choice` bloc de messagerie.

## <a name="unlink_targets"></a><a name="unlink_targets"></a> unlink_targets

Dissocie toutes les cibles de ce `choice` bloc de messagerie.

```cpp
virtual void unlink_targets();
```

### <a name="remarks"></a>Notes

Cette méthode n’a pas besoin d’être appelée à partir du destructeur, car le destructeur du `single_assignment` bloc interne se dissocie correctement.

## <a name="value"></a>Valeur <a name="value"></a>

Obtient le message dont l’index a été sélectionné par le `choice` bloc de messagerie.

```cpp
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>Paramètres

*_Payload_type*<br/>
Type de la charge utile de message.

### <a name="return-value"></a>Valeur renvoyée

Charge de travail du message.

### <a name="remarks"></a>Notes

Étant donné qu’un `choice` bloc de messagerie peut accepter des entrées avec différents types de charge utile, vous devez spécifier le type de la charge utile au point de récupération. Vous pouvez déterminer le type en fonction du résultat de la `index` méthode.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe join](join-class.md)<br/>
[Classe single_assignment](single-assignment-class.md)
