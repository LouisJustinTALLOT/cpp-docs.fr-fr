---
title: Classe d'événements
description: Référence de la classe d’événements du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7dd96ffa3518c58e1b18312bb4fe2c36df26bd67
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923292"
---
# <a name="event-class"></a>Classe d'événements

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `Event` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre n’importe quel événement.

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

[Event](#entity)

### <a name="functions"></a>Fonctions

[Données](#data) 
 [EventID](#event-id)\
[EventInstanceId](#event-instance-id)\
[Protégée](#event-name)\
[EventWideName](#event-wide-name)\
[ProcessId](#process-id)\
[ProcessorIndex](#processor-index)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[Timestamp](#timestamp)

## <a name="event"></a>Événement<a name="entity"></a>

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Tout événement.

## <a name="data"></a><a name="data"></a> Métadonnée

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers des données supplémentaires contenues dans cet événement. Pour plus d’informations sur la façon d’interpréter ce champ, consultez [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="eventid"></a><a name="event-id"></a> 1001

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>Valeur de retour

Numéro qui identifie le type d’événement. Pour obtenir la liste des identificateurs d’événements, consultez [event_id](../c-event-data-types/event-id-enum.md).

## <a name="eventinstanceid"></a><a name="event-instance-id"></a> EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>Valeur de retour

Numéro qui identifie de façon unique l’événement à l’intérieur d’une trace. Cette valeur ne change pas lors de l’analyse ou de la rejournalisation de la même trace plusieurs fois. Utilisez cette valeur pour identifier le même événement dans plusieurs analyses ou dans la journalisation à travers la même trace.

## <a name="eventname"></a><a name="event-name"></a> Protégée

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne ANSI contenant le nom du type d’événement identifié par [eventID](#event-id).

## <a name="eventwidename"></a><a name="event-wide-name"></a> EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne étendue contenant le nom de l’événement identifié par [eventID](#event-id).

## <a name="processid"></a><a name="process-id"></a> ProcessId

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>Valeur de retour

Identificateur du processus dans lequel l’événement s’est produit.

## <a name="processorindex"></a><a name="processor-index"></a> ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro pour le processeur logique sur lequel l’événement s’est produit.

## <a name="threadid"></a><a name="thread-id"></a> ThreadId

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>Valeur de retour

Identificateur du thread dans lequel l’événement s’est produit.

## <a name="tickfrequency"></a><a name="tick-frequency"></a> TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de graduations par seconde à utiliser lors de l’évaluation d’une durée mesurée en graduations pour cet événement.

## <a name="timestamp"></a><a name="timestamp"></a> Confirmé

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>Valeur de retour

Si l’événement est une activité, cette fonction retourne une valeur de graduation capturée au moment du démarrage de l’activité. Pour un événement simple, cette fonction retourne une valeur de graduation capturée au moment où l’événement s’est produit.

::: moniker-end
