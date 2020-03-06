---
title: Structure ANALYSIS_CALLBACKS
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights ANALYSIS_CALLBACKS.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8c35e740d97488969a6b69467d54412297e49227
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332529"
---
# <a name="analysis_callbacks-structure"></a>Structure ANALYSIS_CALLBACKS

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `ANALYSIS_CALLBACKS` est utilisée lors de l’initialisation d’un objet [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) ou [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Elle spécifie les fonctions à appeler lors de l’analyse ou de la reconnexion d’une trace de Suivi d’v nements pour Windows (ETW).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct ANALYSIS_CALLBACKS_TAG
{
    OnAnalysisEventFunc     OnStartActivity;
    OnAnalysisEventFunc     OnStopActivity;
    OnAnalysisEventFunc     OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginAnalysis;
    OnBeginEndPassFunc      OnEndAnalysis;
    OnBeginEndPassFunc      OnBeginAnalysisPass;
    OnBeginEndPassFunc      OnEndAnalysisPass;
} ANALYSIS_CALLBACKS;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `OnStartActivity` | Appelé pour traiter un événement de début d’activité. |
| `OnStopActivity` | Appelé pour traiter un événement d’arrêt d’activité. |
| `OnSimpleEvent` | Appelée pour traiter un événement simple. |
| `OnTraceInfo` | Pour les sessions d’analyse, appelées au début de chaque passe d’analyse. Pour les sessions de rejournalisation, appelées au début de chaque passe d’analyse, et à nouveau au début de la passe de reconnexion. Cette fonction est appelée uniquement après l’appel de OnBeginAnalysisPass. |
| `OnBeginAnalysis` | Pour les sessions d’analyse, appelées avant le début d’une étape d’analyse. Pour les sessions de rejournalisation, appelées deux fois avant le début de la phase d’analyse : une fois pour annoncer le démarrage de la session de rejournalisation, et une fois pour annoncer le début de la phase d’analyse. |
| `OnEndAnalysis` | Pour les sessions d’analyse, cette fonction est appelée une fois tous les tests terminés. Pour les sessions de rejournalisation, cette fonction est appelée lorsque toutes les étapes d’analyse de la phase d’analyse se sont terminées. Ensuite, il est appelé à nouveau une fois la passe de reconnexion terminée. |
| `OnBeginAnalysisPass` | Appelé au début d’un test d’analyse ou de la passe de reconnexion, avant de traiter tout événement. |
| `OnEndAnalysisPass` | Appelée lors de la fin d’un test d’analyse ou de la passe de rejournalisation, après le traitement de tous les événements. |

## <a name="remarks"></a>Notes

La phase d’analyse d’une session de rejournalisation est considérée comme faisant partie de la session de rejournalisation et peut contenir plusieurs passes d’analyse. C’est la raison pour laquelle `OnBeginAnalysis` est appelé deux fois dans une ligne au début d’une session de rejournalisation. `OnEndAnalysis` est appelé à la fin de la phase d’analyse, avant de commencer la phase de rejournalisation, et une nouvelle fois à la fin de la phase de reconnexion. La phase de rejournalisation contient toujours une seule passe de reconnexion.

Il est possible que les analyseurs fassent partie de l’analyse et de la phase de rejournalisation d’une session de rejournalisation. Ces analyseurs peuvent déterminer la phase en cours en effectuant le suivi des paires d’appels OnBeginAnalysis et `OnEndAnalysis`. Deux `OnBeginAnalysis` appels sans appel de `OnEndAnalysis` signifie que la phase d’analyse est en cours. Deux appels de `OnBeginAnalysis` et un appel de `OnEndAnalysis` signifie que la phase de rejournalisation est en cours. Deux appels OnBeginAnalysis et deux `OnEndAnalysis` signifient que les deux phases se sont terminées.

Tous les membres de la structure `ANALYSIS_CALLBACKS` doivent pointer vers une fonction valide. Pour plus d’informations sur les signatures de fonction acceptées, consultez [OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)et [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
