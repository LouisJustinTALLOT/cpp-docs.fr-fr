---
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
ms.openlocfilehash: 7ec574a1f7fce7ab435e2b35b7c3fe9002c3821c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436287"
---
# <a name="choice-class"></a>Classe choice

Un bloc de messagerie `choice` est un bloc à plusieurs sources et à cible unique qui représente une interaction de flux de contrôle avec un jeu de sources. Le bloc choice attend que l'une des multiples sources produise un message et propage l'index de la source qui a généré le message.

## <a name="syntax"></a>Syntaxe

```
template<
    class T
>
class choice: public ISource<size_t>;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Un `tuple`-en fonction du type qui représente les charges utiles des sources d’entrée.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`type`|Alias de type pour `T`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[choix](#ctor)|Surchargé. Construit un bloc de messagerie `choice` .|
|[~ choice, destructeur](#dtor)|Détruit le `choice` bloc de messagerie.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[accept](#accept)|Accepte un message qui a été proposé par ce `choice` bloc, en transférant la propriété à l’appelant.|
|[acquire_ref](#acquire_ref)|Acquiert un décompte de références sur ce `choice` bloc de messagerie, pour empêcher la suppression.|
|[consommer](#consume)|Consomme un message précédemment proposé par ce `choice` bloc de messagerie et réservé avec succès par la cible, en transférant la propriété à l’appelant.|
|[has_value](#has_value)|Vérifie si cela `choice` bloc de messagerie a encore été initialisé avec une valeur.|
|[index](#index)|Retourne un index dans le `tuple` représentant l’élément sélectionné par le `choice` bloc de messagerie.|
|[link_target](#link_target)|Lie un bloc cible à ce `choice` bloc de messagerie.|
|[release](#release)|Libère une réservation de message réussie précédente.|
|[release_ref](#release_ref)|Libère un décompte de références sur ce `choice` bloc de messagerie.|
|[reserve](#reserve)|Réserve un message précédemment proposé par ce `choice` bloc de messagerie.|
|[unlink_target](#unlink_target)|Dissocie un bloc cible de ce `choice` bloc de messagerie.|
|[unlink_targets](#unlink_targets)|Dissocie toutes les cibles à partir de ce `choice` bloc de messagerie. (Substitue [ISource::unlink_targets](isource-class.md#unlink_targets).)|
|[valeur](#value)|Obtient le message dont l’index a été sélectionnée par le `choice` bloc de messagerie.|

## <a name="remarks"></a>Notes

Le bloc choice garantit que seul des messages entrants est consommé.

Pour plus d’informations, consultez [des blocs de messages asynchrones](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>Configuration requise

**En-tête :** agents.h

**Espace de noms :** concurrency

##  <a name="accept"></a> Accepter

Accepte un message qui a été proposé par ce `choice` bloc, en transférant la propriété à l’appelant.

```
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de le proposé `message` objet.

*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `accept` (méthode).

### <a name="return-value"></a>Valeur de retour

Pointeur vers le message dont l’appelant est désormais propriétaire.

##  <a name="acquire_ref"></a> acquire_ref

Acquiert un décompte de références sur ce `choice` bloc de messagerie, pour empêcher la suppression.

```
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un `ITarget` objet lié à cette source pendant le `link_target` (méthode).

##  <a name="ctor"></a> choix

Construit un bloc de messagerie `choice` .

```
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

##  <a name="dtor"></a> ~ choix

Détruit le `choice` bloc de messagerie.

```
~choice();
```

##  <a name="consume"></a> consommer

Consomme un message précédemment proposé par ce `choice` bloc de messagerie et réservé avec succès par la cible, en transférant la propriété à l’appelant.

```
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
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

##  <a name="has_value"></a> has_value

Vérifie si cela `choice` bloc de messagerie a encore été initialisé avec une valeur.

```
bool has_value() const;

```

### <a name="return-value"></a>Valeur de retour

**true** si le bloc a reçu une valeur, **false** dans le cas contraire.

##  <a name="index"></a> Index

Retourne un index dans le `tuple` représentant l’élément sélectionné par le `choice` bloc de messagerie.

```
size_t index();
```

### <a name="return-value"></a>Valeur de retour

L’index de message.

### <a name="remarks"></a>Notes

Charge utile de message peut être extraite à l’aide de la `get` (méthode).

##  <a name="link_target"></a> link_target

Lie un bloc cible à ce `choice` bloc de messagerie.

```
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Un pointeur vers un `ITarget` à lier à ce bloc `choice` bloc de messagerie.

##  <a name="release"></a> Mise en production

Libère une réservation de message réussie précédente.

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de la `message` de l’objet qui est libéré.

*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `release` (méthode).

##  <a name="release_ref"></a> release_ref

Libère un décompte de références sur ce `choice` bloc de messagerie.

```
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Pointeur vers le bloc cible qui appelle cette méthode.

### <a name="remarks"></a>Notes

Cette méthode est appelée par un `ITarget` objet dissocié de cette source. Le bloc source est autorisé à libérer les ressources réservées pour le bloc cible.

##  <a name="reserve"></a> réserver

Réserve un message précédemment proposé par ce `choice` bloc de messagerie.

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_MsgId*<br/>
Le `runtime_object_identity` de la `message` de l’objet en cours de réservation.

*_PTarget*<br/>
Un pointeur vers le bloc cible qui appelle le `reserve` (méthode).

### <a name="return-value"></a>Valeur de retour

**true** si le message a été réservé avec succès, **false** dans le cas contraire. Les réservations peuvent échouer pour de nombreuses raisons, notamment : le message a été déjà réservé ou accepté par une autre cible, la source peut refuser des réservations et ainsi de suite.

### <a name="remarks"></a>Notes

Après avoir appelé `reserve`, si elle réussit, vous devez appeler `consume` ou `release` afin d’accepter ou renoncer à la possession du message, respectivement.

##  <a name="unlink_target"></a> unlink_target

Dissocie un bloc cible de ce `choice` bloc de messagerie.

```
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Un pointeur vers un `ITarget` à dissocier de ce bloc `choice` bloc de messagerie.

##  <a name="unlink_targets"></a> unlink_targets

Dissocie toutes les cibles à partir de ce `choice` bloc de messagerie.

```
virtual void unlink_targets();
```

### <a name="remarks"></a>Notes

Cette méthode n’avez pas besoin d’être appelée à partir du destructeur parce que le destructeur pour interne `single_assignment` bloc dissocie correctement.

##  <a name="value"></a> Valeur

Obtient le message dont l’index a été sélectionnée par le `choice` bloc de messagerie.

```
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>Paramètres

*_Payload_type*<br/>
Le type de charge utile du message.

### <a name="return-value"></a>Valeur de retour

La charge utile du message.

### <a name="remarks"></a>Notes

Étant donné qu’un `choice` bloc de messagerie peut prendre des entrées avec les types de charge utile différente, vous devez spécifier le type de la charge utile au point de récupération. Vous pouvez déterminer le type en fonction du résultat de la `index` (méthode).

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[join, classe](join-class.md)<br/>
[single_assignment, classe](single-assignment-class.md)
