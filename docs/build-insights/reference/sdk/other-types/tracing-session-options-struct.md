---
title: Structure TRACING_SESSION_OPTIONS
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights TRACING_SESSION_OPTIONS.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3f02552d5df4ffe71bc4be5c46e4b5239f25d73c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332207"
---
# <a name="tracing_session_options-structure"></a>Structure TRACING_SESSION_OPTIONS

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `TRACING_SESSION_OPTIONS` est utilisée lors de l’initialisation d’une structure [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) ou [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Il décrit les événements à capturer pendant la collecte d’une trace.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `SystemEventFlags` | Masque de masque décrivant les événements système à capturer. Pour plus d’informations, consultez [TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md). |
| `MsvcEventFlags` | Masque de masque décrivant les événements MSVC à capturer. Pour plus d’informations, consultez [TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md). |

::: moniker-end
