---
title: Structure TRACING_SESSION_STATISTICS
description: En savoir plus sur le kit de développement logiciel (SDK) C++ Build Insights TRACING_SESSION_STATISTICS référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7135c49bdf95ef5ba39db090c95ad46d266d8f65
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919655"
---
# <a name="tracing_session_statistics-structure"></a>Structure TRACING_SESSION_STATISTICS

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `TRACING_SESSION_STATISTICS` structure décrit les statistiques sur une trace qui a été collectée. Ses champs sont définis lors de l’arrêt d’une session de suivi.

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

| Nom | Description |
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
