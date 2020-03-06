---
title: Constantes RELOG_RETENTION_SYSTEM_EVENT_FLAGS
description: Le C++ Kit de développement logiciel (SDK) de Build Insights RELOG_RETENTION_SYSTEM_EVENT_FLAGS référence des constantes.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 74afc10faa26ba39a669a05aa3e3cabd1a211293
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332319"
---
# <a name="relog_retention_system_event_flags-constants"></a>Constantes RELOG_RETENTION_SYSTEM_EVENT_FLAGS

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Les constantes de `RELOG_RETENTION_SYSTEM_EVENT_FLAGS` sont utilisées pour décrire les événements système à conserver dans une trace reconnectée. Utilisez-les pour initialiser le champ `SystemEventsRetentionFlags` de la structure [RELOG_DESCRIPTOR](relog-descriptor-struct.md) .

## <a name="syntax"></a>Syntaxe

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Conservez les événements système de l’exemple de processeur dans une trace reconnectée. |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | Conservez tous les événements système dans une trace reconnectée. |

## <a name="remarks"></a>Notes

::: moniker-end
