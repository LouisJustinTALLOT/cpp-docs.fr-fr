---
title: BottomUp, classe
description: Référence C++ de la classe bottomup du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BottomUp
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fa26acfdf25acc3b78de71fd21b20cbf5a0df66b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333537"
---
# <a name="bottomup-class"></a>BottomUp, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `BottomUp` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [BOTTOM_UP](../event-table.md#bottom-up) .

## <a name="syntax"></a>Syntaxe

```cpp
class BottomUp : public Activity
{
public:
    BottomUp(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la classe `BottomUp` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[BottomUp](#bottom-up)

## <a name="bottom-up"></a>BottomUp

```cpp
BottomUp(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [BOTTOM_UP](../event-table.md#bottom-up) .

::: moniker-end
