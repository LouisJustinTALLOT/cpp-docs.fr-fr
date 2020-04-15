---
title: Classe d’activité
description: La référence de la classe D’activités SDK Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2ea04150aec9c0b2366d97e6e4c15de557a4f47c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325245"
---
# <a name="activity-class"></a>Classe d’activité

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `Activity` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour faire correspondre n’importe quel événement d’activité. Consultez la [table d’événements](../event-table.md) pour voir `Activity` tous les événements qui peuvent être égalés par la classe.

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

Plusieurs fonctions de `Activity` membre dans la classe renvoient un nombre de tiques. Build Insights utilise le compteur de performances de Windows comme source de tiques. Un nombre de tiques doit être utilisé avec une fréquence de tiques pour la convertir en une unité de temps telle que les secondes. La `TickFrequency` fonction membre, disponible dans la classe de base [de l’événement,](event.md) peut être appelée pour obtenir la fréquence des tiques. La page [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) montre un exemple de conversion des tiques en une unité de temps.

Si vous ne voulez pas convertir les tiques `Activity` en unités de temps vous-même, la classe fournit aux membres des fonctions qui retournent des valeurs de temps en nanosecondes. Utilisez la bibliothèque `chrono` standard de C POUR les convertir en d’autres unités de temps.

## <a name="members"></a>Membres

Avec ses membres hérités de la `Activity` classe de base [de l’événement,](event.md) la classe contient les membres suivants :

### <a name="constructor"></a>Constructeur

[Activité](#activity)

### <a name="functions"></a>Fonctions

[CPUTicks](#cpu-ticks)\
[CPUTime (en)](#cpu-time)\
[Durée](#duration)\
[ExclusifCPUTicks](#exclusive-cpu-ticks)\
[ExclusifCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusifWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusifWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp (StopTimestamp)](#stop-timestamp)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a><a name="activity"></a> Activité

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Tout événement d’activité.

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

## <a name="duration"></a><a name="duration"></a>Durée

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Valeur de retour

La durée de l’activité en nanosecondes.

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

Un nombre de tiques qui représente la contribution de cette activité à l’heure globale de l’horloge murale. Une tique de responsabilité temporelle de l’horloge murale est différente d’une tique régulière. Les tiques de temps de l’horloge de mur tiennent compte du parallélisme entre les activités. Deux activités parallèles peuvent avoir une durée de 50 tiques, et le même temps de début et d’arrêt. Dans ce cas, les deux se voient attribuer une responsabilité de temps d’horloge murale de 25 tiques.

::: moniker-end
