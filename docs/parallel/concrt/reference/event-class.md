---
title: Event, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- event
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
dev_langs:
- C++
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74e871255e3308450764e8f65cdb6acebe79df38
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437740"
---
# <a name="event-class"></a>event, classe

Événement de réinitialisation manuelle qui a explicitement connaissance du runtime d'accès concurrentiel.

## <a name="syntax"></a>Syntaxe

```
class event;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[~ event, destructeur](#dtor)|Détruit un événement.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[reset](#reset)|Réinitialise l’événement à un état non signalé.|
|[set](#set)|Signale l’événement.|
|[attente](#wait)|Attend que l’événement soit signalé.|
|[wait_for_multiple](#wait_for_multiple)|Attend que plusieurs événements soit signalé.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|Valeur qui indique qu'une attente ne doit jamais expirer.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [les Structures de données de synchronisation](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`event`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> Événement

Construit un nouvel événement.

```
_CRTIMP event();
```

### <a name="remarks"></a>Notes

##  <a name="dtor"></a> ~ événement

Détruit un événement.

```
~event();
```

### <a name="remarks"></a>Notes

Il est probable qu’il n’y a aucun thread n’attend l’événement lorsque le destructeur s’exécute. Ce qui permet de l’événement de destruction de threads en attente sur ce dernier entraîne un comportement non défini.

##  <a name="reset"></a> Réinitialiser

Réinitialise l’événement à un état non signalé.

```
void reset();
```

##  <a name="set"></a> Ensemble

Signale l’événement.

```
void set();
```

### <a name="remarks"></a>Notes

Signalement de l’événement peut entraîner un nombre arbitraire de contextes d’attendre l’événement soit exécutable.

##  <a name="timeout_infinite"></a> timeout_infinite

Valeur qui indique qu'une attente ne doit jamais expirer.

```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

##  <a name="wait"></a> attente

Attend que l’événement soit signalé.

```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Paramètres

*_Délai*<br/>
Indique le nombre de millisecondes avant l’attente expire. La valeur `COOPERATIVE_TIMEOUT_INFINITE` signifie qu’il n’existe aucun délai d’expiration.

### <a name="return-value"></a>Valeur de retour

Si l’attente a été satisfaite, la valeur `0` est retourné ; sinon, la valeur `COOPERATIVE_WAIT_TIMEOUT` pour indiquer que l’attente a expiré sans que l’événement ne soit signalé.

> [!IMPORTANT]
>  Dans une application Universal Windows Platform (UWP), n’appelez pas `wait` sur l’ASTA thread, car cet appel peut bloquer le thread actuel et peut entraîner l’application à cesser de répondre.

##  <a name="wait_for_multiple"></a> wait_for_multiple

Attend que plusieurs événements soit signalé.

```
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Paramètres

*_PPEvents*<br/>
Un tableau d’événements à attendre. Le nombre d’événements dans le tableau est indiqué par la `count` paramètre.

*count*<br/>
Le nombre d’événements dans le tableau fourni dans le `_PPEvents` paramètre.

*_FWaitAll*<br/>
Si la valeur `true`, le paramètre spécifie que tous les événements dans le tableau fourni dans le `_PPEvents` paramètre doit être signalé pour satisfaire aux exigences de l’attente. Si la valeur `false`, il spécifie que n’importe quel événement dans le tableau fourni dans le `_PPEvents` paramètre ne soit signalé satisfait l’attente.

*_Délai*<br/>
Indique le nombre de millisecondes avant l’attente expire. La valeur `COOPERATIVE_TIMEOUT_INFINITE` signifie qu’il n’existe aucun délai d’expiration.

### <a name="return-value"></a>Valeur de retour

Si l’attente a été satisfaite, l’index dans le tableau fourni dans le `_PPEvents` paramètre qui satisfait la condition d’attente ; sinon, la valeur `COOPERATIVE_WAIT_TIMEOUT` pour indiquer que l’attente a expiré sans que la condition satisfaite.

### <a name="remarks"></a>Notes

Si le paramètre `_FWaitAll` a la valeur `true` pour indiquer que tous les événements doivent être signalés pour répondre à l’attente, l’index retourné par la fonction véhicule aucune signification spéciale autre que le fait qu’il n’est pas la valeur `COOPERATIVE_WAIT_TIMEOUT`.

> [!IMPORTANT]
>  Dans une application Universal Windows Platform (UWP), n’appelez pas `wait_for_multiple` sur l’ASTA thread, car cet appel peut bloquer le thread actuel et peut entraîner l’application à cesser de répondre.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
