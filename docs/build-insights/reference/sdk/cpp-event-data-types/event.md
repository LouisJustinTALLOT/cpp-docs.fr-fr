---
title: Classe d'événements
description: La référence de classe SDK Event build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 25d58f642a1c314e48ddff62553394bcc65e4717
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324961"
---
# <a name="event-class"></a>Classe d'événements

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `Event` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à n’importe quel événement.

## <a name="syntax"></a>Syntaxe

```cpp
class Event
{
public:
    Event(const RawEvent& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             Timestamp() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;
};
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

[Événement](#entity)

### <a name="functions"></a>Fonctions

[Événement de](#data)
[donnéesId](#event-id)\
[EventInstanceId](#event-instance-id)\
[Eventname](#event-name)\
[EventWideName](#event-wide-name)\
[Processid](#process-id)\
[ProcesseurIndex](#processor-index)\
[ThreadId (en)](#thread-id)\
[TickFrequency (tickFrequency)](#tick-frequency)\
[Timestamp](#timestamp)

## <a name="event"></a>Événement<a name="entity"></a>

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
N’importe quel événement.

## <a name="data"></a><a name="data"></a>Données

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur aux données supplémentaires contenues dans cet événement. Pour plus d’informations sur la façon d’interpréter ce domaine, voir [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="eventid"></a><a name="event-id"></a>Eventid

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>Valeur de retour

Un numéro qui identifie le type d’événement. Pour une liste d’identifiants d’événements, voir [EVENT_ID](../c-event-data-types/event-id-enum.md).

## <a name="eventinstanceid"></a><a name="event-instance-id"></a>EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>Valeur de retour

Un nombre qui identifie uniquement l’événement à l’intérieur d’une trace. Cette valeur ne change pas lors de l’analyse ou de la réinstruisation de la même trace plusieurs fois. Utilisez cette valeur pour identifier le même événement dans plusieurs analyses ou relogging passes sur la même trace.

## <a name="eventname"></a><a name="event-name"></a>Eventname

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>Valeur de retour

Une chaîne ANSI contenant le nom du type d’événement identifié par [EventId](#event-id).

## <a name="eventwidename"></a><a name="event-wide-name"></a>EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>Valeur de retour

Une large chaîne contenant le nom de l’événement identifié par [EventId](#event-id).

## <a name="processid"></a><a name="process-id"></a>Processid

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>Valeur de retour

L’identifiant pour le processus dans lequel l’événement s’est produit.

## <a name="processorindex"></a><a name="processor-index"></a>ProcesseurIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>Valeur de retour

L’indice zéro pour le processeur logique sur lequel l’événement s’est produit.

## <a name="threadid"></a><a name="thread-id"></a>ThreadId (en)

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>Valeur de retour

L’identifiant pour le fil dans lequel l’événement s’est produit.

## <a name="tickfrequency"></a><a name="tick-frequency"></a>TickFrequency (tickFrequency)

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de tiques par seconde à utiliser lors de l’évaluation d’une durée mesurée en tiques pour cet événement.

## <a name="timestamp"></a><a name="timestamp"></a>Timestamp

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>Valeur de retour

Si l’événement est une activité, cette fonction renvoie une valeur de tique capturée au moment où l’activité a commencé. Pour un événement simple, cette fonction renvoie une valeur de tique capturée au moment de l’événement.

::: moniker-end
