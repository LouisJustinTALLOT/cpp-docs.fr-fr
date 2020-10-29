---
title: SimpleEvent, classe
description: Référence de la classe SimpleEvent du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SimpleEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dc09a279157482089adedc660395feaa98376dae
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923004"
---
# <a name="simpleevent-class"></a>SimpleEvent, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `SimpleEvent` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre n’importe quel événement simple. Reportez-vous à la [table des événements](../event-table.md) pour afficher tous les événements qui peuvent être mis en correspondance par la `SimpleEvent` classe.

## <a name="syntax"></a>Syntaxe

```cpp
class SimpleEvent : public Event
{
public:
    SimpleEvent(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base d' [événement](event.md) , la `SimpleEvent` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[SimpleEvent](#simple-event)

## <a name="simpleevent"></a><a name="simple-event"></a> SimpleEvent

```cpp
SimpleEvent(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Tout événement simple.

::: moniker-end
