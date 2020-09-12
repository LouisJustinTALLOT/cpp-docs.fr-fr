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
ms.openlocfilehash: 38683ff2c5c5165b5fe2a1969ccf80fbfca3693f
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040455"
---
# <a name="trace_info_data-structure"></a>Structure TRACE_INFO_DATA

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

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

## <a name="remarks"></a>Remarques

Soustrait `StartTimestamp` de `StopTimestamp` pour obtenir le nombre de cycles écoulés pendant l’intégralité de la trace. Utilisez `TickFrequency` pour convertir la valeur obtenue en unité de temps. Pour obtenir un exemple qui convertit des graduations en unités de temps, consultez [EVENT_DATA](event-data-struct.md).

::: moniker-end
