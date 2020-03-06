---
title: Structure TRACING_SESSION_STATISTICS
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights TRACING_SESSION_OPTIONS.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa7c0a861d80fd3ebff85eb7ecb17dd05ae869e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332200"
---
# <a name="tracing_session_statistics-structure"></a>Structure TRACING_SESSION_STATISTICS

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `TRACING_SESSION_STATISTICS` décrit les statistiques sur une trace qui a été collectée. Ses champs sont définis lors de l’arrêt d’une session de suivi.

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
| `MSVCEventsLost` | Nombre d’événements MSVC qui ont été supprimés. |
| `MSVCBuffersLost` | Nombre de mémoires tampons d’événements MSVC qui ont été supprimées. |
| `SystemEventsLost` | Nombre d’événements système qui ont été supprimés. |
| `SystemBuffersLost` | Nombre de mémoires tampons d’événements système qui ont été supprimées. |

## <a name="remarks"></a>Notes

Cette structure est remplie lors de l’appel des fonctions suivantes :

- [StopTracingSession](../functions/stop-tracing-session.md)
- [StopTracingSessionA](../functions/stop-tracing-session-a.md)
- [StopTracingSessionW](../functions/stop-tracing-session-w.md)
- [StopAndAnalyzeTracingSession](../functions/stop-and-analyze-tracing-session.md)
- [StopAndAnalyzeTracingSessionA](../functions/stop-and-analyze-tracing-session-a.md)
- [StopAndAnalyzeTracingSessionW](../functions/stop-and-analyze-tracing-session-w.md)
- [StopAndRelogTracingSession](../functions/stop-and-relog-tracing-session.md)
- [StopAndRelogTracingSessionA](../functions/stop-and-relog-tracing-session-a.md)
- [StopAndRelogTracingSessionW](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
