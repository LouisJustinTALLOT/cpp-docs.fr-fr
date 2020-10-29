---
title: Structure TRACING_SESSION_OPTIONS
description: En savoir plus sur le kit de développement logiciel (SDK) C++ Build Insights TRACING_SESSION_OPTIONS référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3147debbfe1ea7ab4bcb4fa3bb8a803e66163557
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922382"
---
# <a name="tracing_session_options-structure"></a>Structure TRACING_SESSION_OPTIONS

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `TRACING_SESSION_OPTIONS` structure est utilisée lors de l’initialisation d’une structure [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) ou [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Il décrit les événements à capturer pendant la collecte d’une trace.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>Membres

| Nom | Description |
|--|--|
| `SystemEventFlags` | Masque de masque décrivant les événements système à capturer. Pour plus d’informations, consultez [TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md). |
| `MsvcEventFlags` | Masque de masque décrivant les événements MSVC à capturer. Pour plus d’informations, consultez [TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md). |

::: moniker-end
