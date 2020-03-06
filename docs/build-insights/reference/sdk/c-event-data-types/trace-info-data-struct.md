---
title: Structure TRACE_INFO_DATA
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights TRACE_INFO_DATA.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 04cb5c013bca8879507983d169b38e5af0f1322b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333586"
---
# <a name="trace_info_data-structure"></a>Structure TRACE_INFO_DATA

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `TRACE_INFO_DATA` décrit une trace qui est analysée ou rejournalisée.

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
| `LogicalProcessorCount` | Nombre de processeurs logiques sur l’ordinateur où la trace a été collectée. |
| `TickFrequency` | Nombre de graduations par seconde à utiliser lors de l’évaluation d’une durée mesurée en graduations. |
| `StartTimestamp` | Ce champ est défini sur une valeur de graduation capturée au moment du démarrage de la trace. |
| `StopTimestamp` | Ce champ est défini sur une valeur de graduation capturée au moment de l’arrêt de la trace. |

## <a name="remarks"></a>Notes

Soustraire `StartTimestamp` de `StopTimestamp` pour obtenir le nombre de cycles écoulés pendant l’intégralité de la trace. Utilisez `TickFrequency` pour convertir la valeur obtenue en unité de temps. Pour obtenir un exemple qui convertit des graduations en unités de temps, consultez [EVENT_DATA](event-data-struct.md).

::: moniker-end
