---
description: En savoir plus sur la classe d’événements
title: event, classe
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
ms.openlocfilehash: 3c33096795d1980ea78cbce8c38fa9305ee45cd0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331249"
---
# <a name="event-class"></a>event, classe

Événement de réinitialisation manuelle qui a explicitement connaissance du runtime d'accès concurrentiel.

## <a name="syntax"></a>Syntaxe

```cpp
class event;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[~ Event, destructeur](#dtor)|Détruit un événement.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[reset](#reset)|Réinitialise l’événement à un État non signalé.|
|[set](#set)|Signale l’événement.|
|[wait](#wait)|Attend que l’événement soit signalé.|
|[wait_for_multiple](#wait_for_multiple)|Attend que plusieurs événements soient signalés.|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|Valeur qui indique qu'une attente ne doit jamais expirer.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [structures de données de synchronisation](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`event`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="event"></a>Événement<a name="ctor"></a>

Construit un nouvel événement.

```cpp
_CRTIMP event();
```

### <a name="remarks"></a>Notes

## <a name="event"></a><a name="dtor"></a> ~ événement

Détruit un événement.

```cpp
~event();
```

### <a name="remarks"></a>Notes

Il est supposé qu’aucun thread n’attend l’événement lorsque le destructeur s’exécute. Le fait d’autoriser l’événement à se détruire avec les threads qui attendent encore ce problème entraîne un comportement indéfini.

## <a name="reset"></a><a name="reset"></a> initialisation

Réinitialise l’événement à un État non signalé.

```cpp
void reset();
```

## <a name="set"></a><a name="set"></a> définie

Signale l’événement.

```cpp
void set();
```

### <a name="remarks"></a>Notes

La signalisation de l’événement peut provoquer l’indisponibilité d’un nombre arbitraire de contextes qui attendent l’événement.

## <a name="timeout_infinite"></a><a name="timeout_infinite"></a> timeout_infinite

Valeur qui indique qu'une attente ne doit jamais expirer.

```cpp
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

## <a name="wait"></a><a name="wait"></a> qu'

Attend que l’événement soit signalé.

```cpp
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Paramètres

*_Timeout*<br/>
Indique le nombre de millisecondes avant l’expiration du délai d’attente. La valeur `COOPERATIVE_TIMEOUT_INFINITE` signifie qu’il n’y a aucun délai d’attente.

### <a name="return-value"></a>Valeur renvoyée

Si l’attente a été satisfaite, la valeur `0` est retournée ; sinon, la valeur `COOPERATIVE_WAIT_TIMEOUT` pour indiquer que l’attente a expiré sans que l’événement soit signalé.

> [!IMPORTANT]
> Dans une application plateforme Windows universelle (UWP), n’appelez pas `wait` sur le thread asta, car cet appel peut bloquer le thread actuel et peut provoquer le blocage de l’application.

## <a name="wait_for_multiple"></a><a name="wait_for_multiple"></a> wait_for_multiple

Attend que plusieurs événements soient signalés.

```cpp
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Paramètres

*_PPEvents*<br/>
Tableau d’événements à attendre. Le nombre d’événements dans le tableau est indiqué par le `count` paramètre.

*count*<br/>
Nombre d’événements dans le tableau fourni dans le `_PPEvents` paramètre.

*_FWaitAll*<br/>
Si la valeur est définie **`true`** , le paramètre spécifie que tous les événements dans le tableau fourni dans le `_PPEvents` paramètre doivent être signalés pour répondre à l’attente. S’il est défini sur la valeur **`false`** , il spécifie que tout événement dans le tableau fourni dans le `_PPEvents` paramètre qui devient signalé répondra à l’attente.

*_Timeout*<br/>
Indique le nombre de millisecondes avant l’expiration du délai d’attente. La valeur `COOPERATIVE_TIMEOUT_INFINITE` signifie qu’il n’y a aucun délai d’attente.

### <a name="return-value"></a>Valeur renvoyée

Si l’attente a été satisfaite, l’index dans le tableau fourni dans le `_PPEvents` paramètre qui a respecté la condition d’attente ; sinon, la valeur `COOPERATIVE_WAIT_TIMEOUT` pour indiquer que l’attente a expiré sans que la condition soit satisfaite.

### <a name="remarks"></a>Notes

Si le paramètre `_FWaitAll` est défini sur la valeur **`true`** pour indiquer que tous les événements doivent être signalés pour répondre à l’attente, l’index retourné par la fonction n’a pas d’importance particulière, à l’exception du fait qu’il ne s’agit pas de la valeur `COOPERATIVE_WAIT_TIMEOUT` .

> [!IMPORTANT]
> Dans une application plateforme Windows universelle (UWP), n’appelez pas `wait_for_multiple` sur le thread asta, car cet appel peut bloquer le thread actuel et peut provoquer le blocage de l’application.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
