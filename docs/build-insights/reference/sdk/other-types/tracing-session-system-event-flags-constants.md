---
title: Constantes TRACING_SESSION_SYSTEM_EVENT_FLAGS
description: Le C++ Kit de développement logiciel (SDK) de Build Insights TRACING_SESSION_SYSTEM_EVENT_FLAGS référence des constantes.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ce0b0ea373ec53f0d5bcf228269299d69b49bb95
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332354"
---
# <a name="tracing_session_system_event_flags-constants"></a>Constantes TRACING_SESSION_SYSTEM_EVENT_FLAGS

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Les constantes de `TRACING_SESSION_SYSTEM_EVENT_FLAGS` sont utilisées pour décrire les événements système à collecter au cours d’une trace. Utilisez-les pour initialiser le champ `SystemEventFlags` de la structure [TRACING_SESSION_OPTIONS](tracing-session-options-struct.md) .

## <a name="syntax"></a>Syntaxe

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Membres

| Name | Événements activés par cet indicateur |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | Cet indicateur est activé par défaut par le C++ Kit de développement logiciel (SDK) Build Insights même s’il n’est pas spécifié explicitement. Il permet aux événements système de base requis par C++ Build Insights de fonctionner correctement. Les événements activés par cet indicateur fournissent des informations sur les processus, les threads et le chargement d’image. Vous ne pouvez pas désactiver ces événements. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Exemples d’UC |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | Cet indicateur active tous les événements système. |

::: moniker-end
