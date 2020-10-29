---
title: BottomUp, classe
description: Référence de la classe BottomUp du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BottomUp
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4fb5d9165837484477044f200e5a17da0e678e32
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923383"
---
# <a name="bottomup-class"></a>BottomUp, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `BottomUp` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [BOTTOM_UP](../event-table.md#bottom-up) .

## <a name="syntax"></a>Syntaxe

```cpp
class BottomUp : public Activity
{
public:
    BottomUp(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la `BottomUp` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[BottomUp](#bottom-up)

## <a name="bottomup"></a><a name="bottom-up"></a> BottomUp

```cpp
BottomUp(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [BOTTOM_UP](../event-table.md#bottom-up) .

::: moniker-end
