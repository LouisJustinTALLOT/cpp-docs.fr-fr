---
title: OptLBR, classe
description: Référence de la classe OptLBR du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptLBR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5505e50b0acd961a1ff745eee36419bbaa4bd601
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923050"
---
# <a name="optlbr-class"></a>OptLBR, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `OptLBR` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [OPT_LBR](../event-table.md#opt-lbr) .

## <a name="syntax"></a>Syntaxe

```cpp
class OptLBR : public Activity
{
public:
    OptLBR(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la `OptLBR` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[OptLBR](#opt-lbr)

## <a name="optlbr"></a><a name="opt-lbr"></a> OptLBR

```cpp
OptLBR(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [OPT_LBR](../event-table.md#opt-lbr) .

::: moniker-end
