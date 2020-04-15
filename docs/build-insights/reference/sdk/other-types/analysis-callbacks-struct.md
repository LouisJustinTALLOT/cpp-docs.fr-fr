---
title: structure ANALYSIS_CALLBACKS
description: La référence de structure de construction SDK ANALYSIS_CALLBACKS de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c6de999b19657f999f884075ee53e21a4d2f2b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323502"
---
# <a name="analysis_callbacks-structure"></a>structure ANALYSIS_CALLBACKS

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `ANALYSIS_CALLBACKS` structure est utilisée lors de l’initialisation d’un [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) ou [d’un](relog-descriptor-struct.md) objet RELOG_DESCRIPTOR. Il précise quelles fonctions appeler lors de l’analyse ou le réinquage d’une trace de traçage d’événements pour Windows (ETW).

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
| `OnStartActivity` | Appelé à traiter un événement de début d’activité. |
| `OnStopActivity` | Appelé à traiter un événement d’arrêt d’activité. |
| `OnSimpleEvent` | Appelé à traiter un événement simple. |
| `OnTraceInfo` | Pour les séances d’analyse, appelées au début de chaque passage d’analyse. Pour les sessions de rélogging, appelées au début de chaque passage d’analyse, et encore au début du laissez-passer de rélogging. Cette fonction n’est appelée qu’après l’appel d’OnBeginAnalysisPass. |
| `OnBeginAnalysis` | Pour les séances d’analyse, appelées avant le début de toute analyse. Pour les sessions de rélogging, convoquées deux fois avant le début de la phase d’analyse : une fois pour annoncer le début de la session de réinstruation, et une fois de plus pour annoncer le début de la phase d’analyse. |
| `OnEndAnalysis` | Pour les sessions d’analyse, cette fonction est appelée après que toutes les passes d’analyse ont pris fin. Pour les sessions de rélogging, cette fonction est appelée lorsque toutes les analyses passent de la phase d’analyse ont pris fin. Puis, il est appelé à nouveau après la passe de relogging a pris fin. |
| `OnBeginAnalysisPass` | Appelé lors du début d’une passe d’analyse ou le passage de rélogging, avant de traiter tout événement. |
| `OnEndAnalysisPass` | Appelé lors de la fin d’une passe d’analyse ou le passage de rélogging, après traitement de tous les événements. |

## <a name="remarks"></a>Notes

La phase d’analyse d’une session de réinstruation est considérée comme faisant partie de la session de réinstruation et peut contenir plusieurs laissez-passer d’analyse. Pour cette `OnBeginAnalysis` raison, est appelé deux fois de suite au début d’une session de relogging. `OnEndAnalysis`est appelé à la fin de la phase d’analyse, avant de commencer la phase de rélogging, et une fois de plus à la fin de la phase de rélogging. La phase de relogging contient toujours un seul laissez-passer de relogging.

Il est possible pour les analyseurs de faire partie à la fois de l’analyse et de la phase de rélogging d’une session de rélogging. Ces analyseurs peuvent déterminer quelle phase est actuellement en cours en `OnEndAnalysis` gardant une trace des paires d’onBeginAnalysis et d’appels. Deux `OnBeginAnalysis` appels `OnEndAnalysis` sans appel signifie que la phase d’analyse est en cours. Deux `OnBeginAnalysis` appels `OnEndAnalysis` et un appel signifie que la phase de rélogging est en cours. Deux OnBeginAnalysis `OnEndAnalysis` et deux appels signifient que les deux phases ont pris fin.

Tous les `ANALYSIS_CALLBACKS` membres de la structure doivent indiquer une fonction valide. Pour plus d’informations sur les signatures de fonction acceptées, voir [OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md), et [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
