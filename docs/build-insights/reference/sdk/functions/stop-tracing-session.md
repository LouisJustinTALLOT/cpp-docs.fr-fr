---
title: StopTracingSession
description: Référence C++ de la fonction StopTracingSession du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a4be229dcfddef0624869b789ee35e51336ac78e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332550"
---
# <a name="stoptracingsession"></a>StopTracingSession

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La fonction `StopTracingSession` arrête une session de suivi en cours et produit un fichier de trace brut. Les fichiers de trace bruts peuvent être passés aux fonctions [analyze](analyze.md), [AnalzeA](analyze-a.md)et [AnalyzeW](analyze-w.md) pour démarrer une session d’analyse. Les fichiers de trace bruts peuvent également être passés aux fonctions [relog](relog.md), [RelogA](relog-a.md)et [RelogW](relog-w.md) pour démarrer une session de reconsignation. Les exécutables qui appellent `StopTracingSession` doivent avoir des privilèges d’administrateur.

## <a name="syntax"></a>Syntaxe

```cpp
inline RESULT_CODE StopTracingSession(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);

inline RESULT_CODE StopTracingSession(
    const wchar_t*              sessionName
    const wchar_t*              outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>Paramètres

*session*\
Nom de la session de suivi à arrêter. Utilisez le même nom de session que celui passé à [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)ou [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
Chemin d’accès au fichier journal de sortie final dans lequel la trace brute doit être enregistrée.

*statistiques*\
Pointeur vers un objet [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . `StopTracingSession` écrit les statistiques de collection de traces dans cet objet avant de retourner.

### <a name="return-value"></a>Valeur de retour

Code de résultat de l’énumération [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
