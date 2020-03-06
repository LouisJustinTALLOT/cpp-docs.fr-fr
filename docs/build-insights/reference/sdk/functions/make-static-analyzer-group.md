---
title: MakeStaticAnalyzerGroup
description: Référence C++ de la fonction MakeStaticAnalyzerGroup du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5eabb0fcbb0a0bb0eea0f4e6bbf27b8e4c53c3ab
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332816"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La fonction `MakeStaticAnalyzerGroup` est utilisée pour créer un groupe d’analyseurs statiques qui peut être passé à des fonctions telles que [analyze](analyze.md) ou [relog](relog.md). Les membres d’un groupe d’analyseur reçoivent les événements un par un de gauche à droite, jusqu’à ce que tous les événements d’une trace soient analysés.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>Paramètres

*TAnalyzerPtrs*\
Ce paramètre est toujours déduit.

*analyseurs*\
Un jeu de paramètres de pointeurs [IAnalyzer](../other-types/ianalyzer-class.md) inclus dans le groupe de l’analyseur statique. Ces pointeurs peuvent être RAW, `std::unique_ptr`ou `std::shared_ptr`.

### <a name="return-value"></a>Valeur de retour

Un groupe d’analyseur statique. Utilisez le mot clé **auto** pour capturer la valeur de retour.

## <a name="remarks"></a>Notes

Contrairement aux groupes d’analyseurs dynamiques, les membres d’un groupe d’analyseurs statiques doivent être connus au moment de la compilation. En outre, un groupe d’analyseurs statiques contient des pointeurs [IAnalyzer](../other-types/ianalyzer-class.md) qui n’ont pas de comportement polymorphe. Lors de l’utilisation d’un groupe d’analyseurs statiques pour analyser une trace Suivi d’v nements pour Windows (ETW), les appels à l’interface `IAnalyzer` sont toujours résolus en objet directement pointé par le membre du groupe de l’analyseur. Cette perte de flexibilité est une possibilité de temps de traitement des événements plus rapide. Si les membres d’un groupe d’analyseur ne peuvent pas être connus au moment de la compilation, ou si vous avez besoin d’un comportement polymorphe sur vos pointeurs de `IAnalyzer`, envisagez d’utiliser un groupe d’analyseurs dynamiques. Pour utiliser un groupe d’analyseur dynamique, appelez [MakeDynamicAnalyzerGroup](make-static-analyzer-group.md) à la place.

::: moniker-end
