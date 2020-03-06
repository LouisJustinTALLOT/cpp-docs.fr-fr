---
title: MakeStaticReloggerGroup
description: Référence C++ de la fonction MakeStaticReloggerGroup du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 06927af89b16d9de1148e555868dd2022c59b171
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332809"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La fonction `MakeStaticReloggerGroup` est utilisée pour créer un groupe de rejournalisation statique qui peut être passé à des fonctions telles que [relog](relog.md). Les membres d’un groupe de rejournalisation reçoivent les événements un par un de gauche à droite jusqu’à ce que tous les événements d’une trace aient été traités.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Paramètres

*TReloggerPtrs*\
Ce paramètre est toujours déduit.

*rejournalisation*\
Un jeu de paramètres de pointeurs [IRelogger](../other-types/irelogger-class.md) inclus dans le groupe de rejournalisation statique. Ces pointeurs peuvent être RAW, `std::unique_ptr`ou `std::shared_ptr`. Les pointeurs [IAnalyzer](../other-types/ianalyzer-class.md) sont également considérés comme des pointeurs `IRelogger` en raison d’une relation d’héritage.

### <a name="return-value"></a>Valeur de retour

Groupe de rejournalisation statique. Utilisez le mot clé **auto** pour capturer la valeur de retour.

## <a name="remarks"></a>Notes

Contrairement aux groupes de rejournalisation dynamiques, les membres d’un groupe de rejournalisation statique doivent être connus au moment de la compilation. En outre, un groupe de rejournalisation statique contient des pointeurs [IRelogger](../other-types/irelogger-class.md) qui n’ont pas de comportement polymorphe. Lors de l’utilisation d’un groupe de rejournalisation statique pour analyser une trace Suivi d’v nements pour Windows (ETW), les appels à l’interface `IRelogger` sont toujours résolus en objet directement pointé par le membre du groupe de rejournalisation. Cette perte de flexibilité est une possibilité de temps de traitement des événements plus rapide. Si les membres d’un groupe de rejournalisation ne peuvent pas être connus au moment de la compilation, ou si vous avez besoin d’un comportement polymorphe sur vos pointeurs de `IRelogger`, envisagez d’utiliser un groupe de rejournalisation dynamique. Vous pouvez utiliser un groupe de rejournalisation dynamique en appelant [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md) à la place.

::: moniker-end
