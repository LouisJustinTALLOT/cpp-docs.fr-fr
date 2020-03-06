---
title: RawEvent, classe
description: Référence C++ de la classe RawEvent du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4088920d6070e14d64ccd046238c1c49b2556ea1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333061"
---
# <a name="rawevent-class"></a>RawEvent, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `RawEvent` est utilisée pour représenter un événement général dans un [EventStack](event-stack.md).

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

Plusieurs fonctions membres de la classe `RawEvent` retournent un nombre de cycles. C++Build Insights utilise le compteur de performances Windows comme source de battements. Un nombre de cycles doit être utilisé avec une fréquence de cycle pour le convertir en unité de temps, comme les secondes. La fonction membre `TickFrequency` peut être appelée pour obtenir la fréquence de cycle. Consultez la page [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) pour obtenir un exemple sur la façon de convertir des graduations en unités de temps.

Si vous ne souhaitez pas convertir vous-même les graduations, la classe `RawEvent` fournit des fonctions membres qui retournent des valeurs de temps en nanosecondes. Utilisez la bibliothèque C++ de `chrono` standard pour convertir les nanosecondes en d’autres unités de temps.

## <a name="members"></a>Membres

### <a name="constructor"></a>Constructeur

[RawEvent](#raw-event)

### <a name="functions"></a>Fonctions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
[Données](#data)\
[Durée](#duration)\
[EventId](#event-id)
[EventInstanceId](#event-instance-id)
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[ID](#process-id) de l'\
[ProcessorIndex](#processor-index)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
\ [ThreadID](#thread-id)
[TickFrequency](#tick-frequency)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="raw-event"></a>RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>Paramètres

*event*\
Données d'événement.

## <a name="cpu-ticks"></a>CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de cycles de processeur qui se sont produits pendant cette activité. Un battement de l’UC est différent d’un battement normal. Les cycles de l’UC sont comptabilisés uniquement lorsque le processeur exécute du code dans une activité. Les cycles de l’UC ne sont pas comptabilisés lorsque le thread associé à l’activité est en veille.

## <a name="cpu-time"></a>CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>Valeur de retour

Durée d’exécution du code à l’intérieur de cette activité par l’UC. Cette valeur peut être supérieure à la durée de l’activité si les activités enfants sont exécutées sur des threads distincts. La valeur est retournée en nanosecondes.

## <a name="data"></a>Métadonnée

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers des données supplémentaires contenues dans cet événement. Pour plus d’informations sur la façon d’interpréter ce champ, consultez [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="duration"></a>Macauley

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Valeur de retour

Durée de l’activité en nanosecondes.

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

Chaîne étendue contenant le nom du type d’événement identifié par [eventID](#event-id).

## <a name="exclusive-cpu-ticks"></a>ExclusiveCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>Valeur de retour

Identique à [CPUTicks](#cpu-ticks), mais n’inclut pas les cycles de processeur qui se sont produits dans les activités enfants.

## <a name="exclusive-cpu-time"></a>ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>Valeur de retour

Identique à [CPUTime](#cpu-time), à ceci près que le temps processeur des activités enfants n’est pas inclus.

## <a name="exclusive-duration"></a>ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>Valeur de retour

Durée de l’activité en nanosecondes, sans inclure la durée passée dans les activités enfants.

## <a name="exclusive-duration-ticks"></a>ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de graduations qui se sont produites dans cette activité, à l’exclusion du nombre de graduations qui se sont produites dans les activités enfants.

## <a name="exclusive-wall-clock-time-responsibility"></a>ExclusiveWallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Valeur de retour

Identique à [WallClockTimeResponsibility](#wall-clock-time-responsibility), mais n’inclut pas la responsabilité du temps horloge des activités enfants.

## <a name="exclusive-wall-clock-time-responsibility-ticks"></a>ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Valeur de retour

Identique à [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks), mais n’inclut pas les graduations de la responsabilité du temps horloge des activités enfants.

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

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de graduation capturée au moment du démarrage de l’activité.

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de graduation capturée au moment de l’arrêt de l’activité.

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

## <a name="wall-clock-time-responsibility"></a>WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Valeur de retour

Responsabilité du temps horloge de cette activité, en nanosecondes. Pour plus d’informations sur la responsabilité du temps à l’heure du mur, consultez [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks).

## <a name="wall-clock-time-responsibility-ticks"></a>WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de cycles qui représente la contribution de cette activité à l’heure d’horloge globale. Un cycle de responsabilité de l’heure du mur est différent d’un battement normal. La responsabilité de l’horloge du mur prend en compte le parallélisme entre les activités. Deux activités parallèles peuvent avoir une durée de 50 cycles et la même heure de début et de fin. Dans ce cas, tous deux reçoivent une responsabilité de temps horloge de 25 battements.

::: moniker-end
