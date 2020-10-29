---
title: OptICF, classe
description: Référence de la classe OptICF du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptICF
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b816b53e1054c4492320bdb71f2f0c7726907cf4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920526"
---
# <a name="opticf-class"></a>OptICF, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `OptICF` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [OPT_ICF](../event-table.md#opt-icf) .

## <a name="syntax"></a>Syntaxe

```cpp
class OptICF : public Activity
{
public:
    OptICF(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la `OptICF` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[OptICF](#opt-icf)

## <a name="opticf"></a><a name="opt-icf"></a> OptICF

```cpp
OptICF(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [OPT_ICF](../event-table.md#opt-icf) .

::: moniker-end
