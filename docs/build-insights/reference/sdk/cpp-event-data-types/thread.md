---
title: Thread (classe)
description: La référence de classe CMD Build Insights SDK Thread.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Thread
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 397083c63f451b2d3fb8dad529adf73855af8644
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324199"
---
# <a name="thread-class"></a>Thread (classe)

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `Thread` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un événement [THREAD.](../event-table.md#thread)

## <a name="syntax"></a>Syntaxe

```cpp
class Thread : public Activity
{
public:
    Thread(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa `Thread` classe de base [d’activité,](activity.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Fil](#thread)

## <a name="thread"></a><a name="thread"></a>Fil

```cpp
Thread(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un événement [THREAD.](../event-table.md#thread)

::: moniker-end
