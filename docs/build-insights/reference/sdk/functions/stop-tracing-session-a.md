---
title: StopTracingSessionA
description: Référence de la fonction StopTracingSessionA du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 211538c1756d41b91dab6d43f33f4b4a41ceb70c
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922642"
---
# <a name="stoptracingsessiona"></a>StopTracingSessionA

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `StopTracingSessionA` fonction arrête une session de suivi en cours et produit un fichier de trace brut. Les fichiers de trace bruts peuvent être passés aux fonctions [analyze](analyze.md), [AnalzeA](analyze-a.md)et [AnalyzeW](analyze-w.md) pour démarrer une session d’analyse. Les fichiers de trace bruts peuvent également être passés aux fonctions [relog](relog.md), [RelogA](relog-a.md)et [RelogW](relog-w.md) pour démarrer la session de rejournalisation. Les exécutables qui appellent `StopTracingSessionA` doivent avoir des privilèges d’administrateur.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE StopTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>Paramètres

*Session*\
Nom de la session de suivi à arrêter. Utilisez le même nom de session que celui passé à [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)ou [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
Chemin d’accès au fichier journal de sortie final dans lequel la trace brute doit être enregistrée.

*portent*\
Pointeur vers un objet [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . `StopTracingSessionA` écrit les statistiques de collection de traces dans cet objet avant de retourner.

### <a name="return-value"></a>Valeur de retour

Code de résultat de l’énumération [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
