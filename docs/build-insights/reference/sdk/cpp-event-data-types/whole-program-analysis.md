---
title: WholeProgramAnalysis, classe
description: Référence C++ de la classe WholeProgramAnalysis du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- WholeProgramAnalysis
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6b8e41242acb9e902b250bab960b1c2042dd981a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332935"
---
# <a name="wholeprogramanalysis-class"></a>WholeProgramAnalysis, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `WholeProgramAnalysis` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis) .

## <a name="syntax"></a>Syntaxe

```cpp
class WholeProgramAnalysis : public Activity
{
public:
    WholeProgramAnalysis(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la classe `WholeProgramAnalysis` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[WholeProgramAnalysis](#whole-program-analysis)

## <a name="whole-program-analysis"></a>WholeProgramAnalysis

```cpp
WholeProgramAnalysis(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis) .

::: moniker-end
