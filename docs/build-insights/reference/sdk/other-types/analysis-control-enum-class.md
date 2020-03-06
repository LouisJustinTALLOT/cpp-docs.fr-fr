---
title: Classe d’énumération AnalysisControl
description: Référence C++ de l’énumération AnalysisControl du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cf162c11e0a7109b8d733dab79df80782398e14d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332501"
---
# <a name="analysiscontrol-enum-class"></a>Classe d’énumération AnalysisControl

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe d’énumération `AnalysisControl` est utilisée pour contrôler le déroulement d’une session d’analyse ou de rejournalisation. Retournez un `AnalysisControl` code à partir d’une fonction membre [IAnalyzer](ianalyzer-class.md) ou [IRelogger](irelogger-class.md) pour contrôler ce qui doit se passer ensuite.

## <a name="members"></a>Membres

|  |  |
|--|--|
| `BLOCK` | Empêche l’événement actuel de se propager plus loin dans l’analyseur ou le groupe de rejournalisation. |
| `CANCEL` | Annulez la session d’analyse ou de rejournalisation en cours. |
| `CONTINUE` | Poursuivez normalement la session d’analyse ou de rejournalisation actuelle. Propage l’événement actuel au membre de l’analyseur ou du groupe de rejournalisation suivant. |
| `FAILURE` | Annulez l’analyse actuelle ou la session de rejournalisation et signalez une erreur. |

::: moniker-end
