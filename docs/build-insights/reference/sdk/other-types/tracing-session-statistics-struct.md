---
title: structure TRACING_SESSION_STATISTICS
description: La référence de structure de construction SDK TRACING_SESSION_OPTIONS de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 96cff3a231fd515ec1c52a048b8350a63ba46a39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323382"
---
# <a name="tracing_session_statistics-structure"></a>structure TRACING_SESSION_STATISTICS

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `TRACING_SESSION_STATISTICS` structure décrit des statistiques sur une trace qui a été recueillie. Ses champs sont réglés lors de l’arrêt d’une séance de traçage.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct TRACING_SESSION_STATISTICS_TAG
{
    unsigned long MSVCEventsLost;
    unsigned long MSVCBuffersLost;
    unsigned long SystemEventsLost;
    unsigned long SystemBuffersLost;

} TRACING_SESSION_STATISTICS;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `MSVCEventsLost` | Le nombre d’événements MSVC qui ont été supprimés. |
| `MSVCBuffersLost` | Le nombre de tampons d’événements MSVC qui ont été supprimés. |
| `SystemEventsLost` | Le nombre d’événements du système qui ont été supprimés. |
| `SystemBuffersLost` | Le nombre de tampons d’événements système qui ont été supprimés. |

## <a name="remarks"></a>Notes

Cette structure est peuplée lors de l’appel des fonctions suivantes:

- [StopTracingSession (en)](../functions/stop-tracing-session.md)
- [StopTracingSessionA](../functions/stop-tracing-session-a.md)
- [StopTracingSessionW (en)](../functions/stop-tracing-session-w.md)
- [StopAndAnalyzeTracingSession](../functions/stop-and-analyze-tracing-session.md)
- [StopAndAnalyzeTracingSessionA](../functions/stop-and-analyze-tracing-session-a.md)
- [StopAndAnalyzeTracingSessionW](../functions/stop-and-analyze-tracing-session-w.md)
- [StopAndRelogTracingSession](../functions/stop-and-relog-tracing-session.md)
- [StopAndRelogTracingSessionA](../functions/stop-and-relog-tracing-session-a.md)
- [StopAndRelogTracingSessionW](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
