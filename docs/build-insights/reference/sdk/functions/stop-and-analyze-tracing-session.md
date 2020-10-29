---
title: StopAndAnalyzeTracingSession
description: Référence de la fonction StopAndAnalyzeTracingSession du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 81a8ce43ecedfa51874508193637969411ae52d6
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922714"
---
# <a name="stopandanalyzetracingsession"></a>StopAndAnalyzeTracingSession

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `StopAndAnalyzeTracingSession` fonction arrête une session de suivi en cours et enregistre le suivi résultant dans un fichier temporaire. Une session d’analyse est ensuite immédiatement démarrée en utilisant le fichier temporaire comme entrée. Les exécutables qui appellent cette fonction doivent avoir des privilèges d’administrateur.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const char*                                   sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const wchar_t*                                sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>Paramètres

*Session*\
Nom de la session de suivi à arrêter. Utilisez le même nom de session que celui passé à [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)ou [StartTracingSessionW](start-tracing-session-w.md).

*numberOfAnalysisPasses*\
Nombre de passes d’analyse à exécuter sur la trace. La trace est passée par le groupe d’analyseur fourni une fois par passe d’analyse.

*portent*\
Pointeur vers un objet [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . `StopAndAnalyzeTracingSession` écrit les statistiques de collection de traces dans cet objet avant de retourner.

*analyzerGroup*\
Groupe de l’analyseur utilisé pour l’analyse. Appelez [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) pour créer un groupe d’analyseur. Si vous souhaitez utiliser un groupe d’analyseur dynamique obtenu à partir de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), encapsulez-le d’abord à l’intérieur d’un groupe d’analyseur statique en passant son adresse à `MakeStaticAnalyzerGroup` .

### <a name="return-value"></a>Valeur de retour

Code de résultat de l’énumération [RESULT_CODE](../other-types/result-code-enum.md) .

::: moniker-end
