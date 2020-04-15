---
title: AnalyseContrôle enum classe
description: La référence enum de build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e9431f878390127f2cefbe8f0ee42ca509e147de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323642"
---
# <a name="analysiscontrol-enum-class"></a>AnalyseContrôle enum classe

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `AnalysisControl` classe enum est utilisée pour contrôler le flux d’une session d’analyse ou de relogging. Retournez `AnalysisControl` un code d’une fonction de membre [IAnalyzer](ianalyzer-class.md) ou [IRelogger](irelogger-class.md) pour contrôler ce qui devrait se passer ensuite.

## <a name="members"></a>Membres

|  |  |
|--|--|
| `BLOCK` | Empêche l’événement actuel de se propager davantage dans le groupe d’analyseur ou de rélogger. |
| `CANCEL` | Annuler l’analyse en cours ou la session de relogging. |
| `CONTINUE` | Poursuivez l’analyse actuelle ou reloggingez la session normalement. Propagez l’événement actuel au prochain membre du groupe d’analyseur ou de relogger. |
| `FAILURE` | Annuler l’analyse en cours ou la session de relogging et signaler une erreur. |

::: moniker-end
