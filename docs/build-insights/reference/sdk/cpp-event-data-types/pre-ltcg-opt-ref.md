---
title: PreLTCGOptRef, classe
description: Référence C++ de la classe PreLTCGOptRef du kit de développement logiciel (SDK) Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- PreLTCGOptRef
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4690feddcf615a82226ce5ad2f3ee242749db04a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333068"
---
# <a name="preltcgoptref-class"></a>PreLTCGOptRef, classe

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La classe `PreLTCGOptRef` est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [PRE_LTCG_OPT_REF](../event-table.md#pre-ltcg-opt-ref) .

## <a name="syntax"></a>Syntaxe

```cpp
class PreLTCGOptRef : public Activity
{
public:
    PreLTCGOptRef(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la classe `PreLTCGOptRef` contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[PreLTCGOptRef](#pre-ltcg-opt-ref)

## <a name="pre-ltcg-opt-ref"></a>PreLTCGOptRef

```cpp
PreLTCGOptRef(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*event*\
Événement [PRE_LTCG_OPT_REF](../event-table.md#pre-ltcg-opt-ref) .

::: moniker-end
