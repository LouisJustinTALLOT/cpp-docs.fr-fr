---
title: MakeDynamicReloggerGroup
description: Référence C++ de la fonction MakeDynamicReloggerGroup du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4ad394d3ba2982e7ee4f2a497fef2ea65a3c1769
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332823"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La fonction `MakeDynamicReloggerGroup` est utilisée pour créer un groupe de rejournalisation dynamique. Les membres d’un groupe de rejournalisation reçoivent les événements un par un de gauche à droite jusqu’à ce que tous les événements d’une trace aient été traités.

## <a name="syntax"></a>Syntaxe

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>Paramètres

*rejournalisation*\
Vecteur de pointeurs [IRelogger](../other-types/irelogger-class.md) inclus dans le groupe de rejournalisation dynamique. Ces pointeurs peuvent être RAW, `std::unique_ptr`ou `std::shared_ptr`. Les pointeurs [IAnalyzer](../other-types/ianalyzer-class.md) sont également considérés comme des pointeurs `IRelogger` en raison d’une relation d’héritage.

### <a name="return-value"></a>Valeur de retour

Un groupe de rejournalisation dynamique. Utilisez le mot clé **auto** pour capturer la valeur de retour.

## <a name="remarks"></a>Notes

Contrairement aux groupes de rejournalisation statique, les membres d’un groupe de rejournalisation dynamique n’ont pas besoin d’être connus au moment de la compilation. Vous pouvez choisir les membres du groupe de rejournalisation au moment de l’exécution en fonction de l’entrée de programme, ou en fonction d’autres valeurs qui sont inconnues au moment de la compilation. Contrairement aux groupes de rejournalisation statique, les pointeurs [IRelogger](../other-types/irelogger-class.md) dans un groupe de rejournalisation dynamique ont un comportement polymorphe et les appels de fonction virtuelle sont distribués correctement. Cette flexibilité se situe au détriment d’un temps de traitement des événements potentiellement plus lent. Lorsque tous les membres du groupe de rejournalisation sont connus au moment de la compilation et, si vous n’avez pas besoin d’un comportement polymorphe, envisagez d’utiliser un groupe de rejournalisation statique. Pour utiliser un groupe de rejournalisation statique, appelez [MakeStaticReloggerGroup](make-static-relogger-group.md) à la place.

Un groupe de rejournalisation dynamique peut être encapsulé dans un groupe de rejournalisation statique. Vous transmettez son adresse à [MakeStaticReloggerGroup](make-static-relogger-group.md). Utilisez cette technique pour passer des groupes de rejournalisation dynamiques à des fonctions telles que [relog](relog.md), qui acceptent uniquement les groupes de rejournalisation statiques.

::: moniker-end
