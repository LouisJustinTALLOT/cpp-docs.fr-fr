---
title: Structure TRACE_INFO_DATA
description: Le kit de développement logiciel (SDK) C++ Build Insights TRACE_INFO_DATA référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ce6301b168aed9f279fc7aaee9aa3a97221fd23a
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923428"
---
# <a name="trace_info_data-structure"></a>Structure TRACE_INFO_DATA

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `TRACE_INFO_DATA` structure décrit une trace qui est analysée ou rejournalisée.

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

| Nom | Description |
|--|--|
| `LogicalProcessorCount` | Nombre de processeurs logiques sur l’ordinateur où la trace a été collectée. |
| `TickFrequency` | Nombre de graduations par seconde à utiliser lors de l’évaluation d’une durée mesurée en graduations. |
| `StartTimestamp` | Ce champ est défini sur une valeur de graduation capturée au moment du démarrage de la trace. |
| `StopTimestamp` | Ce champ est défini sur une valeur de graduation capturée au moment de l’arrêt de la trace. |

## <a name="remarks"></a>Notes

Soustrait `StartTimestamp` de `StopTimestamp` pour obtenir le nombre de cycles écoulés pendant l’intégralité de la trace. Utilisez `TickFrequency` pour convertir la valeur obtenue en unité de temps. Pour obtenir un exemple qui convertit des graduations en unités de temps, consultez [EVENT_DATA](event-data-struct.md).

::: moniker-end
