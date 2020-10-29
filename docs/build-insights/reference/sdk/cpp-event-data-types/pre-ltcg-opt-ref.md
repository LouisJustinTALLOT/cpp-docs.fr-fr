---
title: PreLTCGOptRef, classe
description: Référence de la classe PreLTCGOptRef du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- PreLTCGOptRef
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6786e317f0221126ec6e15c50f3fad58c5982266
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923011"
---
# <a name="preltcgoptref-class"></a>PreLTCGOptRef, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `PreLTCGOptRef` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre un événement [PRE_LTCG_OPT_REF](../event-table.md#pre-ltcg-opt-ref) .

## <a name="syntax"></a>Syntaxe

```cpp
class PreLTCGOptRef : public Activity
{
public:
    PreLTCGOptRef(const RawEvent& event);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [Activity](activity.md) , la `PreLTCGOptRef` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[PreLTCGOptRef](#pre-ltcg-opt-ref)

## <a name="preltcgoptref"></a><a name="pre-ltcg-opt-ref"></a> PreLTCGOptRef

```cpp
PreLTCGOptRef(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*événement*\
Événement [PRE_LTCG_OPT_REF](../event-table.md#pre-ltcg-opt-ref) .

::: moniker-end
