---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS constantes
description: La référence des perspectives de construction de la CMD SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS constantes.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7110f809a819357b31951c203c1fa6ac9fb9f42e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323468"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS constantes

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

Les `RELOG_RETENTION_SYSTEM_EVENT_FLAGS` constantes sont utilisées pour décrire les événements du système à conserver dans une trace obstruée. Utilisez-les pour initialiser le champ `SystemEventsRetentionFlags` de la structure [RELOG_DESCRIPTOR.](relog-descriptor-struct.md)

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
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Conservez les événements du système d’échantillonnage CPU dans une trace relogged. |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | Gardez tous les événements du système dans une trace relogged. |

## <a name="remarks"></a>Notes

::: moniker-end
