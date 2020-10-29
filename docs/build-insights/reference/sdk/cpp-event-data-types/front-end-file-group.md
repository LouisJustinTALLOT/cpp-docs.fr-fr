---
title: FrontEndFileGroup, classe
description: Référence de la classe FrontEndFileGroup du kit de développement logiciel (SDK) C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 902b394f645030fed4eeb79bae79535e6d246a1f
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923226"
---
# <a name="frontendfilegroup-class"></a>FrontEndFileGroup, classe

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `FrontEndFileGroup` classe est utilisée avec les fonctions [MatchEventStack](../functions/match-event-stack.md) et [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Utilisez-le pour faire correspondre des groupes d’événements [FRONT_END_FILE](../event-table.md#front-end-file) .

## <a name="syntax"></a>Syntaxe

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa classe de base [EventGroup \<FrontEndFile\> ](event-group.md) , la `FrontEndFileGroup` classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[FrontEndFileGroup](#front-end-file-group)

## <a name="frontendfilegroup"></a><a name="front-end-file-group"></a> FrontEndFileGroup

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>Paramètres

*Communauté*\
Groupe d’événements de [FRONT_END_FILE](../event-table.md#front-end-file) .

::: moniker-end
