---
title: MakeDynamicAnalyzerGroup
description: La référence de fonction CMD Build Insights SDK MakeDynamicAnalyzerGroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 148eeea41f29ac6dd75653feed7f3f3f8c301911
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323959"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `MakeDynamicAnalyzerGroup` fonction est utilisée pour créer un groupe d’analyseur dynamique. Les membres d’un groupe d’analyseurs reçoivent des événements un par un de gauche à droite, jusqu’à ce que tous les événements d’une trace soient analysés.

## <a name="syntax"></a>Syntaxe

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>Paramètres

*Analyseurs*\
Un vecteur de pointeurs [IAnalyzer](../other-types/ianalyzer-class.md) inclus dans le groupe d’analyseur dynamique. Ces pointeurs peuvent `std::unique_ptr`être `std::shared_ptr`bruts, , ou .

### <a name="return-value"></a>Valeur de retour

Un groupe d’analyseur dynamique. Utilisez le mot clé **automatique** pour capturer la valeur de retour.

## <a name="remarks"></a>Notes

Contrairement aux groupes d’analyseurs statiques, les membres d’un groupe d’analyseur dynamique n’ont pas besoin d’être connus au moment de la compilation. Vous pouvez choisir les membres du groupe d’analyseur au moment de l’exécution en fonction de l’entrée du programme, ou en fonction d’autres valeurs qui sont inconnues au moment de la compilation. Contrairement aux groupes d’analyseurs statiques, les pointeurs [IAnalyzer](../other-types/ianalyzer-class.md) au sein d’un groupe d’analyseur dynamique ont un comportement polymorphe, et les appels de fonction virtuelle sont expédiés correctement. Cette flexibilité se fait au prix d’un temps de traitement des événements peut-être plus lent. Lorsque tous les membres du groupe d’analyseurs sont connus au moment de la compilation, et si vous n’avez pas besoin d’un comportement polymorphe, envisagez d’utiliser un groupe d’analyseur statique. Pour utiliser un groupe d’analyseur statique, appelez [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) à la place.

Un groupe d’analyseur dynamique peut être encapsulé à l’intérieur d’un groupe d’analyseur statique. Il est fait en passant son adresse à [MakeStaticAnalyzerGroup](make-static-analyzer-group.md). Utilisez cette technique pour passer des groupes d’analyseur dynamiques à des fonctions telles que [Analyze](analyze.md), qui n’acceptent que les groupes d’analyseurs statiques.

::: moniker-end
