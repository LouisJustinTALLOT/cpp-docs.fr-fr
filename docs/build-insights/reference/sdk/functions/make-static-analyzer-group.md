---
title: MakeStaticAnalyzerGroup
description: La référence de fonction CMD Build Insights SDK MakeStaticAnalyzerGroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72f7f5d7a408436902394451a52dd66efe1d93f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323943"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `MakeStaticAnalyzerGroup` fonction est utilisée pour créer un groupe d’analyseur statique qui peut être transmis à des fonctions telles que [Analyze](analyze.md) ou [Relog](relog.md). Les membres d’un groupe d’analyseurs reçoivent des événements un par un de gauche à droite, jusqu’à ce que tous les événements d’une trace soient analysés.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>Paramètres

*TAnalyzerPtrs*\
Ce paramètre est toujours déduit.

*Analyseurs*\
Un pack de paramètres de pointeurs [IAnalyzer](../other-types/ianalyzer-class.md) inclus dans le groupe d’analyseur statique. Ces pointeurs peuvent `std::unique_ptr`être `std::shared_ptr`bruts, , ou .

### <a name="return-value"></a>Valeur de retour

Un groupe d’analyseur statique. Utilisez le mot clé **automatique** pour capturer la valeur de retour.

## <a name="remarks"></a>Notes

Contrairement aux groupes d’analyseurs dynamiques, les membres d’un groupe d’analyseur statique doivent être connus au moment de la compilation. En outre, un groupe d’analyseur statique contient des pointeurs [IAnalyzer](../other-types/ianalyzer-class.md) qui n’ont pas de comportement polymorphe. Lorsque vous utilisez un groupe d’analyseur statique pour analyser une `IAnalyzer` trace de traçage d’événements pour Windows (ETW), les appels à l’interface se résolvent toujours à l’objet directement indiqué par le membre du groupe d’analyseur. Cette perte de flexibilité est accompagnée d’une possibilité de temps de traitement des événements plus rapides. Si les membres d’un groupe d’analyseurs ne peuvent pas être connus au `IAnalyzer` moment de la compilation, ou si vous avez besoin d’un comportement polymorphe sur vos pointeurs, envisagez d’utiliser un groupe d’analyseur dynamique. Pour utiliser un groupe d’analyseur dynamique, appelez [MakeDynamicAnalyzerGroup](make-static-analyzer-group.md) à la place.

::: moniker-end
