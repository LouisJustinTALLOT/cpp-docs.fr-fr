---
title: Classe TraceInfo
description: La référence de la classe CMD Build Insights SDK TraceInfo.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75d53937e3999f5692dee0ecf419e0ce5f49a274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324173"
---
# <a name="traceinfo-class"></a>Classe TraceInfo

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `TraceInfo` classe est utilisée pour accéder à des propriétés utiles sur une trace analysée ou relogged.

## <a name="syntax"></a>Syntaxe

```cpp
class TraceInfo
{
public:
    TraceInfo(const TRACE_INFO_DATA& data);

    const unsigned long& LogicalProcessorCount() const;

    const long long& TickFrequency() const;
    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;

    std::chrono::nanoseconds Duration() const;
};
```

## <a name="remarks"></a>Notes

Soustrayez le `StartTimestamp` de `StopTimestamp` pour obtenir le nombre de tiques écoulées pendant toute la trace. Utilisez `TickFrequency` pour convertir la valeur résultante en une unité de temps. Pour un exemple de conversion des tiques dans le temps, voir [EVENT_DATA](../c-event-data-types/event-data-struct.md).

Si vous ne voulez pas convertir vous-même les tiques, la `TraceInfo` classe fournit une fonction membre qui renvoie la durée des traces en nanosecondes. Utilisez la bibliothèque `chrono` standard de C POUR convertir cette valeur en d’autres unités de temps.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

[TraceInfo (en)](#trace-info)

### <a name="functions"></a>Fonctions

[Durée](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a><a name="duration"></a>Durée

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Valeur de retour

La durée de l’activité en nanosecondes.

## <a name="logicalprocessorcount"></a><a name="logical-processor-count"></a>LogicalProcesseurCompte

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de processeurs logiques sur la machine où la trace a été recueillie.

## <a name="starttimestamp"></a><a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur de tique capturée au moment où la trace a été commencée.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>StopTimestamp (StopTimestamp)

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur de tique capturée au moment où la trace a été arrêtée.

## <a name="tickfrequency"></a><a name="tick-frequency"></a>TickFrequency (tickFrequency)

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de tiques par seconde à utiliser lors de l’évaluation d’une durée mesurée en tiques.

## <a name="traceinfo"></a><a name="trace-info"></a>TraceInfo (en)

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>Paramètres

*Données*\
Les données contenant les informations sur la trace.

::: moniker-end
