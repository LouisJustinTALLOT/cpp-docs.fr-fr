---
title: Classe d’énumération AnalysisControl
description: Référence de l’énumération AnalysisControl du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a7b7fc0ce404f414b3ec07449bdc110d578fa101
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042015"
---
# <a name="analysiscontrol-enum-class"></a>Classe d’énumération AnalysisControl

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `AnalysisControl` classe enum est utilisée pour contrôler le déroulement d’une session d’analyse ou de rejournalisation. Retournez un `AnalysisControl` code à partir d’une fonction membre [IAnalyzer](ianalyzer-class.md) ou [IRelogger](irelogger-class.md) pour contrôler ce qui doit se passer ensuite.

## <a name="members"></a>Membres

| Nom | Description |
|--|--|
| `BLOCK` | Empêche l’événement actuel de se propager plus loin dans l’analyseur ou le groupe de rejournalisation. |
| `CANCEL` | Annulez la session d’analyse ou de rejournalisation en cours. |
| `CONTINUE` | Poursuivez normalement la session d’analyse ou de rejournalisation actuelle. Propage l’événement actuel au membre de l’analyseur ou du groupe de rejournalisation suivant. |
| `FAILURE` | Annulez l’analyse actuelle ou la session de rejournalisation et signalez une erreur. |

::: moniker-end
