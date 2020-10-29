---
title: Constantes RELOG_RETENTION_SYSTEM_EVENT_FLAGS
description: Le kit de développement logiciel (SDK) C++ Build Insights RELOG_RETENTION_SYSTEM_EVENT_FLAGS référence des constantes.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e0144835568dab12c8593fe8fbfa820f6cde7647
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919727"
---
# <a name="relog_retention_system_event_flags-constants"></a>Constantes RELOG_RETENTION_SYSTEM_EVENT_FLAGS

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

Les `RELOG_RETENTION_SYSTEM_EVENT_FLAGS` constantes sont utilisées pour décrire les événements système à conserver dans une trace reconnectée. Utilisez-les pour initialiser le champ de la structure [RELOG_DESCRIPTOR](relog-descriptor-struct.md) `SystemEventsRetentionFlags` .

## <a name="syntax"></a>Syntaxe

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Membres

| Nom | Description |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Conservez les événements système de l’exemple de processeur dans une trace reconnectée. |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | Conservez tous les événements système dans une trace reconnectée. |

## <a name="remarks"></a>Notes

::: moniker-end
