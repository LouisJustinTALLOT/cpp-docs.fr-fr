---
title: Constantes TRACING_SESSION_SYSTEM_EVENT_FLAGS
description: Le kit de développement logiciel (SDK) C++ Build Insights TRACING_SESSION_SYSTEM_EVENT_FLAGS référence des constantes.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 346c955355ffbc6c062a34bf928f16ccd3940154
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922377"
---
# <a name="tracing_session_system_event_flags-constants"></a>Constantes TRACING_SESSION_SYSTEM_EVENT_FLAGS

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

Les `TRACING_SESSION_SYSTEM_EVENT_FLAGS` constantes sont utilisées pour décrire les événements système à collecter au cours d’une trace. Utilisez-les pour initialiser le champ de la structure [TRACING_SESSION_OPTIONS](tracing-session-options-struct.md) `SystemEventFlags` .

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

| Nom | Événements activés par cet indicateur |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | Cet indicateur est activé par défaut par le kit de développement logiciel (SDK) C++ Build Insights, même s’il n’est pas spécifié explicitement. Il permet aux événements système de base requis par C++ Build Insights de fonctionner correctement. Les événements activés par cet indicateur fournissent des informations sur les processus, les threads et le chargement d’image. Vous ne pouvez pas désactiver ces événements. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Exemples d’UC |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | Cet indicateur active tous les événements système. |

::: moniker-end
