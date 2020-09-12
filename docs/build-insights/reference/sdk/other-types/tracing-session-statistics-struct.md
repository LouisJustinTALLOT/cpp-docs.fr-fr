---
title: Structure TRACING_SESSION_STATISTICS
description: Le kit de développement logiciel (SDK) C++ Build Insights TRACING_SESSION_OPTIONS référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5f6126fb469dc13b814b91942fe9f7bc480ba3f1
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041183"
---
# <a name="tracing_session_statistics-structure"></a>Structure TRACING_SESSION_STATISTICS

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

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

## <a name="remarks"></a>Remarques

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
