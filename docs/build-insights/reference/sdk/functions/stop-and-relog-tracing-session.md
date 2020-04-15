---
title: StopAndRelogTracingSession
description: La référence de la fonction SDK StopAndRelogTracingSession.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1f6f5af63d25504226707d977791430463374328
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323665"
---
# <a name="stopandrelogtracingsession"></a>StopAndRelogTracingSession

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `StopAndRelogTracingSession` fonction arrête une séance de traçage en cours et enregistre la trace résultante dans un fichier temporaire. Une session de re-enregistrement est alors immédiatement commencée à utiliser le fichier temporaire comme entrée. La trace relogged finale produite par la session de relogging est enregistrée dans un fichier spécifié par l’appelant. Les exécutables qui appellent cette fonction doivent avoir des privilèges d’administrateur.

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

*sessionName*\
Le nom de la séance de traçage pour s’arrêter. Utilisez le même nom de session que celui passé à [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md), ou [StartTracingSessionW](start-tracing-session-w.md).

*sortieLogFile*\
Le fichier dans lequel écrire la trace relogged produite par la session de relogging.

*Statistiques*\
Pointeur vers un [objet TRACING_SESSION_STATISTICS.](../other-types/tracing-session-statistics-struct.md) `StopAndRelogTracingSession`écrit des statistiques de collecte de traces dans cet objet avant de revenir.

*numberOfAnalysisPasses*\
Le nombre d’analyses passe pour courir sur la trace. La trace passe par le groupe d’analyseur fourni une fois par passage d’analyse.

*systemEventsRetentionFlags*\
Un [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md) le bitmask qui spécifie quels événements ETW système à garder dans la trace relogged.

*analyseurGroup*\
Le groupe d’analyseur utilisé pour la phase d’analyse de la session de réinstruation. Appelez [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) pour créer un groupe d’analyseurs. Si vous souhaitez utiliser un groupe d’analyseur dynamique obtenu à partir de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), d’abord l’encapsuler à l’intérieur d’un groupe d’analyseur statique en passant son adresse à `MakeStaticAnalyzerGroup`.

*reloggerGroup (en anglais)*\
Le groupe relogger qui relogs événements dans le fichier de trace spécifié dans *la sortieLogFile*. Appelez [MakeStaticReloggerGroup](make-static-relogger-group.md) pour créer un groupe de relogger. Si vous souhaitez utiliser un groupe dynamique de relogger obtenu de [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md), d’abord l’encapsuler à l’intérieur d’un groupe de relogger statique en passant son adresse à `MakeStaticReloggerGroup`.

### <a name="return-value"></a>Valeur de retour

Un code de résultat de [l’enum RESULT_CODE.](../other-types/result-code-enum.md)

### <a name="remarks"></a>Notes

La trace d’entrée est passée à travers le nombre de groupe *d’analyseOfAnalysisPasses* fois. Il n’y a pas d’option similaire pour la réinstruisation des laissez-passer. La trace est passée à travers le groupe relogger qu’une seule fois, après que toutes les passes d’analyse sont terminées.

La réengorisation d’événements système comme des échantillons de processeurs dans une classe de relogger n’est pas prise en charge. Utilisez le *paramètre SystemEventsRetentionFlags* pour décider quels événements système conserver dans la trace de sortie.

::: moniker-end
