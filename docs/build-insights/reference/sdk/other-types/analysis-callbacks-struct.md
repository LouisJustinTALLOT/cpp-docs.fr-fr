---
title: Structure ANALYSIS_CALLBACKS
description: Le kit de développement logiciel (SDK) C++ Build Insights ANALYSIS_CALLBACKS référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3fae97370ff9366ffc2fbd8d046a73c30125e554
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919928"
---
# <a name="analysis_callbacks-structure"></a>Structure ANALYSIS_CALLBACKS

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `ANALYSIS_CALLBACKS` structure est utilisée lors de l’initialisation d’un objet [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) ou [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Elle spécifie les fonctions à appeler lors de l’analyse ou de la reconnexion d’une trace de Suivi d’v nements pour Windows (ETW).

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

| Nom | Description |
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

La phase d’analyse d’une session de rejournalisation est considérée comme faisant partie de la session de rejournalisation et peut contenir plusieurs passes d’analyse. Pour cette raison, `OnBeginAnalysis` est appelé deux fois dans une ligne au début d’une session de rejournalisation. `OnEndAnalysis` est appelé à la fin de la phase d’analyse, avant de commencer la phase de rejournalisation, et une nouvelle fois à la fin de la phase de reconnexion. La phase de rejournalisation contient toujours une seule passe de reconnexion.

Il est possible que les analyseurs fassent partie de l’analyse et de la phase de rejournalisation d’une session de rejournalisation. Ces analyseurs peuvent déterminer la phase en cours en effectuant le suivi des paires OnBeginAnalysis et `OnEndAnalysis` Call. Deux `OnBeginAnalysis` appels sans `OnEndAnalysis` appel signifient que la phase d’analyse est en cours. Deux `OnBeginAnalysis` appels et un `OnEndAnalysis` appel signifie que la phase de reconnexion est en cours. Deux appels OnBeginAnalysis et deux `OnEndAnalysis` signifient que les deux phases se sont terminées.

Tous les membres de la `ANALYSIS_CALLBACKS` structure doivent pointer vers une fonction valide. Pour plus d’informations sur les signatures de fonction acceptées, consultez [OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)et [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
