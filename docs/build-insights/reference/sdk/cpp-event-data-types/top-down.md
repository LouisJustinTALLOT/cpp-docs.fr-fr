---
title: Classe de classe
description: Référence C++ de classe du kit de développement logiciel (SDK) de build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TopDown
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2d4ef1f2f824bca9ab8e45f8fb030727e6e4007b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332949"
---
# <a name="topdown-class"></a>Classe de classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `TopDown` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [TOP_DOWN](../event-table.md#top-down) .

## <a name="syntax"></a>Syntaxe

```cpp
class TopDown : public Activity
{
public:
    TopDown(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la classe `TopDown` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[Vers le](#top-down)

## <a name="top-down"></a>Vers le

```cpp
TopDown(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [TOP_DOWN](../event-table.md#top-down) .

::: moniker-end
