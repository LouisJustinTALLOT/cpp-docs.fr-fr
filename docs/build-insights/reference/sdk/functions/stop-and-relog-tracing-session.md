---
title: StopAndRelogTracingSession
description: Référence de la fonction StopAndRelogTracingSession du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d36dee1b16ca467d16b22587abe3ef34ee6ccb29
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919954"
---
# <a name="stopandrelogtracingsession"></a>StopAndRelogTracingSession

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `StopAndRelogTracingSession` fonction arrête une session de suivi en cours et enregistre le suivi résultant dans un fichier temporaire. Une session de rejournalisation est ensuite immédiatement démarrée en utilisant le fichier temporaire comme entrée. La dernière trace rejournalisée produite par la session de rejournalisation est enregistrée dans un fichier spécifié par l’appelant. Les exécutables qui appellent cette fonction doivent avoir des privilèges d’administrateur.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const char*                                   sessionName,
    const char*                                   outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const wchar_t*                                sessionName,
    const wchar_t*                                outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>Paramètres

*Session*\
Nom de la session de suivi à arrêter. Utilisez le même nom de session que celui passé à [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)ou [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
Fichier dans lequel écrire le suivi reconnecté généré par la session de rejournalisation.

*portent*\
Pointeur vers un objet [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . `StopAndRelogTracingSession` écrit les statistiques de collection de traces dans cet objet avant de retourner.

*numberOfAnalysisPasses*\
Nombre de passes d’analyse à exécuter sur la trace. La trace est passée par le groupe d’analyseur fourni une fois par passe d’analyse.

*systemEventsRetentionFlags*\
Masque de [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md) qui spécifie les événements ETW du système à conserver dans le suivi reconnecté.

*analyzerGroup*\
Groupe de l’analyseur utilisé pour la phase d’analyse de la session de rejournalisation. Appelez [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) pour créer un groupe d’analyseur. Si vous souhaitez utiliser un groupe d’analyseur dynamique obtenu à partir de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), encapsulez-le d’abord à l’intérieur d’un groupe d’analyseur statique en passant son adresse à `MakeStaticAnalyzerGroup` .

*reloggerGroup*\
Groupe de rejournalisation qui reconnecte les événements dans le fichier de trace spécifié dans *outputLogFile* . Appelez [MakeStaticReloggerGroup](make-static-relogger-group.md) pour créer un groupe de rejournalisation. Si vous souhaitez utiliser un groupe de rejournalisation dynamique obtenu à partir de [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md), encapsulez-le d’abord à l’intérieur d’un groupe de rejournalisation statique en passant son adresse à `MakeStaticReloggerGroup` .

### <a name="return-value"></a>Valeur de retour

Code de résultat de l’énumération [RESULT_CODE](../other-types/result-code-enum.md) .

### <a name="remarks"></a>Notes

La trace d’entrée est transmise par le biais du groupe de l’analyseur *numberOfAnalysisPasses* fois. Il n’existe aucune option similaire pour la reconnexion des passes. La trace passe le groupe de rejournalisation une seule fois, une fois que toutes les étapes d’analyse sont terminées.

La reconnexion des événements système comme les exemples de PROCESSEURs à partir d’une classe de rejournalisation n’est pas prise en charge. Utilisez le paramètre *systemEventsRetentionFlags* pour décider des événements système à conserver dans la trace de sortie.

::: moniker-end
