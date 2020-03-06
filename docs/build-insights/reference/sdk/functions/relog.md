---
title: Rejournaliser
description: Référence C++ de la fonction relog du kit de développement logiciel (SDK) de build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1ce09101deebd957de4b9305762dc37f38b53f4e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332690"
---
# <a name="relog"></a>Rejournaliser

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La fonction `Relog` est utilisée pour lire des événements MSVC à partir d’une trace Suivi d’v nements pour Windows (ETW) et les écrire dans une nouvelle trace ETW modifiée.

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

*inputLogFile*\
Trace ETW d’entrée à partir de laquelle vous souhaitez lire les événements.

*outputLogFile*\
Fichier dans lequel écrire les nouveaux événements.

*numberOfAnalysisPasses*\
Nombre de passes d’analyse à exécuter sur la trace d’entrée. La trace est passée par le groupe d’analyseur fourni une fois par passe d’analyse.

*systemEventsRetentionFlags*\
Masque de masque qui spécifie les événements ETW du système à conserver dans le suivi reconnecté. Pour plus d’informations, consultez [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md).

*analyzerGroup*\
Groupe de l’analyseur utilisé pour la phase d’analyse de la session de rejournalisation. Appelez [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) pour créer un groupe d’analyseur. Pour utiliser un groupe d’analyseur dynamique obtenu à partir de [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), encapsulez-le d’abord à l’intérieur d’un groupe d’analyseur statique en passant son adresse à `MakeStaticAnalyzerGroup`.

*reloggerGroup*\
Groupe de rejournalisation qui reconnecte les événements dans le fichier de trace spécifié dans *outputLogFile*. Appelez [MakeStaticReloggerGroup](make-static-relogger-group.md) pour créer un groupe de rejournalisation. Pour utiliser un groupe de rejournalisation dynamique obtenu à partir de [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md), encapsulez-le d’abord à l’intérieur d’un groupe de rejournalisation statique en passant son adresse à `MakeStaticReloggerGroup`.

### <a name="return-value"></a>Valeur de retour

Code de résultat de l’énumération [RESULT_CODE](../other-types/result-code-enum.md) .

### <a name="remark"></a>Remarque

La trace d’entrée est transmise par le biais du groupe de l’analyseur *numberOfAnalysisPasses* fois. Il n’existe aucune option similaire pour la reconnexion des passes. La trace passe le groupe de rejournalisation une seule fois, une fois que toutes les étapes d’analyse sont terminées.

La reconnexion des événements système comme les exemples de PROCESSEURs à partir d’une classe de rejournalisation n’est pas prise en charge. Utilisez le paramètre *systemEventsRetentionFlags* pour décider des événements système à conserver dans la trace de sortie.

::: moniker-end
