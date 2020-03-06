---
title: Thread (classe)
description: Référence C++ de classe de thread SDK de build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Thread
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a74eb130bd3f8be949fef0c19d545f61a72f3934
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332963"
---
# <a name="thread-class"></a>Thread (classe)

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `Thread` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement de [thread](../event-table.md#thread) .

## <a name="syntax"></a>Syntaxe

```cpp
class Thread : public Activity
{
public:
    Thread(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la classe `Thread` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Thread](#thread)

## <a name="thread"></a>Thread

```cpp
Thread(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement de [thread](../event-table.md#thread) .

::: moniker-end
