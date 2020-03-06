---
title: LTCG (classe)
description: Référence C++ de la classe LTCG du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LTCG
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8e75795e46d64752fd4d1a643585cf6f131cb096
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333145"
---
# <a name="ltcg-class"></a>LTCG (classe)

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `LTCG` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [LTCG](../event-table.md#ltcg) .

## <a name="syntax"></a>Syntaxe

```cpp
class LTCG : public Activity
{
public:
    LTCG(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la classe `LTCG` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[LTCG](#ltcg)

## <a name="ltcg"></a>LTCG

```cpp
LTCG(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [LTCG](../event-table.md#ltcg) .

::: moniker-end
