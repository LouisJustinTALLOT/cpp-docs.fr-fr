---
title: Classe d'événements
description: Référence C++ de la classe d’événements du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 205a4e0ca9dd9449933f38f02d4ceafd5df8ead2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333397"
---
# <a name="event-class"></a>Classe d'événements

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `Event` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre n’importe quel événement.

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

[ID](#event-id) d’événement de
de [données](#data)\
[EventInstanceId](#event-instance-id)\
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ID](#process-id) de l'\
[ProcessorIndex](#processor-index)\
\ [ThreadID](#thread-id)
[TickFrequency](#tick-frequency)\
[Timestamp](#timestamp)

## <a name="entity"></a>Événement

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Tout événement.

## <a name="data"></a>Métadonnée

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers des données supplémentaires contenues dans cet événement. Pour plus d’informations sur la façon d’interpréter ce champ, consultez [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="event-id"></a>1001

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>Valeur de retour

Numéro qui identifie le type d’événement. Pour obtenir la liste des identificateurs d’événements, consultez [event_id](../c-event-data-types/event-id-enum.md).

## <a name="event-instance-id"></a>EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>Valeur de retour

Numéro qui identifie de façon unique l’événement à l’intérieur d’une trace. Cette valeur ne change pas lors de l’analyse ou de la rejournalisation de la même trace plusieurs fois. Utilisez cette valeur pour identifier le même événement dans plusieurs analyses ou dans la journalisation à travers la même trace.

## <a name="event-name"></a>Protégée

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne ANSI contenant le nom du type d’événement identifié par [eventID](#event-id).

## <a name="event-wide-name"></a>EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne étendue contenant le nom de l’événement identifié par [eventID](#event-id).

## <a name="process-id"></a>ProcessId

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>Valeur de retour

Identificateur du processus dans lequel l’événement s’est produit.

## <a name="processor-index"></a>ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>Valeur de retour

Index de base zéro pour le processeur logique sur lequel l’événement s’est produit.

## <a name="thread-id"></a>ThreadId

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>Valeur de retour

Identificateur du thread dans lequel l’événement s’est produit.

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de graduations par seconde à utiliser lors de l’évaluation d’une durée mesurée en graduations pour cet événement.

## <a name="timestamp"></a>Confirmé

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>Valeur de retour

Si l’événement est une activité, cette fonction retourne une valeur de graduation capturée au moment du démarrage de l’activité. Pour un événement simple, cette fonction retourne une valeur de graduation capturée au moment où l’événement s’est produit.

::: moniker-end
