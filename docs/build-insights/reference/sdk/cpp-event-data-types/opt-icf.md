---
title: Classe OptICF
description: La référence de classe CMD Build Insights SDK OptICF.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptICF
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f63fea61f9defc216390fa377b2d1eeace01371b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324474"
---
# <a name="opticf-class"></a>Classe OptICF

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `OptICF` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement OPT_ICF.](../event-table.md#opt-icf)

## <a name="syntax"></a>Syntaxe

```cpp
class OptICF : public Activity
{
public:
    OptICF(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa `OptICF` classe de base [d’activité,](activity.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[OptICF (optICF)](#opt-icf)

## <a name="opticf"></a><a name="opt-icf"></a>OptICF (optICF)

```cpp
OptICF(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement OPT_ICF.](../event-table.md#opt-icf)

::: moniker-end
