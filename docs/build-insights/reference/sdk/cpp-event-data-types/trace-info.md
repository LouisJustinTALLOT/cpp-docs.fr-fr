---
title: TraceInfo, classe
description: Référence C++ de la classe du kit de développement logiciel (SDK) de build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5cf32c8dc954a803a11888231d35b1050ac81cc3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332942"
---
# <a name="traceinfo-class"></a>TraceInfo, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `TraceInfo` permet d’accéder à des propriétés utiles sur une trace en cours d’analyse ou de retardement.

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

Soustraire la `StartTimestamp` de `StopTimestamp` pour obtenir le nombre de cycles écoulés pendant l’intégralité de la trace. Utilisez `TickFrequency` pour convertir la valeur obtenue en unité de temps. Pour obtenir un exemple de conversion de graduations en temps, consultez [EVENT_DATA](../c-event-data-types/event-data-struct.md).

Si vous ne souhaitez pas convertir vous-même les battements, la classe `TraceInfo` fournit une fonction membre qui retourne la durée de trace en nanosecondes. Utilisez la bibliothèque C++ de `chrono` standard pour convertir cette valeur en d’autres unités de temps.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

[TraceInfo](#trace-info)

### <a name="functions"></a>Fonctions

[Duration](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a>Macauley

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Valeur de retour

Durée de l’activité en nanosecondes.

## <a name="logical-processor-count"></a>LogicalProcessorCount

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de processeurs logiques sur l’ordinateur où la trace a été collectée.

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de graduation capturée au moment du démarrage de la trace.

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de graduation capturée au moment où la trace a été arrêtée.

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de graduations par seconde à utiliser lors de l’évaluation d’une durée mesurée en graduations.

## <a name="trace-info"></a>TraceInfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>Paramètres

\ de *données*
Données contenant les informations relatives à la trace.

::: moniker-end
