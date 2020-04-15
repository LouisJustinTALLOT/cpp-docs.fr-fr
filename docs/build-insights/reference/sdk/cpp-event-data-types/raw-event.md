---
title: Classe RawEvent
description: La référence de classe CMD Build Insights SDK RawEvent.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 83629457ac3a0d1f991f6b084af2f3400612b2ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324381"
---
# <a name="rawevent-class"></a>Classe RawEvent

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `RawEvent` classe est utilisée pour représenter un événement général dans un [EventStack](event-stack.md).

## <a name="syntax"></a>Syntaxe

```cpp
class RawEvent
{
public:
    RawEvent(const EVENT_DATA& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             StartTimestamp() const;
    const long long&             StopTimestamp() const;
    const long long&             ExclusiveDurationTicks() const;
    const long long&             CPUTicks() const;
    const long long&             ExclusiveCPUTicks() const;
    const long long&             WallClockTimeResponsibilityTicks() const;
    const long long&             ExclusiveWallClockTimeResponsibilityTicks() const;
    const void*                  Data() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>Notes

Plusieurs fonctions de `RawEvent` membre dans la classe renvoient un nombre de tiques. Build Insights utilise le compteur de performances de Windows comme source de tiques. Un nombre de tiques doit être utilisé avec une fréquence de tiques pour la convertir en une unité de temps comme secondes. La `TickFrequency` fonction de membre peut être appelée pour obtenir la fréquence des tiques. Voir la [page EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) par exemple sur la façon de convertir les tiques en une unité de temps.

Si vous ne voulez pas convertir vous-même les tiques, la `RawEvent` classe fournit des fonctions de membre qui retournent les valeurs de temps en nanosecondes. Utilisez la bibliothèque `chrono` standard de CM pour convertir les nanosecondes en d’autres unités temporelles.

## <a name="members"></a>Membres

### <a name="constructor"></a>Constructeur

[RawEvent RawEvent](#raw-event)

### <a name="functions"></a>Fonctions

[CPUTicks](#cpu-ticks)\
[CPUTime (en)](#cpu-time)\
[Données](#data)\
[Durée](#duration)\
[EventId](#event-id)
[EventInstanceId](#event-instance-id)
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ExclusifCPUTicks](#exclusive-cpu-ticks)\
[ExclusifCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusifWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusifWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[Processid](#process-id)\
[ProcesseurIndex](#processor-index)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp (StopTimestamp)](#stop-timestamp)\
[ThreadId (en)](#thread-id)\
[TickFrequency (tickFrequency)](#tick-frequency)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="rawevent"></a><a name="raw-event"></a>RawEvent RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Données d'événement.

## <a name="cputicks"></a><a name="cpu-ticks"></a>CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de coches CPU qui s’est produite au cours de cette activité. Une tique CPU est différente d’une tique régulière. Les tiques CPU ne sont comptées que lorsque le processeur exécute du code dans une activité. Les tiques CPU ne sont pas comptées lorsque le fil associé à l’activité dort.

## <a name="cputime"></a><a name="cpu-time"></a>CPUTime (en)

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>Valeur de retour

Le temps pendant que le processeur exécutait le code à l’intérieur de cette activité. Cette valeur peut être supérieure à la durée de l’activité si les activités de l’enfant sont exécutées sur des fils distincts. La valeur est retournée en nanosecondes.

## <a name="data"></a><a name="data"></a>Données

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur aux données supplémentaires contenues dans cet événement. Pour plus d’informations sur la façon d’interpréter ce domaine, voir [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="duration"></a><a name="duration"></a>Durée

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Valeur de retour

La durée de l’activité en nanosecondes.

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

Une large chaîne contenant le nom du type d’événement identifié par [EventId](#event-id).

## <a name="exclusivecputicks"></a><a name="exclusive-cpu-ticks"></a>ExclusifCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>Valeur de retour

Tout comme [CPUTicks](#cpu-ticks), mais sans compter les tiques CPU qui se sont produites dans les activités de l’enfant.

## <a name="exclusivecputime"></a><a name="exclusive-cpu-time"></a>ExclusifCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>Valeur de retour

Idem pour [CPUTime](#cpu-time), sauf que le temps CPU des activités de l’enfant n’est pas inclus.

## <a name="exclusiveduration"></a><a name="exclusive-duration"></a>ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>Valeur de retour

La durée de l’activité en nanosecondes, sans compter le temps passé dans les activités des enfants.

## <a name="exclusivedurationticks"></a><a name="exclusive-duration-ticks"></a>ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de tiques qui se sont produites dans cette activité, à l’exclusion du nombre de tiques qui se sont produites dans les activités des enfants.

## <a name="exclusivewallclocktimeresponsibility"></a><a name="exclusive-wall-clock-time-responsibility"></a>ExclusifWallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Valeur de retour

Tout comme [WallClockTimeResponsibility](#wall-clock-time-responsibility), mais sans compter la responsabilité temporelle des activités de l’enfant.

## <a name="exclusivewallclocktimeresponsibilityticks"></a><a name="exclusive-wall-clock-time-responsibility-ticks"></a>ExclusifWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Valeur de retour

Comme [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks), mais sans compter les tiques de responsabilité de temps de l’horloge murale des activités de l’enfant.

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

## <a name="starttimestamp"></a><a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur de tique capturée au moment où l’activité a commencé.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>StopTimestamp (StopTimestamp)

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur de tique capturée au moment où l’activité s’est arrêtée.

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

## <a name="wallclocktimeresponsibility"></a><a name="wall-clock-time-responsibility"></a>WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Valeur de retour

La responsabilité temporelle de cette activité, en nanosecondes. Pour plus d’informations sur ce que signifie la responsabilité temporelle de l’horloge murale, voir [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks).

## <a name="wallclocktimeresponsibilityticks"></a><a name="wall-clock-time-responsibility-ticks"></a>WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Valeur de retour

Un nombre de tiques qui représente la contribution de cette activité à l’heure globale de l’horloge murale. Une tique de responsabilité temporelle de l’horloge murale est différente d’une tique régulière. Les tiques de temps de l’horloge de mur tiennent compte du parallélisme entre les activités. Deux activités parallèles peuvent avoir une durée de 50 tiques et le même temps de départ et d’arrêt. Dans ce cas, les deux se voient attribuer une responsabilité de temps d’horloge murale de 25 tiques.

::: moniker-end
