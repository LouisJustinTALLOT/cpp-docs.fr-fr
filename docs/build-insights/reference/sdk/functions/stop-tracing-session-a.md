---
title: StopTracingSessionA
description: La référence de fonction SDK StopTracingSessionA de build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 15560ecf4959ccda0d617c09d3645750210f331a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323503"
---
# <a name="stoptracingsessiona"></a>StopTracingSessionA

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `StopTracingSessionA` fonction arrête une session de traçage en cours et produit un fichier de traces brutes. Les fichiers de trace brute peuvent être transmis aux fonctions [Analyze](analyze.md), [AnalzeA](analyze-a.md)et [AnalyzeW](analyze-w.md) pour commencer une session d’analyse. Les fichiers de traces brutes peuvent également être transmis aux fonctions [Relog](relog.md), [RelogA](relog-a.md)et [RelogW](relog-w.md) pour commencer la session de reloglogging. Les appels `StopTracingSessionA` exécutables doivent avoir des privilèges d’administrateur.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE StopTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>Paramètres

*sessionName*\
Le nom de la séance de traçage pour s’arrêter. Utilisez le même nom de session que celui passé à [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md), ou [StartTracingSessionW](start-tracing-session-w.md).

*sortieLogFile*\
Chemin vers le fichier de journal de sortie finale où la trace brute doit être enregistrée.

*Statistiques*\
Pointeur vers un [objet TRACING_SESSION_STATISTICS.](../other-types/tracing-session-statistics-struct.md) `StopTracingSessionA`écrit des statistiques de collecte de traces dans cet objet avant de revenir.

### <a name="return-value"></a>Valeur de retour

Un code de résultat de [l’enum RESULT_CODE.](../other-types/result-code-enum.md)

::: moniker-end
