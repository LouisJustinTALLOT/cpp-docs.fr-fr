---
title: MakeStaticReloggerGroup
description: Référence de la fonction MakeStaticReloggerGroup du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b74ee778ffafbcb4c292b4b36b309d5ff4d66c27
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224160"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `MakeStaticReloggerGroup` fonction est utilisée pour créer un groupe de rejournalisation statique qui peut être passé à des fonctions telles que [relog](relog.md). Les membres d’un groupe de rejournalisation reçoivent les événements un par un de gauche à droite jusqu’à ce que tous les événements d’une trace aient été traités.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Paramètres

*TReloggerPtrs*\
Ce paramètre est toujours déduit.

*rejournalisation*\
Un pack de paramètres de [`IRelogger`](../other-types/irelogger-class.md) pointeurs inclus dans le groupe de rejournalisation statique. Ces pointeurs peuvent être RAW, `std::unique_ptr` ou `std::shared_ptr` . [`IAnalyzer`](../other-types/ianalyzer-class.md)les pointeurs sont également considérés comme `IRelogger` des pointeurs en raison d’une relation d’héritage.

### <a name="return-value"></a>Valeur de retour

Groupe de rejournalisation statique. Utilisez le **`auto`** mot clé pour capturer la valeur de retour.

## <a name="remarks"></a>Notes

Contrairement aux groupes de rejournalisation dynamiques, les membres d’un groupe de rejournalisation statique doivent être connus au moment de la compilation. En outre, un groupe de rejournalisation statique contient [`IRelogger`](../other-types/irelogger-class.md) des pointeurs qui n’ont pas de comportement polymorphe. Lors de l’utilisation d’un groupe de rejournalisation statique pour analyser une trace Suivi d’v nements pour Windows (ETW), les appels à l' `IRelogger` interface sont toujours résolus à l’objet directement pointé par le membre du groupe de rejournalisation. Cette perte de flexibilité est une possibilité de temps de traitement des événements plus rapide. Si les membres d’un groupe de rejournalisation ne peuvent pas être connus au moment de la compilation, ou si vous avez besoin d’un comportement polymorphe sur vos `IRelogger` pointeurs, envisagez d’utiliser un groupe de rejournalisation dynamique. Vous pouvez utiliser un groupe de rejournalisation dynamique en appelant à la [`MakeDynamicReloggerGroup`](make-dynamic-relogger-group.md) place.

::: moniker-end
