---
title: MakeDynamicAnalyzerGroup
description: Référence C++ de la fonction MakeDynamicAnalyzerGroup du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f409d685c6af6514b73cd837d668a962c1a0d01a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332830"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La fonction `MakeDynamicAnalyzerGroup` est utilisée pour créer un groupe d’analyseur dynamique. Les membres d’un groupe d’analyseur reçoivent les événements un par un de gauche à droite, jusqu’à ce que tous les événements d’une trace soient analysés.

## <a name="syntax"></a>Syntaxe

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>Paramètres

*analyseurs*\
Vecteur de pointeurs [IAnalyzer](../other-types/ianalyzer-class.md) inclus dans le groupe de l’analyseur dynamique. Ces pointeurs peuvent être RAW, `std::unique_ptr`ou `std::shared_ptr`.

### <a name="return-value"></a>Valeur de retour

Un groupe d’analyseur dynamique. Utilisez le mot clé **auto** pour capturer la valeur de retour.

## <a name="remarks"></a>Notes

Contrairement aux groupes d’analyseurs statiques, les membres d’un groupe analyseur dynamique n’ont pas besoin d’être connus au moment de la compilation. Vous pouvez choisir des membres de groupe d’analyseur au moment de l’exécution en fonction de l’entrée de programme, ou en fonction d’autres valeurs qui sont inconnues au moment de la compilation. Contrairement aux groupes d’analyseurs statiques, les pointeurs [IAnalyzer](../other-types/ianalyzer-class.md) dans un groupe d’analyseur dynamique ont un comportement polymorphe et les appels de fonction virtuelle sont distribués correctement. Cette flexibilité se situe au détriment d’un temps de traitement des événements potentiellement plus lent. Lorsque tous les membres du groupe analyseur sont connus au moment de la compilation et, si vous n’avez pas besoin d’un comportement polymorphe, envisagez d’utiliser un groupe d’analyseurs statiques. Pour utiliser un groupe d’analyseurs statiques, appelez [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) à la place.

Un groupe d’analyseur dynamique peut être encapsulé dans un groupe d’analyseurs statiques. Pour ce faire, vous pouvez passer son adresse à [MakeStaticAnalyzerGroup](make-static-analyzer-group.md). Utilisez cette technique pour passer des groupes d’analyseurs dynamiques à des fonctions telles que l' [analyse](analyze.md), qui acceptent uniquement des groupes d’analyseurs statiques.

::: moniker-end
