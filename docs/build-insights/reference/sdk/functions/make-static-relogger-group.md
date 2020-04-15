---
title: MakeStaticReloggerGroup
description: La référence de fonction CMD Build Insights SDK MakeStaticReloggerGroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75b638537cb8e0cdeeb5476a3f5277e8e90d9baf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323910"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `MakeStaticReloggerGroup` fonction est utilisée pour créer un groupe de relogger statique qui peut être transmis à des fonctions telles que [Relog](relog.md). Les membres d’un groupe de relogger reçoivent des événements un par un de gauche à droite jusqu’à ce que tous les événements dans une trace aient été traités.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Paramètres

*TReloggerPtrs*\
Ce paramètre est toujours déduit.

*reloggers*\
Un pack de paramètres de pointeurs [IRelogger](../other-types/irelogger-class.md) qui est inclus dans le groupe relogger statique. Ces pointeurs peuvent `std::unique_ptr`être `std::shared_ptr`bruts, , ou . Les pointeurs [IAnalyzer](../other-types/ianalyzer-class.md) sont également considérés comme `IRelogger` des pointeurs en raison d’une relation d’héritage.

### <a name="return-value"></a>Valeur de retour

Un groupe de relogger statique. Utilisez le mot clé **automatique** pour capturer la valeur de retour.

## <a name="remarks"></a>Notes

Contrairement aux groupes dynamiques de relogger, les membres d’un groupe de relogger statique doivent être connus au moment de la compilation. En outre, un groupe de relogger statique contient des pointeurs [IRelogger](../other-types/irelogger-class.md) qui n’ont pas de comportement polymorphe. Lorsque vous utilisez un groupe de relogger statique pour analyser une `IRelogger` trace de traçage d’événements pour Windows (ETW), les appels à l’interface se résolvent toujours à l’objet directement indiqué par le membre du groupe relogger. Cette perte de flexibilité est accompagnée d’une possibilité de temps de traitement des événements plus rapides. Si les membres d’un groupe de relogger ne peuvent pas être connus au `IRelogger` moment de la compilation, ou si vous avez besoin d’un comportement polymorphe sur vos pointeurs, envisagez d’utiliser un groupe dynamique de relogger. Vous pouvez utiliser un groupe dynamique de relogger en appelant [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md) à la place.

::: moniker-end
