---
title: structure TRACE_INFO_DATA
description: La référence de structure de construction SDK TRACE_INFO_DATA de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 70ae17a376f79cad7a669d81e482f551afd0ec62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325277"
---
# <a name="trace_info_data-structure"></a>structure TRACE_INFO_DATA

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `TRACE_INFO_DATA` structure décrit une trace analysée ou relstruée.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct TRACE_INFO_DATA_TAG
{
    unsigned long           LogicalProcessorCount;
    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;

} TRACE_INFO_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `LogicalProcessorCount` | Le nombre de processeurs logiques sur la machine où la trace a été recueillie. |
| `TickFrequency` | Le nombre de tiques par seconde à utiliser lors de l’évaluation d’une durée mesurée en tiques. |
| `StartTimestamp` | Ce champ est réglé à une valeur de tique capturée au moment où la trace a été commencée. |
| `StopTimestamp` | Ce champ est réglé à une valeur de tique capturée au moment où la trace a été arrêtée. |

## <a name="remarks"></a>Notes

Soustrayez `StartTimestamp` `StopTimestamp` pour obtenir le nombre de tiques écoulées pendant toute la trace. Utilisez `TickFrequency` pour convertir la valeur résultante en une unité de temps. Par exemple qui convertit les tiques en unités temporelles, voir [EVENT_DATA](event-data-struct.md).

::: moniker-end
