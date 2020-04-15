---
title: MakeDynamicReloggerGroup
description: La référence de fonction CMD Build Insights SDK MakeDynamicReloggerGroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f49e37f8e1a8b9ca9a800d20b2891a54453095ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323953"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `MakeDynamicReloggerGroup` fonction est utilisée pour créer un groupe dynamique de relogger. Les membres d’un groupe de relogger reçoivent des événements un par un de gauche à droite jusqu’à ce que tous les événements dans une trace aient été traités.

## <a name="syntax"></a>Syntaxe

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>Paramètres

*reloggers*\
Un vecteur de pointeurs [IRelogger](../other-types/irelogger-class.md) inclus dans le groupe dynamique relogger. Ces pointeurs peuvent `std::unique_ptr`être `std::shared_ptr`bruts, , ou . Les pointeurs [IAnalyzer](../other-types/ianalyzer-class.md) sont également considérés comme `IRelogger` des pointeurs en raison d’une relation d’héritage.

### <a name="return-value"></a>Valeur de retour

Un groupe dynamique de relogger. Utilisez le mot clé **automatique** pour capturer la valeur de retour.

## <a name="remarks"></a>Notes

Contrairement aux groupes de relogger statiques, les membres d’un groupe dynamique de relogger n’ont pas besoin d’être connus au moment de la compilation. Vous pouvez choisir les membres du groupe relogger au moment de l’exécution en fonction de l’entrée du programme, ou en fonction d’autres valeurs qui sont inconnues au moment de la compilation. Contrairement aux groupes de relogger statiques, les pointeurs [IRelogger](../other-types/irelogger-class.md) au sein d’un groupe dynamique de relogger ont un comportement polymorphe, et les appels de fonction virtuelle sont expédiés correctement. Cette flexibilité se fait au prix d’un temps de traitement des événements peut-être plus lent. Lorsque tous les membres du groupe relogger sont connus au moment de la compilation, et si vous n’avez pas besoin d’un comportement polymorphe, envisagez d’utiliser un groupe de relogger statique. Pour utiliser un groupe de relogger statique, appelez [MakeStaticReloggerGroup](make-static-relogger-group.md) à la place.

Un groupe dynamique de rélogger peut être encapsulé à l’intérieur d’un groupe de rélogger statique. Vous passez son adresse à [MakeStaticReloggerGroup](make-static-relogger-group.md). Utilisez cette technique pour passer des groupes dynamiques relogger à des fonctions telles que [Relog](relog.md), qui n’acceptent que les groupes de relogger statique.

::: moniker-end
