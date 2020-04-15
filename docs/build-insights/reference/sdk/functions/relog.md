---
title: Relog
description: La référence de fonction CMD Build Insights SDK Relog.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28b290d2bf2880ce2f534fa1cd91750890e2fead
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323775"
---
# <a name="relog"></a>Relog

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `Relog` fonction est utilisée pour lire les événements MSVC à partir d’une trace event Tracing for Windows (ETW) et les écrire dans une nouvelle trace ETW modifiée.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const char*                                   inputLogFile,
    const char*                                   outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const wchar_t*                                inputLogFile,
    const wchar_t*                                outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>Paramètres

*TAnalyzerGroupMembers*\
Ce paramètre est toujours déduit.

*TReloggerGroupMembers*\
Ce paramètre est toujours déduit.

*inputLogFile (en)*\
L’entrée ETW trace que vous souhaitez lire les événements à partir.

*sortieLogFile*\
Le fichier dans lequel écrire les nouveaux événements.

*numberOfAnalysisPasses*\
Le nombre d’analyses passe pour exécuter sur la trace d’entrée. La trace passe par le groupe d’analyseur fourni une fois par passage d’analyse.

*systemEventsRetentionFlags*\
Un petit-train qui spécifie les événements DU système ETW à conserver dans la trace relogged. Pour plus d’informations, voir [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md).

*analyseurGroup*\
Le groupe d’analyseur utilisé pour la phase d’analyse de la session de réinstruation. Appelez [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) pour créer un groupe d’analyseurs. Pour utiliser un groupe d’analyseur dynamique obtenu de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), d’abord l’encapsuler à l’intérieur d’un groupe d’analyseur statique en passant son adresse à `MakeStaticAnalyzerGroup`.

*reloggerGroup (en anglais)*\
Le groupe relogger qui relogs événements dans le fichier de trace spécifié dans *la sortieLogFile*. Appelez [MakeStaticReloggerGroup](make-static-relogger-group.md) pour créer un groupe de relogger. Pour utiliser un groupe dynamique de relogger obtenu de [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md), d’abord l’encapsuler à l’intérieur d’un groupe de rélogger statique en passant son adresse à `MakeStaticReloggerGroup`.

### <a name="return-value"></a>Valeur de retour

Un code de résultat de [l’enum RESULT_CODE.](../other-types/result-code-enum.md)

### <a name="remark"></a>Remarque

La trace d’entrée est passée à travers le nombre de groupe *d’analyseOfAnalysisPasses* fois. Il n’y a pas d’option similaire pour la réinstruisation des laissez-passer. La trace est passée à travers le groupe relogger qu’une seule fois, après que toutes les passes d’analyse sont terminées.

La réengorisation d’événements système comme des échantillons de processeurs dans une classe de relogger n’est pas prise en charge. Utilisez le *paramètre SystemEventsRetentionFlags* pour décider quels événements système conserver dans la trace de sortie.

::: moniker-end
