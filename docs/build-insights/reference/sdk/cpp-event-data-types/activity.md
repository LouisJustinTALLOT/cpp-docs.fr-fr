---
title: Classe d’activité
description: Référence C++ de classe d’activité du SDK Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6de411c375b42e4acfb44bf0fac9d28ad57f1ca7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333558"
---
# <a name="activity-class"></a>Classe d’activité

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `Activity` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre n’importe quel événement d’activité. Reportez-vous à la [table des événements](../event-table.md) pour afficher tous les événements qui peuvent être mis en correspondance par la classe `Activity`.

## <a name="syntax"></a>Syntaxe

```cpp
class Activity : public Event
{
public:
    Activity(const RawEvent& event);

    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;
    const long long& ExclusiveDurationTicks() const;
    const long long& CPUTicks() const;
    const long long& ExclusiveCPUTicks() const;
    const long long& WallClockTimeResponsibilityTicks() const;
    const long long& ExclusiveWallClockTimeResponsibilityTicks() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>Notes

Plusieurs fonctions membres de la classe `Activity` retournent un nombre de cycles. C++Build Insights utilise le compteur de performances Windows comme source de battements. Un nombre de cycles doit être utilisé avec une fréquence de cycle pour le convertir en une unité de temps telle que les secondes. La fonction membre `TickFrequency`, disponible dans la classe de base d' [événement](event.md) , peut être appelée pour obtenir la fréquence de graduation. La page [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) montre un exemple de conversion de graduations en unité de temps.

Si vous ne souhaitez pas convertir les graduations en unités de temps vous-même, la classe `Activity` fournit des fonctions membres qui retournent des valeurs de temps en nanosecondes. Utilisez la bibliothèque C++ de `chrono` standard pour les convertir en d’autres unités de temps.

## <a name="members"></a>Membres

Avec ses membres hérités de la classe de base [Event](event.md) , la classe `Activity` contient les membres suivants :

### <a name="constructor"></a>Constructeur

[Activité](#activity)

### <a name="functions"></a>Fonctions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
[Durée](#duration)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a>Bas

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Tout événement d’activité.

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

## <a name="duration"></a>Macauley

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Valeur de retour

Durée de l’activité en nanosecondes.

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

Nombre de cycles qui représente la contribution de cette activité à l’heure d’horloge globale. Un cycle de responsabilité de l’heure du mur est différent d’un battement normal. La responsabilité de l’horloge du mur prend en compte le parallélisme entre les activités. Deux activités parallèles peuvent avoir une durée de 50 cycles, et la même heure de début et de fin. Dans ce cas, tous deux reçoivent une responsabilité de temps horloge de 25 battements.

::: moniker-end
