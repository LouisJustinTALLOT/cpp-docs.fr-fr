---
title: Thread (classe)
description: Référence de classe de thread SDK C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Thread
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a483536281aaa87a169a40473fe3f0c4ad10bc96
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922942"
---
# <a name="thread-class"></a>Thread (classe)

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `Thread` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement de [thread](../event-table.md#thread) .

## <a name="syntax"></a>Syntaxe

```cpp
class Thread : public Activity
{
public:
    Thread(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la `Thread` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Thread](#thread)

## <a name="thread"></a><a name="thread"></a> Thread

```cpp
Thread(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement de [thread](../event-table.md#thread) .

::: moniker-end
