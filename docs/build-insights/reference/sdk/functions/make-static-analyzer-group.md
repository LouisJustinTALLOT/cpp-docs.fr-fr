---
title: MakeStaticAnalyzerGroup
description: Référence de la fonction MakeStaticAnalyzerGroup du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d7ddb8652400438c38882b1d27e635e8f1e8db51
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920240"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `MakeStaticAnalyzerGroup` fonction est utilisée pour créer un groupe d’analyseur statique qui peut être passé à des fonctions telles que [`Analyze`](analyze.md) ou [`Relog`](relog.md) . Les membres d’un groupe d’analyseur reçoivent les événements un par un de gauche à droite, jusqu’à ce que tous les événements d’une trace soient analysés.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>Paramètres

*TAnalyzerPtrs*\
Ce paramètre est toujours déduit.

*analyseurs*\
Un jeu de paramètres de [`IAnalyzer`](../other-types/ianalyzer-class.md) pointeurs inclus dans le groupe de l’analyseur statique. Ces pointeurs peuvent être RAW, `std::unique_ptr` ou `std::shared_ptr` .

### <a name="return-value"></a>Valeur de retour

Un groupe d’analyseur statique. Utilisez le **`auto`** mot clé pour capturer la valeur de retour.

## <a name="remarks"></a>Notes

Contrairement aux groupes d’analyseurs dynamiques, les membres d’un groupe d’analyseurs statiques doivent être connus au moment de la compilation. En outre, un groupe d’analyseurs statiques contient [`IAnalyzer`](../other-types/ianalyzer-class.md) des pointeurs qui n’ont pas de comportement polymorphe. Lorsque vous utilisez un groupe d’analyseurs statiques pour analyser une trace Suivi d’v nements pour Windows (ETW), les appels à l' `IAnalyzer` interface sont toujours résolus en objet directement pointé par le membre du groupe de l’analyseur. Cette perte de flexibilité est une possibilité de temps de traitement des événements plus rapide. Si les membres d’un groupe d’analyseur ne peuvent pas être connus au moment de la compilation, ou si vous avez besoin d’un comportement polymorphe sur vos `IAnalyzer` pointeurs, envisagez d’utiliser un groupe d’analyseurs dynamiques. Pour utiliser un groupe d’analyseur dynamique, appelez à la [`MakeDynamicAnalyzerGroup`](make-static-analyzer-group.md) place.

::: moniker-end
