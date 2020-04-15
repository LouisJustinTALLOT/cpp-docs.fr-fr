---
title: Classe OptLBR
description: La référence de classe CMD Build Insights SDK OptLBR.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptLBR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4cbd87134741d6fc09521f94bfdfbc099cb426a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324457"
---
# <a name="optlbr-class"></a>Classe OptLBR

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `OptLBR` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement OPT_LBR.](../event-table.md#opt-lbr)

## <a name="syntax"></a>Syntaxe

```cpp
class OptLBR : public Activity
{
public:
    OptLBR(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa `OptLBR` classe de base [d’activité,](activity.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[OptLBR (OptLBR)](#opt-lbr)

## <a name="optlbr"></a><a name="opt-lbr"></a>OptLBR (OptLBR)

```cpp
OptLBR(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement OPT_LBR.](../event-table.md#opt-lbr)

::: moniker-end
